---
title: "packing exe and script together"
date: 2010-07-02
forum: General Help
---

### Post by mayapower on 2010-07-02
Hi,

I am building a package tool for python. The idea is to create a self containing package so that end user can run the application with out any external dependency. Most of the existing tool such as: py2exe(win), pyinstaller(cross platform) creates a bootloader using the main script file. Creating such boot loader is out of my scope as I do have a limited knowledge of c/c++.

The initial package run the app using "python main.py" command. A small shell script set temporary environment and then finally execute the main script. I have heard that are couple of utilities or tools that pack an executable and the script into one executable. The simple example is creating self extractable zip archive on windows using winzip. This would allow to unzip the contents on systems where win zip is not installed.

Could any body shed some more light on this topic.

Cheers

Prashant

---

