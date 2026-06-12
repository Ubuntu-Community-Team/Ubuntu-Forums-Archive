---
title: "Retrieving public keys"
date: 2012-08-02
forum: General Help
---

### Post by pwabrahams on 2012-08-02
After the latest updates I got a message from Synaptic to the effect that I was missing a public key.  My research yielded the following remedy:
```
gpg --keyserver pgpkeys.mit.edu --recv-key  A8AA1FAA3F055C03
```
But when I tried it, I got this:
```
gpg: requesting key 3F055C03 from hkp server pgpkeys.mit.edu
gpgkeys: HTTP fetch error 6: Couldn't resolve host 'pgpkeys.mit.edu'
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```
(Same result with pgpkeys.ubuntu.org.) I encountered this problem a couple of years ago and found a solution, but I no longer remember what it was.  Can anyone help?

The answer to this belongs in some FAQ or other.

---

### Post by plucky on 2012-08-03
> **pwabrahams said:**
> After the latest updates I got a message from Synaptic to the effect that I was missing a public key.  My research yielded the following remedy:
```
gpg --keyserver pgpkeys.mit.edu --recv-key  A8AA1FAA3F055C03
```
But when I tried it, I got this:
```
gpg: requesting key 3F055C03 from hkp server pgpkeys.mit.edu
gpgkeys: HTTP fetch error 6: Couldn't resolve host 'pgpkeys.mit.edu'
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```
(Same result with pgpkeys.ubuntu.org.) I encountered this problem a couple of years ago and found a solution, but I no longer remember what it was.  Can anyone help?

The answer to this belongs in some FAQ or other.


Try a different keyserver.

This works for me ```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys A8AA1FAA3F055C03
```

I tried your line from a terminal and it just sat there waiting to get the information,so I aborted it.
The above line worked right away.

Good Luck

---

### Post by pwabrahams on 2012-08-03
I tried this from a different computer, with these results:
```
root@pwa-K60IJ:/home/pwa# gpg --keyserver hkp://subkeys.pgp.net --recv-keys A8AA1FAA3F055C03
gpg: requesting key 3F055C03 from hkp server subkeys.pgp.net
?: subkeys.pgp.net: Host not found
gpgkeys: HTTP fetch error 7: couldn't connect: Success
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
root@pwa-K60IJ:/home/pwa# gpg --keyserver pgpkeys.mit.edu --recv-key  A8AA1FAA3F055C03
gpg: requesting key 3F055C03 from hkp server pgpkeys.mit.edu
?: pgpkeys.mit.edu: Host not found
gpgkeys: HTTP fetch error 7: couldn't connect: Success
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```
I've concluded that the choice of server isn't the problem.

From what I remember, the 'Host not found" message is bogus.  The problem is that the host isn't seeing what it's expecting.  But knowing that doesn't solve the problem.

---

### Post by pwabrahams on 2012-08-03
I finally bypassed the problems with retrieving the key via gpg and went to the keyserver.mit.edu website (any other keyserver website will work).  I inputted the key, preceding it with 0x.  I then was able to link to a keyblock.  I copied the *entire* keyblock, including the heading and trailing lines, to a file I called **launchpad**.  I then typed this on a superuser command line:```
apt-key add launchpad
```
The key finally got recognized.

Part of the problem with the gpg communication, it seems, is that it works not with the standard port 80 but with a special port 11371.  This port needs to be open.  I opened it with ```
ufw allow 11371
``` but that didn't solve the problem.  

What strikes me is that only a minority of users have this problem.  For most, the usual line ```
gpg --keyserver pgpkeys.mit.edu --recv-key  A8AA1FAA3F055C03
```works correctly.  Whatever the solution, it should account for this fact.

---

