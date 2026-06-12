---
title: "WUSB54GC Help!!! XUBUNTU"
date: 2010-05-23
forum: General Help
---

### Post by iandunn24 on 2010-05-23
Okay so I love Xubuntu after trying both ubuntu and kubuntu ... even mint. But I cant get my wusb54gc to work I have follow all the instructions from [http://ubuntuforums.org/showthread.php?t=1353044](http://ubuntuforums.org/showthread.php?t=1353044) ... first tried it on mint and it worked perfect--I installed the latest xubuntu and ran into a problem @:
Step 9 
 
Code: 
cd /home/user/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0 
 
Code: 
make && make install 
 
terminal puts out:
```
make[1]: Entering directory '/home/ian/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools' gcc -g bin2h.c -o bin2h
make[1]: gcc: Command not found
make[1]: *** [all] Error 127
make [1]: Leaving directory ...same as above
make: *** [build_tools] Error 2 
```

then after that step 10 in Xubuntu there is no such directory as /lib/modules/2.6.31-14-generic/updates

there is a 2.6.32-21...

I'm sorry but I am extremely new to console ... and linux alike... so any detail answer would be much appreciated.

Thanks
Ian

---

### Post by cariboo on 2010-05-24
It looks like you need to install build-essential from the repositories. that will fix this error:

> make[1]: gcc: Command not found

Your driver isn't getting built, that's why your are getting errors.

---

### Post by iandunn24 on 2010-05-24
Cariboo thanks for your help and im a little further. Now im getting the following:

make: *** /lib/modules/2.6.32-21-generic/build: No such directory. Stop

So I assume that I should make this directory but it wont let me? Any advice?

---

### Post by iandunn24 on 2010-05-24
Maybe someone will want to know the fix. I was able to fix this by blacklisting.
 
Enter the following in console (for xubuntu users change gedit to mousepad)
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
 
Then add the following lines at the very bottom of the page and save and quit.
 
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib

---

