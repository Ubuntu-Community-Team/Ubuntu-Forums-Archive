---
title: "locked out!  auto-login doesnt unlock encrypted home folder."
date: 2011-05-28
forum: General Help
---

### Post by op3studios on 2011-05-28
I installed Natty yesterday, and everything went so well that I loaded it up with my favorite applications, rebooted twice to prove it and then backed up the partition.

this morning, I can't get past the login.
I don't get why this didn't happen at the reboot tests,
but I think it must be that I set the option to auto-login, with an encrypted home folder.  (first time to try the encryption option.)

I'm guessing that by not entering a password manually at the log in screen, the encrypted files are not receiving a proper key.

I'm getting error messages on 'iceauthority', nautilus is unable to create or access the home directory, and Gconf error flags.

restoration of the partition image runs out the same, with the gui screen locking right after clicking on my username at login.

I can launch terminal, but I'm in a lot over my head.


my personal data is not at risk since I keep it on a separate partition, but I downloaded a bunch of apps and would rather not have to do that again since I'm on a small data plan here on my little island.  plus I spent all day getting everything configured and tweaked.


thanks for any suggestions.

Jim

---

### Post by linuxinstalledfromhdd on 2011-05-28
Do you really want an encrypted home folder?  Is that something you absolutely needed?

I would re-install, and this time do not select encrypt home folder. It slows down your system, and I have heard numerous issues and serious complaints from users who have installed it.  Don't do it. Encrypting your home folder isn't really going to do much until you switch to something more like SELinux anyhow.

---

### Post by op3studios on 2011-05-28
yeah, it was the wrong experiment at the wrong time.

drat!  everything was so peachy!

---

### Post by prodigy_ on 2011-05-28
You can disable autologin by editing (or deleting) **/etc/gdm/custom.conf**.

---

### Post by linuxinstalledfromhdd on 2011-05-28
If that doesn't work, here is a nice walk through to reinstall Ubuntu 10.10 (I prefer 10.10 over 11.04)

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

You just can't mess up with that if you read everything first.

---

### Post by op3studios on 2011-05-28
yeah, I've been using Ubuntu Studio on 1010 which is great,
but the 11.04 release seems much faster in general.
I think 11.04 is good on newer machines.


thanks for the tip, now I have something to try

I'm also thinking of creating a new user through terminal and then snagging my config files and installed apps, but I'll try editing the auto-login file first.

---

### Post by birsam on 2011-06-17
> **prodigy_ said:**
> You can disable autologin by editing (or deleting) **/etc/gdm/custom.conf**.

Now /etc/gdm/custom.conf  file reads as:
[daemon]
TimedLoginenable=false
AutomaticLoginEnable=true
TimedLogin=basu
TimedLoginDelay=30
DefalutSession= gnome-falsesafe

I suggest to edit as :
AutomaticLoginEnable=false
TimedLoginEnable=true
other things intact 

Whether it will disable AutoLogin and allow login on giving password for relevant user

---

### Post by eveg on 2011-08-01
> **linuxinstalledfromhdd said:**
> If that doesn't work, here is a nice walk through to reinstall Ubuntu 10.10 (I prefer 10.10 over 11.04)
 
[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)
 
You just can't mess up with that if you read everything first.
 
i don't know what adds for chimneysweeps allegedly have to do with fixing a computer, but this link is several places in these forums, and all it does (visibly) is bring up a lot of popups. what it may do to your system invisibly is another matter. i strongly advise against clicking on it.

---

