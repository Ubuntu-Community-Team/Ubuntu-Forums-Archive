---
title: "Where is my disk space going?"
date: 2010-08-29
forum: General Help
---

### Post by CanadianPenguin on 2010-08-29
I tried to install [Portable VirtualBox]("http://www.vbox.me/") using wine and even though I installed it on my /host/ folder (with 19 gb free) it downloaded some massive file on my Wubi installation (with 60 mb free) and now I am down to 3 mb left on Wubi and I can't find the massive file that it downloaded. Tried using the disk usage analyzer but nothing came up. Windows is unbootable so I can't use it.

Before this, Ubuntu would constantly decrease the amount of disk space I had free for no reason as well. It would jump from 120 mb one day to 50 mb. I moved my documents to my Windows folders but the disk space only stayed at 100 for another day or so before it went down again. apt-get auto/clean, localepurge, and deborphan are completely useless and there's something else going on behind the scenes here that I don't know about.

Using Ubuntu Jaunty.

Halp.

---

### Post by CanadianPenguin on 2010-08-29
Top

This is urgent :(

---

### Post by ghetto2ivy on 2010-08-29
I not sure I understand what you did. Not sure anyone can help until you provide more details.

It seems you have ubuntu running via wubi. But you further installed virtual box using wine in ubuntu? Are you trolling? Or are you for real? (Why would you install virtualbox for windows inside of Ubuntu if there is a version for ubuntu?)  

First find out how much disk space you have in ubuntu by using df (diskspace free):
```
df -h --total
```
the last line will say how much space you have and how much space you've used. See if that matches what you'd expect.

I'm not sure what happened to your computer. I'm not even sure if the windows not booting is related. You probably created a disk using virtual box and allocated all the space for it. Start by deleting wine, assuming you have nothing important in it. Then, please, no wine for you. Don't try to make ubuntu run windows programs for the first 6 months ok?

I'm also unfamiliar with how wubi allocates diskspace. I suspect however that your initial assumption -- that it was wubui that automatically grew bigger than your allotment -- is wrong. You probably alloted space then used it windows. If thats the case then windows is your issue, not ubuntu. Use ubuntu to repair windows by mounting the windows filesystem and deleting files there. 

In the mean time go to ~/.wine and delete everything in there. Then remove wine and for your own sake don't use it for a while.

---

### Post by ghetto2ivy on 2010-08-29
Just read this again. I think you are confused as to how a dynamically growing disk works. Wubi doesn't reserve all the space right away, it can simply grow to use the space as needed. This is the space you use for things like browsing, and installing apps.


My suggestion: 

1) boot to a live cd, and delete the ubuntu and wubildr* directories. 

2) You should have enough boot windows. Reboot to windows and attempt to uninstall ubuntu and wubi

> Remove C:\ubuntu and C:\wubildr*

In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi line. For Vista, you can use EasyBCD to edit the boot menu. Alternatively you can modify the boot menu via Control Panel > System > Advanced > Startup and Recovery and pressing "Edit". For Windows 98 you have to edit C:\config.sys and remove the Wubi block.

To remove Wubi from the add/remove list, delete the registry key: HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi

An easy method of removing this registry key is to paste the following text into a plain editor such as Notepad, close and save the file as something like removeWubiKey.reg (you may wish to go to Folder Options > View and disable the "Hide file extensions for known file types" option to check that the .reg extension has been applied correctly). Then you can perform the rest automatically by opening the file in the normal Windows manner, or choosing the "Merge" option from the right click context menu. Note: The formatting is rather strict, so copy the text exactly for best results. You may need to be logged in as the administrator to delete the key, depending on the version of Windows you are using. User Account Control in Vista may also ask for permission, in the typical fashion.

REGEDIT4

[-HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\Wubi]

After deleting the registry key, Ubuntu may still appear in the program list. If this is the case, you may be asked if you would like to remove the item from the list. 

Source: [https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by bcbc on 2010-08-30
> **ghetto2ivy said:**
> Just read this again. I think you are confused as to how a dynamically growing disk works. Wubi doesn't reserve all the space right away, it can simply grow to use the space as needed. This is the space you use for things like browsing, and installing apps.


My suggestion: 

1) boot to a live cd, and delete the ubuntu and wubildr* directories. 

2) You should have enough boot windows. Reboot to windows and attempt to uninstall ubuntu and wubi



Source: [https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

This is strange advice. Deleting the ubuntu directory will remove the wubi install and all data on it. The OP has stated that windows does not boot, so how will deleting the wubi ubuntu help??

---

### Post by bcbc on 2010-08-30
I would run the disk usage analyzer on the filesystem and look if there are any things you can delete. e.g. in the tmp directory. At least identify where the space has gone too.

You could create a separate /home (virtual disk: home.disk) using the script from the wubi guide, since you have space on your windows partition. I believe the LVPM resize still works (even though other parts of LVPM don't). That will make your root.disk bigger, but it's limited to the free space on the drive (you can't just absorb the free space into the root.disk - which is fixed in size).

Remove old kernels you no longer need (keep at least two).

Those are some ideas.

---

### Post by varunendra on 2010-08-30
Well.. a wubi problem & **bcbc **is already present, so no place for me! Still I can't help jumping in 'cause I'm unable to digest one thing-

If windows is unbootable and you (OP) depend upon Ubuntu for everything, why don't you just install it natively on its own partition? If it is data you are worrying about, you can always transfer it to the windows drive. If it is settings and apps, then I guess Remastersys should be able to help you.

Since neither **bcbc**, nor **ghetto **suggested this obvious looking alternative, I'm sure I'm missing something more important. I'd like to know what.

---

### Post by bcbc on 2010-08-30
> **varunendra said:**
> Well.. a wubi problem & **bcbc **is already present, so no place for me! Still I can't help jumping in 'cause I'm unable to digest one thing-

If windows is unbootable and you (OP) depend upon Ubuntu for everything, why don't you just install it natively on its own partition? If it is data you are worrying about, you can always transfer it to the windows drive. If it is settings and apps, then I guess Remastersys should be able to help you.

Since neither **bcbc**, nor **ghetto **suggested this obvious looking alternative, I'm sure I'm missing something more important. I'd like to know what.

lol, yes that is always an option. I always try and address the problem the OP is having.

If the problem cannot be resolved through normal means, then of course I'll suggest reinstalling or migrating.

---

### Post by CanadianPenguin on 2010-08-30
People are obviously incapable of trying the app themselves and comprehending what I'm trying to say, so here is the full story:

A month and a half or so ago, Windows Vista gave me its infamous KSoD error (making it unable to boot), forcing me to use a Wubi installation I had from several months back I used for testing. I was planning on using it until I could get an external HDD to back all of my files to and factory reset the computer. This is irrelevant to the problem but it's why I can't boot Windows and am running Wubi.

Fast forward...

I wanted to give Gentoo a shot the day I posted this, and I didn't have enough space for the .deb installation of VirtualBox to be installed automatically to my Wubi virtual disk, and I wanted to install it to my /host/ directory where Windows is installed, which had roughly 20 gb. So, I downloaded the app Portable VirtualBox.

Here's how it works: It cannot legally contain the VirtualBox files in the download or something, so the app it downloads is basically just a GUI with a button that downloads VirtualBox's files and does something to them to make it smaller. I was running it from somewhere in my /host/ directory and I was assuming it was going to download it there, but it ended up apparently downloading the files to my Wubi virtual disk, and I don't even know where it saved them, and now I have some godawful file from this fraudulent app it downloaded taking up 95% of the 65 mb of space I had left on Wubi. I've checked the disk usage manager and all the possible folders it would've installed to (including my wine directory), but there's absolutely nothing. It's like the file doesn't exist and it's making Wubi report that there's only 1.5 mb left of space on my laptop (checked it this morning). It didn't make any sort of virtual disk that VirtualBox normally does, it tried to download Vbox.

If someone with Windows could test this app and tell me where it normally downloads to, I could check that place in my wine directory. Or, if someone with a copy of Wubi/Ubuntu can try this and track where it is downloading to, I'd appreciate it so I can delete it.

bcbm: That's what I'm trying to find out. Why do you think I'm asking this. I want to know where the file is because it doesn't appear to be anywhere.

ghetto: It's not disk space that is causing Windows to be unbootable. Deleting Wubi won't help because then the computer would be 100% unusable. I also made no assumption about how Wubi uses disk space, I was wondering where the hell the disk space I had in it disappeared to. How about reading the thread.

---

### Post by varunendra on 2010-08-30
Apologies for any misunderstanding. We all suggested as per our interpretation of your problem. Now that you've clarified it more deliberately, I hope we may be able to serve you with precisely what you need.

Apologies again for acting stupid, but I'm still unsure about a couple of things. So am stating how I've interpreted it all so far. Please confirm/correct me:

[LIST]
[*]Your native Vista is completely unusable, and you need an alternative OS to do things until you are able to **factory-reset** your computer.
[*]By the factory-reset thing, I guess you **want to get your Vista back** on that computer after getting things done. And that's why you don't want to take risk of making any changes to the partitions.
[*]Combining above two facts (are they?) all you are left with are two options: First- Run a capable OS from an external media; second- somehow make room in the existing wubi setup & keep using it.
[*]You absolutely don't want any such solution/workaround that includes making changes to your hard disk partitions, since it may sabotage your factory-reset plan.
[/LIST]
If the above are correct, then I've a few quick suggestions for you.

[LIST=1]
[*]Open nautilus with **gksudo nautilus** command and recheck size of all the folders in root (/) directory (excluding /host of course). Normal user can not access some files/folders so can not determine their actual size.
[*]Please confirm if you are open to the option to install Ubuntu (or any distro) natively on the HDD allowing it to make changes to your partitions.
[/LIST]
Meanwhile, I'll try to download the portable VBox app from "wubi in Win7" (could you provide the link?) & see where it downloads the files.

One more stupid question: Why are you even thinking of (if you really are) resetting to factory default when all it is going to give you is **VISTA**????

---

### Post by bcbc on 2010-08-31
> **CanadianPenguin said:**
> People are obviously incapable of trying the app themselves and comprehending what I'm trying to say, so here is the full story:

A month and a half or so ago, Windows Vista gave me its infamous KSoD error (making it unable to boot), forcing me to use a Wubi installation I had from several months back I used for testing. I was planning on using it until I could get an external HDD to back all of my files to and factory reset the computer. This is irrelevant to the problem but it's why I can't boot Windows and am running Wubi.

Fast forward...

I wanted to give Gentoo a shot the day I posted this, and I didn't have enough space for the .deb installation of VirtualBox to be installed automatically to my Wubi virtual disk, and I wanted to install it to my /host/ directory where Windows is installed, which had roughly 20 gb. So, I downloaded the app Portable VirtualBox.

Here's how it works: It cannot legally contain the VirtualBox files in the download or something, so the app it downloads is basically just a GUI with a button that downloads VirtualBox's files and does something to them to make it smaller. I was running it from somewhere in my /host/ directory and I was assuming it was going to download it there, but it ended up apparently downloading the files to my Wubi virtual disk, and I don't even know where it saved them, and now I have some godawful file from this fraudulent app it downloaded taking up 95% of the 65 mb of space I had left on Wubi. I've checked the disk usage manager and all the possible folders it would've installed to (including my wine directory), but there's absolutely nothing. It's like the file doesn't exist and it's making Wubi report that there's only 1.5 mb left of space on my laptop (checked it this morning). It didn't make any sort of virtual disk that VirtualBox normally does, it tried to download Vbox.

If someone with Windows could test this app and tell me where it normally downloads to, I could check that place in my wine directory. Or, if someone with a copy of Wubi/Ubuntu can try this and track where it is downloading to, I'd appreciate it so I can delete it.

bcbm: That's what I'm trying to find out. Why do you think I'm asking this. I want to know where the file is because it doesn't appear to be anywhere.

ghetto: It's not disk space that is causing Windows to be unbootable. Deleting Wubi won't help because then the computer would be 100% unusable. I also made no assumption about how Wubi uses disk space, I was wondering where the hell the disk space I had in it disappeared to. How about reading the thread.

CanadianPenguine: it's not that we're incapable. It's just that realistically, I hope you don't expect that the people trying to help will start installing apps just to find out where a measly 57MB went to!? lol

There are many ways to skin a cat (although why would you want to!?) and one way to solve your problem is to find you more space. Those suggestions are just that - take em or leave them. If you only had 60MB free (before this problem) then this is probably in your best interests. 

After all, once you've worked so hard to fix this, all you'll have is 60MB free.

---

### Post by varunendra on 2010-08-31
> **bcbc said:**
> There are many ways to skin a cat (although why would you want to!?) and one way to solve your problem is to find you more space. Those suggestions are just that - take em or leave them. If you only had 60MB free (before this problem) then this is probably in your best interests. 

After all, once you've worked so hard to fix this, all you'll have is 60MB free.
+1
(on a typical broadband speed here, it takes 5-10 min. to fill up that 60 MB!!)

And by the way, here's the downloaded file (if I've not picked up a wrong app): ~/Downloads/Portable-VirtualBox/VirtualBox.exe (75MB after completion)
(no temp file during download, this file itself was increasing in size with progress in download)

It's strange why you weren't able to find that.

[B]
PS:[/B]
Since this is so obvious a location to find, I suspect you may have a different problem.
So still waiting for your reply with a true will to help.

---

### Post by varunendra on 2010-08-31
<Deleted double Post due to connection error>

---

### Post by JBAlaska on 2010-08-31
> **CanadianPenguin said:**
> 
**Before this, Ubuntu would constantly decrease the amount of disk space I had free for no reason as well. It would jump from 120 mb one day to 50 mb.** I moved my documents to my Windows folders but the disk space only stayed at 100 for another day or so before it went down again. apt-get auto/clean, localepurge, and deborphan are completely useless and there's something else going on behind the scenes here that I don't know about.

Using Ubuntu Jaunty.

Halp.

Have a look in **/var/log** for **kern.log, messages, ufw.log and syslog** Sometimes these will grow to huge sizes (I recently had a usb wireless message filling kern.log to over 40GB). It's safe to delete those files and they will be re-created on boot.

---

