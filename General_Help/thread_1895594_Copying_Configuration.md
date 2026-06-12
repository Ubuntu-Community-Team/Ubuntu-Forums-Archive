---
title: "Copying Configuration"
date: 2011-12-15
forum: General Help
---

### Post by cbennett926 on 2011-12-15
Hello,

I was wondering, and I didn't know where this was supposed to go so feel free to move this thread I apologize in advance, if there is a way to transfer my WUBI configuration to a new PC. I will be buying a System76 in a few weeks and was wondering if I could transfer my WUBI to a full install I.E. my programs and configurations over. 


Thanks in advance as well, 

Cody Bennett

---

### Post by SlugSlug on 2011-12-15
My advise would be to copy the contents of your /home/user

and then copy the /etc/config.files over as and when u need them (IE when you install the programs)

---

### Post by yetiman64 on 2011-12-15
Have a look at [[COLOR=Blue]--this link--[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1519354"), I think it is what you're aiming for[COLOR=Blue][COLOR=Black].
[/COLOR][/COLOR]

---

### Post by cbennett926 on 2011-12-15
Well, I think the first poster was the closest. I apologize if I wasn't clear about my intentions, I want to move the configuration of a WUBI installation (Installed programs, music, background, internet preferences etc.) to another full install of Ubuntu.

---

### Post by drmrgd on 2011-12-15
You might also try something like [remastersys]("http://www.geekconnection.org/remastersys/"), which will create a backup CD that you can use to install on a new system.  I've not yet personally used it, but I've a lot of great things about it.  I think [clonezilla]("http://clonezilla.org/") might be something else worth looking at.  

Both of those options should be able to fully back up your current Ubuntu install and allow you to do a full install on another box later.

---

### Post by Mark Phelps on 2011-12-15
Don't know about remastersys, as I don't use it, but unless you use Clonezilla to back up files, not to save an image, that's not going to work.  Wubi is stored in a single file in a Windows partition.  Imaging it off is only going to allow the restore of the same file -- not what you want.

---

### Post by MartijnNL on 2011-12-15
> **drmrgd said:**
> You might also try something like [remastersys]("http://www.geekconnection.org/remastersys/"), which will create a backup CD that you can use to install on a new system.  I've not yet personally used it, but I've a lot of great things about it.  I think [clonezilla]("http://clonezilla.org/") might be something else worth looking at.  

Both of those options should be able to fully back up your current Ubuntu install and allow you to do a full install on another box later.

He's talking about a WUBI install, not a normal Ubuntu installation.

And by the way I think using Clonezilla or other disk imaging software to copy an installation to another pc with different hardware is unwise.

---

### Post by cbennett926 on 2011-12-15
Alas, 

I think I may have to just write down the programs and back-up the files and put the files on the new machine. Thanks for all your help though!

---

### Post by Synoc on 2011-12-15
Alas, there is no good way. As haz been said clonezilla will not work,  the hardware must be the same. Do back up the /home folder. All users' documents and other personal info is stored there.

---

