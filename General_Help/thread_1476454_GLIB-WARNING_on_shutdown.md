---
title: "GLIB-WARNING on shutdown"
date: 2010-05-07
forum: General Help
---

### Post by blagosphere on 2010-05-07
I recently updated to 10.04 and have been quite impressed; however, I have seen an unsettling warning during shutdown. After the shutdown button is pressed terminal text flashes. The top line states: "GLIB-WARNING **: getpwuid_r(): failed due to unknown user id (0)" below that the text seems normal with processes receiving the TERM signal. After .25 to 1.5 seconds the text disappears and shutdown resumes with the normal splash screen and ends with a shutdown computer about a second later. Is this typical or should i be looking for a fix?

EDIT: I have recently noticed that just before the login screen there is also this warning.

---

### Post by Bluebris on 2010-05-18
> **blagosphere said:**
> I recently updated to 10.04 and have been quite impressed; however, I have seen an unsettling warning during shutdown. After the shutdown button is pressed terminal text flashes. The top line states: "GLIB-WARNING **: getpwuid_r(): failed due to unknown user id (0)" below that the text seems normal with processes receiving the TERM signal. After .25 to 1.5 seconds the text disappears and shutdown resumes with the normal splash screen and ends with a shutdown computer about a second later. Is this typical or should i be looking for a fix?

EDIT: I have recently noticed that just before the login screen there is also this warning.


I have the same message when i try to install any of the *buntu family 10.04 version.  I've tried Ubuntu, Lubuntu, Peppermint, even the Mint 9 RC.  9.10 is fine on all but i can't install 10.04 at all.  Even when i try to upgrade from an earlier ubuntu, after reboot i get this message.

Any solutions?  I'm guessing it's a hardware issue as the software works fine elsewhere

---

### Post by zoomy942 on 2010-05-28
i just noticed mine doing it too

---

### Post by 2nubu on 2010-06-18
Same here... I have Dell Mini 10v.

It just started about a week ago, I think.

There was also something about PAM_TTY , etc, i think... as fast as my eyes could catch a glimpse of the stuff...

I'm a bit worried because it seems to me (just a feeling/impression) that something was interrupted, like a running program or port connection.

Port connection worries me the most, though... the idea that someone hacked in and connected the whole time.

---

### Post by torkna on 2010-06-18
I get the same error. I am running *Lubuntu* 10.04 and after every shutdown I get this error:

glib-warning getpwuid_r failed due to unknown user id (0) 

and then it just hangs. I can manually turn it off, but I get several errors on the reboot before and after the splash screen. Then it eventually boots normally and works fine. Is there a way around this? It is on an old Compaq Presario 7594, 128Mb of RAM and a 10Gb HDD.

---

### Post by 2nubu on 2010-07-13
I still get these... they flash before it complete shut down. Lately, I see "TERM SIGNAL" something disconnected.

On the other hand, i found out today that if I log out, and then shutdown... everything is normal.

---

