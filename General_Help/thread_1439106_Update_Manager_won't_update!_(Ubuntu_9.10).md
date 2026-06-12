---
title: "Update Manager won't update! (Ubuntu 9.10)"
date: 2010-03-25
forum: General Help
---

### Post by trixa_13 on 2010-03-25
When I clicked the option, "Check", an error message would pop-up. And it says:
[COLOR=Red]
W: GPG error: [http://repository.glx-dock.org](http://repository.glx-dock.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1392A97E41317877
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783[/COLOR]

[COLOR=Black]What should I do?[/COLOR]

---

### Post by Dantevus on 2010-03-25
I'd remove the medibuntu repositories and try again. Looks like they are out of date.

---

### Post by wojox on 2010-03-25
Run this in the terminal:

```
gpg --keyserver subkeys.pgp.net --recv 1392A97E41317877
```

```
gpg --export --armor 1392A97E41317877 | sudo apt-key add -
```

Then repeat it for the other number.

---

### Post by trixa_13 on 2010-03-25
> **wojox said:**
> Run this in the terminal:

```
gpg --keyserver subkeys.pgp.net --recv 1392A97E41317877
``````
gpg --export --armor 1392A97E41317877 | sudo apt-key add -
```Then repeat it for the other number.


[FONT=Comic Sans MS][SIZE=4][COLOR=DarkOrange]Thank you very much![/COLOR][/SIZE][/FONT] :KS

---

### Post by wojox on 2010-03-27
Welcome ;)

---

