---
title: "Can never access keyserver.ubuntu.com"
date: 2009-11-01
forum: General Help
---

### Post by nortexoid on 2009-11-01
Whenever I try to add a PPA using add-apt-repository it doesn't work because the key can't be retrieved from the keyserver. I've also tried accessing keyservers via Firefox and it times out.

Is there an alternative server or something for these things? I live in the UK, if that matters.

---

### Post by howefield on 2009-11-01
> **nortexoid said:**
> Is there an alternative server or something for these things?

Try using one of these alternatives.

[http://pgp.mit.edu/](http://pgp.mit.edu/)
keyserver.pgp.com

---

### Post by scout4536 on 2009-11-01
I too have had this problem lately.  Although after repetition of the command in terminal it eventually goes through.  I think maybe the servers are a bit slow because of traffic due to the new release.  I have also noticed that updates download slower as well.  I tried at about 2 in the morning here and the speed seemed to pick up and all the apt-key adv commands went through rather fast.  Hope this helps.

---

### Post by nortexoid on 2009-11-01
Thanks. I wonder, though, is there any way of setting those keyservers as default? Also (dumb question), how do you retrieve a key from those keyservers? Entering the Key ID from the PPA doesn't appear to work for the PGP service.

---

### Post by howefield on 2009-11-01
> **nortexoid said:**
> Thanks. I wonder, though, is there any way of setting those keyservers as default? Also (dumb question), how do you retrieve a key from those keyservers? Entering the Key ID from the PPA doesn't appear to work for the PGP service.

Which key are you after ? if for example it was medibuntu, go to pgp.mit.edu and enter medibuntu in the search field, press enter, and follow the links through to the key which can be copied/pasted into a text file. Then import into Synaptic.

---

### Post by nortexoid on 2009-11-01
Oh that's easy enough. Thanks!

---

### Post by davosmith on 2009-11-01
If you're feeling brave, you could always try typing this:

```
sudo gedit /usr/lib/python2.6/dist-packages/softwareproperties/ppa.py
```

Then change the bit that says 'keyserver.ubuntu.com' to 'pgp.mit.edu'

Worked well for me...

---

### Post by nortexoid on 2009-11-01
> **davosmith said:**
> If you're feeling brave, you could always try typing this:

```
sudo gedit /usr/lib/python2.6/dist-packages/softwareproperties/ppa.py
```

Then change the bit that says 'keyserver.ubuntu.com' to 'pgp.mit.edu'

Worked well for me...

The worst thing that could happen, I imagine, is that keys won't get automatically imported until I change the file back. Thanks!

---

