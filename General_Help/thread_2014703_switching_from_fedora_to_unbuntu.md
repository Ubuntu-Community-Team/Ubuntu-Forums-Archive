---
title: "switching from fedora to unbuntu"
date: 2012-07-02
forum: General Help
---

### Post by spike9128 on 2012-07-02
ok, one, sorry if this is in there somewhere, but i have scoured the web for 24 hours and found nothing

my windows died
 got linux

grabbed fedora 17

didnt like it

i want unbuntu

now is where my problem persists, i need to find a program to make a bootable usb disk,  and i need to be shown how to install it (step by step , i havent worked with linux since my ipod 5G)

so far as i know thats all i need, a file, where to put said file, and the commands to execute said file in the terminal

thanks

spike

---

### Post by bodhi.zazen on 2012-07-02
[https://help.ubuntu.com/community/Installation/FromUSBStickQuick](https://help.ubuntu.com/community/Installation/FromUSBStickQuick)

Unetbootin also works.

Post if you have a specific question on a specific step.

---

### Post by khelben1979 on 2012-07-02
[Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick/")

I recommend you take a look at the above link.

---

### Post by 4linux2 on 2012-07-02
Try this:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by spike9128 on 2012-07-02
yall, i know how to install from a usb stick, i need to know how to _install unetbootin in linux_. i am running linux, idk how yum and all that crap works, i need the codes to install unetbooting via the terminal

---

### Post by bodhi.zazen on 2012-07-02
> **spike9128 said:**
> yall, i know how to install from a usb stick, i need to know how to _install unetbootin in linux_. i am running linux, idk how yum and all that crap works, i need the codes to install unetbooting via the terminal

Are you sure you are up to Linux ?

At any rate, I gave you the code to install unetbootin several hours ago on IRC.

```
sudo yum install unetbootin
```

or if using su

```
 su -c yum install unetbootin
```

Also keep in mind we are all volunteers. I suggest you post in a less aggressive more patient style.

---

### Post by spike9128 on 2012-07-02
ok, well i finally got unetbootin to install, 

now it wont find my flashdrive, 

its completely formatted fat32

and 4gb free


and i wasnt being aggressive lol, just redneck


sorry


oh and, none of those codes worked,  both got "bash:"

---

### Post by bodhi.zazen on 2012-07-02
> **spike9128 said:**
> now it wont find my flashdrive

The flash drive needs to be mounted.

> oh and, none of those codes worked,  both got "bash:"

Then you did not type them in properly. Use copy-paste.

---

### Post by spike9128 on 2012-07-02
> **bodhi.zazen said:**
> The flash drive needs to be mounted.



Then you did not type them in properly. Use copy-paste.


how do i mount the flash drive, and i did copy paste, im not worried about the instaler, because its now installed lol

---

### Post by bodhi.zazen on 2012-07-02
> **spike9128 said:**
> how do i mount the flash drive, and i did copy paste, im not worried about the instaler, because its now installed lol

Remove it and plug it in, should auto mount just like windows.

```
[SIZE="4"]**sudo yum install unetbootin**[/SIZE]

[sudo] password for bodhi:
Loaded plugins: langpacks, presto, refresh-packagekit
Resolving Dependencies
--> Running transaction check
---> Package unetbootin.x86_64 0:0-11.575bzr.fc16 will be installed
--> Processing Dependency: syslinux-extlinux for package: unetbootin-0-11.575bzr.fc16.x86_64
--> Processing Dependency: p7zip-plugins for package: unetbootin-0-11.575bzr.fc16.x86_64
--> Running transaction check
---> Package p7zip-plugins.x86_64 0:9.20.1-2.fc16 will be installed
---> Package syslinux-extlinux.x86_64 0:4.02-5.fc16 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

========================================================================================================================
 Package                          Arch                  Version                            Repository              Size
========================================================================================================================
Installing:
 unetbootin                       x86_64                0-11.575bzr.fc16                   updates                512 k
Installing for dependencies:
 p7zip-plugins                    x86_64                9.20.1-2.fc16                      fedora                 875 k
 syslinux-extlinux                x86_64                4.02-5.fc16                        fedora                 335 k

Transaction Summary
========================================================================================================================
Install  1 Package (+2 Dependent packages)

Total download size: 1.7 M
Installed size: 4.7 M
Is this ok [y/N]: y

...
```

---

### Post by spike9128 on 2012-07-02
> **bodhi.zazen said:**
> Remove it and plug it in, should auto mount just like windows.

```
[SIZE=4]**sudo yum install unetbootin**[/SIZE]

[sudo] password for bodhi:
Loaded plugins: langpacks, presto, refresh-packagekit
Resolving Dependencies
--> Running transaction check
---> Package unetbootin.x86_64 0:0-11.575bzr.fc16 will be installed
--> Processing Dependency: syslinux-extlinux for package: unetbootin-0-11.575bzr.fc16.x86_64
--> Processing Dependency: p7zip-plugins for package: unetbootin-0-11.575bzr.fc16.x86_64
--> Running transaction check
---> Package p7zip-plugins.x86_64 0:9.20.1-2.fc16 will be installed
---> Package syslinux-extlinux.x86_64 0:4.02-5.fc16 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

========================================================================================================================
 Package                          Arch                  Version                            Repository              Size
========================================================================================================================
Installing:
 unetbootin                       x86_64                0-11.575bzr.fc16                   updates                512 k
Installing for dependencies:
 p7zip-plugins                    x86_64                9.20.1-2.fc16                      fedora                 875 k
 syslinux-extlinux                x86_64                4.02-5.fc16                        fedora                 335 k

Transaction Summary
========================================================================================================================
Install  1 Package (+2 Dependent packages)

Total download size: 1.7 M
Installed size: 4.7 M
Is this ok [y/N]: y

...
```


well now you know why i want something different, 

mine works nothing like that, 

but i played around with commands enough i got it mounted and its donloading ubuntu 64 right now, and hopefully next time i speak with you it will be on ubuntu

---

