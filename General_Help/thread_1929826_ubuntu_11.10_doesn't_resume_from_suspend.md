---
title: "ubuntu 11.10 doesn't resume from suspend"
date: 2012-02-22
forum: General Help
---

### Post by CProgramming on 2012-02-22
hey! :)

I have problem:

When I to restore my session on ubuntu 11.10 after Suspend2ram,

Ubuntu doesn't resuming. the monitor still stay at "No connection found" , like when the cumputer is suspend.

IS there fix to that problem? its very important to me!

BTW , on Ubuntu 10.04 its resuming well.

p.s Does anybody know if will be fix at 12.04?

thanks :)

---

### Post by bluexrider on 2012-02-22
You might have noticed that the suspend and hibernation function in  ubuntu/kubuntu won’t work. While there’s no official fix, you might find  this work around helpful_._ Most people need hibernation for their laptops.Next step is to install a tool called «uswsusp»
 ```
sudo apt-get install uswsusp
``` And by typing the below command you check if the suspend [COLOR=darkgreen]_[COLOR=darkgreen]function[/COLOR]_[/COLOR] works now….
 ```
sudo s2ram
``` Same goes for hibernation
 ```
sudo s2disk
``` Now once this is done, and all of the above commands work, they can  be replaced with the old non-working commands that come with ubuntu.
 But attention, before editing the system files, always make sure you back up the files in case something goes completely wrong.
 ```
sudo cp /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux.bak
``` ```
sudo cp /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux  /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux.bak
``` This step is to replace the old commands with the new commands in
 hal-system-power-suspend-linux
 ```
sudo nano /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
``` paste the following:
```
#!/bin/sh
/sbin/s2ram –force
 hal-system-power-hibernate-linux

``````
sudo nano /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
``` paste the following again:
```
#!/bin/sh
/sbin/s2disk
   
```

---

### Post by CProgramming on 2012-02-22
> **bluexrider said:**
> You might have noticed that the suspend and hibernation function in  ubuntu/kubuntu won&#8217;t work. While there&#8217;s no official fix, you might find  this work around helpful_._ Most people need hibernation for their laptops.Next step is to install a tool called «uswsusp»
 ```
sudo apt-get install uswsusp
``` And by typing the below command you check if the suspend [COLOR=darkgreen]_[COLOR=darkgreen]function[/COLOR]_[/COLOR] works now&#8230;.
 ```
sudo s2ram
``` Same goes for hibernation
 ```
sudo s2disk
``` Now once this is done, and all of the above commands work, they can  be replaced with the old non-working commands that come with ubuntu.
 But attention, before editing the system files, always make sure you back up the files in case something goes completely wrong.
 ```
sudo cp /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux.bak
``` ```
sudo cp /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux  /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux.bak
``` This step is to replace the old commands with the new commands in
 hal-system-power-suspend-linux
 ```
sudo nano /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
``` paste the following:
```
#!/bin/sh
/sbin/s2ram &#8211;force
 hal-system-power-hibernate-linux

``````
sudo nano /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
``` paste the following again:
```
#!/bin/sh
/sbin/s2disk
   
```

hey. first of all, thank you on this reply.
I've install the uswsusp:

```

nimrod@nimrod-Product:~$ sudo apt-get install uswsusp
[sudo] password for nimrod: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
uswsusp is already the newest version.
The following packages were automatically installed and are no longer required:
  libboost-program-options1.46.1 libboost-thread1.46.1 python-beautifulsoup
  libboost-date-time1.46.1 compiz-plugins python-tz libkprintutils4
  python-rsvg gnash-common libkutils4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```It's seems like I already have this package.
When I tried to:

```

nimrod@nimrod-Product:~$ sudo cp /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux.bak

```I've got that error:
```

cp: cannot stat `/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux': No such file or directory

```

Then I've tried to browse that directory by get into directory by directory:
```

nimrod@nimrod-Product:/lib$ cd /usr
nimrod@nimrod-Product:/usr$ cd lib
nimrod@nimrod-Product:/usr/lib$ cd hal
bash: cd: hal: No such file or directory
nimrod@nimrod-Product:/usr/lib$ 

```Its seems like the directory "hal" doesn't exist.

Can you give me the file than should be contained there? I mean:

hal-system-power-suspend-linux

Thanks again !

---

### Post by CProgramming on 2012-02-23
Up!

p.s quick reply doesn't work

---

### Post by CProgramming on 2012-02-23
?..

---

### Post by CProgramming on 2012-02-24
?.. :\

---

