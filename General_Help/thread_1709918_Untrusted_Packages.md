---
title: "Untrusted Packages?"
date: 2011-03-19
forum: General Help
---

### Post by Maplesyrup on 2011-03-19
Hi, I am unable to download any updates or software in the software centre as I keep getting this error
"Requires installation of untrusted packages

The action would require the installation of packages from sources that are not authenticated."

After search online and trying a few of the common fixes, it still will not allow me to download any software.
One fix was to check the the source code box in software sources, mine was already checked but was not a tick but a a dash? I've attached a picture.
Any suggestions how to fix this? I'm running 10.10[IMG]http://i52.tinypic.com/rcu613.png[/IMG][/IMG]

---

### Post by cbowman57 on 2011-03-19
Sounds like you're missing the pgp keys for the repositories.

Try clicking the Authentication tab and then the Restore Defaults button on the lower right.  I am hoping that will restore or re-download the authentication keys.

---

### Post by vivek.pandey on 2011-03-19
hi
  is your ubuntu updated?
if no first update and upgrade.if this doesnt work then

Try repairing your gpg keys using the following commands. Open an Applications->Accessories->Terminal and type:

Code:
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 40976EAF437D05B5
then in the same terminal type:

Code:
apt-key add ~/.gnupg/pubring.gpg

hope this helpes

---

### Post by Maplesyrup on 2011-03-19
> **cbowman57 said:**
> Sounds like you're missing the pgp keys for the repositories.

Try clicking the Authentication tab and then the Restore Defaults button on the lower right.  I am hoping that will restore or re-download the authentication keys.

Tried that, it did nothing :\. Thanks anyway

---

### Post by Maplesyrup on 2011-03-19
> **neo_aryan said:**
> hi
  is your ubuntu updated?
if no first update and upgrade.if this doesnt work then

Try repairing your gpg keys using the following commands. Open an Applications->Accessories->Terminal and type:

Code:
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 40976EAF437D05B5
then in the same terminal type:

Code:
apt-key add ~/.gnupg/pubring.gpg

hope this helpes

I have had the worst internet connection recently (at a share house, internet was pretty much dead  -_-) so it hasn't been updated. 
Inserted that into terminal and got "gpg: no valid OpenPGP data found." for both? Would it be easier to do a fresh install? I wouldn't be happy about it...but if it is needed...

---

### Post by cbowman57 on 2011-03-19
Before you resort to a fresh install just change your source server, from Australia to Main for example, and see if it automatically tries to update the keyring.

---

### Post by npattillo on 2011-03-21
That fixed the same issue that I was having with installing new software. Just had to change the server to the main server. Thanks.

---

### Post by Maplesyrup on 2011-03-23
> **cbowman57 said:**
> Before you resort to a fresh install just change your source server, from Australia to Main for example, and see if it automatically tries to update the keyring.
Didn't work...thanks anyway. I'll just do a fresh install :(

---

