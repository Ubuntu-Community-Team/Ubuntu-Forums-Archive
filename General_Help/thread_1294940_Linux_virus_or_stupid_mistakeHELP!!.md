---
title: "Linux virus or stupid mistake?HELP!!"
date: 2009-10-18
forum: General Help
---

### Post by tuff3rthanu on 2009-10-18
Hello I recently wanted to see how openerp would work on my linux machine and couldn't get it to work. I read some forums and it told me to do some steps with python. I was working in the terminal during all of this but just simply copy and paste. After that i went into package manager and wanted to reinstall python again and package manager started uninstalling all kinds of things that I didn't want it to. I think it was a virus or something. In any case I can boot into 9.4 thru grub then it goes and says
"boot from (hd0,0) ext3 ......
starting up...
loading please wait...
19+0 records in
19+0 records out
kinit:name_to_dev_t (/dev/disk/by-uuid/4fdd17c40-a613bb8aaee2b)= dev )8,5)
kinit:trying to resume from /dev/disk/byuuid/4fdd17c-a613-4e65-bcbf-7a6bb8aaee2b
kinit:no resume image, doing normal boot...
ubuntu 9.04 (computer name)
login:


I can login, so from here should I seek a install disk or is there a simple command after?

---

### Post by ApEkV2 on 2009-10-18
try startx (if your stuck in a cli)

---

### Post by tuff3rthanu on 2009-10-18
that brought me to a command prompt and i cannot type in it at all!

---

### Post by igknighted on 2009-10-18
Python is a requirement of much of the Ubuntu desktop, so if you removed python it would have removed most of your apps too in a chain-reaction sort of way.  Then when you only installed python again, it wont automatically restore the other apps.

If you have internet, log in and install the package ubuntu-desktop (sudo apt-get install ubuntu-desktop), assuming you were using regular ubuntu with gnome.  This should restore the default apps, but no promises on your settings or other apps you had installed/removed.

---

### Post by tuff3rthanu on 2009-10-18
I think i need to reinstall gnome and basically the entire package of programs the kernel runs on, this thing uninstalled EVERYTHING it sucks...

---

### Post by igknighted on 2009-10-18
> **tuff3rthanu said:**
> I think i need to reinstall gnome and basically the entire package of programs the kernel runs on, this thing uninstalled EVERYTHING it sucks...

It should always tell you what is being removed/installed before doing an install... did you read the list of what was being installed/removed before you said ok?

---

### Post by tuff3rthanu on 2009-10-18
i told it to reinstall python and then it went and uninstalled every package

---

### Post by tuff3rthanu on 2009-10-18
the apt-get command you told me to use  didn't work it said failed must not have the NIC working?

---

### Post by tuff3rthanu on 2009-10-18
I suppose if its screwed up to the point of reinstall then i may as well wait for the new distro....i have a toshiba netbook running windows xp....i can live for a few days

---

### Post by igknighted on 2009-10-18
> **tuff3rthanu said:**
> i told it to reinstall python and then it went and uninstalled every package

Ah, a problem with the GUI interface... there is no "reinstall" feature in apt, which is what the GUI calls.  Therefor it must uninstall, then install again.  Please file a bug on this, as it shouldn't happen that way.  In the future, if you are messing with major system libraries, use apt from the CLI instead.  That way you can be more sure.

---

### Post by tuff3rthanu on 2009-10-18
> **igknighted said:**
>   Please file a bug on this, as it shouldn't happen that way.   That way you can be more sure.

can you give me a link to report the problem?

---

### Post by igknighted on 2009-10-18
> **tuff3rthanu said:**
> I suppose if its screwed up to the point of reinstall then i may as well wait for the new distro....i have a toshiba netbook running windows xp....i can live for a few days

If you install the beta of 9.10 and install the upgrades along the way, you will be running 9.10 final sometime around 3 or 4 days before final release.  No reason to wait if you have to reinstall anyways.

If you want to fix your current system, you could use the CD to rescue the system (log in and get online via the CD and then reinstall the packages).  Or, you could use the CD as an apt repo (search the forum for what too add, it should have all the packages on there you would need without going online at all).

---

### Post by igknighted on 2009-10-18
> **tuff3rthanu said:**
> can you give me a link to report the problem?

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

The "filing bugs at launchpad.net" section would be most relevant, but there could be other useful info on the page for you.

---

