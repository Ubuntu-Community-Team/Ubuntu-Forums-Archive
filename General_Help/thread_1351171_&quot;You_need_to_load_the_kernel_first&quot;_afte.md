---
title: "&quot;You need to load the kernel first&quot; after update"
date: 2009-12-10
forum: General Help
---

### Post by mlsquad on 2009-12-10
I installed the latest kernel updates this morning and now when I boot with Linux 2.6.31-16-generic I get "You need to load the kernel first."  If I boot with Ubuntu, Linux 2.6.31-14-generic boots fine.  Attached is my grub.cfg.  I am running Ubuntu Karmic 9.10.

---

### Post by buteomont on 2009-12-13
I'm having the same problem.  Version 2.6.31-14-generic still works, but the 2.6.31-16-generic says "Error, you need to load the kernel first."  :(

David

---

### Post by mlsquad on 2009-12-13
> **buteomont said:**
> I'm having the same problem.  Version 2.6.31-14-generic still works, but the 2.6.31-16-generic says "Error, you need to load the kernel first."  :(

DavidThis is on a Wubi install.  Is your install also via Wubi?

---

### Post by buteomont on 2009-12-20
I don't even know what a Wubi is. But I finally fixed the problem - I _moved_ all of the files in the /boot directory that ended in "-16-generic" to a temporary directory, and then _copied_ them back.  I then ran **update-grub**, followed by **grub-install /dev/sda**.  I can now boot into the new 2.6.31-16 kernel. 

Hope everyone that has this problem finds it this easy to fix.

David

---

### Post by mlsquad on 2009-12-20
More about Wubi at [http://wubi-installer.org/](http://wubi-installer.org/)
I'm excited that you found a fix.  I look forward to giving this a shot on Monday.

---

### Post by Gtklocker on 2009-12-20
> **mlsquad said:**
> I installed the latest kernel updates this morning and now when I boot with Linux 2.6.31-16-generic I get "You need to load the kernel first."  If I boot with Ubuntu, Linux 2.6.31-14-generic boots fine.  Attached is my grub.cfg.  I am running Ubuntu Karmic 9.10.

> **buteomont said:**
> I'm having the same problem.  Version 2.6.31-14-generic still works, but the 2.6.31-16-generic says "Error, you need to load the kernel first."  :(

David

Try to get on your desktop by the previous kernel at recovery mode, take yourself at a terminal and:

```
apt-get update
apt-get upgrade
apt-get dist-upgrade
```

May devolopers have put a new update solving this :)

---

### Post by ExpressNature on 2009-12-20
I don't know much about ubuntu. Last two previous updates does not caused problems. But yesterday I updated resulted in GRUB shell. I don't know what to do next. How to boot or load ubuntu 9.10? :confused:

---

### Post by mlsquad on 2009-12-20
> **ExpressNature said:**
> I don't know much about ubuntu. Last two previous updates does not caused problems. But yesterday I updated resulted in GRUB shell. I don't know what to do next. How to boot or load ubuntu 9.10? :confused:

Did you get the error message posted in this thread?  If not, please start a new thread and document exactly what you get on boot up along with any error message you might be receiving.

---

### Post by indian_gamer2003 on 2010-01-12
update-grub worked for me, thanks!

---

### Post by Technical on 2010-03-10
I've tried both Kubuntu and Ubuntu with wubi.
I'm getting the "You need to load the kernel first" with all options (2.6.31-14-generic and 2.6.31-20-generic), some days ago I got the same for 2.6.31-19-generic.
The problem must be in the beta version of Grub.
It's a shame that we have such an instable release.
I've lost all my files and settings on wubi.
Tried to install 4 times, lose time...
I've tried to install a virtual machine having Windows 7 as host. The same.

My self-confidence on this distro...
It's not the first time I need to install all over again...

---

### Post by mlsquad on 2010-03-10
> **Technical said:**
> I've tried both Kubuntu and Ubuntu with wubi.
I'm getting the "You need to load the kernel first" with all options (2.6.31-14-generic and 2.6.31-20-generic), some days ago I got the same for 2.6.31-19-generic.
The problem must be in the beta version of Grub.
It's a shame that we have such an instable release.
I've lost all my files and settings on wubi.
Tried to install 4 times, lose time...
I've tried to install a virtual machine having Windows 7 as host. The same.

My self-confidence on this distro...
It's not the first time I need to install all over again...
The problem is not in Ubuntu.  It is in Wubi.  A native install of Ubuntu 9.10 will give you a very stable experience.
I used to run 9.10 with Wubi at work and ran into all sorts of problems.  I converted over to a full install and everything has been really great ever since.

---

### Post by Technical on 2010-03-11
I can't believe I'm alone with this...
Am I the only one who couldn't install wubi at all?
I mean, I can install, just Ubuntu and Kubuntu fail to load.

Edited: Thanks mlsquad. But I've tried to install Kubuntu in a virtual machine and it failed also with the same error message.

---

### Post by mlsquad on 2010-03-11
> **Technical said:**
> I can't believe I'm alone with this...
Am I the only one who couldn't install wubi at all?
I mean, I can install, just Ubuntu and Kubuntu fail to load.

Edited: Thanks mlsquad. But I've tried to install Kubuntu in a virtual machine and it failed also with the same error message.Out of curiosity, are you sure that you are using the final release CD.  This was a [known issue]("https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/387326") in one of the pre-release CDs.

---

### Post by Technical on 2010-03-11
> **mlsquad said:**
> Out of curiosity, are you sure that you are using the final release CD.  This was a [known issue]("https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/387326") in one of the pre-release CDs.
Of course. I've downloaded the iso files today...

---

### Post by Technical on 2010-03-12
Wubi has a problem.
No files into grub folder. No grup.cfg for instance.
I have root.disk and swap.disk files.

How can I troubleshoot?
Isn't there anybody that could help me?

---

### Post by mlsquad on 2010-03-12
> **Technical said:**
> Wubi has a problem.
No files into grub folder. No grup.cfg for instance.
I have root.disk and swap.disk files.

How can I troubleshoot?
Isn't there anybody that could help me?What does the sentence "No files into grub folder." mean?  I assume you are trying to say, "There are no files in the grub folder."  Which grub folder are you talking about?
root.disk and swap.disk are not in any grub folder.  They are on your Windows drive at c:\ubuntu\disks.  That is what you are supposed to have in there.
Are you saying that the folder /boot/grub within Linux is empty?

---

### Post by Technical on 2010-03-12
> **mlsquad said:**
> What does the sentence "No files into grub folder." mean?  I assume you are trying to say, "There are no files in the grub folder."  Which grub folder are you talking about?
Sorry. I mean what you've guess. There is no files into C:\ubuntu\...\grub folder.

> **mlsquad said:**
> What does the sentence "No files into grub 
root.disk and swap.disk are not in any grub folder.  They are on your Windows drive at c:\ubuntu\disks.  That is what you are supposed to have in there.
Yes. They were there, into C:\ubuntu\disks folder.

> **mlsquad said:**
> What does the sentence "No files into 
Are you saying that the folder /boot/grub within Linux is empty?
Yes, I am.
Now I've uninstalled wubi (and kubuntu).
2.6.31-19-generic and 2.6.31-14-generic kernels aren't loading anyway (not even in the recovery mode).
By the way, Windows is not loading by grub also. Is there anything wrong in the partition identification?

---

### Post by mlsquad on 2010-03-12
There should not be any files under C:\ubuntu\disks\boot\grub, so that is normal.
If you have uninstalled Wubi, then the folder c:\ubuntu should be gone, and when you boot Ubuntu should not be an option.  Your computer should just boot right up into Windows like normal.

---

### Post by Technical on 2010-03-12
> **mlsquad said:**
> There should not be any files under C:\ubuntu\disks\boot\grub, so that is normal.
Thanks.

> **mlsquad said:**
> There should not be any files under 
If you have uninstalled Wubi, then the folder c:\ubuntu should be gone, and when you boot Ubuntu should not be an option.  Your computer should just boot right up into Windows like normal.
Of course, but I want wubi back and I'm not being able due to this error: "You need to load the kernel first".

---

### Post by mlsquad on 2010-03-12
> **Technical said:**
> Thanks.


Of course, but I want wubi back and I'm not being able due to this error: "You need to load the kernel first".

I really wouldn't recommend anyone run Ubuntu 9.10 with Wubi.  I did it as my main development station and work and it was a very bad experience.  I had problems that went well beyond the grub2 issues.
I would recommend either running 9.04 with Wubi (which was always a good experience for me) or creating a separate partition for Ubuntu.

---

### Post by Technical on 2010-03-12
Thanks, but right now... wubi does not offer configuration options... I'll have to download the old 9.04 iso and find the old 9.04 wubi...

Seems that I'll have to wait for 10.04 version.
Right now, I'm using the stable Linux Mint instead of (k)Ubuntu.

---

### Post by mlsquad on 2010-03-12
> **Technical said:**
> Thanks, but right now... wubi does not offer configuration options... I'll have to download the old 9.04 iso and find the old 9.04 wubi...

Seems that I'll have to wait for 10.04 version.
Right now, I'm using the stable Linux Mint instead of (k)Ubuntu.

You can get it at [http://releases.ubuntu.com/9.04/wubi.exe](http://releases.ubuntu.com/9.04/wubi.exe)

---

### Post by Technical on 2010-03-14
You cannot use Wubi 9.04 anymore...
Cannot download the metalink and the ISO therefore.

Wubi is becoming a failure to get Kubuntu running...

---

### Post by abrarkiani on 2010-03-18
i install ubuntu 9.10 weubi with xp on my d:/drive 
after update the ubuntu wont boot
i select ubuntu from list and kernel 2.6.31-16-generic it gave an error 
"you need to load the kernel first"
please help its urgent

---

### Post by drs305 on 2010-03-18
> **abrarkiani said:**
> i install ubuntu 9.10 weubi with xp on my d:/drive 
after update the ubuntu wont boot
i select ubuntu from list and kernel 2.6.31-16-generic it gave an error 
"you need to load the kernel first"
please help its urgent

Based on the information you have provided, take a look at this fix to a bug in wubi 9.10:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

Please let us know if this fixed the problem.

---

### Post by Technical on 2010-03-18
I've lost everything...
The only way to install is downloading kubuntu iso 9.04 and the old wubi 9.04 and putting them in the same folder.
Install wubi 9.04.
Upgrade the the installed Kubuntu from 9.04 to 9.10.

---

### Post by zespri on 2010-03-25
This is what helped me: [https://answers.launchpad.net/ubuntu/+question/104757](https://answers.launchpad.net/ubuntu/+question/104757)

---

### Post by degenerate32 on 2010-07-10
Hey guys. I am new to this forum. I have the same problem and I am unable to fix it. I 've tried to with the solution provided to the and of this site:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)
but I have the ubuntu installed in a USB stick and there are unreadable from windows. 

Bear in mind that I cannot open any of the installed ubuntu versions, nor the recovery modes! What should I do? Please help me, thank's in advance..

---

