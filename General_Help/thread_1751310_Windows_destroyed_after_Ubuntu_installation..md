---
title: "Windows destroyed after Ubuntu installation."
date: 2011-05-06
forum: General Help
---

### Post by Zortis on 2011-05-06
Back again with another problem.

Installed Ubuntu 10.10 and straight after decided to upgrade to 11.04.

Just tried booting Windows, all seemed fine until it said "preparing desktop" never seen this before.

Cannot use most programs.

Unfortunately, and to my horror, the Windows repair disc did not work.

I'll upload a picture shortly of what it now looks like.

---

### Post by Zortis on 2011-05-06
What it looks like now.

---

### Post by Zortis on 2011-05-06
Help :'(

---

### Post by Zortis on 2011-05-07
.

---

### Post by josephku on 2011-05-07
Looks like your windows profile has been renewed.  This normally means your old profile was somehow corrupt and windows gave you a new one.  It is likely that the files of your old profile (e.g. Documents, Pictures, etc) are still on your hard drive but not obvious to you where.

---

### Post by Thewhistlingwind on 2011-05-07
Know the names of some of your old documents? Go digging and grab them if/while you still can.

---

### Post by Zortis on 2011-05-07
Was really looking for a fix.

I can't access any files in Windows or through wine.

---

### Post by mr clark25 on 2011-05-07
can you access your files from ubuntu?

you might have better luck asking on a windows forum about this.

---

### Post by Zortis on 2011-05-07
> Looks like your windows profile has been renewed.  This normally means  your old profile was somehow corrupt and windows gave you a new one.  It  is likely that the files of your old profile (e.g. Documents, Pictures,  etc) are still on your hard drive but not obvious to you where.

I read that you can change a registry key to fix this but I can't access the regedit in Windows or through Wine I get this error:

The file '/media/Windows/Windows/regedit.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

---

### Post by Zortis on 2011-05-07
> can you access your files from ubuntu?

you might have better luck asking on a windows forum about this

I can access files from Ubuntu.

I can't run ANYTHING though.

And since Ubuntu caused this disaster I thought I'd ask here first...

Note: Windows is now labeled E:/ after installing Ubuntu.

---

### Post by Thewhistlingwind on 2011-05-07
> **Zortis said:**
> I read that you can change a registry key to fix this but I can't access the regedit in Windows or through Wine I get this error:

The file '/media/Windows/Windows/regedit.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

Flip the executable bit in properties. (If that's indeed the problem.)

Also, I think I've heard of this problem before, the reason that your having trouble may in fact be that your drive is mounted as E:. Basically windows expects a C: drive and will hire gremlins to steal your personal affects should you deviate from this standard.

Don't have a fix, sorry.

---

### Post by Zortis on 2011-05-07
When I try check the box that allows it to be an executable it will immediately uncheck it.

Still need a fix.

...Or a new copy of Windows...

---

### Post by Zortis on 2011-05-07
Bump

---

### Post by Thewhistlingwind on 2011-05-07
> **Zortis said:**
> When I try check the box that allows it to be an executable it will immediately uncheck it.

Still need a fix.

...Or a new copy of Windows...

Well I have an IDEA of a fix, but I'm not sure it's what you want.

Step one, use a disk cloning program like DD (Warning: Nicknamed Disk Destroyer for dangerous features, may be safer to use alternatives.) to clone your drive to an external.

Step two: Mess with partitions until windows mounts as C:

Step three: If partitions broken, restore from image. If it works however, Resize windows partition and clone it. Optionally delete old backup image to comply with applicable licensing laws.

Notes:

1. This is incredibly dangerous, and very high level abstractions, each actual step is more like a set of fifty. 
2. Make sure you know EXACTLY how to restore from your backed up image, having that not work would be a disaster.
3. This assumes your problem is with mount points.

Good luck, this is BAD advice, which is why I didn't initially give it.

---

### Post by Zortis on 2011-05-07
Had problems cloning drives in the past, not going to try your suggestion.

Still need a fix :'(

---

### Post by dragonfly41 on 2011-05-07
I've been through a scenario where my Vista user profile (desktop) was corrupted.

I had installed Ubuntu using wubi.   But now after re-installing Vista I keep Vista and Ubuntu in separate partitions.

But to turn to your problem.

Can you boot up windows in safe mode?   F8?

If yes can you create a new user account with admin rights in Windows?

You can then recover your corrupted windows profile .. but try to restart into this fresh user account first.

---

### Post by Thewhistlingwind on 2011-05-07
> **Zortis said:**
> Had problems cloning drives in the past, not going to try your suggestion.

Still need a fix :'(

Whats currently mounted as your C: drive?

---

### Post by Zortis on 2011-05-07
> I've been through a scenario where my Vista user profile (desktop) was corrupted.

I had installed Ubuntu using wubi.   But now after re-installing Vista I keep Vista and Ubuntu in separate partitions.

But to turn to your problem.

Can you boot up windows in safe mode?   F8?

If yes can you create a new user account with admin rights in Windows?

You can then recover your corrupted windows profile .. but try to restart into this fresh user account first.

Will try this.

---

### Post by dragonfly41 on 2011-05-07
If you can start in a new user account here are the instructions for recovery (you don't write what version of Windows you have):-

[http://windows.microsoft.com/en-us/windows-vista/fix-a-corrupted-user-profile](http://windows.microsoft.com/en-us/windows-vista/fix-a-corrupted-user-profile)

---

### Post by Zortis on 2011-05-07
I'm pretty sure I've found the problem.

I was looking around the registry and saw the profileimage path was C:\users\usernamehere

Meaning that it's trying to look in C:\ for my profile but C:\ no longer exists, so it creates a new one.

However upon installing Ubuntu the Windows partition was renamed E:\

Is there any possible way to rename the Windows partition to C:\ again?

Note: It must be done in Ubuntu because Windows will only log me on with a temporary profile which cannot save any changes made to files/registry entries.

---

### Post by wilee-nilee on 2011-05-07
> **Zortis said:**
> I'm pretty sure I've found the problem.

I was looking around the registry and saw the profileimage path was C:\users\usernamehere

Meaning that it's trying to look in C:\ for my profile but C:\ no longer exists, so it creates a new one.

However upon installing Ubuntu the Windows partition was renamed E:\

Is there any possible way to rename the Windows partition to C:\ again?

Note: It must be done in Ubuntu because Windows will only log me on with a temporary profile which cannot save any changes made to files/registry entries.

I think you put to many partitions on the hd possibly, making it dynamic, post a screen shot of gparted or run the bootscript in my signature and post it in code tags. The instructions on wrapping the text are in my sig as well.

I could be wrong but your pecking at a pretty messed up setup you may brick it without taking a closer look. By brick it mean make all of it unrecoverable.

---

### Post by Zortis on 2011-05-07
Are you sure it isn't as simple as renaming Windows back to C:\?

---

### Post by dragonfly41 on 2011-05-07
No .. it isn't that simple !

---

### Post by Zortis on 2011-05-07
The full path would be

C:\Windows\Users\Username

---

### Post by Thewhistlingwind on 2011-05-07
AFAIK no, in fact it's probably easier to hack your registry files to look for your stuff on the E: drive. ;-)

PS. In case it wasn't obvious, please don't try doing that, especially without a disk clone.

EDIT: Also, to clarify, at this point I would still consider my advice to be untrustworthy. (And so should you.) Though I'm pretty rock solid on the line next to PS unless there's a detailed tutorial out there on the net. (Even then it's still bomb-defusing dangerous.)

---

### Post by Zortis on 2011-05-07
I can't edit ANYTHING in the registry.

Is there any other way than using regedit.exe to edit the registry?

I can't open regedit.exe with Wine.

---

### Post by Zortis on 2011-05-07
Bump

---

### Post by 3rdalbum on 2011-05-07
> **Zortis said:**
> I can't edit ANYTHING in the registry.

Is there any other way than using regedit.exe to edit the registry?

I can't open regedit.exe with Wine.

That won't help. It will just open the Wine registry, not the Windows registry. I'm no Windows user so I'm sorry I can't really help.

I noticed the words "This copy of Windows is not genuine" in your screenshot - could your problem be related to Windows' anti-piracy code?

---

### Post by Zortis on 2011-05-07
This computer is store-bought from PC World, I can assure you the copy of Windows IS genuine.

I'm pretty sure the problem is due to the fact that Windows is now named E:\ but all the paths look for files in C:\

---

### Post by dragonfly41 on 2011-05-07
Re: your post #18 .. did you try booting into safe mode as suggested?

publish the results of running **[COLOR=DarkGreen]sudo fdisk -l[/COLOR]**

---

### Post by Zortis on 2011-05-07
Yes, I tried booting in safe mode and I couldn't access control panel to create a new user.

I also couldn't edit registry entries because no changes are saved when you're on a temporary user.

---

### Post by dragonfly41 on 2011-05-07
So we've established that you **[COLOR=DarkGreen]can[/COLOR]** boot into safe mode.

I do not advise touching anything in the registry.   There should be no need.

It's not clear why you could not get into control panel.

If you try to run a simple command .. like **[COLOR=DarkGreen]notepad[/COLOR]** .. does it open notepad?

If you are in run can you type **[COLOR=DarkSlateBlue]msconfig?[/COLOR]**

---

### Post by Zortis on 2011-05-07
Yes notepad opens, but only in safe mode though.

---

### Post by dragonfly41 on 2011-05-07
you can try opening a new user account via command line ..

[http://help.wugnet.com/windows2/Create-User-Account-Command-Line-ftopict520066.html](http://help.wugnet.com/windows2/Create-User-Account-Command-Line-ftopict520066.html)

and here ..

[http://www.techrepublic.com/article/controlling-user-accounts-from-the-command-line/5031577](http://www.techrepublic.com/article/controlling-user-accounts-from-the-command-line/5031577)

---

### Post by Zortis on 2011-05-07
I created a new user account however when I try log on it says the usual:

"Welcome"

Then after about 10-15 seconds it logs off.

It didn't load the desktop it just switched from "Welcome" to "Logging off..."

---

### Post by dragonfly41 on 2011-05-07
Troubleshooting discussed here ..

[http://www.neowin.net/forum/topic/915162-win7-logs-off-and-shuts-down-at-welcome-screen-when-logging-in/](http://www.neowin.net/forum/topic/915162-win7-logs-off-and-shuts-down-at-welcome-screen-when-logging-in/)


[EDIT] Also in safe mode can you get to a system restore point?

---

### Post by Zortis on 2011-05-07
The user accounts aren't the problem.

The Windows drive was renamed E:\ and all of the filepaths are still looking for C:\

Nobody seems to understand that >.>

---

### Post by dragonfly41 on 2011-05-07
re: post #30

> publish the results of running **[COLOR=DarkGreen]sudo fdisk -l[/COLOR]**[COLOR=DarkGreen][COLOR=Black][/COLOR][/COLOR]

---

### Post by Zortis on 2011-05-07
```
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb11e9751

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           72858       91202   147344385    5  Extended
/dev/sda2   *           1       72858   585228027    7  HPFS/NTFS
/dev/sda5           72858       90452   141320192   83  Linux
/dev/sda6           90452       91202     6023168   82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by Zortis on 2011-05-07
Bump

---

### Post by jramshu on 2011-05-07
It looks like, even though it's not a pirated copy, windows definitely thinks it is. What you may have to do is try and recover your data, using Ubuntu, and reinstall windows 7 from your recovery disks.  

I'm not trying to make you mad or anything. I have to ask though. With a  hard drive that HUGE why would you go the way of wubi and not let  windows 7 "shrink" the drive for you and then install on the empty  partition it created?

---

### Post by Zortis on 2011-05-07
I used the Ubuntu USB to install Ubuntu... And then it went to ****.

---

### Post by jramshu on 2011-05-07
Sorry. I could have swore that I saw a wubi install in there somewhere. 

Can you recover and backup your files you need and restore windows from the recovery cd's?

---

### Post by dragonfly41 on 2011-05-07
That reference to "wubi" (post #16) was in fact my experience .. and I ended up having to reinstall Vista.

But ..

I suspect that Zortis might be confusing wine windows folders with the Microsoft windows folder.

If he can get into the command line then that is progress.

I have not seen a reply to trying to run**[COLOR=DarkSlateBlue] msconfig[/COLOR]** in safe mode.

*And Zortis don't "bump" after 28 minutes quiet period.   We all have to eat and drink between posts!*

---

### Post by Zortis on 2011-05-07
Bump it for other people not just you guys - I need all the help I can get.

Can someone just tell me a way to rename E: to C:

---

### Post by jramshu on 2011-05-07
Dude, dragonfly41 is trying to help, have you tried to run "msconfig" from the command line in safe mode?

---

### Post by uRock on 2011-05-07
Please seek help for Windows on a Windows forum.

Your version of Windows appears to be illegitimate.

For future reference. Our policy on bumping is to bump only after 24 hours of dormancy.

Thread closed.

---

