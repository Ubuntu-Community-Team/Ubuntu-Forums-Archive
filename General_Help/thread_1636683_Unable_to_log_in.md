---
title: "Unable to log in"
date: 2010-12-03
forum: General Help
---

### Post by dab1414 on 2010-12-03
Hello. This is my first post asking for help. I have been unable to find answers in the forum that works for me. Recently (on my wifes netbook) I tried to bypass the NM from asking for the default keyring. so here is what I did (I forget where I got these instructions.

```
sudo apt-get libpam-keyring
sudo gedit /etc/pam.d/gdm
``` added the following in the bottom: @include common-pamkeyring Changed the following: auth optional pam_keyring.so  
TO
auth optional pam_keyring.so try_first_pass

and
session optional pam_keyring.so auto_start
TO
session optional pam_keyring.soAt this point when I rebooted I was unable to log in. Actually when I clicked on the username the box for a password never appeared.

So I went to Ctrl + Alt + F1 for console mode. I was able to log in there. Then this is what I did.

 ```
sudo apt-get remove libpam-keyring
sudo nano
```edited the /etc/pam.d/gdm file back to default. ( removed what I had changed)
 Ctrl + Alt + F7 to go back to desktop mode

Ok now when I click on the username the box appears for password but now permission is denied. But I can still log in through the console mode.

Thanks in advance for any help.

---

### Post by galvatron408 on 2010-12-03
I couldn't figure out what the GUI wanted either so I logged in as root via the GUI and used the root account to reset the password for my account.

if anyone knows what the GUI wants, I'd like to know too.

---

### Post by dab1414 on 2010-12-06
well no answer but thats ok. Kids spilled a soda on it, so whole thing fried, gotta rebuild. So I am marking as solved cause no problem now.

---

