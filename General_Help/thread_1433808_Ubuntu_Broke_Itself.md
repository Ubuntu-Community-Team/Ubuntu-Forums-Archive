---
title: "Ubuntu Broke Itself"
date: 2010-03-19
forum: General Help
---

### Post by Rocket J Squirrel on 2010-03-19
This morning Ubuntu had a message on the screen that it needed to be restarted. I restarted the computer and selected 2.6.31-20-generic, but then received 

error: You need to load the kernel first. Failed to boot default entries. Press any key to continue. 

If I select "recovery mode" I get

error: You need to load the kernel first. Press any key to continue. 

Ubuntu does boot to 2.6.31-19-generic

When I did that, I saw the "crash" icon and ubuntu wanted to upload the crash report, which I let it do.

How do I repair ubuntu?

---

### Post by ajgreeny on 2010-03-19
It would seem likely that you updated and a new kernel was installed but not done properly, for some reason.  So start in the 2.6.31-19 kernel, and use synaptic to search for and remove completely the 2.6.31-20 version, and any other 2.6.31-20 items also installed.

I suggest you now remove the .deb file for the 2.6.31-20 kernel from your cache, /var/cache/apt/archives, (you will have to do this as root, I suggest gksudo nautilus) as it is possible that it may be corrupt in some way.

Now reboot; this may not be necessary, but could be, so worth doing, I think.

Now install the 2.6.31-20 kernel again along with the other items you just uninstalled.  That should, in theory, get you back to the position of being able to boot to the -20 version.

---

### Post by Rocket J Squirrel on 2010-03-19
Thank you ajgreeny. Some questions: 

> **ajgreeny said:**
> It would seem likely that you updated and a new kernel was installed but not done properly, for some reason.  So start in the 2.6.31-19 kernel, and use synaptic to search for and remove completely the 2.6.31-20 version, and any other 2.6.31-20 items also installed.

Pretty new to ubuntu and synaptic, I've used synaptics to get packages but don't know how to focus it on this task and get it to remove the stuff. 

> **ajgreeny said:**
> I suggest you now remove the .deb file for the 2.6.31-20 kernel from your cache, /var/cache/apt/archives, (you will have to do this as root, I suggest gksudo nautilus) as it is possible that it may be corrupt in some way.

Sounds straightforward, and can do.

Now reboot; this may not be necessary, but could be, so worth doing, I think.

> **ajgreeny said:**
> Now install the 2.6.31-20 kernel again along with the other items you just uninstalled.  That should, in theory, get you back to the position of being able to boot to the -20 version.

Easy for you to say! A little more detail possible?

I greatly appreciate the help.

---

### Post by eriktheblu on 2010-03-19
> **Rocket J Squirrel said:**
> Pretty new to ubuntu and synaptic, I've used synaptics to get packages but don't know how to focus it on this task and get it to remove the stuff. 
Same way you install stuff. Find the package, mark for removal.

> 
Easy for you to say! A little more detail possible?


Just run the update manager like normal.

---

### Post by Rocket J Squirrel on 2010-03-19
Oh, okay. Or how about just updating to 10.04 beta? Can the system leapfrog over the broken 2.6.31-20 version?

---

### Post by Rocket J Squirrel on 2010-03-19
Following ajgreeny's approach, gksudo nautilus returned:

Initializing nautilus-gdu extension

** (nautilus:2481): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2481): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2481): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

----------------
Hesitant about embarking on the package removal and re-install with that. Abort, Retry, Continue?

---

### Post by Rocket J Squirrel on 2010-03-19
/var/lib/samba/ is empty -- there is no usershares

So whatever gksudo nautilus was trying to do, it can't.

---

### Post by Rocket J Squirrel on 2010-03-20
Okay, 

1. I are an idiot. Not getting any answers to my questions, above, I decided to install ubuntu 10.04 beta. This because I was tired last night and somehow got it into my head that Linux = ubuntu and that upgrading to 10.04 I would bypass the problem of not being able to load 2.6.31-20-generic, which was my original problem. 

2. The upgrade seemed to go well, but after restarting the computer, 2.6.31-20-generic still would not load, as previously described. So I loaded 2.6.31-19-generic.

3. Ubuntu managed to load as far as the wallpaper, then stopped dead. 

I reckon I'm going to remove ubuntu from the machine (Windows 7 dual-boot) and start over with a fresh wubi install. No sense trying to tinker around with a broken install with as little knowledge as I have and as little support as I've been able to find.

---

### Post by ajgreeny on 2010-03-20
> I reckon I'm going to remove ubuntu from the machine (Windows 7 dual-boot) and start over with a fresh wubi install. No sense trying to tinker around with a broken install with as little knowledge as I have and as little support as I've been able to find.A few comments, suggestions and questions.

Don't forget that no-one here answering is paid to do so, and it is done because we enjoy helping where we can, so your noted comment about lack of support is a bit speedy.

Was the install in question also a wubi install?  If so, you should have said so at the start, as it can make a huge difference to answers given.

I would suggest that you do not use a wubi install if you want to use ubuntu seriously as your main OS, either now, or in the future. It is really only meant as a way to check out the system before a proper install on a separate partition.

When I suggested using synaptic to remove packages, I assumed you knew how to use it and the search facility available in it.  Just click on the search button and enter 2.6.31-20, then click on any packages that appear, and are shown as installed (green square icon showing), and choose to remove completely.

When I talked about re-installing the 2.6.31-20 kernel, I should have simply realised that an update would do it for you, so just allow the system to update as normal and all should be OK; the removed version of the kernel should be re-installed automatically.

If you are having problems with the current stable version of ubuntu 9.10, now is not the right moment to try the unstable beta version of a ubuntu not yet released as a new version as this may cause you even more headaches.

Finally I would say, stick with ubuntu and be prepared to learn.  It may be a hard climb at the start, but believe me, it is definitely worth it.

---

### Post by Rocket J Squirrel on 2010-03-20
Please, I don't think anyone here is under any obligation to assist me.  That was not what I was trying to suggest. If it sounded otherwise, I apologize. It is the very nature of free community support that makes it a sometimes hit or miss proposition. 

I'm bored with Windows. I expected some  speedbumps along the way and have no issue with having it stripped off the machine and then  doing a re-install. I only had ubuntu on for a couple weeks and  installed it with wubi for the reason you suggested: to test drive it. I'm  not giving up. 

Sorry I didn't mention it was a wubi install, I didn't know that  mattered. 

I managed to break it myself and I'm willing to have another go at it. 

> **ajgreeny said:**
> When I suggested using synaptic to remove packages, I assumed you knew how to use it and the search facility available in it.  

Oh, there's the problem. You thought I knew what I was doing! I did not mean to give that impression. Not in the least. My last exposure to *nix was in mid '80s. After that my company went to Windows. And unbuntu? Forget it -- no idea at all what I'm doing. 

> **ajgreeny said:**
> Just click on the search button and enter 2.6.31-20, then click on any packages that appear, and are shown as installed (green square icon showing), and choose to remove completely.

Ah well, water under the bridge, now that the 10.04 beta has been installed and won't even last. _Unless I miss my guess, my best hope is to strip off the ubuntu partition and start over. _

I initially had a lot of trouble with unreliable wireless, I posted for help in the wireless forum, no one was able to help me, but I sorted it out on my very own. (I'm glad I posted the solution, too, as I'll probably need it again.) 

Alas, once 2.6.31-20-generic got broken (this thread's original topic) the wireless got conked again. Until I'm certain the wireless is stable I can't devote the machine to ubuntu as I use it on the road. 

> **ajgreeny said:**
> When I talked about re-installing the 2.6.31-20 kernel, I should have simply realised that an update would do it for you, so just allow the system to update as normal and all should be OK; the removed version of the kernel should be re-installed automatically.

Water under the bridge. Too late now, I reckon. 

> **ajgreeny said:**
> If you are having problems with the current stable version of ubuntu 9.10, now is not the right moment to try the unstable beta version of a ubuntu not yet released as a new version as this may cause you even more headaches.

Yeah, it was a bonehead move to update ubuntu when Linux was looking unstable. That was my own darn fault and I know it. 

> **ajgreeny said:**
> Finally I would say, stick with ubuntu and be prepared to learn.  It may be a hard climb at the start, but believe me, it is definitely worth it.

The advantage of the wubi dual boot thing is that it gives me a fallback while doing the learning curve. This isn't exactly a mission-critical machine, so if I get things tangled up it's not the end of the world, but I do want to be able to use it while I sort things out. My hope is to get ubuntu working well and have enough familiarity with it that I can toss W7.

I appreciate the time and help you've given. I'm sorry if I sounded ungrateful.

---

