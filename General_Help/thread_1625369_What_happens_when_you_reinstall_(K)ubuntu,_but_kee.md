---
title: "What happens when you reinstall (K)ubuntu, but keep your /home dir?"
date: 2010-11-19
forum: General Help
---

### Post by pgagy on 2010-11-19
I think I need to reinstall Kubuntu due to a severe crash problem that I have (self inflicted, oops).  I have my /home directory on a separate partition.  Once I do the reinstall, how do my applications know to use the files already in my home directory?  for example, how will firefox know to use the profile in /home already, and not create a new profile.

also, how do I actually make the old /home directory the new /home directory during/after install?

---

### Post by dcstar on 2010-11-19
> **pgagy said:**
> I think I need to reinstall Kubuntu due to a severe crash problem that I have (self inflicted, oops).  I have my /home directory on a separate partition.  Once I do the reinstall, how do my applications know to use the files already in my home directory?  for example, how will firefox know to use the profile in /home already, and not create a new profile.

also, how do I actually make the old /home directory the new /home directory during/after install?

In the install procedure you specify where /home is at the Partitioning stage. Write down what the actual partition is before you commence the install.

Alternatively you manually change your /etc/fstab file after a normal install.

---

### Post by pgagy on 2010-11-19
Once I install firefox, thunderbird and all my other apps, will they just recoginze the old configuration files/settings/bookmarks/auto completes/etc?

---

### Post by dcstar on 2010-11-19
> **pgagy said:**
> Once I install firefox, thunderbird and all my other apps, will they just recoginze the old configuration files/settings/bookmarks/auto completes/etc?

Yep. The big advantage of a separate /home is you can install/reinstall as many times as you like and all that stuff remains.

---

### Post by lovinglinux on 2010-11-19
> **pgagy said:**
> Once I install firefox, thunderbird and all my other apps, will they just recoginze the old configuration files/settings/bookmarks/auto completes/etc?

Yes. As long as you don't format your home partition and properly mount it as /home, all your applications will use the same settings as before. Your can reinstall Ubuntu many times and still keep your personal settings and files. That is the major advantage of having a separate partition.

---

### Post by pgagy on 2010-11-19
Can you point me to some help showing how to properly mount it as /home?  

> **lovinglinux said:**
> Yes. As long as you don't format your home partition and properly mount it as /home, all your applications will use the same settings as before. Your can reinstall Ubuntu many times and still keep your personal settings and files. That is the major advantage of having a separate partition.

---

### Post by lovinglinux on 2010-11-19
> **pgagy said:**
> Can you point me to some help showing how to properly mount it as /home?

I can't find a tutorial right now, but basically you will put the live CD as if you are installing Ubuntu for the first time, then you will select the manual partition method, select the root partition to install Ubuntu and mount your current home partition as /home, without formatting it.

I would recommend that you try it in a virtual machine to get familiarized with the partitioner options before applying to your system. Once you understand how it works, it is pretty easy. However, any mistake during the partitioning steps might result in complete data loss. For instance, if you chose the wrong partition to install Ubuntu or if you select the option to format your home partition.

On a virtual machine you can install Ubuntu as many times you need and can make serious mistakes without affecting your host system. You can use [VirtualBox]("http://en.wikipedia.org/wiki/VirtualBox") for that. It is in the repositories and can be installed from the Software Center.

Also check the [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") forum.

---

### Post by Tsu Dho Nimh on 2011-01-25
> **lovinglinux said:**
> Yes. As long as you don't format your home partition and properly mount it as /home, all your applications will use the same settings as before.

This is exactly what I need to do ... can you explain "properly"? 

I am annoyed that preserving the old /home and data drive settings is not part of the Ubuntu install choices.

---

### Post by Vaphell on 2011-01-25
this is what the manual partitioning mode looks like

[img]http://www.dedoimedo.com/images/computers_new_1/ubuntu-install-partitioning-custom-layout.jpg[/img]
as you can see there is a list of partitions - partition symbol, filesystem (usually extX for linux), mountpoint, checkbox for formatting

make sure you can identify which one of your existing partitions is the system and which one is /home.
system one gets / as mount point and [x] as format (i think that formatting is mandatory for /)
home gets /home as a mount point and [ ] as format (leave unchecked, the most important thing in this whole exercise)
swap if you need one is marked as swap

---

### Post by yetiman64 on 2011-01-25
> **Tsu Dho Nimh said:**
> This is exactly what I need to do ... can you explain "properly"?...As is described in the next quote, how you use the installer is what allows this proceedure (already explained).
> **lovinglinux said:**
> ... but basically you will put the live CD as if you are installing Ubuntu for the first time, then you will select the manual partition method, select the root partition to install Ubuntu and mount your current home partition as /home, **without formatting it**.... I have bolded the quote "without formatting it" for emphasis.

> **Vaphell said:**
> ...i think that formatting is mandatory for /... I regularly prepare my partitions prior to using the installer. The installer will throw up a warning about several system folders being overwritten (from memory /var and /usr are a couple), even though they no longer exist for me. This does not stop the installation though, root can be overwritten with the installer. It is probably a good idea to reformat root everytime, however the installer does go through the step of "removing conflicting operating system files".

---

