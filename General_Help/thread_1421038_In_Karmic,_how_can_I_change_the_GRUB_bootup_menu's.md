---
title: "In Karmic, how can I change the GRUB bootup menu's default choice?"
date: 2010-03-03
forum: General Help
---

### Post by rewyllys on 2010-03-03
Yesterday I installed on my laptop (an IBM Thinkpad T42) "virt manager" using the Synaptic Package Manager.  I'm running Karmic.

As part of the installation, SPM had me reboot the computer (which is dual-booted with Windows XP, which I use less than 1% of the time).  The new GRUB screen came up showing two new initial lines, the first 2 of the following 4 lines:[INDENT]Ubuntu, Linux 2.6.31-19-generic-pae
Ubuntu, Linux 2.6.31-19-generic-pae (recovery mode)
Ubuntu, Linux 2.6.31-19-generic
Ubuntu, Linux 2.6.31-19-generic (recovery mode)
   .
   .
   .
[/INDENT]When I allow the default choice of the first line to prevail, Ubuntu boots up into a condition in which the Wireless Network Connection fails to open, and in which nothing I've been able to think of makes it open.

If, instead, I scroll down to the third line (which was the initial default choice line, i.e., the default choice line prior to the "virt manager" installation), Ubuntu boots up into a condition in which the Wireless Network Connection operates as usual, viz., immediately.  

Scrolling down works, but it would be better, it seems to me, to return to the condition in which the current line 3 either becomes line 1 or else becomes the default bootup choice.

I've used SPM to uninstall "virt manager", but the 2 new intial lines in the GRUB options remain.  I understand that with Karmic's version of GRUB, viz., GRUB-2, it is no longer possible to change the bootup menu choices easily.

Can anyone suggest how I can either eliminate the first 2 lines in my current GRUB screen, or make line 3 the default choice?

Thanks in advance for any and all help.

---

### Post by Revolutionary101 on 2010-03-03
I use a program called Start Up Manager to manage my GRUB menu. To install it type this into terminal:

```
sudo apt-get install startupmanager
```

This program provides an easy to use GUI to edit GRUB.

---

### Post by oldfred on 2010-03-03
This kernel is used for 32 bit systems to allow addressing more that 3GB of memory. If you do not have lots of memory or paln on trying to make it work, you should be able to go into synaptic and totally uninstlal it.

---

### Post by patchwork on 2010-03-03
To change the default grub entry, you can do several things when editing your /etc/default/grub

First, the most direct way, change 

```
GRUB_DEFAULT=0
```to 

```
GRUB_DEFAULT=2
```Alternatively, you can set it to 

```
GRUB_DEFAULT=saved
```and enter 

```
sudo grub-set-default 2
```in the command line.  This will allow you a little more flexibility when new kernels are downloaded to change your default entry without manually editing the file.  Simply redo the sudo grub-set-default X  (where X is the number of the entry in the menu, starting from 0)

---

### Post by rewyllys on 2010-03-04
> **Revolutionary101 said:**
> I use a program called Start Up Manager to manage my GRUB menu. To install it type this into terminal:

```
sudo apt-get install startupmanager
```This program provides an easy to use GUI to edit GRUB.

I appreciate your suggestion, Revolutionary101.  However, when I went into Terminal and issued the above command, the response was:

E: Couldn't find package startupmanager

Using the Synaptic Package Manager, I searched for a variety of spellings of "Startup", with and without "Manager", all without success.

Next, I tried the Ubuntu Software Center.  It lists "StartUp-Manager" under "System Tools", but after I clicked in USC on "StartUp-Manager" the response was "Not available in the current data".

Bearing in mind that Karmic introduced--as I understand it--a major change in GRUB, I'm leery of trying to install "StartUp-Manager" without using either SPM or USC.

Does anyone have further suggestions?

---

### Post by rewyllys on 2010-03-04
> **oldfred said:**
> This kernel is used for 32 bit systems to allow addressing more that 3GB of memory. If you do not have lots of memory or paln on trying to make it work, you should be able to go into synaptic and totally uninstlal it.

Oldfred, thank you for your suggestion.  I'd like to try to use it, since I have less than 3GB of RAM on my laptop.

Could you please provide me (a newbie) details on just what kernel I should uninstall to get rid of the "pae" lines?

Thanks again.

---

### Post by oldfred on 2010-03-04
You can use synaptic or command line but be sure not to uninstall the one you are using to boot. We normally recommend everyone keep at least 2 versions, one older that you know worked as just in case.

In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by rewyllys on 2010-03-04
> **patchwork said:**
> To change the default grub entry, you can do several things when editing your /etc/default/grub

First, the most direct way, change 

```
GRUB_DEFAULT=0
```to 

```
GRUB_DEFAULT=2
```Alternatively, you can set it to 

```
GRUB_DEFAULT=saved
```and enter 

```
sudo grub-set-default 2
```in the command line.  This will allow you a little more flexibility when new kernels are downloaded to change your default entry without manually editing the file.  Simply redo the sudo grub-set-default X  (where X is the number of the entry in the menu, starting from 0)

Patchwork, thank you for your suggestion.  I just tried your "most direct way", i.e., I edited file /etc/default/grub to read GRUB_DEFAULT=2 

However, I then re-booted, and the menu lines came up with the initial line, line 0, shown highlighted as the default option.  This behavior is consistent with what I believe I recall as a general warning that accompanied the release of Karmic, viz., that Karmic had adopted GRUB-2, in which the user no longer has direct access to the GRUB menu, unlike the situation with the original GRUB. 

So, I'm still at a loss as to how to change the default choice in the new GRUB-2.  I'll be grateful for any and all suggestions.

---

### Post by rewyllys on 2010-03-04
> **oldfred said:**
> You can use synaptic or command line but be sure not to uninstall the one you are using to boot. We normally recommend everyone keep at least 2 versions, one older that you know worked as just in case.

In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

Thanks again, oldfred, but I'm still in trouble.  From the post #8 comment, I used the idea of entering "uname -r" at the command line.  It yields the result 

2.6.31-20-generic 

which I find completely puzzling, since the bootup menu, which bears the header

GNU GRUB version 1.97~beta4

tells me that its initial 3 choices are

Ubuntu, Linux 2.6.31-19-generic-pae
Ubuntu, Linux 2.6.31-19-generic-pae (recovery mode)
Ubuntu, Linux 2.6.31-19-generic

none of which is kernel 2.6.31-20-generic, and since Synaptic PM tells me that 

2.6.31-19-generic-pae

is NOT installed.

This situation is confusing me more and more.:confused:  Help, please!

---

### Post by oldfred on 2010-03-04
Just this morning for me the update included -20 and when I rebooted that was the default choice.
Is your grub not getting updated?
I would try this which should rewrite grub.cfg with all the kernels it finds.
sudo update-grub

---

### Post by rewyllys on 2010-03-04
> **oldfred said:**
> Just this morning for me the update included -20 and when I rebooted that was the default choice.
Is your grub not getting updated?
I would try this which should rewrite grub.cfg with all the kernels it finds.
sudo update-grub

Thanks, oldfred. THAT did the trick!

After "sudo update-grub", not only has the kernel been updated to number

2.6.31-20

but also the default choice has become the third option, in accord with my earlier assignment of GRUB_DEFAULT=2 following patchwork's suggestion.

Many thanks for all the advice.  It's solved my problem!:popcorn:

---

