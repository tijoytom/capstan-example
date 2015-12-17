# Capstan Example

This is a "hello world" C# application that shows how to use Capstan to
package and run  C# CoreRT native applications on OSv.

## Prerequisites

You need to have [Capstan](https://github.com/cloudius-systems/capstan)
installed on your computer.

## Usage

To build and launch the example application under QEMU, type:

```
$ capstan run
```

This makes Capstan automatically pull a base image, invoke ``make`` to
build the software, build an image, and finally launch the application
under QEMU.

test.so : this shared library was generated using CoreRT native toolchain 

Here are the instructions to build the test.so from your C# source files 

Step1 : 

Compile to  IL and then to C#  :  dotnet compile --native -cpp
The above step should generate a test.cpp 

Step2:
Compile the generated cpp to a position independent shared library


clang-3.5 -g -lstdc++ -lrt -Wno-invalid-offsetof -shared -fPIC -pthread 
 -I /home/tijoytom/unikernel/corert/bin/tools/cli/bin/appdepsdk/CPPSdk/ubuntu.14.04 
 -I /home/tijoytom/unikernel/corert/bin/tools/cli/bin/appdepsdk/CPPSdk 
 /home/tijoytom/unikernel/corert/bin/tools/cli/bin/test/obj/Debug/dnxcore50/test.cpp 
 /home/tijoytom/unikernel/corert/bin/tools/cli/bin/appdepsdk/CPPSdk/ubuntu.14.04/lxstubs.cpp 
 /home/tijoytom/unikernel/corert/bin/tools/cli/bin/libbootstrappercpp.a 
 /home/tijoytom/unikernel/corert/bin/tools/cli/bin/libPortableRuntime.a 
 /home/tijoytom/unikernel/corert/bin/tools/cli/bin/libSystem.Private.CoreLib.Native.a 
 /home/tijoytom/unikernel/corert/bin/tools/cli/bin/appdepsdk/CPPSdk/ubuntu.14.04/x64/libSystem.Native.a 
 -lm -ldl -o "/home/tijoytom/unikernel/corert/bin/tools/cli/bin/test/bin/Debug/dnxcore50/native/test.so"



