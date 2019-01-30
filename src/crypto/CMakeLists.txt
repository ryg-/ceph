add_custom_target(crypto_plugins)
set(crypto_plugin_dir ${CMAKE_INSTALL_PKGLIBDIR}/crypto)

if(CMAKE_SYSTEM_PROCESSOR MATCHES "i386|i686|amd64|x86_64|AMD64|aarch64|(powerpc|ppc)64le")
  add_subdirectory(openssl)
endif()

if(HAVE_INTEL AND HAVE_BETTER_YASM_ELF64 AND (NOT APPLE))
  add_subdirectory(isa-l)
endif()

if(WITH_QAT)
  add_subdirectory(qat)
endif()
