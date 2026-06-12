---
title: "Administrator mode does not work"
date: 2006-02-20
forum: General Help
---

### Post by garton on 2006-02-20
"Administrator Mode" button in "System Settings" does not work properly.

I've got a newly installed Kubuntu Breeze, and if I hit K->System Settings->Disk&Filesystems (for example), I get an "Administrator Mode" button beneath the disk & filesystems config. If I hit it and enter my password, *nothing happens.*

I don't get administrator rights, it just thrown me right back there with all the text greyed out.

I've searched the forums, and it seems that I'm not the only one with this problem, but I have not found a solution.

I also tried this; start kcontrol from a console and this is what is printed when I enter my password in the dialog box:

---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /root/.DCOPserver_lovin__0
and start dcopserver again.
---------------------------------

WARNING: Waiting for already running klauncher to exit.
WARNING: Waiting for already running klauncher to exit.
WARNING: Another instance of klauncher is already running!
kdeinit: Communication error with launcher. Exiting!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kcmshell (kdelibs): WARNING: Could not find module 'System/mountconfig'.

Does anyone have any idea how this can be fixed? Thanks!

---

### Post by bscbrit on 2006-02-20
I don't know what the cure is (I'm Gnome) but this is the third mention of this problem in the last 3 days.  Has there been a recent update that might have a bug in it?

---

### Post by aysiu on 2006-02-20
Try pressing Alt-F2 and typing ```
kdesu kcontrol
```

---

### Post by GoldBuggie on 2006-02-20
what aysiu mentioned is the workaround to the bug that is present in kubuntu with kde 3.4. I would recommend upgrading to kde 3.5.1, I have not seen anyone mention having problems with it there.

---

### Post by Robgould on 2006-02-20
Administrator mode in kubuntu was broken when I tried it.  It is well documented in the kubuntu forums.
 
[http://www.kubuntuforums.net/]("http://www.kubuntuforums.net/")
 
I don't know if it is fixed in the new version or not.
 
There are several workarounds available.

---

### Post by Jucato on 2006-02-20
I think it was fixed in 3.5.1 (or even 3.5). This was a bug I also encountered before KDE 3.5 was released in Breezy. Never had it again after upgrading.

---

### Post by miesnerd on 2007-10-29
so is there no fix in gnome?
I dont see/know where a Administrator Mode button in GNOME even would be...

---

### Post by garton on 2007-10-29
> **miesnerd said:**
> so is there no fix in gnome?
I dont see/know where a Administrator Mode button in GNOME even would be...

You pull up a thread that's almost *two years old* to ask for a fix in Gnome when the entire bug is KDE and in no way applies to Gnome?

---

### Post by sammael666 on 2007-11-02
> **garton said:**
> You pull up a thread that's almost *two years old* to ask for a fix in Gnome when the entire bug is KDE and in no way applies to Gnome?
well i pull it too as i have this same issue in fresh install of Kubuntu 7.10. any workarounds apart from  "This was a bug I also encountered before KDE 3.5 was released in Breezy. Never had it again after upgrading." ?
i am using kde 3.5.8

---

### Post by sleet01 on 2007-11-25
I ran into the same problem and despite the power of Google was unable to find a solution, until I noticed that most of the reported issues included some sort of DCOP server error.  I decided to just take a stab in the dark and shutdown, then restarted, the DCOP server.  This cleared the problem right up where things like changing the sudo password, restarting X, and even restarting the entire machine had not helped.

There isn't a '--restart' option for dcopserver, so here is what I did:

```
sudo bash
/usr/bin/dcopserver_shutdown
/usr/bin/dcopserver
exit
```

Next I ran systemsetup from the console to see if any errors were logged, but didn't see anything from systemsetup.  There was a line about dcopserver cleaning up dead connections, however, which I thought was significant.  At any rate, this fixed my problem.

---

### Post by apanloco on 2007-12-05
I have the same problem (Administrator mode button does not work). The DCOP-server-restarting did NOT do the trick for me. Please help! This is a fresh install of Kubuntu 7.10.

/A

---

### Post by likes2skate on 2007-12-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/kde-systemsettings/+bug/176518](https://bugs.launchpad.net/ubuntu/+source/kde-systemsettings/+bug/176518) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I just installed Gutsy on two different systems, and I cannot get into Administrator Mode in System Settings on either install.

I will continue using one (at my residence), but at my workshop, I am back to 6.10.

I reported a bug:

[https://bugs.launchpad.net/ubuntu/+source/kde-systemsettings/+bug/176518](https://bugs.launchpad.net/ubuntu/+source/kde-systemsettings/+bug/176518)

---

### Post by oneloveamaru on 2008-04-04
The dcop fix worked for me. Kubuntu 7.10 here.

My problem was, I would hit Administrator Mode, it would act like it's going to do it, then falls right back to non-admin mode with the button being clickable still. Fixed me up, I'm happy!

---

### Post by Cato2 on 2008-05-17
I had this as well after upgrading Feisty to Gutsy.  The workaround I found was to create a new KDE menu entry for kcontrol that uses ```
gksudo kcontrol
```
This somehow resets DCOP server setup without restarting it (try running it from Konsole to see what it does.)

[https://bugs.launchpad.net/ubuntu/+source/kdesudo/+bug/175909](https://bugs.launchpad.net/ubuntu/+source/kdesudo/+bug/175909) has more discussion of this bug.

The script to restart DCOP server may be a better workaround as it could be put in the KDE Autostart directory giving a more invisible 'fix'.

---

