---
title: "Real-time antivirus?"
date: 2010-10-12
forum: General Help
---

### Post by vagaerg on 2010-10-12
Hello to all... I'm new in UBUNTU and would like to get a real-time antivirus
Maybe it's not necessary, but I still want it (I've got an iMAC and have installed an antivirus... :guitar: ) So, please... which antivirus is good and in real-time (I mean that, if I try to open an infected file or go to a bad website, it stops it). Is KLAMav good and in Real time?
Thanks a lot.

---

### Post by tuxulin on 2010-10-12
[https://help.ubuntu.com/community/BitDefender](https://help.ubuntu.com/community/BitDefender)

you can also try CLAMV but in real time you might want to
do some research and fiddling

good luck
TUX

---

### Post by gandaran on 2010-10-12
bitdefender only works on demand.
list of free antivirus for linux
[http://www.tuxradar.com/content/get-best-virus-scanner-linux](http://www.tuxradar.com/content/get-best-virus-scanner-linux)

---

### Post by vagaerg on 2010-10-13
Thanks to all,
but which one is in real time and which one of the real time ones do you recommend me? I'm new and I can tell you about Windows, but Not about UBUNTU...
Thanks in advance

---

### Post by WorMzy on 2010-10-13
Clamav is on-demand too. I'm not sure that there even is a real-time anti-virus application for Linux, since there's little to no point to one.

---

### Post by gandaran on 2010-10-13
> **vagaerg said:**
> Thanks to all,
but which one is in real time and which one of the real time ones do you recommend me? I'm new and I can tell you about Windows, but Not about UBUNTU...
Thanks in advance
check them on the link in my first post, some of them can work in real time, you will have to install the dazuko module for this, dazuko is the real time scanning engine for linux antivirus but is very hard to setup, I believe it still conflicts with apparmor so you must disable apparmor to run dazuko.
look antivirus is unnecessary in linux and real time scanning probably would slow down your computer but you can try it.
what I think would be useful is just the scanning of emails, this can be done easily by setting up a evolution filter to use any installed on demand antivirus to scan incoming or outgoing emails.
I would recommend bitdefender for this, it is in fact the best of them all with spyware, antivirus and adaware updates just like the windows version.

---

### Post by tgm4883 on 2010-10-13
Symantec AntiVirus for Linux has a real time scanner.

---

### Post by vagaerg on 2010-10-14
Thanks to everyone...
Well... I've seen Symantec's antivirus, but as you've said that a real time antivirus is completely unnecessary and will slow down my computer, do you think Avast! free antivirus is ok?
I've tried to install Avira Antivir free for Ubuntu, but it says that Dazuko can not be installed, and AVG will not install. So, what can I do to install them?
How could I set up the email antivirus scanner in Evolution?

And the last thing. Is a real time antivirus necessary? (Please note that Ubuntu is installed in a computer that also has Windows, so please, think a bit about the answer... :P )

Thanks in advance

---

### Post by a-user on 2010-10-14
i doubt you will find your answer here. no one uses an antivirus program under linux, except some administrators to scan for windows virus in a network. there is no need for virusscanning on linux.

and if you use a virus scnanner under linux to scan for windows virus you don't need a realtime one.

---

### Post by necromonger on 2010-10-14
I use clamav for my network no need for a real time antivirus.

---

### Post by WorMzy on 2010-10-14
> **vagaerg said:**
> And the last thing. Is a real time antivirus necessary?

Not at all. Viruses designed for Windows will not work on Linux, and Linux viruses are practically non-existent. You'd have to be a [total fool to fall victim to a Linux virus]("http://www.gnu.org/fun/jokes/evilmalware.html") in the first place anyway. Unless you download a Windows virus, move it to your NTFS partition, reboot into Windows, and then execute it, your Windows installation will be safe.

For the record, I *do* have anti-virus installed on Linux. I use clamav to scan all my firefox downloads, and periodically run a full-system scan. I never use Windows for anything other than playing games, so I never have a chance to run a virus scan on it. Running a scan from Linux gives me peace of mind.

---

### Post by vagaerg on 2010-10-14
OK, thanks to all of you. I think that with Firestarter (firewall) and Avast! with scheduled scan I will have a quite good protection. Thanks to all.

---

### Post by oldos2er on 2010-10-14
You might want to read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by vagaerg on 2011-01-01
Thanks, I've read that

---

### Post by gabriella on 2011-01-01
> **vagaerg said:**
> Thanks to everyone...

And the last thing. Is a real time antivirus necessary? (Please note that Ubuntu is installed in a computer that also has Windows, so please, think a bit about the answer... :P )

Thanks in advance

That doesn't make any sense what you are saying because Windows will be on a separate partition. So just use the anti-virus in Windows. As others have said you dont need one in Linux.

---

