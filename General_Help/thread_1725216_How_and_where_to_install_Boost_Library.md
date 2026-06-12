---
title: "How and where to install Boost Library?"
date: 2011-04-09
forum: General Help
---

### Post by iconoclast hero on 2011-04-09
10.10 desktop.
Trying to install e4rat that was on LifeHacker on Friday and have zero idea what I am doing.
I have the e4rat extracted to a directory in /usr/local/src
The README says that there are dependencies including boost library components.  I am fine installing the whole boost library but sudo apt-get install libboost* did not work.  

```
sudo apt-get install libboost-thread-dev
``` got part of it

When I went to execute the command 
```
cmake . -DCMAKE_BUILD_TYPE=release
``` I got the following:
```
CMake Error at /usr/share/cmake-2.8/Modules/FindBoost.cmake:910 (message):
  Unable to find the requested Boost libraries.

  Boost version: 1.42.0

  Boost include path: /usr/include

  The following Boost libraries could not be found:

          boost_system
          boost_filesystem
          boost_regex

  No Boost libraries were found.  You may need to set Boost_LIBRARYDIR to the
  directory containing Boost libraries or BOOST_ROOT to the location of
  Boost.
Call Stack (most recent call first):
  CMakeLists.txt:19 (find_package)


CMake Error at src/cmake/Findext2fs.cmake:17 (MESSAGE):
  Could not find ext2fs
Call Stack (most recent call first):
  src/CMakeLists.txt:48 (FIND_PACKAGE)


-- Configuring incomplete, errors occurred!
```I did download the file boost_1_46_1.tar.gz to my /tmp directory and was about to extract it but realized I don't know what the proper directory is.  I would prefer to use apt-get but whatever is fine.

Anyway, as I don't know what directory the portions I have installed are in, I don't know how to modify the config file cmake is looking for.  I also have no idea if I have any of the other non-standard dependencies that e4rat is looking for which are:
The e4rat toolset has the following external dependencies:
 - Linux Kernel (>= 2.6.31) #i think this is probably a joke, i must have this
 - CMake (>= 2.6) # installed
 - pod2man  - Boost Library (>=1.41): 
                   You need the following components installed:        system, filesytem, regex, signals2
 - Linux Audit Library (libaudit >=0.1.7) #unknown package
 - Block Device Identification Library (libblkid) #unknown package
   - Ext2 File System Utilities (e2fsprogs)  #I have this one 
[FONT=Arial]
I tried to bang around a little to try to learn something with this but can't get any further so help is appreciated.[/FONT]

Thanks

---

### Post by iconoclast hero on 2011-04-09
Ok, I missed the comment in the online documentation that it should be in /usr/local/boost_1_46_1

...but then it goes onto say "To compile anything in Boost, you need a directory containing the boost/ subdirectory in your #include path."  What is an "#include path?"

---

### Post by wbar2 on 2011-04-10
I'm trying this as well. I think the following line worked for me:

```
sudo apt-get install libboost-all-dev
```

I'm using Linux Mint Julia. Still having some issues with ext2fs though, even though I have it installed. I'm getting this now when running the cmake line:

```
-- Boost version: 1.42.0
-- Found the following Boost libraries:
--   system
--   filesystem
--   regex
CMake Error at src/cmake/Findext2fs.cmake:17 (MESSAGE):
  Could not find ext2fs
Call Stack (most recent call first):
  src/CMakeLists.txt:48 (FIND_PACKAGE)


-- Configuring incomplete, errors occurred!
```

---

### Post by wbar2 on 2011-04-10
I was able to complete the cmake process with the following libraries on Linux Mint Julia:

```
sudo apt-get install cmake libblkid-dev e2fslibs-dev libboost-all-dev libaudit-dev
```

---

### Post by a5h3n on 2011-04-12
I've been trying to install it too, but am trying to avoid having to compile anything myself. I can't find any .deb files for any version of version of libboost beyond 1.40, which is too old.

Sorry I can't be of any help, but maybe the bump will give this thread the attention it needs.

---

### Post by iconoclast hero on 2011-04-12
After following the suggestions above about installing boost, I think I may have gotten e4rat compiled.  Not sure, so I'll let you know if my computer boots up 50% faster or I broke GRUB.

```
/usr/local/src/e4rat-0.2$ cmake . -DCMAKE_BUILD_TYPE=release
-- Boost version: 1.42.0
-- Found the following Boost libraries:
--   system
--   filesystem
--   regex
-- Found ext2fs: /usr/lib/libext2fs.so
-- Found blkid: /usr/lib/libblkid.so
-- Found audit: /usr/lib/libaudit.so
-- Found auparse: /usr/lib/libauparse.so
-- Looking for include files CMAKE_HAVE_PTHREAD_H
-- Looking for include files CMAKE_HAVE_PTHREAD_H - found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE
-- Configuring done
-- Generating done
-- Build files have been written to: /usr/local/src/e4rat-0.2

```

---

