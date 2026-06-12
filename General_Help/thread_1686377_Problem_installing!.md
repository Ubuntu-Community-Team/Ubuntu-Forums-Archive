---
title: "Problem installing!"
date: 2011-02-12
forum: General Help
---

### Post by DipreW on 2011-02-12
OS: Windows XP Pro SP3

I just attempted to install Ubuntu via Wubi about 5 times today. Every time the installer tells me to reboot, I do, but then my computer goes straight into Windows. Doesn't even give me the option to boot Ubuntu. And in addition to that, when Windows DOES start up, I get a system error that says that my comp will shut down in 60 seconds. GET ME OUT OF THIS SITUATION!

I'm also unable to uninstall ubuntu.

---

### Post by An Sanct on 2011-02-12
As far as i know wubi, it is a "inside windows" install, so you see your Ubuntu as a program in the strat menu, I'm not 100% sure on this, maybe someone else can confirm this.

The second thing is the forced reboot of windows, it can be halted if you click "start", "run..." and type in "shutdown -a", this will kill the shutdown dialog.

After the shutdown dialog is killed, its time for you to find out what causes the shutdown.

---

### Post by bcbc on 2011-02-12
Look in the C:\boot.ini (it's a hidden file). there should be an entry for Ubuntu (C:\wubildr.mbr) and the timeout must not be zero.

Best place to look is right click My Computer, Properties, Advanced, click Settings under Startup & Recovery.

I've never heard of Wubi causing Windows to shut down in the manner you described.

---

### Post by DipreW on 2011-02-13
> **bcbc said:**
> Look in the C:\boot.ini (it's a hidden file). there should be an entry for Ubuntu (C:\wubildr.mbr) and the timeout must not be zero.

Best place to look is right click My Computer, Properties, Advanced, click Settings under Startup & Recovery.

I've never heard of Wubi causing Windows to shut down in the manner you described.


I looked in C:\, and there was no boot.ini file! (I enabled 'show hidden files' btw)
What should I do?

Oh and by the way, I fixed the services.exe problem that I was getting. Just random spyware on the comp, had nothing to do with Ubuntu.

---

### Post by Rubi1200 on 2011-02-13
Hi,
this is what we need from you please:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by DipreW on 2011-02-13
> **Rubi1200 said:**
> Hi,
this is what we need from you please:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.


I don't have a Live CD, and I am also unable to make one. Plus, I don't have an external USB HDD. All I have is Wubi! Is there anything else I can do?

---

### Post by Rubi1200 on 2011-02-13
What is the current situation? Are you able to boot Windows normally?

You must have a boot.ini file. Without it, you would be unable to boot Windows!

Try using the search function from the Start Menu.

---

### Post by DipreW on 2011-02-13
> **Rubi1200 said:**
> What is the current situation? Are you able to boot Windows normally?

You must have a boot.ini file. Without it, you would be unable to boot Windows!

Try using the search function from the Start Menu.

I am able to run Windows normally without the boot.ini. In fact, I just finished rebooting to make sure of this.

Why do I feel like I'm the only person on this planet who has ever been in this situation?

---

### Post by bcbc on 2011-02-13
> **DipreW said:**
> I looked in C:\, and there was no boot.ini file! (I enabled 'show hidden files' btw)
What should I do?

Oh and by the way, I fixed the services.exe problem that I was getting. Just random spyware on the comp, had nothing to do with Ubuntu.
I think I gave instructions how to get there from My Computer!? Maybe my post was a little vague ;)

Anyway - windows is tricky - not only is it hidden, it's also a 'system file' so you have to check off "Hide system files" or something like that...

---

### Post by DipreW on 2011-02-13
> **bcbc said:**
> I think I gave instructions how to get there from My Computer!? Maybe my post was a little vague ;)

Anyway - windows is tricky - not only is it hidden, it's also a 'system file' so you have to check off "Hide system files" or something like that...

LMAO! Idk why that was so funny. But anyways, I followed your instructions and when I clicked on 'edit' (after opening Startup and Recovery) a pop-up told me that it could not find a boot.ini, so it made one for me! 

Horray! right? NO. When I click on the boot.ini file, it opens up a completely blank notepad!!!!!

ARRRRGH [nerd rage]

EDIIIIIT: Btw, the boot file shows up as 'boot', and not 'boot.ini' in C:\. Is this normal?

---

### Post by bcbc on 2011-02-13
> **DipreW said:**
> LMAO! Idk why that was so funny. But anyways, I followed your instructions and when I clicked on 'edit' (after opening Startup and Recovery) a pop-up told me that it could not find a boot.ini, so it made one for me! 

Horray! right? NO. When I click on the boot.ini file, it opens up a completely blank notepad!!!!!

ARRRRGH [nerd rage]

EDIIIIIT: Btw, the boot file shows up as 'boot', and not 'boot.ini' in C:\. Is this normal?

It's normal if you have selected "Hide known extensions". 

Well... I've never heard of Windows XP SP3 not having a boot.ini. That is strange. :???:

Unless maybe you are also running Vista/7 on the same computer as a dual boot?

EDIT: ah the random spyware - that might explain it.

---

### Post by DipreW on 2011-02-13
> **bcbc said:**
> It's normal if you have selected "Hide known extensions". 

That's exactly what is was.

> Well... I've never heard of Windows XP SP3 not having a boot.ini. That is strange. :???:

Wanna be my partner during assisted suicide?

> Unless maybe you are also running Vista/7 on the same computer as a dual boot?

Nope.

And do you happen to be a Python programmer by any chance?

---

### Post by DipreW on 2011-02-13
I'm actually afraid of shutting down now because of the blank boot.ini. I feel like it being blank is worse than it not being there at all!

And does anybody know what 'UNetbootin' is and if I can use that to install Ubuntu as well?

---

### Post by bcbc on 2011-02-13
> **DipreW said:**
> That's exactly what is was.



Wanna be my partner during assisted suicide?



Nope.

And do you happen to be a Python programmer by any chance?

Please don't joke about suicide - it's not funny. 

See [http://support.microsoft.com/kb/330184](http://support.microsoft.com/kb/330184) 
> To resolve this issue, start the computer from the Windows XP CD, start the Recovery Console, and then use the Bootcfg.exe tool to rebuild the Boot.ini file. To do this, follow these steps:
Configure the computer to start from the CD-ROM or DVD-ROM drive. For information about how to do this, see your computer documentation, or contact your computer manufacturer.
Insert the Windows XP CD-ROM into your CD-ROM or DVD-ROM drive, and then restart your computer.
When you receive the "Press any key to boot from CD" message, press a key to start your computer from the Windows XP CD-ROM.
When you receive the "Welcome to Setup" message, press R to start the Recovery Console.
If you have a dual-boot or multiple-boot computer, select the installation that you have to use from the Recovery Console.
When you are prompted, type the administrator password, and then press ENTER.
At the command prompt, type bootcfg /list, and then press ENTER. The entries in your current Boot.ini file appear on the screen.
At the command prompt, type bootcfg /rebuild, and then press ENTER. This command scans the hard disks of the computer for Windows XP, Microsoft Windows 2000, or Microsoft Windows NT installations, and then displays the results. Follow the instructions that appear on the screen to add the Windows installations to the Boot.ini file. For example, follow these steps to add a Windows XP installation to the Boot.ini file:
When you receive a message that is similar to the following message, press Y:
Total Identified Windows Installs: 1

[1] C:\Windows 
Add installation to boot list? (Yes/No/All)
You receive a message that is similar to the following message:
Enter Load Identifier
This is the name of the operating system. When you receive this message, type the name of your operating system, and then press ENTER. This is either Microsoft Windows XP Professional or Microsoft Windows XP Home Edition.
You receive a message that is similar to the following:
Enter OS Load options
When you receive this message, type /fastdetect, and then press ENTER. 

Note The instructions that appear on your screen may be different, depending on the configuration of your computer.
Type exit, and then press ENTER to quit Recovery Console. Your computer restarts, and the updated boot list appears when you receive the "Please select the operating system to start" message.

No I'm not a python programmer - ask me again in a few months - I have a plan to develop something in python.

PS If you ran some anti-virus or anti-spam program - look in it's quarantined items - maybe the boot.ini was infected and it just deleted it. Then just undelete it, and edit it by hand to remove the junk. Maybe your spam software thought Ubuntu was a problem.

---

### Post by DipreW on 2011-02-13
> **bcbc said:**
> Please don't joke about suicide - it's not funny. 

See [http://support.microsoft.com/kb/330184](http://support.microsoft.com/kb/330184) 


No I'm not a python programmer - ask me again in a few months - I have a plan to develop something in python.

PS If you ran some anti-virus or anti-spam program - look in it's quarantined items - maybe the boot.ini was infected and it just deleted it. Then just undelete it, and edit it by hand to remove the junk. Maybe your spam software thought Ubuntu was a problem.

Jesus Christ, nothing seems to be going my way. My Windows XP disc is long lost by now.

And! I've got breaking news! I successfully restarted my machine and I was FINALLY given the option to boot into Ubuntu. But then my smile turned into a frown again as I sat there and read this error message:

[IMG]http://oi52.tinypic.com/10h5bax.jpg[/IMG]



You think I'm getting closer and closer?

EDIT: Now my boot.ini is GONE again! What the heck???

---

### Post by bcbc on 2011-02-13
Those message mean that the wubildr file is missing. Likely whatever killed boot.ini killed wubildr as well. So... you need to turn off whatever antivirus/spam you are running so it stops deleting things, and copy the wubildr file back (i.e. copy c:\ubuntu\winboot\wubildr  to c:\wubildr )

That should kick off the install.

Although I'm confused - if the boot.ini is missing, how did wubildr.mbr get called? Are you sure it's not there somewhere?

(Wubi boots when the user selects to run wubildr.mbr (from the windows bootmanager), which then looks for wubildr on the root of all partitions, but someone has to call wubildr.mbr to start off the process)

---

### Post by DipreW on 2011-02-13
> **bcbc said:**
> Those message mean that the wubildr file is missing. Likely whatever killed boot.ini killed wubildr as well. So... you need to turn off whatever antivirus/spam you are running so it stops deleting things, and copy the wubildr file back (i.e. copy c:\ubuntu\winboot\wubildr  to c:\wubildr )

That should kick off the install.

Although I'm confused - if the boot.ini is missing, how did wubildr.mbr get called? Are you sure it's not there somewhere?

(Wubi boots when the user selects to run wubildr.mbr (from the windows bootmanager), which then looks for wubildr on the root of all partitions, but someone has to call wubildr.mbr to start off the process)


Maybe the boot.ini somehow gets deleted every time Windows boots? I think I might still have some malware.

---

### Post by bcbc on 2011-02-13
> **DipreW said:**
> Maybe the boot.ini somehow gets deleted every time Windows boots? I think I might still have some malware.

I don't know - something is weird... go to Microsoft Updates and download run their malware remover.

Or this link might help
[http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/](http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/)

Anyway - I gotta go - good luck!

---

### Post by Rubi1200 on 2011-02-13
I agree with bcbc that something is not right here. It's possible you might have a boot sector virus which is why you are stuck in this loop, so to speak.

Definitely try and do some "cleaning" with the tools bcbc linked to and then see where you get.

---

### Post by DipreW on 2011-02-13
Good news! 

[IMG]http://farm6.static.flickr.com/5256/5441178943_0720838aa8_b.jpg[/IMG]



Now.. I don't want to be greedy, so here's how I did it:

1. Ran three different virus/malware scanners.
   1a. Found over 700 infected files, 90% of which were extreme threats.
1b. "Healed"/ deleted the pesks.
1c. Reboot.

2.  Manually edited my boot.ini file, to add a spot for Ubuntu.

3.  Rebooted machine.

4.  Ubuntu showed up on the boot menu. Booted that sucker up and it went straight into the installation process. 

5.  Celebrated!


So far so good guys. And again, thank you so much!

EDIT: Now to start programming in Python!

---

### Post by Rubi1200 on 2011-02-13
Excellent! What a relief to have finally got things sorted out and, of course, you are more than welcome for the help :-)

Please mark this thread Solved using the Thread Tools near the top of the page. It will help other users find a working solution should they ever find themselves in a similar situation.

Enjoy!

---

### Post by bcbc on 2011-02-13
That sounds like quite the adventure.

I think if your windows is so compromised you might do better with partitioning your drive and installing Ubuntu directly... to avoid having a virus delete the wubi boot files again (or maybe the root.disk). A separate partition it's going to be safer.

Just a thought.

---

### Post by DipreW on 2011-02-13
> **Rubi1200 said:**
> Excellent! What a relief to have finally got things sorted out and, of course, you are more than welcome for the help :-)

Please mark this thread Solved using the Thread Tools near the top of the page. It will help other users find a working solution should they ever find themselves in a similar situation.

Enjoy!

Will do!

> 
I think if your windows is so compromised you might do better with partitioning your drive and installing Ubuntu directly... to avoid having a virus delete the wubi boot files again (or maybe the root.disk). A separate partition it's going to be safer.


I'll see what I can do. Thanks again!

---

