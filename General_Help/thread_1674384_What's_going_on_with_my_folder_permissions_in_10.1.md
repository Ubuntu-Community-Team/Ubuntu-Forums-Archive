---
title: "What's going on with my folder permissions in 10.10?"
date: 2011-01-23
forum: General Help
---

### Post by carusoswi on 2011-01-23
I created a file called Temp on my desktop onto which I have been storing photos opened from an external NTFS drive using Gimp.  Edits are primarily the adding of a text caption on each imaging, then, I have been saving them to this desktop/temp folder.

Gimp can open the files if I select 'recent', and I can hover the mouse over the file name under 'recent' and observe the path, but, if I explore to that folder, only one file is present.  If I use Gimp's 'open' menu selection and explore to that folder, again, only one file is showing.

I never experienced these sorts of problems in any previous version of Gimp. 

What the heck is going on?

Sorry to sound so frustrating, but I am not getting it.  This seems like a very basic operation.  Why should I be having trouble.

I wonder where those files are, really?

If I close Gimp, is my work going to be lost because I cannot locate the files on the disk?

Thanks in advance for any assistance.

Caruso

---

### Post by Vaphell on 2011-01-23
doesn't gimp save files in home directory by default?
what file type are we talking about?

drop to terminal and run this command using some file name that one of your missing pictures should have. If it's anywhere in your home directory it will find it.
```
find ~ -name <file.name>
```

---

### Post by carusoswi on 2011-01-23
I was purposely saving these files to a temp directory that I created on the Desktop so that I could copy them to a memory card for insertion into a digital photo frame.

For some reason, the Temp directory was created in a folder called Desktop in the Root directory.

I pulled the images out of there, copied them to the temp directory that is on my Desktop, then transfered them to a folder (also on the Desktop) called SD Card, and then copied the whole mess to the card itself which was mounted from a card reader.

For some reason, Ubuntu would not allow me permission to write directly to the card, so I emptied it of images, formatted it, and then copied the files back onto the card along with others from the Temp directory.

I'm wondering what has changed in 10.10, because I've never been so perplexed by folder permissions in any previous version (and I've had them all since 6.04.

. . . makes me wonder why we are provided with a GUI route to change permissions when none of the setting changes seem possible - all are denied.

What's the point.  It's as if my 10.10 installation is protecting itself from me.

The folder that wound up under Root was created by me when browsing to the Desktop, so, why it resides under Root in a manner that makes it inaccessible from the Desktop is still puzzling me.

I was able to accomplish my task, but wasted probably half an hour or so fumbling around trying to figure out where my files were hiding.

Thanks for the reply.

Still frustrated,
Caruso

---

### Post by Vaphell on 2011-01-23
how did you copy the files from the external source to your desktop? have you run nautilus as an administrator, with sudo/gksu or something like that by any chance?
try **gksu nautilus** and see that the Desktop dir there is not the same as the Desktop located in your home (this one is in /root which is the home of the root user). Probably this is what happened here, context has changed to root but you haven't noticed that.

Try to not overuse sudo if not necessary. Writing to your home dir certainly doesn't require that and may lead to confusion when you don't know exactly how things work. I understand that root rights may be somewhat required to copy stuff in the opposite direction but use them only for that. It's possible to configure system to allow ordinary users to write to external disks, flash drives, ...

[http://www.ubuntugeek.com/mount-manager-user-friendly-management-of-disks-and-partitions.html](http://www.ubuntugeek.com/mount-manager-user-friendly-management-of-disks-and-partitions.html)
check this out, maybe this will help you to sort things out with access issues.

---

### Post by carusoswi on 2011-01-24
All I wanted to do, initially, was open the DPF card as a folder, load selected photos into my Gimp, make some adjustments, and save them.

My children gave me the DPF as a birthday present.  They cleverly asked me for access to my photo files to pre-load the card with photos.  But, some of the photos are pre-edited versions, so I wanted to correct that.

Ubuntu refused me access to that card, and trying to change permissions, for some reason, is counter-productively difficult.  I was able to copy the images to the 'SC Card' folder that I created on my Desktop, but, again, Ubuntu was entertaining none of my desire to make that folder accessible.  Attempts to save changes to files were met with messages that access was denied.

After searching this forum, I found a bit about a program that gives you the option to access a folder as an administrator, and that allowed me to start writing to the SD Card folder, but, still, no option to make changes to files and save them, hence, the temp folder, which, finally, gave me a place where I could save changes to the files I wished to edit.

I am all for security, but, frankly, am quite annoyed that Ubuntu put this level of constraint upon me.

If the mistake was mine, let me know, and I will humbly apologize for my angst.  For the moment, I am thoroughly disgusted.

I was attempting no tasks that I have not undertaken within numerous OS's over the years.  My computer knowledge is not at the programming level, but I am certainly more than a novice.

Why should Ubuntu make simple tasks such as this so complicated?

No one can even get into my machine without my permission.  My 'user' is the only one present.

Oh, and if you are wondering, the exploration of my drive by my children were performed before I installed 10.10, so the current issues have nothing to do with their use of my system.

I am all ears towards instruction that will simplify this seemingly new wrinkle in security on my system.

I've not experienced such problems in previous versions of Linux, Ubuntu or otherwise.

Caruso

> **Vaphell said:**
> how did you copy the files from the external source to your desktop? have you run nautilus as an administrator, with sudo/gksu or something like that by any chance?
try **gksu nautilus** and see that the Desktop dir there is not the same as the Desktop located in your home (this one is in /root which is the home of the root user). Probably this is what happened here, context has changed to root but you haven't noticed that.

Try to not overuse sudo if not necessary. Writing to your home dir certainly doesn't require that and may lead to confusion when you don't know exactly how things work. I understand that root rights may be somewhat required to copy stuff in the opposite direction but use them only for that. It's possible to configure system to allow ordinary users to write to external disks, flash drives, ...

[http://www.ubuntugeek.com/mount-manager-user-friendly-management-of-disks-and-partitions.html](http://www.ubuntugeek.com/mount-manager-user-friendly-management-of-disks-and-partitions.html)
check this out, maybe this will help you to sort things out with access issues.

---

### Post by Vaphell on 2011-01-24
> Why should Ubuntu make simple tasks such as this so complicated?

it's not that complicated once you know your way around the permissions and stuff. It's more locked down that windows - that's true but that because in linux world security is not surrendered for the user's convenience. It could be easier and there are apps for that, but they are not in the default package so the user needs to find them in the repos and install.

Either way install that mountmanager app, plug your card/disk in, in terminal run mountmanager with admin rights so it will be able to save the changes made in the system configuration (gksu mountmanager) and check the settings for the device in question that causes the grief.

I see that there are options available that allow ordinary users to mount drives, give read/write permissions and such. I think your settings will be remembered so next time when you plug your storage in it will work without hassle.

That mountmanager app looks pretty straightforward, i am sure you will find what you need there.

---

### Post by carusoswi on 2011-01-25
Is this mount manager stuff new in this version.  As stated previously, I've used every version of Ubunty since 6.04, and never recall ever getting so tangled up as I did this past weekend.

I would expect that, when I initially created my folder on the desktop using the GUI without any invocation of sudo, the folder would have defaulted to read-write permission. It was an empty folder, after all.  I then copied the contents of my memory card to that folder (so, obviously, I had write permission at that point).  It was at this point that the problems started.  I found that, while I could open a file using Gimp, I could not save any edits made to the file.  I also could not open files from other locations on my system and copy or save them to the folder on my destop.

Then, and only then did I try to tinker with permissions, only to discover that the GUI provided for that purposes would not allow permission changes.

That is when I logged onto the forum to look for more info on permissions and such.

I will try the application you suggest, but I remain confused as to why I am experiencing this problem in 10.10 when I didn't experience it in previous versions.

What, exactly, is the purpose of the GUI that seems to indicate that permission changes are possible if, in fact, permissions are not allowed to be altered?

This is not making sense to me.

Sorry if I seem dense.

Thanks for your reply.

Caruso

> **Vaphell said:**
> it's not that complicated once you know your way around the permissions and stuff. It's more locked down that windows - that's true but that because in linux world security is not surrendered for the user's convenience. It could be easier and there are apps for that, but they are not in the default package so the user needs to find them in the repos and install.

Either way install that mountmanager app, plug your card/disk in, in terminal run mountmanager with admin rights so it will be able to save the changes made in the system configuration (gksu mountmanager) and check the settings for the device in question that causes the grief.

I see that there are options available that allow ordinary users to mount drives, give read/write permissions and such. I think your settings will be remembered so next time when you plug your storage in it will work without hassle.

That mountmanager app looks pretty straightforward, i am sure you will find what you need there.

---

### Post by Vaphell on 2011-01-26
i don't know why jumping through the hoops was not the case earlier. Maybe some design choice, different set of defaults - who knows. Accept it as a fact of life and move on.
You can change these defaults in fstab file manually or use the mountmanager tool that makes it easy for an inexperienced user. I don't think you really want to edit some file by hand, so go with the gui tool.

---

### Post by redmk2 on 2011-01-26
@carusoswi

> ...opened from an external NTFS drive 

I'll bet this has something to do with it.  The NTFS file system has no provisions for UNIX style permissions.  When the files opened and subsequently saved they are owned by *root *and root stores its files in its own home directory (/root).

This has always been this way.

I think you will find the DPF card is formated FAT32.  This will act the same as NTFS as far as file ownership and permissions.

---

### Post by carusoswi on 2011-01-29
I appreciate all the replies, and will excuse what seem like mild put downs (inexperienced user, etc.), and it could be that the interaction with the external memory card might be to blame, however, my system resides as a dual boot with Windows XP, and I can read/write to my NTFS partitions, my firewire external drives, and my USB external drives, all formatted NTFS without a problem.

While I was a bit frustrated, I'm not knocking Linux or Ubuntu, but it still makes no sense to me to provide a graphical interface that appears to allow me to set permissions for a device when that is not possible.

I appreciate that no rogue routine can invade my system without my permission, but I should be able to function with my own files.

I will move on, but will ever seek an explanation that makes sense to me.  Why feature that GUI if it doesn't release the medium to which you desire to read/write?

That simply doesn't make sense to me.

As mentioned previously, I've been working with Ubuntu since version 6 and never encountered this problem previously (ok, we used to have to download and install a bit of code to make NTFS drives/partitions read/writeable, but I believe that is done for us in these later versions).

Just wonderin'/thinkin', that's all.

Caruso

---

