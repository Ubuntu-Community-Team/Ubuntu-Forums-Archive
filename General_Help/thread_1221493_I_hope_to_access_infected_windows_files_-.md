---
title: "I hope to access infected windows files -"
date: 2009-07-23
forum: General Help
---

### Post by lsouth on 2009-07-23
I have just installed 9.04 (dual booting) on my Dell notebook which has been totally hijacked by ***System Security 4.52***.  I did this as a last resort. My hope is to be able to access windows files and delete the infected files. I have a list of those files and they are numerous.  Can anyone tell me how to access Windows files through ubuntu? Any help is appreciated.
Lee   :confused:

---

### Post by Finalfantasykid on 2009-07-23
If you look at the top panel under Places, you should see something like '120GB media' or something like that, which is your Windows partition.  From there you can read/write any file.

---

### Post by lsouth on 2009-07-23
Thanks! So cool for you to help an old far   fogey.
Best to 'ya.
Lee:D

---

### Post by lsouth on 2009-07-24
Sorry, but under PLACES It's not there.  I see:

Home folder, 
Desktop, 
Documents, 
Music, 
Pictures, 
Videos, 
Computer which shows only ubuntu files, 
Network, 
Connect to Server, 
Search for files  - does not find windows, and 
Recent Documents.
I could not find the hard drive.
Any other things I could look for?
Lee

---

### Post by pastalavista on 2009-07-24
Open a terminal [Applications > Accessories > Terminal] and post the output of ```
sudo fdisk -l
```

---

### Post by Finalfantasykid on 2009-07-24
You could also try checking in your /media/ folder.

For example, my windows partition is located at /media/disk

---

### Post by Tipped OuT on 2009-07-24
It's located in File System< Host.

This is where it is always located when you do an automatic dual boot installation.

---

### Post by jocko on 2009-07-24
> **Tipped OuT said:**
> It's located in File System< Host.

This is where it is always located when you do an automatic dual boot installation.
No. That's where it is if you do a wubi install (which installs ubuntu as an image file within the windows partition, which will then act as a host file system).
I don't know if an automatic dual boot installation (a real installation where ubuntu gets it's own file system and you let the installer use the default partitioning) sets up a mount point for a windows partition, but for my install, where I chose the partitioning myself, the installer suggested that my windows partition should be mounted as /windows.

---

### Post by egalvan on 2009-07-24
Can you fire up gparted and post a screen shot?

The XP drive should be under 

/mnt

or

/media


you'll find both of these under 

Places -> Computer -> File System

---

### Post by jocko on 2009-07-24
> **egalvan said:**
> Can you fire up gparted and post a screen shot?

The XP drive should be under 

/mnt

or

/media


you'll find both of these under 

Places -> Computer -> File System
Or it's under /windows

---

### Post by Tipped OuT on 2009-07-24
> **jocko said:**
> No. That's where it is if you do a wubi install (which installs ubuntu as an image file within the windows partition, which will then act as a host file system).
I don't know if an automatic dual boot installation (a real installation where ubuntu gets it's own file system and you let the installer use the default partitioning) sets up a mount point for a windows partition, but for my install, where I chose the partitioning myself, the installer suggested that my windows partition should be mounted as /windows.

I meant "automatic dual boot installation" as Wubi, or any other process that installs it like Wubi (Like Ubuntu's "Install Inside Windows" option).

The O.P. has already tried the other suggestions from the members, but no luck. So File System< Host is the only last place it could possible be.

---

### Post by jerome1232 on 2009-07-24
> **Tipped OuT said:**
> I meant "automatic dual boot installation" as Wubi, or any other process that installs it like Wubi (Like Ubuntu's "Install Inside Windows" option).

The O.P. has already tried the other suggestions from the members, but no luck. So File System< Host is the only last place it could possible be.

No.

The OP has only checked the places menu. Most likely it's not currently mounted at all. As soon as we get the output of fdisk -l we can help the op mount it though.

---

### Post by Tipped OuT on 2009-07-24
> **jerome1232 said:**
> No.

The OP has only checked the places menu. Most likely it's not currently mounted at all. As soon as we get the output of fdisk -l we can help the op mount it though.

Ah, okay. :)

---

### Post by lsouth on 2009-07-24
Thanks for all the help.  I finally found the drive and looked at properties and found Ubuntu and free space.  Windows is gone.  Probably just as well though I lost a lot of "good stuff".
Not sure what happened in installation but I checked side by side installation.  I booted again from the installation disk this morning and followed it through the analysis of the disk and found no Windows.  I exited out of the installation.
Now when I opened ubuntu from the HD, the drive showed up just as FinalFantasyKid sugested in the first reply to my post.
I'm an older guy, 70, and still amazed at the idea of computers. 
 Sincere thanks to all who contributedl
Lee

---

