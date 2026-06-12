---
title: "dual boot confusion"
date: 2010-10-13
forum: General Help
---

### Post by Baxterton on 2010-10-13
Hello, I am wanting to dual boot my comp with ubuntu and windows, I have looked at many threads and guides on how to dual boot ubuntu after windows, however I installed ubuntu first.

I found a guide telling me how to partition my drive making it ntfs, however when I tried to partition, gparted would not let me touch my HD. I looked back at this guide and it said absolutely nothing about this type of thing, instead went on with the installation, leaving me in it's wake confused.

I just can't seem to find a guide or forum thats remotely useful, it's all from the user perspective, which doesn't help me or others one bit.

Thanks in advance.

---

### Post by lindsay7 on 2010-10-13
Your drive has to be unmounted, so you can not work on it if you are running Ubuntu on your computer.  What you need to do is use the Ubuntu live cd to make partition changes using gparted. or you can download gparted from their web site which will boot up and do it that way.

Here is a site that gives you the info on how to dual boot.

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

---

### Post by BigCityCat on 2010-10-13
The problem is that a windows install from what I understand will not install itself on a divided partition, and it will not recognize your ubuntu install. It will install on the entire disk and wipe everything out, Like I said from what I understand.

It's much easier to install windows first. Then in windows right click computer and click computer management. When the window opens goto disk drive and right click. Select shrink partition. Select the size to shrink.

After that there is a program called easybcd. Install that and re write the MBR before you log out.

Then install ubuntu and select use largest continous space and that will install ubuntu to the empty partition.

---

### Post by lindsay7 on 2010-10-13
bad info and web link,

---

