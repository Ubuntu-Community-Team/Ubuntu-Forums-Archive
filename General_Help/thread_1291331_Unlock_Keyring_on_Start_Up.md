---
title: "Unlock Keyring on Start Up"
date: 2009-10-14
forum: General Help
---

### Post by nbesteman2136 on 2009-10-14
Not sure what I did, but all of a sudden on each startup, Ubuntu presents a dialog box with the following instructions:

###########
Unlock Keyring

Enter password for default keyring to unlock

The application 'nm-applet' (/usr/bin/nm-applet) wants access to the default keyring, but it is locked

###########

It is no real problem, as I just type in my administrator password and everything goes smoothly from there. It is a little annoying, so if there is a way to get rid of it, that would be greeeeaaatt....

---

### Post by doas777 on 2009-10-14
same problem. I'm trying to give the kids access to select shares on samba without giving them the password, but if i don't put in the passwd for share access, I have to put it in to unlock the keyring. rather circular and frustrating.

---

### Post by Bonster on 2009-10-14
just clear ur keyring pass and leave it empty next time it prompts to set a password.

---

### Post by tempus on 2009-10-15
> **Bonster said:**
> just clear ur keyring pass and leave it empty next time it prompts to set a password.

what do you mean "just clear ur keyring pass"?

---

### Post by sloggerkhan on 2009-10-15
a keyring stores saved passwords in an encrypted file.
Because the login process is not chained to decrypt your keyring, you have to enter the password yourself. This prevents others who access your computer from being able to find your saved passwords easily.

---

### Post by tempus on 2009-10-15
> **sloggerkhan said:**
> a keyring stores saved passwords in an encrypted file.
Because the login process is not chained to decrypt your keyring, you have to enter the password yourself. This prevents others who access your computer from being able to find your saved passwords easily.

that may be so but it is only me using the computer so how do I get rid of the keyring prompt?

---

### Post by sloggerkhan on 2009-10-15
[http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14](http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14)
Or google 'ubuntu unlock keyring on login'

---

### Post by kelvin.illa on 2009-10-15
the problem here is the nm-applet (i.e., network manager applet); it always asks for your password every login. There's another network manager called "wicd" (or **W**ireless **I**nterface **C**onnection **D**aemon) in the repos that doesn't ask for password anymore; this is the one I'm using right now. I do think it's not as good-looking -- by a bit -- as the default network manager ([here are screens]("http://wicd.sourceforge.net/screenshot.php")), but I can't take the constant nagging of the default. Maybe this will get fixed in Karmic, but while it isn't yet, you may use wicd and reinstall network manager the same way you installed wicd if it does get fixed.

You can install it via add/remove, synaptic package manager, or terminal (sudo apt-get install wicd) and it automatically uninstalls the default network manager.

It's just as easy to bring back the default if you don't like wicd.

---

### Post by kelvin.illa on 2009-10-15
Oh yeah -- about what you did, you probably set your log-in to 'automatic log-in.' If it's not on automatic (meaning, you have to log-in via the log-in screen) the nm-applet password prompt won't show up because you already typed-in your password at the log-in screen.

---

### Post by doas777 on 2009-10-16
ok, so how do I set it up to not ask for a password at all (not for keyring, or for samba)? I am set to autologin, and the users are not to know the password.

---

