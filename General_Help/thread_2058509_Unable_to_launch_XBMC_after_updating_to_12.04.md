---
title: "Unable to launch XBMC after updating to 12.04"
date: 2012-09-15
forum: General Help
---

### Post by Dayv5 on 2012-09-15
After doing the update, I am now having problems launching the app. I uninstalled it in the software center, rebooted and the app is still located under applications. I then went into the terminal and used the command -   sudo apt-get purge xbmc xbmc-standalone then put in my password, then a few moments later it looked like it was finished. I then rebooted again and the XBMC app is still in applications and the shortcut is still on the left side quick launch. I am hoping to fully remove it and then try to install it again to see if it works better. When I try to launch XBMC, I click on the icon and the icon just flashes. I'm not getting any error message. Any suggestions would be greatly appreciated. Thanks  Dave

---

### Post by Dayv5 on 2012-09-21
I am really amazed that over a hundred people have looked at this post, and no one has any idea how to fully uninstall a program. I will check out another forum. Thanks

---

### Post by BlinkinCat on 2012-09-21
> **Dayv5 said:**
> I am really amazed that over a hundred people have looked at this post, and no one has any idea how to fully uninstall a program. I will check out another forum. Thanks

It is O.K. to bump the thread at around 24 hours - :D

---

### Post by josephmills on 2012-09-21
Hello there I know a little bit about media center so lets give a couple things a run 

1) open termianl and enter in 
```

sudo apt-get update
apt-cache policy xbmc

```


Does it say that it is installed ? 

Next if it is What is the version Number and Where is the Software coming form ? 

Example 
```

~$ apt-cache policy xbmc
xbmc:
  Installed: 2:11.0~git20120510.82388d5-1ubuntu1
  Candidate: 2:11.0~git20120510.82388d5-1ubuntu1
  Version table:
 *** 2:11.0~git20120510.82388d5-1ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
        100 /var/lib/dpkg/status


```

If you could paste that back for us to see that would help out a bunch. 

Now you can do that for all of the packages that xbmc reqires to see if there are also installed o removed. 

How do we know what packages are attached to xbmc 
with this command 

```
 apt-cache show xbmc | awk '/Depends:/,/Size:/'
```

You should get something kinda like this. 


```

Depends: xbmc-bin (>= 2:11.0~git20120510.82388d5-1ubuntu1), xbmc-bin (<< 2:11.0~git20120510.82388d5-1ubuntu1.1~), mesa-utils, x11-utils, ttf-liberation, ttf-dejavu-core, python-imaging, python, python-support (>= 0.90.0)
Recommends: python-qt3
Breaks: xbmc-data (<< 2:11.0~git20111222.22ad8e4), xbmc-skin-confluence (<< 2:11.0~git20111222.22ad8e4), xbmc-standalone (<< 2:11.0~git20111222.22ad8e4)
Filename: pool/universe/x/xbmc/xbmc_11.0~git20120510.82388d5-1ubuntu1_all.deb
Size: 25347728


```

Let me try to explain what this is.    
If you look at this you will see that there are a few important parts, 

Depends:   This means that the packages (xbmc) 100% needs all the other packages that are under this KEYWORD of Depends:

Recommends: Indicates what other packages are recommended when (in this case, xbmc) is installed

Breaks:  Indicates what packages will conflict with this package. Conflicting packages cannot be installed on the same computer.

If you have removed all of the packages that THE OLD xbmc was using and you have also purged and removed the packages, i.e.
```
sudo apt-get --purge remove <package>
```

then you should be able to install re-install xbmc 


Let us know how it works out

---

### Post by Dayv5 on 2012-09-22
Installed: (none)
  Candidate: 2:11.0~git20120423.cd20772-1
  Version table:
     2:11.0~git20120423.cd20772-1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe amd64 Packages

---

### Post by Dayv5 on 2012-09-22
Depends: xbmc-bin (>= 2:11.0~git20120423.cd20772-1), xbmc-bin (<< 2:11.0~git20120423.cd20772-1.1~), mesa-utils, x11-utils, ttf-liberation, ttf-dejavu-core, python-imaging, python, python-support (>= 0.90.0)
Recommends: python-qt3
Breaks: xbmc-data (<< 2:11.0~git20111222.22ad8e4), xbmc-skin-confluence (<< 2:11.0~git20111222.22ad8e4), xbmc-standalone (<< 2:11.0~git20111222.22ad8e4)
Filename: pool/universe/x/xbmc/xbmc_11.0~git20120423.cd20772-1_all.deb
Size: 25388040

---

### Post by Dayv5 on 2012-09-23
Any ideas would be greatly appreciated.

Dave

---

### Post by Dayv5 on 2012-09-26
Any ideas?

---

### Post by Dayv5 on 2012-10-01
I guess no one knows. Thanks anyways. I will check out another forum.

---

### Post by josephmills on 2012-10-01
Did you purge and remove all the dependency's ? then re-install ? 
Thanks

---

### Post by Dayv5 on 2012-10-02
dave@HTPC:~$ sudo apt-get --purge remove xbmc
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libswscale0 libavutil50 libunity6 libx264-106 libbluray0 libdee-1.0-1
  libmysqlclient16 libavcodec52 libindicator6 libgladeui-1-11 libvpx0
  libpostproc51 libavformat52
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xbmc*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 249416 files and directories currently installed.)
Removing xbmc ...
Purging configuration files for xbmc ...
dave@HTPC:~$

---

### Post by Dayv5 on 2012-10-02
I again uninstalled the app in the software centre, did the purge (results are above) and it said it was done but the XBMC quicklaunch button was still on the toolbar on the left side, I undocked it, rebooted and then went back into the software Centre and it said install (meaning it is not there) so I did and the icon shows up in the quick launch bar and still when I click on it, it flashes but will not launch.

---

### Post by Dayv5 on 2012-10-06
I guess I will just need to reload Ubuntu unless anyone has any more ideas. Thanks to those that tried.

---

### Post by Dayv5 on 2012-10-12
Kind of a useless forum.

---

### Post by scratman on 2012-10-13
You may consider the forum useless, but had you gone to the trouble of attaching tags to your original post, far more people would have found your thread.

As far as assistance goes, it sounds to me that you simply have an icon in the Unity Panel that is associated with an application that is not installed.  From memory, I'm fairly sure that you can simply right click the icon, and select the option to remove the icon.

Once you've done that, simply reinstall XBMC if you so wish.

---

### Post by Dayv5 on 2012-10-15
Nearly 700 people have viewed this post so I really don't think that is the problem. And also if you had actually read the issue, you would have known that deleting the shortcut from the quicklaunch bar wasn't the problem. It's annoying that the only time I get responses are after waiting for weeks and stating that I am going to get answers somewhere else.

---

