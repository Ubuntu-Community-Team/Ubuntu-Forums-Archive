---
title: "problem running cmake .."
date: 2010-08-28
forum: General Help
---

### Post by ddmn on 2010-08-28
hi, 

i'm trying to install .tar.bz2 app.
when i run cmake i get this error message:
```

-- Found KDE 4.4 include dir: /usr/include
-- Found KDE 4.4 library dir: /usr/lib
-- Found the KDE4 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found automoc4: /usr/bin/automoc4
CMake Error at /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:70 (MESSAGE):
  Could NOT find ZLIB (missing: ZLIB_LIBRARIES ZLIB_INCLUDE_DIRS)
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindZLIB.cmake:39 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)
  CMakeLists.txt:15 (find_package)


-- Configuring incomplete, errors occurred!

```any help on how to solve this?

---

### Post by minigeek on 2010-08-28
> **ddmn said:**
> hi, 

i'm trying to install .tar.bz2 app.
when i run cmake i get this error message:
```

-- Found KDE 4.4 include dir: /usr/include
-- Found KDE 4.4 library dir: /usr/lib
-- Found the KDE4 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found automoc4: /usr/bin/automoc4
CMake Error at /usr/share/cmake-2.8/Modules/FindPackageHandleStandardArgs.cmake:70 (MESSAGE):
  Could NOT find ZLIB (missing: ZLIB_LIBRARIES ZLIB_INCLUDE_DIRS)
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindZLIB.cmake:39 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)
  CMakeLists.txt:15 (find_package)


-- Configuring incomplete, errors occurred!

```any help on how to solve this?

Hi 

Look for the ZLIB in Synaptic package manager to see if they are installed.
:)

---

### Post by ddmn on 2010-08-28
> **minigeek said:**
> Hi 

Look for the ZLIB in Synaptic package manager to see if they are installed.
:)

thanks. i had to install zlib1g-dev

---

