---
title: "How to access Windows system if ubuntu installed within"
date: 2011-05-13
forum: General Help
---

### Post by healee on 2011-05-13
I installed the unbuntu within a Windows 7 system.  After booting up the ubuntu I tried to read some linux files stored on the Windows 7 system.  However I couldn't find the Windows 7 system in the corresponding partition at all though I could see the next partition where Windows 2008 was installed.  In the place of the Windows 7 system I could see a system called boot.

Nevertheless, when I booted the computer where the Windows 7 system was installed with the ubuntu disk in the CD drive,  I could clearly see the same Windows 7 system with all the files in their right places.

Please tell me how I can access the Windows partition where I have ubuntu installed within.

---

### Post by wilee-nilee on 2011-05-13
> **healee said:**
> I installed the unbuntu within a Windows 7 system.  After booting up the ubuntu I tried to read some linux files stored on the Windows 7 system.  However I couldn't find the Windows 7 system in the corresponding partition at all though I could see the next partition where Windows 2008 was installed.  In the place of the Windows 7 system I could see a system called boot.

Nevertheless, when I booted the computer where the Windows 7 system was installed with the ubuntu disk in the CD drive,  I could clearly see the same Windows 7 system with all the files in their right places.

Please tell me how I can access the Windows partition where I have ubuntu installed within.

Your not looking for a partition but a file I forget where it is but keep looking it is there.

---

### Post by dragonfly41 on 2011-05-13
I remember when I first tried installing ubuntu "alongside" Windows Vista (which was corrupted) when I booted into ubuntu I could see all the Vista files in a folder called "isodevices" (equivalent to c:\ directory).

I now keep Windows Vista and ubuntu on separate partitions.

---

### Post by coffeecat on 2011-05-13
@healee, you installed Ubuntu using Wubi within the Windows C: partition? If so, open a Nautilus file browser, click on "File System" in the left Places pane and then open the "host" folder. Your Windows C: partition files will all be there.

By the way, **please** mention which version of Ubuntu you are using when asking for help. Now that Natty has been released and many people are using the Unity desktop, it is all the more important in order for you to get appropriate instructions for your particular desktop.

---

### Post by healee on 2011-05-13
> **coffeecat said:**
> @healee, you installed Ubuntu using Wubi within the Windows C: partition? If so, open a Nautilus file browser, click on "File System" in the left Places pane and then open the "host" folder. Your Windows C: partition files will all be there.

By the way, **please** mention which version of Ubuntu you are using when asking for help. Now that Natty has been released and many people are using the Unity desktop, it is all the more important in order for you to get appropriate instructions for your particular desktop.

I have found it with your guide.  Thanks!  I am using Ubuntu 10.04 LTS - the Lucid Lynx - released in April 2010.  I didn't mention the version as I had supposed they would be all the same in this regard.  I like new features but I am not too sure if I like willy-nilly changes of existing features, be it Windows or Linux.

---

### Post by healee on 2011-05-13
When I click on Computer, I can see 250 GB Hard Disk: 2008SBS, and 250 GB Hard Disk: SYSTEM.  What are supposed to be in the SYSTEM?

What is Generic- Multi-Card?

When I click on SYSTEM -> Boot, I see all the directories with all the alphabetical characters, such as cs-CZ, da-DK etc.  What are they?  When I click on a few of them, they all come up with bootmgr.exe.mui.

---

### Post by coffeecat on 2011-05-14
> **healee said:**
> When I click on Computer, I can see 250 GB Hard Disk: 2008SBS, and 250 GB Hard Disk: SYSTEM.  What are supposed to be in the SYSTEM?

What is Generic- Multi-Card?

When I click on SYSTEM -> Boot, I see all the directories with all the alphabetical characters, such as cs-CZ, da-DK etc.  What are they?  When I click on a few of them, they all come up with bootmgr.exe.mui.

Hi - "SYSTEM" is your Windows 7 100MB boot partition. You'd be advised to leave it well alone. The Places menu offers you all mountable partitions which is both a convenience and a potential danger. Accidentally change/delete a file in that partition and you will have an unbootable Windows. Ditto with your Windows C: partition. My personal rule is to mount my Windows C: partition only when really needed and only to read or copy a file. I **never** write to my Windows C: partition from Ubuntu. I use Ubuntu on a separate partition - not wubi - but the principle is the same.

The "250GB" bit of "250 GB Hard Disk: SYSTEM" is a bit confusing. It refers to the capacity of the whole hard drive, not the partition.

"Generic - Multi-Card"? I guess you have a multi-card reader on your computer.

---

### Post by healee on 2011-05-15
> **coffeecat said:**
> Hi - "SYSTEM" is your Windows 7 100MB boot partition. You'd be advised to leave it well alone. The Places menu offers you all mountable partitions which is both a convenience and a potential danger. Accidentally change/delete a file in that partition and you will have an unbootable Windows. Ditto with your Windows C: partition. My personal rule is to mount my Windows C: partition only when really needed and only to read or copy a file. I **never** write to my Windows C: partition from Ubuntu. I use Ubuntu on a separate partition - not wubi - but the principle is the same.

The "250GB" bit of "250 GB Hard Disk: SYSTEM" is a bit confusing. It refers to the capacity of the whole hard drive, not the partition.

"Generic - Multi-Card"? I guess you have a multi-card reader on your computer.
Thanks for your advices and guidance!  That was what I guessed.  However I couldn't find the Windows files I expect in "SYSTEM" but another place you told me.

I try to follow the "path" on the "explorer" using "ls" on the terminal so that I can understand the file hierarchy better but I was confused so I couldn't follow at all.  Would you mind telling the PATH of the Windows files so that I can trace using "ls" command.

Yes, I do have a multi-card reader on my computer.

---

### Post by coffeecat on 2011-05-15
If you open the hosts folder as I described earlier you will see the main C: partition filesystem. Be careful what you do now for the reasons I posted earlier.

You should see a number of folders, the main ones being "Windows", "Program Files" and "Users". Leave the rest alone and leave the contents of "Windows" alone - that last is where most of the operating system files are kept. Leave "Program Files" alone as well, because... Well, that should be self-explanatory. :) Open the folder "Users" and you will see a folder with your account name with all your personal folders and files in that.

Personally, I wouldn't use 'ls' from the terminal to explore a Windows filesystem.

---

### Post by healee on 2011-05-15
> **coffeecat said:**
> If you open the hosts folder as I described earlier you will see the main C: partition filesystem. Be careful what you do now for the reasons I posted earlier.

You should see a number of folders, the main ones being "Windows", "Program Files" and "Users". Leave the rest alone and leave the contents of "Windows" alone - that last is where most of the operating system files are kept. Leave "Program Files" alone as well, because... Well, that should be self-explanatory. :) Open the folder "Users" and you will see a folder with your account name with all your personal folders and files in that.

Personally, I wouldn't use 'ls' from the terminal to explore a Windows filesystem.
I thank you for all your help.  Have a good day!

---

