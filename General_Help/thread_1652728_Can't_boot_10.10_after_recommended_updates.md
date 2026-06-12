---
title: "Can't boot 10.10 after recommended updates"
date: 2010-12-25
forum: General Help
---

### Post by kat9505 on 2010-12-25
I have Ubuntu 10.10 but I can only use Windows 7 now (I hate it). Here's why: when I go to the boot screen and I am given the choice of using Windows 7 or Ubuntu and I select Ubuntu, the screen goes black and says:

error: unknown command 'loadfont'
error: file not found

Then I have to reset my laptop and use Windows 7. This happened when I was using Ubuntu like I usually did and I downloaded recommended updates from Ubuntu. I downloaded them and I was asked to reset my laptop for it to be effective. I did and when the boot screen came up it said what it says above. I can't even get to the login screen. I've been searching everywhere for an answer. Please help, I miss Ubuntu so much.

Thanks in advance, Kat.

*If you need more info, please ask.

---

### Post by Rubi1200 on 2010-12-25
Hi and welcome to the forums :)

Did you install Ubuntu inside Windows using Wubi?

If yes, see here for Wubi issues and solutions:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

problem #2, solution relevant to your situation.

---

### Post by kat9505 on 2010-12-25
> **Rubi1200 said:**
> Hi and welcome to the forums :)

Did you install Ubuntu inside Windows using Wubi?

If yes, see here for Wubi issues and solutions:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

problem #2, solution relevant to your situation.


I can use this even though I didn't update from one version of Ubuntu to another (like Ubuntu 10.04 to 10.10)? Because these were just updates on 10.10, not upgrading to 10.10. And thanks for the welcome :p

---

### Post by Rubi1200 on 2010-12-25
If you recently downloaded and installed via Wubi it was actually the 10.04.1 version and not 10.10 as the website seems to indicate.

In your situation, use solution #1

If you need more help or if anything is unclear, let me know.

---

### Post by kat9505 on 2010-12-25
> **Rubi1200 said:**
> If you recently downloaded and installed via Wubi it was actually the 10.04.1 version and not 10.10 as the website seems to indicate.

In your situation, use solution #1

If you need more help or if anything is unclear, let me know.


I installed Ubuntu onto my laptop using one of the official disks from Linux. If that helps should I use solution #1 or#2?

---

### Post by Rubi1200 on 2010-12-25
To be clear, was this _definitely_ a Wubi install?

If yes, boot the laptop with the CD, choosing to try not install and then follow the instructions in the thread for solution #1.

If you want to make sure, boot the laptop as above and at the live desktop go to Applications > Accessories > Terminal and run this command:

```
 sudo parted -l
```

(lowercase L not 1)
Copy/paste the output and post it here so we can advise you further.

Thanks.

---

### Post by kat9505 on 2010-12-25
> **Rubi1200 said:**
> To be clear, was this _definitely_ a Wubi install?

If yes, boot the laptop with the CD, choosing to try not install and then follow the instructions in the thread for solution #1.

If you want to make sure, boot the laptop as above and at the live desktop go to Applications > Accessories > Terminal and run this command:

```
 sudo parted -l
```(lowercase L not 1)
Copy/paste the output and post it here so we can advise you further.

Thanks.


Is there a way that I can just uninstall Ubuntu and reinstall it? Since I can't get into Ubuntu there's no way I can back up my files is there? (I'm finding this a bit complicated). And what does "loop mount" mean in solution #1 mean?

---

### Post by Rubi1200 on 2010-12-25
You could do that; it is always an option.

However, there is a way to fix this and we can be done in less than an hour. 

I am more than willing to walk you through it step by step if you decide to do this.

If all of the above seems overwhelming, you can recover your data from the Wubi install from _within_ Windows. In this case, you can use [ext2read]("http://ext2read.blogspot.com/") to recover any important data from the Ubuntu root.disk. 

But, the next time you install Wubi and there is an update you will find yourself in the same/similar situation.

To avoid that, you can do this if you reinstall completely:
prevent GRUB updates from breaking the Wubi install again:

Go to System > Administration > Synaptic Package Manager and  select the grub-pc and grub-common packages. Click on Package > Lock  Version.

Let me know what you decide.

Also, do not let this put you off trying Ubuntu, or Linux in general. This is a specific issue affecting Wubi installs at the moment.
There are also fixes of course.

---

### Post by veggen on 2010-12-25
Sure you can, just boot from a live disk and copy the files somewhere.
But you should, for now at least, listen to the previous advice(s), since you can probably repair the damage.

---

### Post by kat9505 on 2010-12-25
Thank you very much. I'm going to try the solution (and yes it seems very overwhelming!). I've never had a problem like this so it is very new to me. What does "loop mount" mean on solution #1?

---

### Post by Rubi1200 on 2010-12-25
It means you can access the Wubi virtual disk even though you are not actually booted into Ubuntu.

I would still like you to run the code I posted before you do anything just so we can be sure:
```
sudo parted -l
```

Thanks.

---

