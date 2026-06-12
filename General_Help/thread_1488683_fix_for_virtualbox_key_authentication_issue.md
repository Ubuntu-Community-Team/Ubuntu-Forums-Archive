---
title: "fix for virtualbox key authentication issue"
date: 2010-05-20
forum: General Help
---

### Post by zeus77 on 2010-05-20
Just thought I'd post this in case anyone else is experiencing the same problem.  For awhile now, I have been running VirtualBox which was installed by adding the virtualbox.org repository to my apt sources.  Starting sometime yesterday, the Update Manager started complaining about key authentication problems, namely:

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://download.virtualbox.org karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139

W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/karmic/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

Apparently VirtualBox 3.2 just got released, and it's the first release under the Oracle name (since Oracle's acquisition of Sun).  As such, you need to get a new key:

```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```

Problem solved.  I then promptly upgraded to 3.2...

Hope this helps someone... Cheers,

zeus77

---

### Post by csocci on 2010-05-20
Thanks Zeus,

That was quite handy.

Cheers

---

### Post by pricetech on 2010-05-20
If I understand correctly, this shouldn't affect the OSE version should it ??

---

### Post by detrate on 2010-05-20
thanks, it just helped me

---

### Post by J@n on 2010-05-20
Hi Zeus77,

Thanks! Solved my issue :smile:

Regards,

J@n

---

### Post by GedWarren on 2010-05-20
Thanks that fixed it for me :)

---

### Post by Brandel Valico on 2010-05-21
Thanks also

---

### Post by Objekt on 2010-05-22
I was having the same problem as the OP.  It's fixed now.  Thanks!

---

### Post by Tipoz on 2010-05-23
Thanks, no error anymore, but no offering of version 3.2. Maybe cause i'm still running Karmic Koala (9.10). I had to upgrade  through Synaptic, but it works great (and have to acustom me not to look for Sun virtual box in my menu but Oracle virtual box).

---

### Post by Blümchen Blau on 2010-05-23
Thanks!
My problems with authentication were solved already, but I didn't recognise that version 3.2 is in the repos! Synaptic helped!;)

---

### Post by hey-you on 2010-05-23
Thanks, you helped me too.

---

### Post by anaon on 2010-05-25
I was having the same problem. You saved me some time, thanks!

---

### Post by Objekt on 2010-05-25
This should be stickied in the "Virtualization" forum, if it isn't already.

---

### Post by Danny d on 2010-08-18
As soon as I run 
wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -

I get the error,

gpg: no valid OpenPGP data found.

Can someone please help me :(

---

