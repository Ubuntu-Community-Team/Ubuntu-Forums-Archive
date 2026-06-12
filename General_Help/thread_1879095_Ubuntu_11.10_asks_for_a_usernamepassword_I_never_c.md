---
title: "Ubuntu 11.10 asks for a username/password I never created"
date: 2011-11-10
forum: General Help
---

### Post by Up4Daze on 2011-11-10
I am running Ubuntu on a flash drive, and it has been working fine until just now, it asked me for a username and password.

I restarted and hit escape to read the text that came up when it was starting, and it said like "account already has the name 'ubuntu' or something. So I put in ubuntu for the account and nothing as the password and hit enter.

The screen went back to the text screen, then returned to the username/password screen.

It occurred after doing an update, I don't know if that affected it or something but yeah. Any suggestions?

---

### Post by LowSky on 2011-11-11
Welcome to the forums.

You can't update a Live version of Ubuntu without issues popping up.

Do a real install to the USB drive if you wish to use it in that capacity.

You should really use a normal hard drive if you can, if you wish to use it beyond a portable OS. A normal install needs about 8-10 GB with the user installing anything else.

---

### Post by Up4Daze on 2011-11-11
I'll do that. Thanks, i appreciate the info.

---

### Post by grahammechanical on 2011-11-11
I recently created a Live USB with persistence of Edubuntu and that situation is normal.

Remember, it is a live boot from a removable disk drive. There has to be a user. And the user is Ubuntu. It happens with a boot from a live CD only we do not notice that we are logged in as user Ubuntu with administrator privileges. But without that we could not use the Live CD/USB to install Ubuntu to a hard disk or use it as a rescue disk.

This happens when you create another user for the OS on a Live USB with persistence. You can log in to that user and when you log out you need to login as Ubuntu in order to shut down correctly.

If you go the System Settings>User Accounts you might find Ubuntu as one of the users.

Regards.

---

