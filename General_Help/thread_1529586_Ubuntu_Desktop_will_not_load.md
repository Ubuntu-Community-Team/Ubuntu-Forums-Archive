---
title: "Ubuntu Desktop will not load"
date: 2010-07-12
forum: General Help
---

### Post by Chris_cur on 2010-07-12
I believe I have deleted my ubuntu-desktop. 

I have 10.04 Lucid installed. My computer loads fine up to the splash login screen. After entering my password the screen goes black, my mouse still shows and is movable. Then I get returned back to my login screen again.

I have tried to get a recovery console by pressing combination Ctrl+Alt+F1 through F6, only thing that happens is my mouse disappears until I return back with Ctrl+Alt+F7.

I can not find any other way to boot in recovery mode or failsafe mode. Is there any other way to get to a console so that I can re-install Ubuntu-desktop? I have not found any other fixes.

I really need to get this running again. And, no, I did not back up like a good user should. I can access *SOME* of my files and folders when I boot with my bootable thumbdrive, but not all the important files I need to pull off, it says I do not have permission.

Main issue: How do I restore Ubuntu-desktop if I can not access console and get past login screen?

---

### Post by audiomick on 2010-07-12
Hi.
I don't know how to sort out the login, but if you boot into your thumb drive and start the file manager with

```
gksu nautlius
```

you should then have permission to pull your files off.

It might be a good idea to do this just in case before attempting to repair the system.

---

### Post by Chris_cur on 2010-07-12
Thanks Mick,

I am trying that now.

---

### Post by Chris_cur on 2010-07-12
> **Chris_cur said:**
> Thanks Mick,

I am trying that now.

That is a no-go. I get
> Nautilus could not create the following required folders:/root/Desktop, /root/.nautilus
Before running Nautilus, please create these folders or set permission such that Nautilus can create them.

---

### Post by Chris_cur on 2010-07-12
Crap! Now I can not access my HD either. I get:
> Unable to mount 491 GB Filesystem
Error creating moint point: No space left on device


and yes it says "moint" not "mount".  It is not my typo.

Goodness.

---

### Post by Chris_cur on 2010-07-12
Pressing SHIFT while booting also does not help me.  I am not dual booting so I have no grub menu that appears.

---

### Post by audiomick on 2010-07-12
Hallo again.

I just tried the gksu nautilus thing on my laptop with a 64bit 9.10 CD, and it worked.

Your error message about not being able to create a mount point sounds odd. As I understand it, the device on which it should be trying to create the mount point is the file system that is created in RAM when you boot from the live CD / thumb drive.

This raises the question for me of how much RAM your machine has?

It also suggests that you might be able to mount if you re-boot.

On the other hand, the mount failure together with the failure of 'gksu nautilus' suggests to me that there is something wrong somewhere.

Why do you think that the desktop has been deleted? Because you did something that might have led to that, or just because it wont boot?

I think the first thing I would do at this point is to run the memory check from the boot menu of the live CD (thumbdrive) to make sure the RAM is ok.

Other than that, it is a bit of a mystery to me.

---

### Post by Chris_cur on 2010-07-12
I think the desktop has been deleted because I get no desktop after my login. I perpetually login and then get booted BACK to the login screen. I have searched and searched online and though the forums and any one having a similar issue deleted the ubuntu-desktop...

I am running Test Memory from my bootable thumb drive, right now. Just off the top of my head I am sure I have 1.5G or more of RAM.

Thanks again for trying to help Mick.

---

### Post by Chris_cur on 2010-07-12
How long does it take for the Memory Test?

---

### Post by audiomick on 2010-07-12
> **Chris_cur said:**
> How long does it take for the Memory Test?
It takes a while. It does various tests one after the other, and then I think cycles back and starts again. You should let it run for a good while, maybe a couple of hours. If the RAM is good, it should show zero errors.

I think it is unlikely that your desktop is deleted. That is not something that happens all by itself. There is obviously something wrong, but I don't think the problem is the the desktop is missing.

Let the memory check run for a bit and see what it says. Then you know that at least that is good (or not).

---

### Post by Chris_cur on 2010-07-12
Mick you are being a blessing, thanks for your time. I'm not getting to far but I am learning.

> **audiomick said:**
> You should let it run for a good while, maybe a couple of hours.

I don't have hours. I have work that is due in 4 hours and two of the documents can easily take up 2 hours a piece, if I bust them out!

Goodness, goodness.

So you think I didn't delete the desktop? I was trying to remove Tomboy Notes, Empathy IM Client and Evolution Mail and Calendar. I removed those three through the synaptic package manager. I marked them for "complete removal."

That's why I think I deleted it somehow.

---

### Post by Chris_cur on 2010-07-12
I almost got somewhere. I finally was able to get GRUB to load up, I saw that there were like 6 kernels and their recovery modes. 
2.6.32-24-generic
2.6.32-23
         -22
         -21
         -20
         -19
         -17
I selected the topmost version and recovery mode. I saw code scrolling but now I only have a blank screen, no mouse, no cursor nothing....

I am going to try a different kernel, and if that doesn't work then it's recovery mode

---

### Post by audiomick on 2010-07-12
> **Chris_cur said:**
> 
I am going to try a different kernel, and if that doesn't work then it's recovery mode

Sounds like a good plan. Good luck.

---

### Post by Chris_cur on 2010-07-12
Different kernels do not work. Recovery Mode brings up a complete blank screen with no console cursor...

But Hey! Now I can get into grub!

---

