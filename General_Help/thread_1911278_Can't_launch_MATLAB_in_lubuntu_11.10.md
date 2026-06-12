---
title: "Can't launch MATLAB in lubuntu 11.10"
date: 2012-01-18
forum: General Help
---

### Post by dlinx90 on 2012-01-18
Hi,

I just installed Matlab R2011a on my laptop running lubuntu 11.10 without any problems but I can't for my life manage to start it. I followed the instructions here to install the launcher but it is not working: [https://help.ubuntu.com/community/MATLAB ]("https://help.ubuntu.com/community/MATLAB")

I can't find any way to launch it with the terminal either. I have tried 

Input: 
```
matlab 
``````
matlab -desktop
```Output:
```
matlab: command not found
```Input:
```
/usr/local/MATLAB/R2011a/bin/matlab
```Output:
```
/usr/local/MATLAB/R2011a/bin/glnx86/MATLAB: error while loading shared libraries: libXp.so.6: cannot open shared object file: No such file or directory
```Earlier output: 
```
/usr/local/MATLAB/R2011a/bin/util/oscheck.sh: 605: /lib/libc.so.6: not found
/usr/local/MATLAB/R2011a/bin/glnx86/MATLAB: error while loading shared libraries: libXp.so.6: cannot open shared object file: No such file or directory
```but i managed to (fix?) the first part by using 
```
sudo ln -s /lib/i386-linux-gnu/libc-2.13.so /lib/libc.so.6
```as suggested here:
[http://www.mathworks.se/support/solutions/en/data/1-F68FSA/index.html?solution=1-F68FSA](http://www.mathworks.se/support/solutions/en/data/1-F68FSA/index.html?solution=1-F68FSA)

Installation folder is usr/local/MATLAB/R2011a

Thank you for any help! I don't want to have to go back to windows because I can't get Matlab working

/D

---

### Post by malcomar on 2012-08-01
I have the same problem on ubuntu 12.04 :(

---

### Post by malcomar on 2012-08-01
Try to install libxp-dev

---

