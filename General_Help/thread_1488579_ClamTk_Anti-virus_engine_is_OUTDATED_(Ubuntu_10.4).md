---
title: "ClamTk Anti-virus engine is OUTDATED (Ubuntu 10.4)"
date: 2010-05-20
forum: General Help
---

### Post by trixa_13 on 2010-05-20
Hi everyone! I wanted to run a virus scan but then, I saw that the ClamTk Anti-virus engine is outdated. How do I get to upgrade to the latest version?

---

### Post by dino99 on 2010-05-20
check "clam" into synaptic and be sure you have all ('8') packages installed.
if you run clamav against a file, a dialog box popup with a built-in menu, from there you can check for updates (note: signatures have to be updated, if the gui is not its because a new release exist but ubuntu dont upgrade it into its repo, no worry about that)

---

### Post by 3rdalbum on 2010-05-20
> **trixa_13 said:**
> Hi everyone! I wanted to run a virus scan but then, I saw that the ClamTk Anti-virus engine is outdated. How do I get to upgrade to the latest version?

I just wanted to check with you: You're aware that Ubuntu is not affected by any viruses at the moment? No Windows viruses work (unless you're dumb enough to *purposely* run them in Wine) and there are no Linux viruses that work these days.

If you want ClamAV to scan some files that will go onto a Windows computer, then go ahead.

---

### Post by trixa_13 on 2010-05-23
> **dino99 said:**
> check "clam" into synaptic and be sure you have all ('8') packages installed.
if you run clamav against a file, a dialog box popup with a built-in menu, from there you can check for updates (note: signatures have to be updated, if the gui is not its because a new release exist but ubuntu dont upgrade it into its repo, no worry about that)

Um, what are those "8" packages?

---

### Post by frogging on 2010-05-24
> **3rdalbum said:**
> I just wanted to check with you: You're aware that Ubuntu is not affected by any viruses at the moment? No Windows viruses work (unless you're dumb enough to *purposely* run them in Wine) and there are no Linux viruses that work these days.

If you want ClamAV to scan some files that will go onto a Windows computer, then go ahead.

I really hope all Linux users are not as dumb as you sound.  Your right we can not get infected BUT you can have a virus and if you e-mail a friend that uses Windows they will not like you when your e-mail infects their machine.  So you still need to run a scan and make sure your not a carrier.  Rock on baby :guitar:

---

### Post by bodhi.zazen on 2010-05-24
> **trixa_13 said:**
> Um, what are those "8" packages?

See : [http://ubuntuforums.org/showpost.php?p=9265657&postcount=9](http://ubuntuforums.org/showpost.php?p=9265657&postcount=9)

---

### Post by wannacme16 on 2011-06-17
> **frogging said:**
> I really hope all Linux users are not as dumb as you sound.  Your right we can not get infected BUT you can have a virus and if you e-mail a friend that uses Windows they will not like you when your e-mail infects their machine.  So you still need to run a scan and make sure your not a carrier.  Rock on baby :guitar:
An education is a powerful and wonderful tool that brings light into an otherwise dark existence. The lack thereof is self explanatory. While your response brings a truth to the necessity for keeping your system up to date and virus free for everyone's benefit it nonetheless testifies to your lack of education into the very philosophy that Ubuntu has as its foundation. I hope all Linux users are not as ignorant as you are as to what makes Linux and more specifically Ubuntu truly great.

---

### Post by mcduck on 2011-06-17
> **frogging said:**
> I really hope all Linux users are not as dumb as you sound.  Your right we can not get infected BUT you can have a virus and if you e-mail a friend that uses Windows they will not like you when your e-mail infects their machine.  So you still need to run a scan and make sure your not a carrier.  Rock on baby :guitar:

If you send such infected file to a windows user their antivirus application will catch it so it won't cause any problems.

If the Windows user's antivirus isn't up to the task, they are already in serious trouble, no matter if you send them an infected file or not.

So no, there really isn't much point in scanning for Windows viruses on a Linux machine, apart from special situations like when running a mail server or something like that.

---

### Post by northd_tech on 2011-09-03
> **mcduck said:**
> If you send such infected file to a windows user their antivirus application will catch it so it won't cause any problems. If the Windows user's antivirus isn't up to the task, they are already in serious trouble, no matter if you send them an infected file or not. So no, there really isn't much point in scanning for Windows viruses on a Linux machine, apart from special situations like when running a mail server or something like that. 

I disagree with the above for several reasons- 

1. Not every Windows user has (or understands the need for) antivirus software that is **both installed AND CURRENT** (many of the Windows machines came with a 60- or 90-day or 12-month antivirus 'subscription' that can and DOES EXPIRE). Not every Windows user who has come to [COLOR=Red]**trust their "internet computer"**[/COLOR] understands that an UNPROTECTED/"expired" Windows machine ONLINE is like a turkey serving platter covered with a mound $100 bills sitting in a 'bad neighbo[u]rhood...' 

2. The attitude that 'they [Windows users with 'iffy' anti-virus protection] are already in serious trouble' **DOES NOTHING to help eliminate/curtail the spread of viruses on servers WORLDWIDE**. Don't we all (as **RESPONSIBLE** Internet users WORLDWIDE) share the burden of trying to limit/eliminate exactly that? 

3. I believe there are hundreds or more people **just like me** who "dual boot" (or more) Windows and/or [Ubuntu, or Fedora, or SUSE, or ArchLinux, or PCLinuxOS, or Scientific Linux, or FreeBSD, or MacOS, or UNIX, etc...] and often browse/download online while in the "other" OS. I find myself needing to "push" dozens/hundreds of MegaBytes (if not GigaBytes) of downloaded mixed Windows/Linux data from one OS to the other, usually one or several directories at a time. I often want to scan the 'suspicious' files/directories first from Ubuntu (that's actually about **95+% of the reason why I used Linux** **for the download in the first place**). Once "safe?" on the Windows partition (or more likely an external USB drive), I usually scan that Windows 'download' directory with 3-5 Windows based anti-virus programs (before I archive and/or install[COLOR=Red]** anything**[/COLOR]). 

Guess how many times that a virus has 'infected' my Windows partition(s), esp. since I went to this 'dual-boot method' somewhere around 1995? Generally, I find myself using a Linux LiveCD/DVD to repair the virus damage on someone else's **Windows-ONLY** machine so that I can attempt to "rescue" their personal data and possibly programs. 

Anyway, I can see a HUGE reason to virus scan periodically on Linux systems (especially since so many of the Linux servers are [COLOR=Red]**PRIMARILY**[/COLOR] Internet **[windows] file Servers**...). Can anyone here **honestly** tell me that an average Apache Web Server has NEVER relayed **A SINGLE infected** Windows (or less likely Mac) file and/or malware/script? Sorry, but I can see an immediate need for [COLOR=Red]**MORE**[/COLOR], not NO Linux anti-virus scanning. 

All that said, I found the following thread (as well as this one) while I was searching for a way to keep my own ClamTk anti-virus program and definitions more current:
 [B]How to update 'ClamTK' anti-virus
[/B] [http://www.linuxquestions.org/questions/linux-newbie-8/how-to-update-clamtk-anti-virus-900566/](http://www.linuxquestions.org/questions/linux-newbie-8/how-to-update-clamtk-anti-virus-900566/) 

The ClamTk update 'methods' are **definitely less user-friendly** than damn-near any of the methods under Windows (with the Windows 'cousin' ClamWin included in my assessment here- I've run them both- often concurrently- for years/decades now)- perhaps that is what the Ubuntu 'newbies' that are migrating here from Windows are trying to tell us here...

---

### Post by yakkeh on 2012-03-03
> **3rdalbum said:**
> I just wanted to check with you: You're aware that Ubuntu is not affected by any viruses at the moment? No Windows viruses work (unless you're dumb enough to *purposely* run them in Wine) and there are no Linux viruses that work these days.

If you want ClamAV to scan some files that will go onto a Windows computer, then go ahead.
I really don't want to discourage you, but there are viruses and other malware for Linux systems!! Although there aren't millions of them like on Windows sytems, the creation is on the rise.

Like i said, you shouldn't be too worried if you're using Linux (for the moment), but it's plain ignorance and denial that will increase the success them. To get you started, check out Wikipedia: [http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

---

### Post by yakkeh on 2012-03-03
> **northd_tech said:**
> I disagree with the above for several reasons- 

1. Not every Windows user has (or understands the need for) antivirus software that is **both installed AND CURRENT** (many of the Windows machines came with a 60- or 90-day or 12-month antivirus 'subscription' that can and DOES EXPIRE). Not every Windows user who has come to [COLOR=Red]**trust their "internet computer"**[/COLOR] understands that an UNPROTECTED/"expired" Windows machine ONLINE is like a turkey serving platter covered with a mound $100 bills sitting in a 'bad neighbo[u]rhood...' 

2. The attitude that 'they [Windows users with 'iffy' anti-virus protection] are already in serious trouble' **DOES NOTHING to help eliminate/curtail the spread of viruses on servers WORLDWIDE**. Don't we all (as **RESPONSIBLE** Internet users WORLDWIDE) share the burden of trying to limit/eliminate exactly that? 

3. I believe there are hundreds or more people **just like me** who "dual boot" (or more) Windows and/or [Ubuntu, or Fedora, or SUSE, or ArchLinux, or PCLinuxOS, or Scientific Linux, or FreeBSD, or MacOS, or UNIX, etc...] and often browse/download online while in the "other" OS. I find myself needing to "push" dozens/hundreds of MegaBytes (if not GigaBytes) of downloaded mixed Windows/Linux data from one OS to the other, usually one or several directories at a time. I often want to scan the 'suspicious' files/directories first from Ubuntu (that's actually about **95+% of the reason why I used Linux** **for the download in the first place**). Once "safe?" on the Windows partition (or more likely an external USB drive), I usually scan that Windows 'download' directory with 3-5 Windows based anti-virus programs (before I archive and/or install[COLOR=Red]** anything**[/COLOR]). 

Guess how many times that a virus has 'infected' my Windows partition(s), esp. since I went to this 'dual-boot method' somewhere around 1995? Generally, I find myself using a Linux LiveCD/DVD to repair the virus damage on someone else's **Windows-ONLY** machine so that I can attempt to "rescue" their personal data and possibly programs. 

Anyway, I can see a HUGE reason to virus scan periodically on Linux systems (especially since so many of the Linux servers are [COLOR=Red]**PRIMARILY**[/COLOR] Internet **[windows] file Servers**...). Can anyone here **honestly** tell me that an average Apache Web Server has NEVER relayed **A SINGLE infected** Windows (or less likely Mac) file and/or malware/script? Sorry, but I can see an immediate need for [COLOR=Red]**MORE**[/COLOR], not NO Linux anti-virus scanning. 

All that said, I found the following thread (as well as this one) while I was searching for a way to keep my own ClamTk anti-virus program and definitions more current:
 [B]How to update 'ClamTK' anti-virus
[/B] [http://www.linuxquestions.org/questions/linux-newbie-8/how-to-update-clamtk-anti-virus-900566/](http://www.linuxquestions.org/questions/linux-newbie-8/how-to-update-clamtk-anti-virus-900566/) 

The ClamTk update 'methods' are **definitely less user-friendly** than damn-near any of the methods under Windows (with the Windows 'cousin' ClamWin included in my assessment here- I've run them both- often concurrently- for years/decades now)- perhaps that is what the Ubuntu 'newbies' that are migrating here from Windows are trying to tell us here...

I completely agree with the above, but I think a lot of people are missing the point completely and are only thinking about their own "desktop" experience. As soon as you connect your ethernet cable or wifi, you should have your antivirus installed and updated. Just like when you put on your seat belt in a car. And personally, I find there should be fines for people who don't, because they are directly putting other people in danger (unlike the seat belt in my comparisson, for which you do get fined!).

Up to this day, most people continue to use Windows as a workstation to get their daily jobs done, while Linux systems provide services on networks like file sharing, mail servers, etc.

If you have a file server with multiple clients connecting to it, sharing their file... it only takes 1 infected client to screw up all the other people's work and a busy day/week for the admin to clean up all the mess and try to restore all the files from backup (if there are any!). 
Running Clamav on the server can detect problems early and prevent greater damage.

And for all those people saying that viruses don't affect Linux, think again! If you have an infected windows station, it can affect ALL of your servers and network equipment to the point that nobody else is able to use any of it. It's a hell of a work for administrators to find the source and clean everything up, and a huge financial cost to the affected company.

If you think it is alright to store any sort of malware on a device, even if it doesn't affect the system it is on, you shouldn't be allowed to operate a computer and most definitely not call yourself an advanced user, expert or professional.

---

### Post by Paqman on 2012-03-03
> **yakkeh said:**
> I really don't want to discourage you, but there are viruses and other malware for Linux systems!! Although there aren't millions of them like on Windows sytems, the creation is on the rise.


Not really. All known vulnerabilities should have been patched, that's why we get kernel updates so often. I've not seen anything that suggests Linux malware is increasing.

Linux isn't immune to malware, but neither does it particularly need 3rd party software to be secure. Keeping your system up-to-date and not doing silly things with your system should be perfectly sufficient for most desktop users.

If you do decide to install an antivirus package for peace of mind, you can do a lot better than ClamAV. For a decent solution you're going to have to go outside the repos and install something like Avast or AVG.

---

### Post by 3rdalbum on 2012-03-03
> **yakkeh said:**
> I really don't want to discourage you, but there are viruses and other malware for Linux systems!! Although there aren't millions of them like on Windows sytems, the creation is on the rise.

That Wikipedia list is only a couple of entries longer than it was back in 2005. I didn't look at every single page, but all the references predated 2010; it doesn't seem like Linux malware is on the rise unless you're also referring to Android trojans. Old Linux viruses are no longer compatible with new distros.

There are still rootkits, sure, but these are not detectable by Clam.

There are malicious scripts like the one that was on Gnome Look for a while, but as far as I know no anti-virus program cares about that script (that no longer works).

Now let this thread go back to sleep, please.

---

