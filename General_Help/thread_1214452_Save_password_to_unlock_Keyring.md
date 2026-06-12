---
title: "Save password to unlock Keyring"
date: 2009-07-15
forum: General Help
---

### Post by villalcalde84 on 2009-07-15
I'm using Ubuntu 8.04, and I do not want to type my username and password everytime I start my computer. I selected the "Enable Automatic Login" option under Login Window Preferences, but now everytime the system starts I'm asked to enter my password to unlock the Keyring because some applications wants to access it, as shown in the image below.

This only happens when the option mentioned above is selected, so is there a way to save my password so that I am not asked to enter the password to unlock the Keyring?

Thanks!

---

### Post by SteveDee on 2009-07-16
> **villalcalde84 said:**
> I'm using Ubuntu 8.04, and I do not want to type my username and password everytime I start my computer. I selected the "Enable Automatic Login" option under Login Window Preferences, but now everytime the system starts I'm asked to enter my password to unlock the Keyring because some applications wants to access it, as shown in the image below.

This only happens when the option mentioned above is selected, so is there a way to save my password so that I am not asked to enter the password to unlock the Keyring?

Thanks!

When set to auto-login, Gnome will still ask for a password for your Wifi. The easy solution to this is to set a blank password, but please consider security implications if your system is exposed to potentially malicious users!

The user keyring is held in $Home/.gnome2/keyrings/default.keyring
Deleting this file forces a request for fresh network keyphrase next time system starts.

If you clear the keyring file (as above) then restart, enter the Wifi keyphrase when requested. But for keyring password just accept a blank.

Now your system should auto boot into your default user account without asking for passwords.

**************************
Here is a solution {that I copied from somewhere} that retains your keyring password, but I don't think this worked for me:-

Append the following to the end of /etc/pam.d/gdm:-
@include common-pamkeyring
..as follows...
open terminal;
- to install libpam-keyring enter:-
sudo apt-get install libpam-keyring
- and to modify the gdm login file do:-
sudo gedit /etc/pam.d/gdm
- then it will open the file in a text editor. add the line:-
@include common-pamkeyring
to the end of the file w/o erasing the stuff above it. save it and close.

This only works if your keyring pw is the same as your login pw. if it isn't, before doing any of this just delete your keyring (as above).
***********************

---

### Post by villalcalde84 on 2009-07-16
Thaks SteveDee for your answer, but the problem is that I do not use the WiFi; I'm asked to enter the password to use Cgmail, as the picture attached shows, or/and when I start Evolution.

I have searched and found your recommendation in this post: [Stop having to enter keyring over and over again]("http://ubuntuforums.org/showthread.php?t=463639"). But, as you mentioned, this is to solve the problem of wifi. Does this work with other applications too?

---

