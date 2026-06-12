---
title: "Can't fix resolution."
date: 2010-03-31
forum: General Help
---

### Post by zaza410 on 2010-03-31
I clean installed xubuntu on an old laptop. I think I messed up the original configuration of xorg though because the highest resolution is 800x600. 

# dpkg-reconfigure xserver-xorg 

or 

$ sudo dpkg-reconfigure xserver-xorg

doesn't work. 

Also I can't get anything on this page to work: [http://forum.xbmc.org/showthread.php?t=54685]("http://forum.xbmc.org/showthread.php?t=54685")

^ I can get a blank xorg file, but I don't know what section it refers to. 

Any help would be greatly appreciated.


edit: the commands listed above simply don't do anything, sometimes I have to put in my password, but nothing happens after that.

---

### Post by zaza410 on 2010-03-31
I'm trying the help on this page: [http://ubuntuforums.org/showthread.php?t=904690](http://ubuntuforums.org/showthread.php?t=904690)

but after I do

sudo mousepad /etc/X11/xorg.conf 

I get a blank xorg.conf file. There is no device section.

edit:

andrew@Andrew-laptop:~$ xrandr -q
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
andrew@Andrew-laptop:~$ lspci |grep VGA
00:04.0 VGA compatible controller: Trident Microsystems Cyber 9525 (rev 49)
andrew@Andrew-laptop:~$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory

---

