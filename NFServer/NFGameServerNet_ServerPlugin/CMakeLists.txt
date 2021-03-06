set(ProjectName "NFGameServerNet_ServerPlugin")
file(GLOB NFGameServerNet_ServerPlugin_ROOT_Cpp
	dllmain.cpp
	NFCGameServerNet_ServerModule.cpp
	NFGameServerNet_ServerPlugin.cpp)
file(GLOB NFGameServerNet_ServerPlugin_ROOT_Hpp 
	NFCGameServerNet_ServerModule.h
	NFGameServerNet_ServerPlugin.h)

add_library(NFGameServerNet_ServerPlugin SHARED
	${NFGameServerNet_ServerPlugin_ROOT_Cpp}
	${NFGameServerNet_ServerPlugin_ROOT_Hpp})
	
set_target_properties( NFGameServerNet_ServerPlugin PROPERTIES OUTPUT_NAME_DEBUG "NFGameServerNet_ServerPlugin_d")
set_target_properties( NFGameServerNet_ServerPlugin PROPERTIES PREFIX "")
set_target_properties( NFGameServerNet_ServerPlugin PROPERTIES 
	FOLDER "NFServer/GameServer"
	ARCHIVE_OUTPUT_DIRECTORY ${NFOutPutDir}
	RUNTIME_OUTPUT_DIRECTORY ${NFOutPutDir}
	LIBRARY_OUTPUT_DIRECTORY ${NFOutPutDir} )
link_NFSDK("NFGameServerNet_ServerPlugin")

if(UNIX)
	add_definitions(
		-D_USRDLL
		-DELPP_NO_DEFAULT_LOG_FILE
	)
	
else()
	add_definitions(
		-DWIN
		-D_USRDLL
		-DELPP_NO_DEFAULT_LOG_FILE
	)
endif()
