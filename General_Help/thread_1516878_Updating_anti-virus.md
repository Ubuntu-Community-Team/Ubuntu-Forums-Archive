---
title: "Updating anti-virus"
date: 2010-06-24
forum: General Help
---

### Post by bigseb on 2010-06-24
How do I update my antivirus? If I open it and look under help it allows me to _check_ for updates but gives no button or anything to actually install the updates. How do I do this?

---

### Post by warfacegod on 2010-06-24
You'll likely need to open your AV as root. Hit Alt+F2. Enter gksudo nameof-avapp

---

### Post by WorMzy on 2010-06-24
What are you using?

If clamAV, run 'sudo freshclam'. You can configure it to automatically update (which I think it does by default, 24 times a day) by running 'sudo dpkg-reconfigure clamav'

---

### Post by bigseb on 2010-06-24
> **WorMzy said:**
> What are you using?

If clamAV, run 'sudo freshclam'. You can configure it to automatically update (which I think it does by default, 24 times a day) by running 'sudo dpkg-reconfigure clamav'
sudo freshclam gives me this:

 ClamAV update process started at Thu Jun 24 18:25:38 2010
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.95.3 Recommended version: 0.96.1
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cvd is up to date (version: 52, sigs: 704727, f-level: 44, builder: sven)
WARNING: getpatch: Can't download daily-11109.cdiff from database.clamav.net
WARNING: getpatch: Can't download daily-11109.cdiff from database.clamav.net
WARNING: getpatch: Can't download daily-11109.cdiff from database.clamav.net
WARNING: getpatch: Can't download daily-11109.cdiff from database.clamav.net
WARNING: getpatch: Can't download daily-11109.cdiff from database.clamav.net
WARNING: Incremental update failed, trying to download daily.cvd
WARNING: Can't download daily.cvd from database.clamav.net
Trying again in 5 secs...

This loops over and over... Should I uninstall and install from scratch? And on that note (kinda off-topic) how does one uninstall programs? There are a couple of other program I want to get rid of.

---

### Post by WorMzy on 2010-06-24
You can remove programs by running 'sudo apt-get remove <program name>', you can remove programs **and** their config files by running 'sudo apt-get remove --purge <program name>'. Or you can use the Synaptic Package Manager (System -> Administration -> Synaptic Package Manager) to install/remove programs.

I don't get that message when running Freshclam, but I'm using Clamav 0.96.1-1. I don't know if it's available in the normal repos yet, but you can probably install it if you enable the backports repo in Software Sources (System -> Administration -> Software Sources).

I don't know what to make of the getpatch error. You're not behind a firewall are you?

---

### Post by warfacegod on 2010-06-24
> you can remove programs and their config files by running 'sudo apt-get remove --purge <program name>'

Using just "purge" would be sufficient. "remove", in this case, is redundant.

---

### Post by bigseb on 2010-06-24
> **WorMzy said:**
>  You're not behind a firewall are you?
No. 

Not too sure about the program name either. I *assume* it's ClamAV but in Applications ---> Accessories it's listed just as 'Virus Scanner'... I'd get rid of it and reinstall. That styill seems like the best option imo.

---

### Post by warfacegod on 2010-06-24
```
sudo apt-get purge clamav
```

Will get rid of it. The name listed in the Menu often has little to do with what the package is called and the package is what you need to deal with.

---

### Post by bigseb on 2010-06-24
> **WorMzy said:**
> Or you can use the Synaptic Package Manager (System -> Administration -> Synaptic Package Manager) to install/remove programs.
Tried to upgrade through Synaptic... wouldn't do it!! Removed it completely. Reinstalling now.

---

### Post by bigseb on 2010-06-24
Reinstalled the Virus scanner and it's _***still***_ out of date, with no option update!! I mean... wth!?

See here:
[ATTACH]161439[/ATTACH]

---

### Post by warfacegod on 2010-06-24
Which brings us back to my first post.

Hit Alt+F2> gksudo clamav or gksudo clamtk. I can't remember which.

---

### Post by bigseb on 2010-06-24
> **warfacegod said:**
> Which brings us back to my first post.

Hit Alt+F2> gksudo clamav or gksudo clamtk. I can't remember which.
  gksudo clamav gives me this message:

     (gksudo:3393): Gtk-WARNING**: cannot open display

gksudo clamtk gives me this message:

     (gksudo:3416): Gtk-WARNING**: cannot open display

---

### Post by warfacegod on 2010-06-24
Try it in a Terminal.

Alternatively you can read the "Help" that comes with clamav.

---

### Post by mr clark25 on 2010-06-24
my server has the same "update problem". on my server, it is the latest version, but i still get a update warning when running "clamscan"

this is a known bug. i just dont know where i found the bug report. i think it was on clamav's wiki.\

somewhere on thier wikipedia page, they have a command that will report the version that you have installed. ill see if i can find it....

---

### Post by mr clark25 on 2010-06-24
i found it! this should help:
> 
**I upgraded to the latest stable version but I still get the message *Your [ClamAV]("http://wiki.clamav.net/bin/view/Main/ClamAV") installation is OUTDATED*, why? **

  Make sure there is really only one version of [ClamAV]("http://wiki.clamav.net/bin/view/Main/ClamAV") installed on your system: 
=$ whereis freshclam 
  $ whereis clamscan=
 Also make sure that you haven't got old libraries (libclamav.so*) lying around your filesystem. You can verify it using: 
$ ldd `which freshclam`  As of 2007-02-19, I get this message on my Windows box. The latest version at [http://clamwin.com/](http://clamwin.com/) is still version 0.88.7 -- when I do "Tools | download database update", I get the message 
    WARNING: Your ClamAV installation is OUTDATED!
    WARNING: Local version: 0.88.7 Recommended version: 0.90
    DON'T PANIC! Read [http://www.clamav.net/faq.html](http://www.clamav.net/faq.html)
 but "Help | check latest version" gives me a seemingly-contradictory message 
    You have the latest version of ClamWin Free Antivirus (0.88.7).
 (This was caused by [ClamAV]("http://wiki.clamav.net/bin/view/Main/ClamAV") and its CVD files having been updated from 0.88.7 to 0.90 while [ClamWin]("http://wiki.clamav.net/bin/view/Main/ClamWin") had not.) 


i found this at [http://wiki.clamav.net/Main/FAQ](http://wiki.clamav.net/Main/FAQ)

---

### Post by bigseb on 2010-06-28
Sorry guys but none of that actually helped me. Why is it when I uninstall ClamAV then reinstall it t is still out of date?

---

### Post by mr clark25 on 2010-06-28
could you post the output of:
```

whereis freshclam

```
and
```

  whereis clamscan=

```

one of these (i cant remember which) will report you current version.

---

### Post by bigseb on 2010-06-29
user@user-laptop:~$ whereis freshclam
freshclam: /usr/bin/freshclam /usr/share/man/man1/freshclam.1.gz
user@user-laptop:~$

user@user-laptop:~$ whereis clamscan=
clamscan=:
user@user-laptop:~$

---

### Post by mr clark25 on 2010-06-29
sorry, i should have run those on my computer first to make sure they worked.

i found the one that works (tested it on my computer this time):
```

clamscan --version

```

sorry if i confused you in my earlier posts.

---

### Post by bigseb on 2010-07-09
> **mr clark25 said:**
> sorry, i should have run those on my computer first to make sure they worked.

i found the one that works (tested it on my computer this time):
```

clamscan --version

```sorry if i confused you in my earlier posts.


ClamAV 0.95.3/11273/Mon Jun 28 17:06:55 2010

---

### Post by Braik on 2010-07-09
Just a little bit curious.... Why do you have an antivirus?

---

### Post by bigseb on 2010-07-09
To scan Windows stuff...

---

### Post by WorMzy on 2010-07-09
That's the reason I have it. I download all my downloads to an ntfs partion which is shared with Windows, so I have an automatic scan set up to process every downloaded file. If a virus is found, the infected file is moved to a folder on one of my ext4 partitions, so that Windows cannot access it.

Bigseb: If you've already got the latest version in the repositories, and it's complaining that it's out of date, then you just need to wait for Canonical to approve a more recent version and move it to the update repository. If you don't want to wait, then there's a pretty high chance that the updated version is already in the "proposed" or "backports" repositories. Navigate to System -> Administration -> Software Sources, and enable the proposed and backport repositories. Close, and reload package information if prompted. Then open Synaptic (System -> Administration -> Synaptic Package Manager), search for Clamav, and see if there's an update for it now.

If you still have no luck, then you can always compile the latest version from source and install that way. Download the source here: [http://www.clamav.net/lang/en/download/sources/](http://www.clamav.net/lang/en/download/sources/)

---

### Post by bigseb on 2010-07-09
> **WorMzy said:**
> Bigseb: If you've already got the latest version in the repositories, and it's complaining that it's out of date, then you just need to wait for Canonical to approve a more recent version and move it to the update repository. If you don't want to wait, then there's a pretty high chance that the updated version is already in the "proposed" or "backports" repositories. Navigate to System -> Administration -> Software Sources, and enable the proposed and backport repositories. Close, and reload package information if prompted. Then open Synaptic (System -> Administration -> Synaptic Package Manager), search for Clamav, and see if there's an update for it now.
Checked that, nothing. Just for interests sake I have uploaded a screenshot

[ATTACH]162908[/ATTACH]

The left window is the Virus Scanner UI, the right window shows whether or not updates are available. Neither has an option to actually update though

> **WorMzy said:**
> If you still have no luck, then you can always compile the latest version from source and install that way. Download the source here: [http://www.clamav.net/lang/en/download/sources/](http://www.clamav.net/lang/en/download/sources/)

This is beyond me unfortunately :(

---

### Post by WorMzy on 2010-07-09
I've never used clamtk (the GUI) myself, but try running it under gksu (gksu clamtk), if that fails to present an option to update, then I'd re-suggest my earlier advice to use Synaptic.

You could also try adding the Lucid mirrors to your software sources, and getting the update that way. As [this link]("http://packages.ubuntu.com/search?keywords=clamav") suggests, Lucid has 0.96.1 available in the main repository.

---

### Post by ov3rcl0ck on 2010-07-09
You probably needed to upgrade the client to get the new definitions using freshclam. You probably just needed to run
```

sudo apt-get update
sudo apt-get dist-upgrade

```
To get the new client, or possibly ubuntu failed to put an up to date version in its repos. It's happened before. The up to date version will probably be in the backport repos.

However I don't see why you need an antivirus, there hasn't been a virus in the wild in about 3 years for linux, and only one major exploit that was patched about a week later. And if you did get a virus you'd need to "chmod +x" to allow it to execute then run it as root...

However if you need and antivirus, just use the "clamscan" command.
To scan and remove all maleware do this
```

clamscan -r --remove DIR

```
DIR would obviously be where you'd place the path to the directory you wanted to scan, if you wanted to scan your windows partition and it was mounted at /mnt/windows it would be like this
```

clamscan -r --remove /mnt/windows

```

---

### Post by DAB4970 on 2010-11-15
running 'sudo freshclam' gives me updates definitions, but doesn't update GUI or AVEngine.   is there something to run in terminal for this?

---

### Post by DAB4970 on 2010-11-28
I added this

deb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) maverick main

to the sources list and updated av engine is installed.  Thanks to all here.

---

