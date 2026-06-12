---
title: "Default crypttab needed"
date: 2009-11-16
forum: General Help
---

### Post by potam on 2009-11-16
Hello all,

I had to reinstall Karmic, luckily my encryped home folder was on a separate partition. Now everything is fine :) but the installer did not encrypt my swap partition. I did it by hand, [following this tutorial]("http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu"). My encrypttab file now is this:
```

# <target name>	<source device>		<key file>	<options>
cryptoswap	/dev/sda2	/dev/urandom	cipher=aes-cbc-essiv:sha256,size=256,hash=sha256,swap

```

What about yours? I am curious that the default installation, with home encryption uses direct dev devices (/dev/sda2 in my case), or UUID? I noticed that my swap UUID changes on every boot.

Plus one question: did the installer encrypt your /tmp or not?

---

### Post by potam on 2009-11-17
I answer my own question: Karmic does not encrypt swap or tmp, just home.

---

