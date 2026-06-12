---
title: "XSBS Cmake Fails With &quot;Could NOT find PythonLibs&quot;"
date: 2010-06-20
forum: General Help
---

### Post by Aklem on 2010-06-20
I am trying to build the XSBS source code with cmake ([http://xsbs.greghaynes.net/](http://xsbs.greghaynes.net/))
but it fails to find PythonLibs with this error:
```
CMake Error at /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:70 (MESSAGE):
  Could NOT find PythonLibs (missing: PYTHON_LIBRARIES PYTHON_INCLUDE_DIRS)
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindPythonLibs.cmake:110 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)
  src/CMakeLists.txt:3 (find_package)


-- Configuring incomplete, errors occurred!

```
I have python installed.
I am using 32 bit ubuntu 10.04

---

### Post by Aklem on 2010-06-25
This is a generic error where CMake can't find the PythonLibs.

---

### Post by Aklem on 2010-06-27
Come on....

---

### Post by bezda on 2010-07-18
try installing python-dev package.

---

### Post by LasTSuRvivoR on 2010-10-11
After installing python-dev and ruby-dev packages, everything is totally fine now.

Thank you very much !

---

