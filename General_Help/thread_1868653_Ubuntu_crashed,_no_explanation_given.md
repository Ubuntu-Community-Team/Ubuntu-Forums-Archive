---
title: "Ubuntu crashed, no explanation given"
date: 2011-10-24
forum: General Help
---

### Post by tudor117 on 2011-10-24
Hi,
I was casually working (had Office 2007 in wine, skyping using cam, and browsing internet with chrome) and all of a sudden the screen starts to pixelate, skype repeats the same sounds over and over and then the computer crashes and reboots.

I looked through all the logs in */var/log/*, but I couldn't find any messages from around the time of the crash. Where else could I look?

Some things to note:[LIST]
[*]I had two cameras plugged in, one of which I've never used before but was testing. It seemed to work great. It was a Logitech c525.
[*] The call was about 14 minutes long.
[*]I'm using the binary Nvidia driver 285.05.09 with a e-GeForce 7900 GT.
[*]64-bit machine
[*]10.10 Maverick
[/LIST]
I've never had this happen before (except some other OS)...
I also have no idea what happened or what could have caused this.
Any ideas will be appreciated.

---

### Post by tudor117 on 2011-10-24
bump?

---

### Post by haqking on 2011-10-24
the computer crashed using 3 non linux applications ? I wonder why ;-)

Unless it is a repeating occurence there is no suggestion.

I dont think a Wine/Wine App causing a crash is really indicitative of a Linux issue im afraid.

See how often it happens

and best to only bump every 24 hours or so

---

### Post by tudor117 on 2011-10-24
It's never happened before though and I'm curious if it's the cam.

And there was only one non-Linux app (Office).
Chrome and Skype have their own native versions.

Thanks anyways.

---

### Post by haqking on 2011-10-24
> **tudor117 said:**
> It's never happened before though and I'm curious if it's the cam.

And there was only one non-Linux app (Office).
Chrome and Skype have their own native versions.

Thanks anyways.

ahh i see, i read it as all 3 apps were running in wine.

The fact is you say it never happened before.  A one off crash is not uncommon and could mean something or nothing.

If it is a repeat issue then yes, but to troubleshoot one crash which hasnt happened before is difficult.

Is it causing issues now ? is something not working ? does it keep crashing etc ?

---

### Post by tudor117 on 2011-10-24
I was only borrowing the cam... after that I returned it...

Interesting thing is that when I first plugged the cam in and tried to run lsusb, nothing would happen. It was as if lsusb froze. It took multiple plugings and repluging to get lsusb to work. 
Then I tried it with cheese and it worked fine. And then with skype.

I expected there to be some kind of a log somewhere about something related to it. But there's *nothing*.
There's messages from when the cam was plugged in and then from when the system rebooted. I have no idea where else to look.

On the other hand, I found out why one of my devices didn't work after suspend, but I have yet to worry about that...

---

### Post by LinuxFan999 on 2011-10-24
> **tudor117 said:**
> Hi,
I was casually working (**had Office 2007 in wine**, skyping using cam, and browsing internet with chrome) and all of a sudden the screen starts to pixelate, skype repeats the same sounds over and over and then the computer crashes and reboots.

I looked through all the logs in */var/log/*, but I couldn't find any messages from around the time of the crash. Where else could I look?

Some things to note:[LIST]
[*]I had two cameras plugged in, one of which I've never used before but was testing. It seemed to work great. It was a Logitech c525.
[*] The call was about 14 minutes long.
[*]I'm using the binary Nvidia driver 285.05.09 with a e-GeForce 7900 GT.
[*]64-bit machine
[*]10.10 Maverick
[/LIST]
I've never had this happen before (except some other OS)...
I also have no idea what happened or what could have caused this.
Any ideas will be appreciated.
Why not just use OpenOffice.org or LibreOffice?

---

### Post by tudor117 on 2011-10-24
I do have LirbeOffice and I use it, but I found that when working with others, and when I need to send them Word files, there are less compatibility issues when using Word, specifically with drawings and charts.

---

