---
title: "apt-get is broken"
date: 2010-12-19
forum: General Help
---

### Post by inverser on 2010-12-19
So, I wanted to monitor my CPU temps so I installed sensor-applets: 

```
sudo apt-get install sensors-applet
```It hung, so I closed terminal and now apt-get is broken. I can't install or uninstall anything via CL or GUI.

Here is the output: [http://i.min.us/ibnzMM.png](http://i.min.us/ibnzMM.png)

```
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 938, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the libsensors-applet-plugin0 package. This might mean you need to manually fix this package.

```

Halp, please?

---

### Post by sikander3786 on 2010-12-19
Welcome to the forums :-)

First of all, I would request to Edit you above post and remove the Screenshot or crop/resize it to match the size here.

Then go to Applications > Accessories > Terminal and try these commands and post the output as well.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by inverser on 2010-12-19
> **sikander3786 said:**
> Welcome to the forums :-)

First of all, I would request to Edit you above post and remove the Screenshot or crop/resize it to match the size here.

Then go to Applications > Accessories > Terminal and try these commands and post the output as well.

```
sudo apt-get install -f
``````
sudo dpkg --configure -a
``````
sudo apt-get update && sudo apt-get upgrade
```

```
dragonfly@ubuntu:~$ sudo apt-get install -f
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
dragonfly@ubuntu:~$
```

```
dragonfly@ubuntu:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process

``````
dragonfly@ubuntu:~$ sudo apt-get update && sudo apt-get upgrade
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Get:1 http://dl.google.com stable Release.gpg [197B]                           
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Hit http://us.archive.ubuntu.com maverick Release.gpg                          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/docky-core/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/docky-core/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Get:2 http://dl.google.com stable Release.gpg [197B]                           
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en      
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US   
Hit http://security.ubuntu.com maverick-security Release                       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Get:3 http://dl.google.com stable Release [1,347B]                             
Hit http://archive.canonical.com maverick Release                              
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg        
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Get:4 http://dl.google.com stable Release [1,347B]                             
Hit http://security.ubuntu.com maverick-security/main Sources                  
Hit http://archive.canonical.com maverick/partner i386 Packages                
Hit http://ppa.launchpad.net maverick/main Sources                             
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release                              
Get:5 http://dl.google.com stable/main i386 Packages [1,076B]                  
Hit http://security.ubuntu.com maverick-security/restricted Sources            
Hit http://security.ubuntu.com maverick-security/universe Sources              
Hit http://security.ubuntu.com maverick-security/multiverse Sources            
Hit http://security.ubuntu.com maverick-security/main i386 Packages            
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://us.archive.ubuntu.com maverick-updates Release                      
Get:6 http://dl.google.com stable/main i386 Packages [735B]                    
Hit http://security.ubuntu.com maverick-security/universe i386 Packages        
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com maverick/main Sources                         
Hit http://us.archive.ubuntu.com maverick/restricted Sources                   
Hit http://us.archive.ubuntu.com maverick/universe Sources                     
Hit http://us.archive.ubuntu.com maverick/multiverse Sources                   
Hit http://us.archive.ubuntu.com maverick/main i386 Packages                   
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages             
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages               
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages             
Hit http://us.archive.ubuntu.com maverick-updates/main Sources                 
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources           
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources             
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources           
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages           
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages     
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages       
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages     
Fetched 4,899B in 8s (561B/s)                                                  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  language-pack-en language-pack-gnome-en libsensors-applet-plugin0
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 561kB/586kB of archives.
After this operation, 3,248kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main language-pack-en all 1:10.10+20101204 [219kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main language-pack-gnome-en all 1:10.10+20101204 [341kB]
Fetched 561kB in 19s (28.6kB/s)                                                
(Reading database ... 
dpkg: warning: files list file for package `libsensors-applet-plugin0' missing, assuming package has no files currently installed.
(Reading database ... 144320 files and directories currently installed.)
Preparing to replace libsensors-applet-plugin0 2.2.5-4ubuntu1 (using .../libsensors-applet-plugin0_2.2.5-4ubuntu1_i386.deb) ...
Unpacking replacement libsensors-applet-plugin0 ...
```Hangs again.

---

### Post by sikander3786 on 2010-12-19
> ```
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

This error suggests that some other package manager like another instance of apt-get or Software Center or update-manager or Synaptic is running. Close all those package manager and try these commands one-by-one.

```
sudo apt-get clean
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by inverser on 2010-12-19
> **sikander3786 said:**
> This error suggests that some other package manager like another instance of apt-get or Software Center or update-manager or Synaptic is running. Close all those package manager and try these commands one-by-one.

```
sudo apt-get clean
``````
sudo apt-get install -f
``````
sudo dpkg --configure -a
```
Is it possible that my first attempt at install of sensor-applets still has control of the process? How do I release it? This is what I did:

```
dragonfly@ubuntu:~$ sudo rm /var/lib/dpkg/lock
dragonfly@ubuntu:~$ sudo dpkg --configure -a
dragonfly@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglew1.5 linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsensors-applet-plugin0
The following packages will be upgraded:
  libsensors-applet-plugin0
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B/25.2kB of archives.
After this operation, 94.2kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: warning: files list file for package `libsensors-applet-plugin0' missing, assuming package has no files currently installed.
(Reading database ... 144320 files and directories currently installed.)
Preparing to replace libsensors-applet-plugin0 2.2.5-4ubuntu1 (using .../libsensors-applet-plugin0_2.2.5-4ubuntu1_i386.deb) ...
Unpacking replacement libsensors-applet-plugin0 ...

```It hangs here again as it did during first attempt at installation.

Output for other commands are same as my first reply to you.

---

### Post by Foxcow on 2010-12-19
It does look like the process is still somehow running. Can you look at your process via System Monitor to see if something is running that could be using the package manger?  Did you try a reboot?

---

### Post by inverser on 2010-12-19
> **Foxcow said:**
> It does look like the process is still somehow running. Can you look at your process via System Monitor to see if something is running that could be using the package manger?  Did you try a reboot?
I just restarted:

```
dragonfly@ubuntu:~$ sudo apt-get clean
[sudo] password for dragonfly: 
dragonfly@ubuntu:~$ sudo apt-get clean
dragonfly@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglew1.5 linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsensors-applet-plugin0
The following packages will be upgraded:
  libsensors-applet-plugin0
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 25.2kB of archives.
After this operation, 94.2kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
dragonfly@ubuntu:~$ sudo dpkg --configure -a
dragonfly@ubuntu:~$ 

```

If I had answered Y, terminal would hang again. 

WTF is going on. So frustrated.

---

### Post by Foxcow on 2010-12-19
> **inverser said:**
> I just restarted:

```
dragonfly@ubuntu:~$ sudo apt-get clean
[sudo] password for dragonfly: 
dragonfly@ubuntu:~$ sudo apt-get clean
dragonfly@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglew1.5 linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsensors-applet-plugin0
The following packages will be upgraded:
  libsensors-applet-plugin0
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 25.2kB of archives.
After this operation, 94.2kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
dragonfly@ubuntu:~$ sudo dpkg --configure -a
dragonfly@ubuntu:~$ 

```

If I had answered Y, terminal would hang again. 

WTF is going on. So frustrated.


That is bizarre that even after the restart, it hangs.  I'm not sure what to tell you in this situation.  Both Synaptic and Update Manager hang after the restart as well?

---

### Post by inverser on 2010-12-19
> **Foxcow said:**
> That is bizarre that even after the restart, it hangs.  I'm not sure what to tell you in this situation.  Both Synaptic and Update Manager hang after the restart as well?

Whoa that did it, man! There was an update that needed to be installed in Update Manager that was preventing my original install of sensor-applet from completing. Now it's all installed and apt-get is once again functional. Thanks for you help to the both of you!

---

### Post by karthick87 on 2010-12-19
Mark it as [COLOR=Red][SOLVED][/COLOR]

---

### Post by Foxcow on 2010-12-19
Allright!

---

