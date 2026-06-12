---
title: "Can't mount eCryptfs /home"
date: 2010-01-15
forum: General Help
---

### Post by pablomics on 2010-01-15
I installed Kubuntu Karmic Koala with encrypted /home partition.

Since I decided to change my password I couldn't graphically log in. So I learned that I had to change the eCryptfs' passphrase.
And I did:
[FONT="Courier New"]
$ ecryptfs-wrap-passphrase .ecryptfs/wrapped-passphrase
  Passphrase to wrap: <I put my login password here>
  Wrapping passphrase: <I put my login password here too>
[/FONT]

Now when I log in my home folder only contains two files:
[FONT="Courier New"]Access-Your-Private-Data.desktop  README.txt[/FONT]
The README.txt says that I have to mount my Private folder with [FONT="Courier New"]ecryptfs-mount-private[/FONT] and so I do, but after I enter my login password I get:

[FONT="Courier New"]Inserted auth tok with sig [****************] into the user session keyring
keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'[/FONT]

And my files doesn't appear... I did [FONT="Courier New"]ecryptfs-insert-wrapped-passphrase-into-keyring[/FONT] then I logged out and in but it haven't worked either.

I wonder if anybody could help me to recover my files.

---

### Post by Byb on 2011-02-17
It seems you make a confusion between password and passphrase.
This post [http://doc.ubuntu-fr.org/ecryptfs](http://doc.ubuntu-fr.org/ecryptfs) explains what happens when one changes one's password from command line : one's home becomes unavailable. There is an "howto recover" if you remember the passphrase.
This could help too : [http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/)

---

