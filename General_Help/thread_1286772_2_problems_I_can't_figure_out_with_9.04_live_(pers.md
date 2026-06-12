---
title: "2 problems I can't figure out with 9.04 live (persistant)"
date: 2009-10-09
forum: General Help
---

### Post by Crumbles on 2009-10-09
I have installed 9.04 onto a portable seagate freeagent as a live (persistant) install.  This way I can take my ubuntu desktop with me anywhere!

However, I have run into two problems that I cannot figure out for the life of me.  Any help is greatly appreciated.

The first problem is for some reason my time is NEVER correct.  It's always off by -4 hours.  The minutes are correct, just  not the hour which leaves me to think this is some sort of weird Time Zone issue.  I'm in EST time zone.  I have run

sudo dpkg-reconfigure tzdata

and made sure it is correct, and it is.  My original work around was to change it to some really weird time zone to get the time right, however, this totally jacks up my email dates when I send and receive.  The time IS correct in the BIOS.  Windows sees the time correctly on the laptop, as well as ubuntu (have a dual boot system)  -- it's ONLY the portable live version that has the time wrong.  Any ideas?

My second issue is...

How in the WORLD do I change the password so the system will no longer log in as root by default?  I've tried changing the password with passwd and going to ABOUT ME=>CHANGE PASSWORD -- however, each reboot chnages the password back to blank!!  How can I fix this?

Thanks in advance for any help.

---

### Post by Crumbles on 2009-10-10
Friends?

---

### Post by Crumbles on 2009-10-11
I love you?

---

### Post by Ocxic on 2009-10-11
your problem comes from the time set in the BIOS. Ubuntu applies the 4hr offset from BIOS set time, as it expects the BIOS to be set to GMT. set you time zone to GMT or 0hr offset and the time will be correct from now on.

your installed Ubuntu has the correct time because during installation it will ask if your BIOS time is local or GMT and make the necessary changes so you don't get this conflict. 

TIP: Windows reset the BIOS/hardware time, so if you set your BIOS to GMT, windows will re-set it to local time whenever it boots.

the root thing is normal, you want to use sudo to run a command or sudo -i to get a root prompt. having root enabled is a security risk
try creating another user on the system for you to use, and remove the automatic login form the login screen options, in the admin menu..

---

### Post by vttay03 on 2009-10-11
Problem #1: Open a shell and type 

```

sudo gedit /etc/default/rcS

```

Change

```

UTC=yes

```

to

```

UTC=no

```

This is what is causing the four hour difference.  Linux defaults to UTC time whereas Windows doesn't.  

Problem #2: Can't recall off the top of my head how to do this, I think when I was using a live persistent disk I ended up creating a separate user account under System-->Administration-->Users and Groups.  That way when you click 'Try Ubuntu without any changes to your computer' (or whatever that option is), you can login as yourself.

---

### Post by Crumbles on 2009-10-12
> **vttay03 said:**
> Problem #1: Open a shell and type 

```

sudo gedit /etc/default/rcS

```Change

```

UTC=yes

```to

```

UTC=no

```
Thanks so much! It appears that this has fixed the time issue!

> **Ocxic said:**
> 
try creating another user on the system for you to use, and remove the automatic login form the login screen options, in the admin menu..How do I give the new user that I create my desktop so I don't have to set up all the icons again?  Is there a profile copy like in Windows?

---

