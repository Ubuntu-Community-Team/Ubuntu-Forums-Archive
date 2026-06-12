---
title: "Serious Filesystem Bug in Nautilus! (9.10)"
date: 2009-11-25
forum: General Help
---

### Post by lvalen18 on 2009-11-25
In Ubuntu 9.10 while in Nautilus with Root privileges (sudo nautilus). I cannot do anything in directory "/sys/" Yes there are files and folders in there but i cant do nothing except read them.. Even logged in as root it says the same thing. Below is a Screen Shot when using "sudo nautilus" and trying to create a simple untitled folder.

[IMG]http://i270.photobucket.com/albums/jj84/lvalen17/Screenshot.png[/IMG]

Can anyone give any in sight as to why this is happening? It's only on Ubuntu 9.10 that this is happening

---

### Post by Mr. Devil on 2009-11-25
By the first, never ever use sudo for launching Nautilus.

```
gksudo nautilus /sys
```

---

### Post by iponeverything on 2009-11-25
please see:

[http://en.wikipedia.org/wiki/Sysfs](http://en.wikipedia.org/wiki/Sysfs)

/sys is virtual filesystem that exist in memory only.

---

### Post by lvalen18 on 2009-11-25
> **Mr. Devil said:**
> By the first, never ever use sudo for launching Nautilus.

```
gksudo nautilus /sys
```

okay didnt kno that....

---

### Post by lvalen18 on 2009-11-25
> **iponeverything said:**
> please see:

[http://en.wikipedia.org/wiki/Sysfs](http://en.wikipedia.org/wiki/Sysfs)

/sys is virtual filesystem that exist in memory only.

okay but still why can't i create anything within this "virtual filesystem" even doing the gksudo nautilus thing it still says the same message... 
If you ask why? i want to do something i this directory.. 
Long story short three folders need to be created in the /sys/module/ directory but the script that installs a program an some drivers is prevented from doing anything in there.

---

### Post by egalvan on 2009-11-25
/sys is a rather low-level directory.
not really something that casual users should be mucking around with...

What are you trying to accomplish?
Experimenting?
Trying to learn more Unix?

Just be aware that you can do serious damage to your instalation.

Breaking and fixing Linux is a good way to learn.
Painful, but good. :)

---

### Post by lvalen18 on 2009-11-25
> **egalvan said:**
> /sys is a rather low-level directory.
not really something that casual users should be mucking around with...

What are you trying to accomplish?
Experimenting?
Trying to learn more Unix?

Just be aware that you can do serious damage to your instalation.

Breaking and fixing Linux is a good way to learn.
Painful, but good. :)

doing damage isnt an issue for me... Its a fresh install of Ubuntu so I wont lose noting if i need to reformat

---

### Post by iponeverything on 2009-11-25
> **lvalen18 said:**
> okay but still why can't i create anything within this "virtual filesystem" even doing the gksudo nautilus thing it still says the same message... 
If you ask why? i want to do something i this directory.. 
Long story short three folders need to be created in the /sys/module/ directory but the script that installs a program an some drivers is prevented from doing anything in there.

Indeed. It's intended for kernel data structures. Note that /sys is volatile and does not retain data outside of the live system. 

It it not intended to to be changed directly from userspace.

---

### Post by lvalen18 on 2009-11-25
> **iponeverything said:**
> Indeed. It's intended for kernel data structures. Note that /sys is volatile and does not retain data outside of the live system. 

It it not intended to to be changed directly from userspace.

How would I go about creating folder/files then in .sys

---

### Post by iponeverything on 2009-11-25
> **lvalen18 said:**
> How would I go about creating folder/files then in .sys

load a module ;) note the changes in /sys -- The side effect of loading a module is the creation of new kernel objects.

I am not trying to cryptic. I am not not kernel programer, but do understand a little bit about OS design. If I am wrong about this someone can let me know. But my guess is that ojects in /sys are created by the kernel directly to provide the information to userspace applications.

---

### Post by t0p on 2009-11-25
Can I ask: why do you think your script needs to write directly to /sys?

---

### Post by louieb on 2009-11-25
> **lvalen18 said:**
> doing damage isnt an issue for me... Its a fresh install of Ubuntu so I wont lose noting if i need to reformat

> **lvalen18 said:**
> How would I go about creating folder/files then in .sys

Haven't tried it. But given that you want to see if you can - try the CLI.

```
sudo mkdir /sys/canibreakit
``` 

Curious now - let us know what happened.

---

### Post by Mr. Devil on 2009-11-25
> **louieb said:**
> Haven't tried it. But given that you want to see if you can - try the CLI.

```
sudo mkdir /sys/canibreakit
```Curious now - let us know what happened.

/sys isn't *human writable*.

---

### Post by lvalen18 on 2009-11-25
mkdir: cannot create directory `/sys/canibreakit': No such file or directory
That happens....
I'm trying to load up a 3DSP Wifi PCi Card... I made it work with the updated kernel in 9.10 but only the programs are installed right but the drivers aren't.. Compared to the Install in both 9.04 and in 9.10 the folders in /sys/ are the only things that aren't there after the Installer is finished. I could be wrong on this one but thats the only conclusion I've come up with and since all the other threads on help with 3dsp have come to a halt I decided to stop waiting for other people to solve the problem.

Edit: Checking the files and such that were created there are a few that ask for the folders in the /sys/ directory.. That proves that the folders are crucial...
Example: "pci:3dspbus" is a link/syslink that isn't functional and gives this Error message...
" This link cannot be used, because its targat "/sys/bus/pci/drivers/3dspbus" doesn't exist."
They are suppose to be made during the installer but are not if i cannot create things using the gui or terminal.

---

### Post by iponeverything on 2009-11-26
> **lvalen18 said:**
> mkdir: cannot create directory `/sys/canibreakit': No such file or directory
That happens....
I'm trying to load up a 3DSP Wifi PCi Card... I made it work with the updated kernel in 9.10 but only the programs are installed right but the drivers aren't.. Compared to the Install in both 9.04 and in 9.10 the folders in /sys/ are the only things that aren't there after the Installer is finished. I could be wrong on this one but thats the only conclusion I've come up with and since all the other threads on help with 3dsp have come to a halt I decided to stop waiting for other people to solve the problem.

Edit: Checking the files and such that were created there are a few that ask for the folders in the /sys/ directory.. That proves that the folders are crucial...
Example: "pci:3dspbus" is a link/syslink that isn't functional and gives this Error message...
" This link cannot be used, because its targat "/sys/bus/pci/drivers/3dspbus" doesn't exist."
They are suppose to be made during the installer but are not if i cannot create things using the gui or terminal.

You have things a bit backward, manually creating a kernel object is not going to cause the device to appear. It's the detection of a known device causes the creation of the kobjects.

The kernel finds a device and says "here are your hooks to use this thing" -- 

What you need to be looking at is why the kernel is not detecting the device.. That is the reason the hooks are not appearing on /sys. 

You are chasing a red herring.

---

### Post by lvalen18 on 2009-11-27
> **iponeverything said:**
> You have things a bit backward, manually creating a kernel object is not going to cause the device to appear. It's the detection of a known device causes the creation of the kobjects.

The kernel finds a device and says "here are your hooks to use this thing" -- 

What you need to be looking at is why the kernel is not detecting the device.. That is the reason the hooks are not appearing on /sys. 

You are chasing a red herring.

I see what you mean...If it's the kernel there's Notting I can do except wait and see if support for this new kernel is available.

---

