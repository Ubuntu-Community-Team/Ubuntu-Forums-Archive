---
title: "&quot;System program problem detected&quot; dialog box on startup"
date: 2012-05-03
forum: General Help
---

### Post by prshah on 2012-05-03
Hello,

On startup of Ubuntu 12.04, I get an error message as shown in the attachment. 

It is simply a dialog with "System program problem detected" as the title, and text "Do you want to report the problem now?". Available buttons are "Cancel" and "Report problem". Clicking "Report problem" asks for elevated priviliges.

Being the suspicious kind of guy that I am, I didn't enter the password since I don't know the source of the dialog box.

apport dialog boxes usually have a details button to show what information is being sent.

I am reasonably certain that it is not a rogue program; all software is from the repos and only GoogleTalk PPAs are installed.

syslog does not yield any clues except this (possibly unrelated) error message:```
 init: Failed to spawn nmbd main process: unable to execute: No such file or directory
```

Searching both Google and UF did not yield any satisfactory results.

Everything works fine after dismissing the dialog box by "Cancel". However, it is irritating to do this everytime. It also seems to pop up more frequently with running Opera (.deb install direct from Opera).

[ATTACH]217167[/ATTACH]

Any suggestions?

Background: Ubuntu 12.04 64 bit, s10-3t laptop, tech level: intermediate-high

---

### Post by Peter09 on 2012-05-03
During the Beta phase this box often pops up as the error reporting is set to 'very sensitive', however now that it is released this is not the case. Have you installed a beta version of 12.04 - if so upgrading may fix the problem.

---

### Post by prshah on 2012-05-03
> **Peter09 said:**
> Have you installed a beta version of 12.04 - if so upgrading may fix the problem.

Hello,

Thank you for your reply. However, I am running a fully updated 12.04 install, not a beta```

Thu May 03 @14:40:21:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise
Thu May 03 @14:40:27:~$ 
```

Though I must mention that I upgraded from 10.10->11.04->11.10->12.04 in a single sitting (over the weekend after release of 12.04).

Any idea where I can check/change the "error sensitivity" settings?

In your opinion, should I go ahead with filing a report?

---

### Post by Peter09 on 2012-05-03
I should go ahead and report the problem, note that during the reporting process you may get some information on what the problem is.

---

### Post by markiangooley on 2012-05-18
> **prshah said:**
> 
Though I must mention that I upgraded from 10.10->11.04->11.10->12.04 in a single sitting (over the weekend after release of 12.04).

Any idea where I can check/change the "error sensitivity" settings?

In your opinion, should I go ahead with filing a report?

Something similar after upgrading from 11.04 to 11.10 and then almost immediately to 12.04 (a few hours later)...

---

### Post by bogan on 2012-05-19
Hi!,** prshah**,

Try running:```
 sudo dpkg-reconfigure -a
```The man file warns it may take a long time, and there is no feed back in the terminal that anything is happening, unless it finds errors. Just wait it out.

The first time I ran it, it took about 20 minutes.  Before, for the first 6 days, I was getting 'System Problem' and 'XXXX Stopped Unexpectedly' messages in large numbers. Afterwards, they reduced to perhaps one a day.

Only one of the many score of "crashes" required a complete reboot, the others all resumed without any apparent problem.

Chao!, **bogan**.

---

### Post by Ashrael on 2012-05-25
I have the same thing since a day or three....Also suspicious and declined to give out password, so far. I also did a clean install, so no beta. One thing that keeps crashing (maybe related or not) is "Weather Indicator 11.11.28 'Cloudy 9'" Is there going to be an update to fix this, soon? 

Using kernel version: 3.2.0-24-generic-pae, it got updated a few days ago, could this be the source?

Can anyone point me to where to find the cause?


TIA!

---

### Post by bogan on 2012-05-25
Hi!, **prshah**,

Since my Post #6, I have done a complete install of 12.04-24LTS into another partition, and it produces just as many error messages as the updated version did.

However, at least it does not produce a "could not write bytes: Broken pipe" message at every boot and log-in or -out.

Most of the messages I get now are of the "Sorry 12.04 has encountered  a problem" or "XXXXX has stopped unexpectedly", and mainly from 'Nautilus' or 'lightdm'.

Judging from other threads reporting similar messages, this is something that has to be bourne: but keep  sending the error reports: hopefully, the more they get, the more likely something will be done.

Chao!, **bogan**.

---

### Post by Ashrael on 2012-05-27
Strangely enough I haven't seen it since my last post....weird...

---

### Post by Ashrael on 2012-06-05
and since 2 days it is back again.... gonna ignore it from now on, system runs fine anyway....:popcorn: just move it to another desk... it's anoying tho...

---

### Post by CDR Services on 2012-12-16
On my systems this seems to be happening since the switch to Unity and seems to happen on any machine i have tried with Nvidia graphics! I am assuming it has something to do with the graphics driver but it would be nice to track it down! I like the Unity interface, It took some getting used to but in my opinion it is far better than Gnome 3!

---

### Post by tjwilli on 2013-01-19
I just started getting this today (19-Jan-2013) after an update. I'm also leery about supplying my admin password.  This last update also included a kernel update. Could that have something to do with it?

---

### Post by OliverHaslam on 2013-03-27
I appear to be getting the same issue. I thought it was SAMBA related, but apparently not. That said, when trying to compile the error report the app complained that it related to an uninstalled app (smbd).

---

### Post by achim_59 on 2013-06-05
Aaaah Haaa! 

I can report the problem without worrying about malware... good to know. Sooner or later the report will end up with some one who can fix it I guess. 

None-the-less, for those of you with influence in such matters please note: adding a little "details" button to the pop-up error would calm the fears we suspicious types have about giving out passwords. The way things are, it is not at all clear why that is necessary.

Ciao

Achim ;)

---

### Post by Charlotte18 on 2013-06-05
This thread appears to have been started more than a year ago, but . . .

When the "System problem detected" kept showing up for me upon every reboot and login, I put this into the rc.local file and the message stopped:

rm /var/crash/*

---

