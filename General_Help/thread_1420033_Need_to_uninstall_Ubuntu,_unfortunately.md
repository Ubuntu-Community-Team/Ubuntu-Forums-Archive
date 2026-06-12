---
title: "Need to uninstall Ubuntu, unfortunately"
date: 2010-03-02
forum: General Help
---

### Post by hedgeberg on 2010-03-02
Recently, I downloaded Ubuntu to my Dell inspiron 1525. I spent a long time trying to get it to work, and finally managed to get the wi-fi functional. Unfortunately, now I can't run windows. As much as I hate it, (unless you know any alternatives), I have to uninstall ubuntu, without being able to boot into windows. Does anyone know how to do this?

---

### Post by pricetech on 2010-03-02
Did you install Ubuntu in a dual boot configuration or did you use the entire hard drive for Ubuntu ??  If you dual booted, you should be able to get access to your winders install by making sure there is an entry for it in grub, which there should already be if you installed as a dual boot.

Another alternative is to install winders in a Virtual Machine.  Install Virtual Box OSE from the repos or download the non Open Source version from virtualbox.org and install it.  After that, you install winders using Virtual Box.

If you have to have winders outside of a VM, which is possible depending on what you'll be doing with it, then you'll have to make space for it on the hard drive and install it back on the computer, then fix grub to boot both.

Guides for whatever you decide to do are posted here on the forums, but you need to decide what you're going to do before you start, though it might well be worth looking at the howtos to help you decide.

---

### Post by hedgeberg on 2010-03-02
I am using dual boot. I have access to all of my old files, and AFTER I start up windows it screws up.  I believe that (once again, unfortunately), my only option is to uninstall ubuntu. is this the right way to go about this? Unfortunately, I have until the end of the week to fix this, and i have limited time to work with my computer. as such, What procedure takes the least time?

---

### Post by mikewhatever on 2010-03-02
You can delete the Ubuntu partition, in fact, any partition, with Gparted, while running from the live cd. That said, I don't really understand what the problem with Windows has to do with Ubuntu. Anyway, best of luck.

---

### Post by mechro on 2010-03-02
> **mikewhatever said:**
> That said, I don't really understand what the problem with Windows has to do with Ubuntu. Anyway, best of luck.

Perhaps hedgeberg has a Wubi installation and not a dual boot.

hedgeberg... if it's a Wubi installation then Ubuntu is "inside" Windows and you'll have to fix your Windows installation/boot first. Insert your Windows CD and do a repair using that.

---

### Post by bcbc on 2010-03-02
Don't delete your ubuntu partition - then you won't be able to boot anything. Run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post it back here.

Also, describe exactly what happens when you try and boot windows.

After you first installed ubuntu were you able to boot windows, or did it stop working immediately?

---

### Post by hedgeberg on 2010-03-02
bcdc,
heres the file. the weirdest part is that it seemed to stop working immediately. For a while, what would happen is I would open vista, and it would show the loading bar for a few seconds, and then I would get the blue screen of death. due to my computers settings, it immediately restarted. like mechro suggested, i have already run system repair. however, now when I boot vista it will load for a longer time then usual, and then the screen will go black with the cursor in the middle of the screen. This is when the login screen should appear. I have the feeling that ubuntu is still loading in the windows partition, but i don't know how to fix it. heres the boot log [ATTACH]148804[/ATTACH] . I want to uninstall ubuntu, but i can try to fix the partition first, and see what happens. can anyone help me with this as i can't understand gparted.

---

### Post by hedgeberg on 2010-03-02
oh, mechro, when you say the windows cd, do you mean the drivers?

---

### Post by bcbc on 2010-03-02
Since you are using wubi, I think you need to try what mechro suggests - repair Vista using the recovery CD. This shouldn't have any impact on your wubi install, and you should be able to use this after you fix vista.

Since you can boot ubuntu now and see your drives - it's probably a good idea to backup your data first.

---

### Post by hedgeberg on 2010-03-03
when i run the disk, it gives me the option to install vista. if i do this, is there a risk of losing files? or will i keep everything?

---

### Post by bcbc on 2010-03-03
> **hedgeberg said:**
> when i run the disk, it gives me the option to install vista. if i do this, is there a risk of losing files? or will i keep everything?
You should have a 'Repair your computer' option. Here's something I found on the web that might help: [http://www.bleepingcomputer.com/tutorials/tutorial148.html]("http://www.bleepingcomputer.com/tutorials/tutorial148.html")

One thing I've found really useful on XP and Vista is System Restore. It rolls back updates without destroying your own data. If the automated repair doesn't find anything, maybe this will help. It rolls back everything including windows updates. Just pick a date prior to your wubi install.

---

### Post by hedgeberg on 2010-03-03
no dice. the only thing thats an option on the disk that would do anything is to install. I have tried startup repair. there were, unfortunately, no restore points, either. as such, i need to bring up this again. i have found a way to uninstall ubuntu, i believe. The question is whether or not it will help. if I were to uninstall ubuntu, would this fix the problem?

---

### Post by bcbc on 2010-03-03
> **hedgeberg said:**
> no dice. the only thing thats an option on the disk that would do anything is to install. I have tried startup repair. there were, unfortunately, no restore points, either. as such, i need to bring up this again. i have found a way to uninstall ubuntu, i believe. The question is whether or not it will help. if I were to uninstall ubuntu, would this fix the problem?
I don't see how this can help since you have installed wubi. It's just a file on your ntfs system that's being virtually loaded as a drive.

Anyway - I'm about out of ideas - maybe you can try this: [http://support.microsoft.com/kb/927392/en-us]("http://support.microsoft.com/kb/927392/en-us")

---

### Post by mechro on 2010-03-03
> **hedgeberg said:**
> no dice. the only thing thats an option on the disk that would do anything is to install. I have tried startup repair. there were, unfortunately, no restore points, either. as such, i need to bring up this again. i have found a way to uninstall ubuntu, i believe. The question is whether or not it will help. if I were to uninstall ubuntu, would this fix the problem?

Try your "way to uninstall Ubuntu", it may or may not work... without knowing the full details of this "way" I doubt that anybody could tell you if it will fix your non-booting Windows problem.

If you're not sure whether you have an official Windows Vista disc (perhaps it's a Dell recovery disc) then you can download an ISO (file to burn to CD) containing Vista's repair/recovery tools from here...

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by hedgeberg on 2010-03-03
my way of uninstalling ubuntu is rather interesting. the basic concept is that when i download wubi and run it with wine on ubuntu, it doesn't work. However, when i access my windows downloads, and run that with wine, it asks if i want to uninstall. Also, using this website: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide), I found that i can unsinstall it manually if that doesn't work. I am taking enormous precautions in case it doesn't. ill see if this works. Wish me luck!

---

### Post by pricetech on 2010-03-04
> **hedgeberg said:**
> my way of uninstalling ubuntu is rather interesting. the basic concept is that when i download wubi and run it with wine on ubuntu, it doesn't work. However, when i access my windows downloads, and run that with wine, it asks if i want to uninstall. Also, using this website: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide), I found that i can unsinstall it manually if that doesn't work. I am taking enormous precautions in case it doesn't. ill see if this works. Wish me luck!

Whaaat ?????

I've never run Wubi, but running it under Wine in Ubuntu makes no sense at all.

If you're trying to get winders back, just use the Ubuntu live CD to salvage your data and then install winders back using your restore / install disk.  Once you have that done, and everything updated, then if you want Ubuntu back, I suggest a dual boot, not Wubi.

---

### Post by Mark Phelps on 2010-03-04
If your Vista CD came with the machine, presuming Vista was preinstalled, then it's most probably a Restore CD -- meaning it will wipe the drive, removing ALL the files, and restore Vista back to it's original condition.  This doesn't sound like what you want.

If you haven't already, use the NeoSmart Technology link to download and burn a Vista Repair CD.

You will need to boot from this and select Startup Repair several times.  It only finds and repairs one problem at a time. It could take three passes for it to find an repair all the boot problems.

---

### Post by hedgeberg on 2010-03-06
My method did not work. Now, as to a "neo smart technology link", would you mind providing this, as I have no idea what you mean. Also, would a system repair disk do anything different from what has already been suggested? I have tried a system repair, and it has not worked. at this point i am backing up my files, so i will probably wipe the disk and just bring all my files back in.

---

### Post by mechro on 2010-03-07
> **hedgeberg said:**
> My method did not work. Now, as to a "neo smart technology link", would you mind providing this, as I have no idea what you mean. Also, would a system repair disk do anything different from what has already been suggested? I have tried a system repair, and it has not worked. at this point i am backing up my files, so i will probably wipe the disk and just bring all my files back in.

The link is in my post above (#14 in the thread).

---

