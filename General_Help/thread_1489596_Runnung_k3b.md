---
title: "Runnung k3b"
date: 2010-05-21
forum: General Help
---

### Post by FNC on 2010-05-21
Hi Everyone,

-- Short Introduction --
I am a new ubuntu user although I'm not new to Linux. I used to run OpenSUSE and PCLinuxOS and a couple of other flavours.
When Lucid Lynx was released I thought I'll give it a try. So far I'm more than impressed with it, for the first time ALL the hardware on my laptop (Lenovo R61) is working.


-- Problem --
Anyway, since I'm used to KDE, I am trying to get k3b to work.
I have installed ubuntu 10.04 64bit desktop.
To install k3b I did:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install k3b

When I try to run k3b it crashes with a segmentation fault.

I tried to search the forum but could not find anything.

Please assist.

Thank you

---

### Post by tommcd on 2010-05-21
I have no idea what the problem is; but to help diagnose the problem, try running k3b from the terminal. Just open the terminal and type **k3b**.
Post back what errors the terminal reports.
If you are more familiar with KDE, and if you want to use K3B, then perhaps you should install Kubuntu (with KDE) instead of Ubuntu (with Gnome).

And welcome to the Ubuntu forums!!

---

### Post by krishnandu.sarkar on 2010-05-21
well....I just installed k3b now. It worked fine. I just used sudo apt-get install k3b.

---

### Post by cascade9 on 2010-05-21
> **tommcd said:**
> I have no idea what the problem is; but to help diagnose the problem, try running k3b from the terminal. Just open the terminal and type **k3b**.
Post back what errors the terminal reports.
If you are more familiar with KDE, and if you want to use K3B, then perhaps you should install Kubuntu (with KDE) instead of Ubuntu (with Gnome).

+1. 

I've always found I'm more likely to get errors, etc with K3B running gnome/xfce/etc than when I'm running K3B from within KDE.

---

### Post by edw666 on 2010-06-02
Hi everyone,

I'm also new to Ubuntu!  I am slowly switching all my machines over to Ubuntu 10.04. 

K3b is working without any problem on my big Tower at home both in a virtualbox as guest on a Vista OS as well as on a dual-boot Ubuntu installation on that PC.
 
However, on my Dell laptop (which also features VISTA and UBUNTU as dual-boot OS) K3b crashes everytime with a segmentation fault. I am only getting this window that is telling me that the crash log is not helpful! The suggested installation of additional software to help determine the problem is - of course - also not helping!

By the way - Brasero is also not working!   
Only Gnome Baker seams to work OK!

I hate to reboot and Dual-Boot VISTA just to use Nero!!! :(

I can give you more information about the environment (PC and software as well as logs) if you need additional details to better understand the problem! I would just like to fix this problem because Ubuntu really rocks !!!

Any idea highly appreciated!

---

### Post by tommcd on 2010-06-03
> **edw666 said:**
> 
I'm also new to Ubuntu! 
Welcome to the Ubuntu forums!  
> **edw666 said:**
> 
However, on my Dell laptop (which also features VISTA and UBUNTU as dual-boot OS) K3b crashes everytime with a segmentation fault. I am only getting this window that is telling me that the crash log is not helpful! The suggested installation of additional software to help determine the problem is - of course - also not helping!
What additional software did you install?
Did you try running **k3b** from the terminal (applications > accessories > terminal) to see what errors you get? Post the output from running k3b in the terminal here.
Some things to try:
Install **krename**. See post #5 in this thread:
[http://ubuntuforums.org/showthread.php?t=1486562](http://ubuntuforums.org/showthread.php?t=1486562)
In the system settings for k3b, make sure it detects your cdrom drive properly. Go through the various settings for k3b and try to see if anything is amiss. 
When k3b launches, it will normally report any errors with it's configuration. Does it report any errors when you start k3b?
Try renaming the .k3b directory in your home directory to .kde.bak. Then restart k3b. This will generate a fresh k3b configuration file. In the Nautilus file manager window click on: view > show hidden files. Then search for the .kde directory and rename it to .kde.bak.
> **edw666 said:**
> 
By the way - Brasero is also not working!   
Only Gnome Baker seams to work OK!

So what happens when you use brasero? You can also run brasero from the terminal and post back any errors it reports.
In the past I have had better luck with Gnomebaker than I did with Brasero. I have not actually used eithe of those recently though. I burn all my CDs and DVDs on Slackware using either k3b, or cdrecord from the terminal. K3b, at least on Slackware, always works well in my experience.

---

### Post by edw666 on 2010-06-08
Hello Tmmcd,

thanks a lot for your kind words and friendly welcome!

Well - I followed your advice and started k3b from the terminal !  I must admit that I am still reluctant to use the terminal commands being such an old Windows-User :-)

and...  what can I say:   The Terminal showed that the program tried to open a temp-file in the kde directory. However, that directory was owned by ROOT and a normal user was not allowed to do anything. Therefor the temp-file could not be created and k3b (after trying for many times) gave up and did not even start. So I changed the permission of the directory and voila ... everything worked!!!   :-)

There are a number of lessons that I learned:

1)  This forum is really great and thanks to your quick suggestion the problem was solved! 
2)  I think that I have to learn more about these Terminal commands!    =>  only problem is so far I have not been able to find something useful
3)  The front-end gui is not always showing all the errors - which is something that should be improved!  Maybe I will try to get in touch with the guys who developed k3b. They could then decide if it is worth to include an improved error handling procedure.
4)  I am not aware that I installed k3b differently on my laptop from my other 2 PCs where everything worked right from the start.  That's why I originally thought that the problem may be related with my Dell Laptop!   But as usual - most problems occur because of wrong assumptions or misunderstandings!   So the first thing is to free one's mind and to look at the problem objectively - and to ask for a different point of view from others!!!  :-)  :-)  :-)
 

Thank you once again for your quick and precise help!!!   I hope that some day I can give this help back!!!  ):P

---

### Post by tommcd on 2010-06-08
> **edw666 said:**
> 
Well - I followed your advice and started k3b from the terminal 
... The Terminal showed that the program tried to open a temp-file in the kde directory. However, that directory was owned by ROOT and a normal user was not allowed to do anything.
Try running k3b with sudo privileges then. Open a terminal and run 
```
sudo k3b
```
Then under (I think it is in) settings > configure k3b (or something like that) set k3b user permissions so that normal users can run k3b.
Then try to run k3b as a normal user (either from the terminal or from the GUI launcher) and see if it works ok.

---

### Post by egalvan on 2010-06-08
> **tommcd said:**
> Try running k3b with sudo privileges then. Open a terminal and run 
```
sudo k3b
```

k3b is a graphical application.

take care when running it with sudo, as this can cause changes in the ownership/permissions of user files/directorires.

graphical apps are better run with "graphical" sudo

```
gksudo k3b
```

note that this is the gnome version...
kde uses another command...

---

### Post by 4Orbs on 2010-06-08
Here is another important point to consider. Because K3b default temporary folder is located in the root filesystem, you need to be sure and have plenty of empty space in your root partition to handle temp files which could be very large (such as 1:1 copies of a dvd), at least 10 GB available for temp files is normally recommended by other apps like dvd-rip, Handbrake, etc. Those apps usually use the user's personal /home folder for temp storage, which is more likely to have plenty of extra space available. It is not uncommon for people to install Ubuntu with separate root and /home partitions. Often the root partition is too small to allow for large temporary files in the /usr/share/tmp directory.

You can specify a different temp directory in the K3b settings, which is what I do when I first install K3b in Xubuntu. Doing this, however, will cause permission errors for any other user accounts who attempt to use K3b.

---

