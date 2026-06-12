---
title: "Can I remove Antivirus Soft from Windows using Ubuntu?"
date: 2010-05-23
forum: General Help
---

### Post by MrKrabz on 2010-05-23
My Windows computer was recently infected by Antivirus Soft (or was it AntiSpyware Soft) and it corrupted my isapnp.sys file, so I can't run WIndows. I have dual boot because I use Ubuntu, so Is there anyway to remove the malware from Windows and fix that problem using Ubuntu?

---

### Post by aysiu on 2010-05-23
I think the best thing to do if you're infected with malware in Windows is to reinstall Windows and then implement some proper security afterwards (limited user accounts, NoScript, education about social engineering, automatic Windows updates).

That is the only way to be 100% sure the malware is fully removed and will stay off.

---

### Post by MrKrabz on 2010-05-23
> **aysiu said:**
> I think the best thing to do if you're infected with malware in Windows is to reinstall Windows and then implement some proper security afterwards (limited user accounts, NoScript, education about social engineering, automatic Windows updates).

That is the only way to be 100% sure the malware is fully removed and will stay off.

I have way too much stuff on it, and I doubt its severe enough to absolutely have to delete everything. I get malware all the time (of course it never damaged any sys files before, though).

I'd rather do it this way so I can at least get WIndows started, and then clean it out after I can safely store my files. So is this possible?

---

### Post by akakingess on 2010-05-23
I haven't tried it myself, but I would think that you could mount the Windows partition and run some utilities (such as, but not limited to clamav) on the partition to get back into Windows. However, I do agree with aysiu's advice about a clean install, so maybe you could mount the Windows partition and at least backup your critical materials and then do the clean install. Just an FYI, I use AVG and I haven't seen any problems in years, although I am also very careful with what I do/download and what my kids are allowed to do.

---

### Post by howefield on 2010-05-23
Have you tried booting Windows in safe mode with networking, then install malwarebytes (it has a 30 day trial).

Then scan your machine with Malwarebytes.

---

### Post by aysiu on 2010-05-23
> **MrKrabz said:**
> I have way too much stuff on it, You can use Ubuntu to back up your stuff before you reinstall. If you're talking about programs, after you reinstall, use CloneZilla to clone your perfect setup so that if it happens again, you can easily revert to that pristine state. > and I doubt its severe enough to absolutely have to delete everything. I get malware all the time (of course it never damaged any sys files before, though). The fact you get malware all the time is symptomatic of a flawed approach. Take my advice and you won't get malware any time, let alone all the time.

---

### Post by MrKrabz on 2010-05-23
> **howefield said:**
> Have you tried booting Windows in safe mode with networking, then install malwarebytes (it has a 30 day trial).

Then scan your machine with Malwarebytes.

As I mentioned in the first post, the malware corrupted my isapnp.sys file. I don't have a WIndows XP CD, so I can't just replace it. I have to remove the malware.

[quote=aysiu]You can use Ubuntu to back up your stuff before you reinstall. If you're  talking about programs, after you reinstall, use CloneZilla to clone  your perfect setup so that if it happens again, you can easily revert to  that pristine state.[/quote]
I realize that, which is why I'm going to do a clean install after. But I'd much rather get WIndows working first, because I have to remove Ubuntu from this computer after today (however I'm putting it on my laptop in a few days).

---

### Post by wojox on 2010-05-23
Do you have a Windows CD? [http://support.microsoft.com/kb/315311](http://support.microsoft.com/kb/315311)

Never mind. Just saw your new post.

---

### Post by jamesisin on 2010-05-23
If you can boot into Windows you can use ComboFix and then regular spyware (Spybot) and viral-scanning (Avast!) to remove what remains.  I wrote an article on ComboFix:

[http://www.soundunreason.com/InkWell/?p=470](http://www.soundunreason.com/InkWell/?p=470)

---

### Post by philinux on 2010-05-23
> **MrKrabz said:**
> My Windows computer was recently infected by Antivirus Soft (or was it AntiSpyware Soft) and it corrupted my isapnp.sys file, so I can't run WIndows. I have dual boot because I use Ubuntu, so Is there anyway to remove the malware from Windows and fix that problem using Ubuntu?

one thing you could try is using the livecd install clamav and then scan windows.

---

### Post by MrKrabz on 2010-05-23
> **philinux said:**
> one thing you could try is using the livecd install clamav and then scan windows.

I installed clamav using "sudo apt-get install clamav". How do I scan the Windows partition (its named 80 GB FIlesystem or something like that)? I'm not sure if this will make a difference, but I didn't fully install ubuntu yet. I'm just trying it out.

---

### Post by howefield on 2010-05-23
There is a GUI frontend to clam called clamtk.

Might make it a bit easier.

There are also dozens of well known anti virus applications that run natively in linux, eg avast , bitdefender.

---

### Post by akakingess on 2010-05-23
I don't know that clamav by itself will solve the problem, so you may also need to search/look for other malware/anti-virus software for Ubuntu. That said, you need to mount the Windows partition, so look for the device information by opening a terminal and entering "sudo fdisk -l" without the quotes, and that is the lettler l not a 1. That should show you the device names for the partitons/drives, then just mount the Windows partition (sudo mount dev/sda1) just use your own information obviously.

---

### Post by MrKrabz on 2010-05-23
> **akakingess said:**
> I don't know that clamav by itself will solve the problem, so you may also need to search/look for other malware/anti-virus software for Ubuntu. That said, you need to mount the Windows partition, so look for the device information by opening a terminal and entering "sudo fdisk -l" without the quotes, and that is the lettler l not a 1. That should show you the device names for the partitons/drives, then just mount the Windows partition (sudo mount dev/sda1) just use your own information obviously.

1. Will mounting the disk effect anything? Will I lose any files on Windows?

2. How do I use clamav?

3. What other Antivirus software is there, and what is the command to install it (for example, sudo apt-get install FILENAME).

---

### Post by akakingess on 2010-05-23
clamav is in the repositories, which means you can go to System-->Administration-->Synaptic Package Manager, and enter your password, then do a quick search for clamav, it will show up, right-click on it and choose install? or whatever it says, can't remember off of the top of my head. Then click on the 'Apply' button in the Package Manager and it will install. Also, mounting the drive will not cause you to lose any data, simply puts it on the desktop via a drive icon and will allow clamav to see it. Also, you may want to install the GUI version clamtk that howefield mentioned as it will make it easier. Then, launch clamtk and have it choose to scan the mounted Windows partition/drive.

---

### Post by MrKrabz on 2010-05-23
> **akakingess said:**
> clamav is in the repositories, which means you can go to System-->Administration-->Synaptic Package Manager, and enter your password, then do a quick search for clamav, it will show up, right-click on it and choose install? or whatever it says, can't remember off of the top of my head. Then click on the 'Apply' button in the Package Manager and it will install. Also, mounting the drive will not cause you to lose any data, simply puts it on the desktop via a drive icon and will allow clamav to see it. Also, you may want to install the GUI version clamtk that howefield mentioned as it will make it easier. Then, launch clamtk and have it choose to scan the mounted Windows partition/drive.
The problem with that is I didn't install Ubuntu. I'm just trying it out, so I can't even use the Synaptic Package Manager (when I click on it, nothing happens). I used apt-get to install clamav. Not sure if that'll make a difference or not.

But how do I install clamtk? I downloaded and extracted it, and it gave me two .tar.gz files (control and data) and a file named debian-binary.

---

### Post by akakingess on 2010-05-23
I would start [here]("http://manpages.ubuntu.com/manpages/lucid/man1/dh_installdocs.1.html") although that may not have all of your answers, and since I don't know the specifics, I recommend going to the Ubuntu Help link at the top of the forum page, and doing a search, the site manuals.ubuntu.org or something like that has plenty of documentation that is search-able to help you find the answers that you need.

---

### Post by philinux on 2010-05-23
@OP sudo apt-get instal clamtk

---

### Post by akakingess on 2010-05-23
Yeah, I do apologize for being so blunt or abrupt, however you want to put it, but I am trying to keep track of my 3 kids, while replying to multiple posts, and unloading groceries, so if my info has been insufficient, please keep in mind that I am usually very polite and helpful ;)  Good Luck, and keep us updated, please.

---

### Post by MrKrabz on 2010-05-23
EDIT: Ignore this post.

---

### Post by jamesisin on 2010-05-23
Did you see my previous post?

---

### Post by akakingess on 2010-05-24
> **jamesisin said:**
> Did you see my previous post?

The OP can't boot into Windows at all and doesn't have a Windows CD to use either.

---

### Post by jamesisin on 2010-05-24
Oops.  I overlooked that.  Of course, being ignored doesn't make me any smarter...

---

### Post by mike555 on 2010-05-24
if I were you I would get "dr.Web" .iso , burn it as image to cd , start up your computer to it and run it .......... I have had good luck with this product ...
   [http://tinyurl.com/6fhkoy](http://tinyurl.com/6fhkoy)

---

### Post by akakingess on 2010-05-24
> **jamesisin said:**
> Oops.  I overlooked that.  Of course, being ignored doesn't make me any smarter...

Just so you know, I wasn't trying to single you out, there had been multiple posts in which I don't think the poster had read the OP's post thoroughly. Like I've said before and will say again, we are all here as one big happy family trying to help each other out ;)

---

### Post by jamesisin on 2010-05-24
It's easy enough to overlook things.  I don't mind it when folks set me right.

---

### Post by pricetech on 2010-05-24
If you have a friend with a working install of XP, you can mount your windows partition from Ubuntu and replace the corrupt file with a known good copy.  That should allow you to boot windows after which you can do whatever cleanup you want to do.

I'd still back up my data first though, if it was me.

---

### Post by wilee-nilee on 2010-05-24
> **aysiu said:**
> I think the best thing to do if you're infected with malware in Windows is to reinstall Windows and then implement some proper security afterwards (limited user accounts, NoScript, education about social engineering, automatic Windows updates).

That is the only way to be 100% sure the malware is fully removed and will stay off.

I would agree with this, it is very difficult to find rootkits, and keyloggers. Once you have been infected, you can do a clean up and it seems okay but these two types of problems can destroy your credit, accounts with your bank...etc if used to gather information and used against you. 
 
The best thing to do is always have a backup of all your important things you can't lose on a external hard drive. This way in a situation like this all you have to do is clean the HD or overwrite it with a new install. 

When you can buy a terabyte external off the web for less then 100$ US not being prepared for a sudden reinstall is not being prepared. As well having install discs or loaded thumbs or ISO's of the used system is part of being prepared for any problem with the correct tool set.

Windows can be run without problems if set up correctly, I have never gotten anything but adware cookies, as far as I know since there are rootkits that can't be detected basically, and 0 day attacks.

---

### Post by talkingtree on 2010-06-08
> **MrKrabz said:**
> My Windows computer was recently infected by Antivirus Soft (or was it AntiSpyware Soft) and it corrupted my isapnp.sys file, so I can't run WIndows. I have dual boot because I use Ubuntu, so Is there anyway to remove the malware from Windows and fix that problem using Ubuntu?

i got the same problem thus the question too :)

---

### Post by scottuss on 2010-06-08
To be honest, your best bet is to format and start again, you can then be sure the malware has gone.

Otherwise, I'd use a live cd such as the Kaspersky live boot CD (or similar) which will run a full scan.

ClamAV is OK, but not fantastic.

---

### Post by talkingtree on 2010-06-08
> **scottuss said:**
> To be honest, your best bet is to format and start again, you can then be sure the malware has gone.

Otherwise, I'd use a live cd such as the Kaspersky live boot CD (or similar) which will run a full scan.

ClamAV is OK, but not fantastic.

interestingly enough, i tried using avast start up scan, but it doesnt work.. although it detects, the malware still stays.. it's very annoying.. i'm going to try out kaspersky as you suggested

formatting would be the cleanest way to go i guess.. but there are so many program customised/installed... which is very troublesome to reinstall again :P

---

### Post by julio_cortez on 2010-06-08
Well, if also mounting the HD on a clean system and scanning it didn't solve the problem, I don't see much alternatives to it: I'd format, too.

Be sure you backed all your important documents up, before formatting..
I had a couple of not-so-funny experiences with customers that claimed they backed up all their data and it turned out they forgot that ***C:\temp\todelete\this-folder-has-to-be-deleted-asap\vital-document-that-no-one-can-live-without.txt** *file.
Thanks Heaven I always had the habit to perform backups of their entire drives before formatting so no-one ever lost a file :D

---

