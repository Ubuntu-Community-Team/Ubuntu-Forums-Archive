---
title: "Unlock Keyring window pops up at login with Xubuntu 11.10"
date: 2012-04-07
forum: General Help
---

### Post by Rytron on 2012-04-07
Hi.

Each time I log into Xubuntu 11.10, this Unlock Keyring window pops up [attached image]. How do I rectify this?

Thanks.

---

### Post by jbrice on 2012-04-15
Just had the same problem here with Xubuntu 12.04 when running DejaDup backup. 
The Seahorse data encryption and digital signature app. is not installed by default in Xubuntu. It seems to take care of providing access to passwords for some Ubuntu applications - install it and the nagging requests to unlock the Keyring should go away.

---

### Post by Rytron on 2012-04-15
> **jbrice said:**
> Just had the same problem here with Xubuntu 12.04 when running DejaDup backup. 
The Seahorse data encryption and digital signature app. is not installed by default in Xubuntu. It seems to take care of providing access to passwords for some Ubuntu applications - install it and the nagging requests to unlock the Keyring should go away.

Hi jbrice. I installed seahorse and rebooted but the same window popped up. :confused:

---

### Post by jbrice on 2012-04-17
Yes - it's back again here. :(

---

### Post by Rytron on 2012-04-17
> **jbrice said:**
> Yes - it's back again here. :(

Damn. :mad:

I'm running Xubuntu inside Vbox but am thinking of putting Xubuntu 12.04 on my main PC. I hope the programmers sort out bugs/glitches such as this.

---

### Post by squilookle on 2012-04-17
Running Xubuntu 12.04 here and have not experienced this issue. 

Did this start when you first installed 12.04, or did it appear suddenly after some time? Have you recently (or before the issue appeared) installed anything?

---

### Post by Rytron on 2012-04-17
> **squilookle said:**
> Running Xubuntu 12.04 here and have not experienced this issue.

That is good to hear.

> **squilookle said:**
> 
Did this start when you first installed 12.04, or did it appear suddenly after some time? Have you recently (or before the issue appeared) installed anything?

It is Xubuntu 11.10 in VirtualBox. I cannot remember.

---

### Post by jbrice on 2012-04-20
Hmm, "changed" the password for "Passwords: login" in Seahorse (Settings > Passwords and Keys) but used exactly the same password (my system login password) for both the old and the new passwords. 
And now it seems to working as it should - no nagging about unlocking keyring. Crazy I know, but there it is!

Guess there must be something slightly buggy with the keyring in the Xubuntu environment.

---

### Post by Habitual on 2012-04-20
> **jbrice said:**
> ...Guess there must be something slightly buggy with the keyring in the Xubuntu environment.

Maybe, but do you utilize the auto-login feature (if one exists for Xubuntu)?
If so, disable that and login manually and seahorse will unlock.

---

### Post by Rytron on 2012-04-20
I unchecked a few items in **Applications Autostart**. The problem seems to be gone. I am not sure which item was causing the problem - Ubuntu One or Bluetooth or other?

---

### Post by aljoriz on 2013-02-17
I know this reply is late but I found this to work for me

Goto system>User Groups.  change your account type from custom to administrator.  

No more nagging keyring request.

---

### Post by Rytron on 2013-02-17
> **aljoriz said:**
> I know this reply is late but I found this to work for me

Goto system>User Groups.  change your account type from custom to administrator.  

No more nagging keyring request.

Kudos.

---

