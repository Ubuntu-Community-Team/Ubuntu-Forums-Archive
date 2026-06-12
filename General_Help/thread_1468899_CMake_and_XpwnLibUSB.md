---
title: "CMake and Xpwn/LibUSB"
date: 2010-05-01
forum: General Help
---

### Post by liquidated on 2010-05-01
Hello,

I have searched these forums, as well as a few others, including the instruction pages but I am still stuck.

I have managed to download the git-xpwn files, cmake files, libusb etc as detailed, but when trying to run cmake I get the following error;

```
dan@dan-desktop:~/xpwn/build-dir$ cmake ..
CMake Error: Error in cmake code at
/home/dan/xpwn/xpwn/FindUSB.cmake:8:
Parse error.  Expected a command name, got unquoted argument with text "<!DOCTYPE".
CMake Error at CMakeLists.txt:1 (INCLUDE):
  include could not find load file:

    /home/dan/xpwn/xpwn/FindUSB.cmake


-- libusb is required for xpwn!
-- Configuring incomplete, errors occurred!
dan@dan-desktop:~/xpwn/build-dir$ 

```

Could anyone shed any light on this?
(Not new to Linux, but treat me as a noob if you can. :P)

Thanks.

EDIT: Forgot to mention, I am running a clean install of 9.10 Ubuntu.

---

### Post by liquidated on 2010-05-01
I worked it out. I'd copied the wrong FindUSB.cmake file over. Stupid stupid mistake. >.>

Here comes the new error :/
```
dan@dan-desktop:~/xpwn/build-dir$ cd ..
dan@dan-desktop:~/xpwn$ make
Scanning dependencies of target xpwn-bin
[ 50%] Building CXX object CMakeFiles/xpwn-bin.dir/src/xpwn.o
/home/dan/xpwn/xpwn/src/xpwn.cpp:1:20: error: common.h: No such file or directory
/home/dan/xpwn/xpwn/src/xpwn.cpp:2:26: error: xpwn/pwnutil.h: No such file or directory
/home/dan/xpwn/xpwn/src/xpwn.cpp:3:24: error: xpwn/plist.h: No such file or directory
/home/dan/xpwn/xpwn/src/xpwn.cpp:4:30: error: xpwn/outputstate.h: No such file or directory
/home/dan/xpwn/xpwn/src/xpwn.cpp:5:24: error: hfs/hfslib.h: No such file or directory
/home/dan/xpwn/xpwn/src/xpwn.cpp:6:26: error: xpwn/ibootim.h: No such file or directory
In file included from /home/dan/xpwn/xpwn/src/xpwn.cpp:7:
/home/dan/xpwn/xpwn/include/libibooter.h:6:26: error: abstractfile.h: No such file or directory
In file included from /home/dan/xpwn/xpwn/src/xpwn.cpp:7:
/home/dan/xpwn/xpwn/include/libibooter.h:63: error: ‘AbstractFile’ has not been declared
/home/dan/xpwn/xpwn/src/xpwn.cpp: In function ‘void TestByteOrder()’:
/home/dan/xpwn/xpwn/src/xpwn.cpp:20: error: ‘IS_LITTLE_ENDIAN’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:20: error: ‘IS_BIG_ENDIAN’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp: In function ‘int main(int, char**)’:
/home/dan/xpwn/xpwn/src/xpwn.cpp:29: error: ‘OutputState’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:29: error: ‘ipswContents’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:31: error: ‘Dictionary’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:31: error: ‘info’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:32: error: ‘StringValue’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:32: error: ‘kernelValue’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:33: error: ‘AbstractFile’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:33: error: ‘ramdisk’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:35: error: ‘applelogo’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:36: error: ‘recoverymode’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:37: error: ‘iboot’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:52: error: ‘fopen’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:52: error: ‘createAbstractFileFromFile’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:62: error: ‘fopen’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:62: error: ‘createAbstractFileFromFile’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:71: error: ‘fopen’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:71: error: ‘createAbstractFileFromFile’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:89: error: ‘parseIPSW’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:92: error: ‘printf’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:97: error: ‘ramdiskSrc’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:97: error: ‘fopen’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:97: error: ‘createAbstractFileFromFile’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:107: error: ‘io_func’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:107: error: ‘myRamdisk’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:107: error: ‘createAbstractFileFromMemoryFile’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:107: error: ‘IOFuncFromAbstractFile’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:108: error: ‘Volume’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:108: error: ‘ramdiskVolume’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:108: error: ‘openVolume’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:110: error: ‘ibootDict’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:110: error: expected primary-expression before ‘)’ token
/home/dan/xpwn/xpwn/src/xpwn.cpp:110: error: expected ‘;’ before ‘getValueByKey’
/home/dan/xpwn/xpwn/src/xpwn.cpp:117: error: expected primary-expression before ‘)’ token
/home/dan/xpwn/xpwn/src/xpwn.cpp:117: error: expected ‘)’ before ‘getValueByKey’
/home/dan/xpwn/xpwn/src/xpwn.cpp:118: error: ‘patchValue’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:118: error: expected primary-expression before ‘)’ token
/home/dan/xpwn/xpwn/src/xpwn.cpp:118: error: expected ‘;’ before ‘getValueByKey’
/home/dan/xpwn/xpwn/src/xpwn.cpp:123: error: ‘printf’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:124: error: ‘doPatchInPlace’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:128: error: ‘add_hfs’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:134: error: ‘fileValue’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:139: error: expected primary-expression before ‘)’ token
/home/dan/xpwn/xpwn/src/xpwn.cpp:139: error: expected ‘;’ before ‘getValueByKey’
/home/dan/xpwn/xpwn/src/xpwn.cpp:140: error: ‘printf’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:140: error: ‘stdout’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:140: error: ‘fflush’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:141: error: ‘getFileFromOutputState’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:141: error: ‘replaceBootImage’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:141: error: ‘ASSERT’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:142: error: ‘createAbstractFileFromMemory’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:142: error: ‘add_hfs’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:146: error: expected primary-expression before ‘)’ token
/home/dan/xpwn/xpwn/src/xpwn.cpp:146: error: expected ‘;’ before ‘getValueByKey’
/home/dan/xpwn/xpwn/src/xpwn.cpp:147: error: ‘printf’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:147: error: ‘stdout’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:147: error: ‘fflush’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:148: error: ‘getFileFromOutputState’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:148: error: ‘replaceBootImage’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:148: error: ‘ASSERT’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:149: error: ‘createAbstractFileFromMemory’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:149: error: ‘add_hfs’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:155: error: ‘closeVolume’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:156: error: ‘CLOSE’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:160: error: expected primary-expression before ‘)’ token
/home/dan/xpwn/xpwn/src/xpwn.cpp:160: error: expected ‘;’ before ‘getValueByKey’
/home/dan/xpwn/xpwn/src/xpwn.cpp:186: error: ‘getFileFromOutputState’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:254: error: ‘sprintf’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:291: error: ‘releaseOutput’ was not declared in this scope
/home/dan/xpwn/xpwn/src/xpwn.cpp:292: error: ‘releaseDictionary’ was not declared in this scope
make[2]: *** [CMakeFiles/xpwn-bin.dir/src/xpwn.o] Error 1
make[1]: *** [CMakeFiles/xpwn-bin.dir/all] Error 2
make: *** [all] Error 2
dan@dan-desktop:~/xpwn$ 

```

---

