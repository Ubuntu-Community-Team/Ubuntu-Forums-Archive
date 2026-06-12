---
title: "Files copied from windows to ubuntu are locked"
date: 2012-01-21
forum: General Help
---

### Post by iamgregor on 2012-01-21
So I wrote a script to recursively take ownership of files transferred so I can rename them at least, but then after I own them, I can't copy or manipulate them from windows anymore. 

So I could chmod 666 all of it, but I just keep thinking there's something simple I'm missing.

A lil help?

---

### Post by varunendra on 2012-01-21
> **iamgregor said:**
> So I wrote a script to recursively take ownership of files transferred so I can rename them at least, but then after I own them, **I can't copy or manipulate them [COLOR=Red]from windows[/COLOR] anymore.** 

So I could chmod 666 all of it, but I just keep thinking there's something simple I'm missing.

A lil help?
What do you mean by "from windows.."? Normally, windows can't see Linux partitions, and Linux can't change or set permissions on a windows partition.

Is it a samba sharing issue? Please provide some background info and some details about the problem.

---

### Post by iamgregor on 2012-01-21
I copy the files to an ubuntu share, but I want to be able to copy them back if needed. I have a movie computer over by the TV and I want to be able to push and pull movies in case I update them, need to re-encode them or just change the box art.

I do have VNC, but also shared folders. Sometimes I can't copy something away from Linux or it won't let me change a filename. It's annoying. Even if I walk over to the Linux box, sometimes it won't let me do anything because the files are locked automatically after they've been copied from Win to Ubuntu

---

### Post by varunendra on 2012-01-22
To me it seems to be indeed a samba share issue which may be fixed by appropriately editing /etc/samba/smb.conf file.

Unfortunately, my knowledge and experience about samba configuration is next to 'zero'. But I can (and would like to.., for sake of learning) simulate the setup myself on VMs to figure out the right configuration.

Accordingly, please provide as much info as you can about:

[LIST]
[*]how you setup those shares,
[*]which machines and OS (with versions) are involved,
[*]which user accounts are involved, and which domain (or workgroup) they belong to
[*]what is where,
[*]how did you try to set/modify permissions on the share(s)
[*]have you tried editing relevant configuration file(s) apart from normal "chmod"?
[*]Plus, any more info you think can be important/relevant.
[/LIST]
I have successfully tried basic samba shares sometimes, but didn't ever have to edit the smb.conf file.


If you need expert advise, please consider having a look at this comprehensive [HowTo by dmizer]("http://ubuntuforums.org/showthread.php?t=1169149"), and post your questions there.

---

### Post by iamgregor on 2012-01-22
> **varunendra said:**
> To me it seems to be indeed a samba share issue which may be fixed by appropriately editing /etc/samba/smb.conf file.

Unfortunately, my knowledge and experience about samba configuration is next to 'zero'. But I can (and would like to.., for sake of learning) simulate the setup myself on VMs to figure out the right configuration.

Accordingly, please provide as much info as you can about:

[LIST]
[*]how you setup those shares,
[*]which machines and OS (with versions) are involved,
[*]which user accounts are involved, and which domain (or workgroup) they belong to
[*]what is where,
[*]how did you try to set/modify permissions on the share(s)
[*]have you tried editing relevant configuration file(s) apart from normal "chmod"?
[*]Plus, any more info you think can be important/relevant.
[/LIST]
I have successfully tried basic samba shares sometimes, but didn't ever have to edit the smb.conf file.


If you need expert advise, please consider having a look at this comprehensive [HowTo by dmizer]("http://ubuntuforums.org/showthread.php?t=1169149"), and post your questions there.

Windows 7 machine (main)
Ubuntu 11 (movie machine)

I navigate from Win 7 to Ubuntu share using Windows Explorer and copy files over. The Ubuntu shared folder is shared by just right-clicking the folder and selecting "share".

After the copy, the Ubuntu machine has the files locked and they're a pain. I want to be able to move/rename them from either machine whenever I want, but apparently it's not in the cards.

---

### Post by varunendra on 2012-01-22
I just created a folder in my home directory in Ubuntu 11.10 VM, and shared it with "Allow others...." & "Guest access...." options enabled.

Now I can create, delete and rename files in that folder from both Ubuntu and an XP machine. Some examples-

[LIST]
[*]If a file is created in Ubuntu, I can read, rename, copy, move and delete it from XP. I can not edit it from XP though.
[*]If a file is created from XP, I can read, rename, copy, move and delete it from Ubuntu (even though it has the 'lock' icon on it). Can't edit though (hmm.. so that's what the lock is there for).
[*]I am experiencing some issues with permissions of subfolder and their contents (still experimenting).
[/LIST]
So if you can further elaborate your problem with some practical examples, we can figure out solutions for them.

So far I didn't have to touch the smb.conf file.

---

### Post by iamgregor on 2012-01-22
At this exact moment, everything works perfectly. Stand by. Will watch for specific issue (though I did notice something I couldn't move yesterday now works (sigh)

---

### Post by ottosykora on 2012-01-22
you could also use fat32 formated common partition, there all permissions will be lost and files equally useful for both win and linux.

---

### Post by iamgregor on 2012-01-22
For a common drive, that's not a bad idea otto.

---

### Post by varunendra on 2012-01-22
> **ottosykora said:**
> you could also use fat32 formated common partition, there all permissions will be lost and files equally useful for both win and linux.
Yeah, I would +1 this suggestion.

Especially when your files are large movie files, you won't be losing anything by choosing FAT32 filesystem. You can add it to your **/etc/fstab** file in Ubuntu to mount it automatically when ubuntu starts.

---

