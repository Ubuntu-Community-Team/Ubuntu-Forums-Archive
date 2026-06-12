---
title: "Can't see Ext HDD Directories in Nautilus but can in Terminal"
date: 2010-01-09
forum: General Help
---

### Post by Donalb on 2010-01-09
Hey all,

I'm using an external USB Iomega Rev 70GB HDD. (Have been for a few years).
It uses UDF format for higher transfer speeds of large files. (This is not an option, & not changeable), therefore natively recognised since 2.6.20, I think. (But no official Linux support).

Occasionally though, I run into problems such as can't format a disk in Linux, need to boot to Wins to do it.
Also like today:
So I have a bunch of comic pdfs & cbrs on it, mix of .rar files & folders. They were there yesterday. Today I went to read something and I couldn't see them.
Thought maybe I'd deleted it by accident, but no.
Looked at the drive in terminal and I can see the "missing" files and folders fine, but can't see them in Nautilus to open in Comix.
-Tried setting all permissions on the whole drive to R/W/E through Nautilus. 
-Files & Folders aren't hidden. 
-Tried rebooting. 
-Tried using Administrator Nautilus. 
-Thought it might be a re-emergence of the recent Nautilus Preview bug, so swiched File Preview off.

Ain't got no other ideas.

Any help gratefully accepted.

---

### Post by happyhamster on 2010-01-09
- Are you connecting and disconnecting the drive, or is it always plugged in?

- Also, when the drive isn't visible in nautilus, you wrote you can see the files from within a terminal, but can you also *access* the files? In other words, does:

comix filename

- open the file in comix? Also, could you perhaps show the output of:

cat /etc/fstab

- And:

mount

- It would be interesting to see the output of "mount" when the drive is working fine and also when it isn't.

---

### Post by Donalb on 2010-01-10
Cheers. Thanks for the reply! (Mentioning UDF usually means I never get a response).

It's always plugged in but it is a Removable media cartridge drive, however, when the problem developed, the cartridge had not been unmounted or ejected.
(Because it's UDF format, and Linux thinks UDF is only for CD/DVD, Ubuntu considers it a large Optical type drive, like a 70GB DVD).

The Drive IS visible in Nautilus, but the problem is that some recent files and directories aren't. The drive seems to be operating normally. I can unmount, eject and re-insert and mount the cartridge. No change in what is visible. 

The cartridge currently holds an archive of pdfs & cbrs in various dirs under a top level Comics Directory.
i.e. :

~\Rev-70\Comics
~\Rev-70\archive1.rar
~\Rev-70\archive2.rar

~\Rev-70\Comics\Comic_1_Folder
~\Rev-70\Comics\Comic_2_Folder
etc

The problem developed at the "top directory level" ("root" on the cartridge), at the same level as the top level "Comics" directory, where some recent files had been put as .rars. 
Some had been extracted and placed into new created folders, (again, all at "top" level). 
Those extracted files and newly created folders aren't visible. 
Rar archive that have not yet been extracted are visible. Once extracted the originating Rars and the newly extracted files, are invisible.

In brief, Nautilus showed 7 items, including hidden, at the top level. In Terminal I could see 24. 

(I realise that may not be very clear).

In terminal I could see the newly extracted files & directories, and cd into the "missing" directories.
I ran Comix from terminal on those files but wasn't  able to open one.  

I got this:
```
** (comix:15050): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
```

I've had a look for this error, related to Comix, and found
```
http://ubuntuforums.org/showthread.php?t=1339323
```
so I installed libstd5+++. No difference but didn't do a restart and anyway it looks like a different issue.

In the same vein though, of being able to run an action on one of the invisible files or folders, I was able to Unrar the archives from the command line. Extracts ok AND those extracted files are subsequently visible in Nautilus...

Output of cat /etc/fstab

```

proc            /proc           proc    defaults        0       0
UUID=59838ba2-459c-4537-bf14-fc2e9b09cb14 /               ext4    errors=remount-ro 0       1
UUID=220ac46d-3570-4d28-b25f-ae767035221c /home           ext3    defaults        0       2
UUID=2c0d9fc0-6ef3-457e-91d0-c234a7bab736 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Colour me confused.

Oh,relevant part of Mount:
```
/dev/sr1 on /media/REV 70 type udf (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,iocharset=utf8,umask=0077)
```

---

### Post by happyhamster on 2010-01-10
I misunderstood the situation and thought it might be some mount problem, but it doesn't look like that now. In fact, colour me confused as well.

Some random ideas: do the invisible files/folders contain any weird characters, or is there anything else peculiar about their names?

Are the permissions of those files as they should be?

Does nautilus show any output when started from a terminal (from within an invisible folder)? Just type:

nautilus

Do you still have those top-level rar-files that produced invisible stuff when extracted? If so, copy one of them to a regular drive (or an USB-stick or whatever) and see if you get the same result there. (If you don't get the same result, it would indicate filesystem corruption on the UDF drive I think.)

---

### Post by Donalb on 2010-01-10
Well my friend, in this benighted world, there is little to count on, but at least we know this: you and I can both spell colour correctly.;)

All the digging around in terminal has gotten me only so far. I now know I can at least find/move the files & folders that way.
I can see, run move etc files and folders on the UDF drive (all of which are normally named, no tildes or odd characters.
All permissions seem normal. (I tried chmod 777 on some of the invisible files & folders just in case but no difference).  
If I mv them to /home & back to the Rev they are again visible.

Thunar also will see files and folders on the Rev that Nautilus won't.
 
They appear/disappear in Nautilus mainly after moving large files. 

I'm coming to the conclusion that it's a Nautilus bug. If it was UDF f/s corruption, surely I'd have problems in terminal also, where everything seems fine. (If I'm wrong on that, let me know).


Oh, btw, the top level rar files would extract the files on the Rev...then disappear, along with the result.
And the Directory Comics, which I was doing nothing with, seems good also.

Thoughts?

---

### Post by happyhamster on 2010-01-10
> **Donalb said:**
> I'm coming to the conclusion that it's a Nautilus bug. If it was UDF f/s corruption, surely I'd have problems in terminal also, where everything seems fine. (If I'm wrong on that, let me know).
Yes, agreed. And I think I've seen a weaker form of this behaviour from nautilus on ext3. Some files you expect to be in some folder, but they aren't, only to show in nautilus some time later (or after clicking the reload button, although I can't remember if that worked all the time). Resetting nautilus ("killall nautilus") made them show too.

- Does nautilus complain when you start it from a terminal like this:

nautilus path-to-hidden-folder


- edit: and what is the output of:

gvfs-ls path-to-hidden-folder

---

### Post by Donalb on 2010-01-11
There was Nautilus bug in Karmic, where if preview was switched on in folders where large files had been ,moved or copied, those files would become invisible & Nautilus would often hang, which may be what you are referring to. Switching off preview would stop the behaviour but a fix was released a few weeks ago.
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/397192](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/397192)

I'd deleted the folder so can't try that. I'll have to wait and see if it re-occurs.

---

### Post by Mohammed Lee on 2010-03-15
I'm having the exact same problem with my external Maxtor 1TB (USB2.0). I was listening to some music on Rhythmbox, and decided I wanted to burn some but couldn't find the directories in question through Nautilus. I'm able to open them by invoking Nautilus from the terminal.

I've tried disabling the preview options in Edit > Preferences > Preview as per your suggestion Donalb, to no avail. At this point, I'll just wait for Lucid.

Also, this might be related -- if the drive is plugged in when I start the system, it doesn't see any directories (or maybe 1 of the 5 base directories) half the time, but if I unplug and re-plug it live, it suddenly reads them all again.

Sorry I don't have much information to add. I just wanted to let you know you're not alone ;)

---

