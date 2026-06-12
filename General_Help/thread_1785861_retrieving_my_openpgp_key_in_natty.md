---
title: "retrieving my openpgp key in natty"
date: 2011-06-18
forum: General Help
---

### Post by fremantle on 2011-06-18
hy folks, im trying to register my openpgp key in launchpad
> Importing an OpenPGP key

To import your OpenPGP key into Launchpad, you first need the key's fingerprint.

Note: You must ensure your key is in the Ubuntu keyserver before you try to add it to Launchpad.

Retrieving the key in Ubuntu

The easiest way to generate a new OpenPGP key in Ubuntu is to use the Passwords and Encryption Keys tool. If you are using Ubuntu 10.04 or an earlier version, it is located at Applications > Accessories > Passwords and Encryption Keys. In Ubuntu 10.10 and later versions, it is located at System > Preferences > Passwords and Encryption Keys.

Step 1 Open Passwords and Encryption Keys.

Step 2 Select the My Personal Keys tab, select your key and open the property window by pressing Space Bar or double clicking with your pointer. Select the Details tab of the property window.

Step 3 Select the Fingerprint text (the ten blocks of numbers and letter). Copy the text by pressing the Ctrl+c keys together.

Retrieving the key using the GPG command

Open a terminal and enter:

gpg --fingerprint

GPG will display a message similar to:

pub 1024D/12345678 2007-01-26
Key fingerprint = 0464 39CD 2486 190A 2C5A 0739 0E68 04DC 16E7 CB72
Geoffrey Hayes (My OpenPGP key) <geoffrey@bungle.com>
sub 2048g/ABCDEF12 2007-01-26

Highlight and copy only the numeric fingerprint: 0464 39CD 2486 190A 2C5A 0739 0E68 04DC 16E7 CB72 in the example above.

so i followed these instructions, and there was nothing in my "personal keys", same for the command. so my question is how do i get the fingerprint to be able to register my key in launchpad?

---

### Post by fremantle on 2011-06-18
holy snap i just googled my question and it brought me back here. wow.

---

### Post by Habitual on 2011-06-18
You have to generate a key before you can export or get its fingerprint.

[http://irtfweb.ifa.hawaii.edu/~lockhart/gpg/gpg-cs.html](http://irtfweb.ifa.hawaii.edu/~lockhart/gpg/gpg-cs.html)

---

### Post by silex89 on 2011-06-18
[THIS]("http://screencasts.ubuntu.com/2010/12/22/004-SigningCoC") may resolve your problem :P It's from the Code of Conduct, but the part of the pgp key is what you're looking for.

Best Luck :)

---

