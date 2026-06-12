---
title: "Whats a Solid Backup Tool?"
date: 2011-03-23
forum: General Help
---

### Post by ventrical on 2011-03-23
Hi All,

  I am trying to do an experiment with my Ubuntu Installation of Maveric Meerkat. It is currently running Kernel Linux 2.6.35-28 using the GNOME 2.32.0 desktop. The hardware platform is an older Acer Aspire 3620 with 1.5 GHz processor and 1.5 GB ddr.

  All the programs work , Flash, sound, youtube, scanner VLC, USB camera, cell phone .. etc.. It's just a great system.

  My problem is that I hear everyone talking about backing up the HOME directory and then doing a fresh install - if the system has slowed down or for whatever reason. I would just like to get my hands dirty here on this topic.

 So my two questions are:

What free Canonical sponsored program will do a back up of home directory using Ubuntu? (I know there is Deja-dup but that is for Fedroa - is it not ?)

2. After I do this backup how do I restore my HOME directory with all my files, settings and current updates into the fresh install???

 Thanks in advance.

---

### Post by ventrical on 2011-03-23
ok.. I tried the Deja-dup program and it was useless. It told me I have a backend error .. etc..

I'd like to try remastersys but it keeps poping up that it is  not supported by cannonical..etc..

---

### Post by cottfcfan on 2011-03-23
Backintime has always worked for me.

---

### Post by ventrical on 2011-03-23
> **cottfcfan said:**
> Backintime has always worked for me.


Thanks ... I'll check that out. I finally got sbackup to work ... BRAVO!!

:)

---

### Post by CoolJohnB on 2011-03-23
> **ventrical said:**
> Thanks ... I'll check that out. I finally got sbackup to work ... BRAVO!!

:)


I use Luckybackup and find that works really well and it's easy to use.

---

### Post by LemursDontExist on 2011-03-23
> **ventrical said:**
> Hi All,

  I am trying to do an experiment with my Ubuntu Installation of Maveric Meerkat. It is currently running Kernel Linux 2.6.35-28 using the GNOME 2.32.0 desktop. The hardware platform is an older Acer Aspire 3620 with 1.5 GHz processor and 1.5 GB ddr.

  All the programs work , Flash, sound, youtube, scanner VLC, USB camera, cell phone .. etc.. It's just a great system.

  My problem is that I hear everyone talking about backing up the HOME directory and then doing a fresh install - if the system has slowed down or for whatever reason. I would just like to get my hands dirty here on this topic.

 So my two questions are:

What free Canonical sponsored program will do a back up of home directory using Ubuntu? (I know there is Deja-dup but that is for Fedroa - is it not ?)

2. After I do this backup how do I restore my HOME directory with all my files, settings and current updates into the fresh install???

 Thanks in advance.

I would use rsync and schedule a cron job to back up regularly.  Rsync if fast, utterly reliable, and easy to use if you're at all comfortable with the command line (I think there might be some gui versions of rsync out there if you prefer).

As far as restoring things goes, if you get everything in the home directory, then putting those files back in place, and then logging out and back in is all it takes!  (actually, you probably don't even have to log out and back in for most purposes, but some settings are loaded on login).

That said, what most people do is to have a separate /home partition so that they can format their / partition and reinstall without having to ever erase /home.  So!  It's probably a little late for that now, but, if you do reinstall, I would strongly encourage you to do that - it makes your life a lot easier!

---

### Post by ventrical on 2011-03-23
> **LemursDontExist said:**
> I would use rsync and schedule a cron job to back up regularly.  Rsync if fast, utterly reliable, and easy to use if you're at all comfortable with the command line (I think there might be some gui versions of rsync out there if you prefer).

As far as restoring things goes, if you get everything in the home directory, then putting those files back in place, and then logging out and back in is all it takes!  (actually, you probably don't even have to log out and back in for most purposes, but some settings are loaded on login).

That said, what most people do is to have a separate /home partition so that they can format their / partition and reinstall without having to ever erase /home.  So!  It's probably a little late for that now, but, if you do reinstall, I would strongly encourage you to do that - it makes your life a lot easier!

I have been reading this one about making a *home* partition during install and I more or less  just  ripped all my installs. So , yes .. it's too late. The sbackup backed up O K but it foobarred when I tired to restore some files and test it.

I'd like to try remastersys but  too many warnings from UbuntuOne .. etc...

  Ok .. I'll give the rsync a try. I'm trying to see if I can find a relaible backup program and then try to build that into a sort of -system-restore concept- for Ubuntu. I guess some are saying that I am lucky so far about not having a major crash with 10.04 or maveric but I have been reading enough posts and my old Linux books and yup, I hate to admit it but there is a real problem with upstream updates and wirless drivers . etc... I haven't has an incident with 10.04 or 10.10 as of yet but I did with (natty).

thanks again .. I'll give it a try (rsync) and get back.

 Thanks all of you for being so helpful!
Best Regards,

Ventrical

---

### Post by ventrical on 2011-03-23
I'll have to try again in the morning... I'm pooped.

---

