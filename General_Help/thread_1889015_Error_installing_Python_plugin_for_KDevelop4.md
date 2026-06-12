---
title: "Error installing Python plugin for KDevelop4"
date: 2011-11-30
forum: General Help
---

### Post by vamc on 2011-11-30
I've downloaded tarball of KDevelop's Python plugin from [here]("https://projects.kde.org/projects/playground/devtools/plugins/kdev-python/repository"). The following is the error I got in cmake:

```
CMake Warning at cmake/FindKDevPlatform.cmake:41 (find_package):
  Could not find a configuration file for package "KDevPlatform" that is
  compatible with requested version "1.2.60".

  The following configuration files were considered but not accepted:

    /usr/lib/cmake/kdevplatform/KDevPlatformConfig.cmake, version: 1.0.2

Call Stack (most recent call first):
  CMakeLists.txt:12 (find_package)


CMake Error at /usr/share/kde4/apps/cmake/modules/FindPackageHandleStandardArgs.cmake:198 (MESSAGE):
  Could NOT find KDevPlatform (missing: KDevPlatform_CONFIG) (Required is at
  least version "1.2.60")
Call Stack (most recent call first):
  cmake/FindKDevPlatform.cmake:45 (find_package_handle_standard_args)
  CMakeLists.txt:12 (find_package)


-- Configuring incomplete, errors occurred!
```

From this, I understood that I need is KDevPlatform 1.2.60 (I have 1.0.2 installed). I could not find any update for this package (tried in KPackageKit  and packages.ubuntu.com).

How am I supposed to update this package?
Should I build it from git?

Thanks in advance.

---

