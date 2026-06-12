---
title: "Removing the /boot and not messing up anything."
date: 2006-02-11
forum: General Help
---

### Post by shawn524 on 2006-02-11
OK, after using ubuntu, I loved it. But I also need windows for other things. I installed a dual boot using grub with windows on my master 60gig and ubuntu on a 50gig partition on my 300gig slave drive.

I want to remove grub all together and just change the boot order of the two hard drives when i want to use linux. How do I do that without deleting all of my sensitive data (music mostly). 

I usually just search when i have problems with this stuff but I didn't know what to look for this time.

---

### Post by Robgould on 2006-02-11
ok...I can't tell you how to choose which hard drive to boot, I assume you would do this with your bios settings? I can tell you how to remove grub. If you did a default installation grub was installed to your master boot record. To remove it, boot to your windows install cd or windows boot disk, depending on your verstion of windows. if you sue the install disk, boot to rescue mode
 
once at a prompt type:
 
```

fixmbr

```
 
-or-
```

fdisk /mbr

```
 
which command depends on which version of windows (XP uses fixmbr).
 
This will rewrite your master boot record and consequently erase grub. Now windows will boot as normal.
 
You can use your Ubuntu install cd to boot to your linux installation. I hope this helps you.

---

### Post by shawn524 on 2006-02-11
Last time I did fixmbr it reased my whole windows folder and I had to reinstall everything. Did I do something wrong, or is that what is supposted to happed?

---

### Post by nikosft on 2006-02-11
i have used fixmbr a lot of times without any problem. nevertheless in the ubuntu documentation there is a section about grub. There it says how to set its parameters. May be setting the timer parameter to 0 make your life more convinient!

---

### Post by Robgould on 2006-02-11
fixmbr should not hurt anything.  I should just make it like it was before you installed ubuntu.

---

### Post by shawn524 on 2006-02-11
Oh, I forgot to mention that i have a /boot partition. Does that make a difference?

---

### Post by Robgould on 2006-02-12
I don't know what you mean when you say you have a /boot partition.  I know you have a /boot directory as part of ubuntu, but a partition?  How did you set that up?  I don't know what you are saying.

---

### Post by shawn524 on 2006-02-12
I read somewhere that i should make a small partition and sit it's mountpoint as /boot.

---

### Post by Robgould on 2006-02-13
I have never done that, nor heard that it should be done.  I don't even know how to do it.  All that does not meant alot as I am a bit of a noob myself.  I'm giving this a little bump to see if someone else knows.  I would like to hear the answer myself.

---

### Post by Robgould on 2006-02-13
I have never done that, nor heard that it should be done.  I don't even know how to do it.  All that does not meant alot as I am a bit of a noob myself.  I'm giving this a little bump to see if someone else knows.  I would like to hear the answer myself.

---

### Post by xerosis on 2006-02-13
you can have a /boot partition and in fact i believe it is recommended, for protection of data etc. to answer the original question it shouldn't prove a problem.

---

### Post by wrtrdood on 2006-02-13
A boot partition can come in quite handy at times.  Don't remove it, though, unless you first create a /boot directory on your Ubuntu partition and copy everything over.

The fixmbr program should install a standard Windows boot loader on the master drive.  I doubt that it was responsible for losing a "Windows folder" but I'm not sure what that means.  If you have a standard Windows installation, there should be no problem booting it up after using fixmbr.  

As for Ubuntu, you will then have install grub to the correct location on the slave drive for it to know where it is and you'll find that to be rather involved.  It really sounds to me like a heck of a lot more trouble than it's worth.

  Have you considered simply editing the /boot/grub/menu.lst file and changing the **default** value (should be the first parameter in the file) to point to the Windows boot file so that it is the default OS to boot?  It's quite simple.  Open the menu.lst file (using sudo) in gedit, nano, or other editor.  Scroll the file down until you find the line that reads:

## ## End Default Options ##

Below this line should be where the menu choices are defined.  You can recognize this by the first value of each menu selection starting with the word **title**.  Starting at 0, count the number of **title** entries down until you find the one labeled Windows (probably near the bottom).  That count is the value you need to change the **default** parameter at the top of the file to.  That line should currently read as:

*default 0*

Save and exit the file.  Now when your system reboots, Windows will be the default system to boot.

Seems much easier to do that than fiddling with boot orders, cable swaps and what have you.

---

