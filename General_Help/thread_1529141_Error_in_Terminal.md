---
title: "Error in Terminal"
date: 2010-07-11
forum: General Help
---

### Post by calebcaudill on 2010-07-11
Hi sorry if this is in the wrong place. I'm attempting to make my own World of Warcraft server so I can play offline with some friends over LAN but there's a step I'm stuck on. I'm following this guide: [http://www.wikihow.com/Build-and-Maintain-a-Private-World-of-Warcraft-Server-on-Linux. ]("http://www.wikihow.com/Build-and-Maintain-a-Private-World-of-Warcraft-Server-on-Linux")

I've completed up to step 6 with little or no problems. However, when I run the command it gives me in step 6 I get this in the terminal:

caleb@caleb-laptop:~/src/trinitycore/build$ cmake ../ -DPREFIX=/home/caleb/bin
-- Detected 64-bit platform.
-- Found ACE library: /usr/lib/libACE.so
-- Found ACE headers: /usr/include
-- Using mysql-config: /usr/bin/mysql_config
-- Found MySQL library: /usr/lib/libmysqlclient_r.so
-- Found MySQL headers: /usr/include/mysql
-- Could NOT find BZip2  (missing:  BZIP2_LIBRARIES BZIP2_INCLUDE_DIR)
CMake Error at cmake/FindReadline.cmake:19 (MESSAGE):
  ** Readline library not found!

  ** Your distro may provide a binary for Readline e.g.  for ubuntu try
  apt-get install libreadline5-dev
Call Stack (most recent call first):
  CMakeLists.txt:100 (find_readline)


-- Configuring incomplete, errors occurred!

I have searched various forums looking for an answer and can't find anything that helps. Any help will be appreciated and thanks in advance! :D

---

### Post by Darkness Des on 2010-07-11
It needs you to install readline. Just run
```
sudo apt-get install libreadline5-dev
```
in the terminal and then try to build it once more.

---

### Post by patchwork on 2010-07-11
> ** Your distro may provide a binary for Readline e.g.  for ubuntu try
  apt-get install libreadline5-dev

Have you done this?

Step One did not list this package in the required files list.

---

### Post by Penguin Guy on 2010-07-11
> **calebcaudill said:**
> ```
for ubuntu try
apt-get install libreadline5-dev
```
You might want to put [FONT="Courier New"]sudo[/FONT] in front of that:
```
sudo apt-get install libreadline5-dev
```

---

### Post by calebcaudill on 2010-07-11
So simple haha. Worked perfectly, thanks a ton!!

---

