---
title: "What does it mean when a release stops being supported?"
date: 2011-07-16
forum: General Help
---

### Post by redss on 2011-07-16
I've got a PC incompatible with Lucid so installing Maverick to it.

What does it mean that Maverick will be supported with security updates until April 2012?  

Will the apt-get repositories stop working at some point after that?

---

### Post by Ad@m on 2011-07-16
It means it will no longer receive updates from the ubuntu repositories. So yes, you are correct.

---

### Post by Frogs Hair on 2011-07-16
If you have questions about when releases reach end of life , see the link. 

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by redss on 2011-07-24
Does this mean that if I use apt-get to install a software application today (like flashplugin-nonfree) that apt-get may not work to install it after April 2012 when 10.10 is desupported?

---

### Post by HermanAB on 2011-07-25
It means that you are now a grown-up and has to look after the server yourself...

---

### Post by linuxman94 on 2011-07-25
> **HermanAB said:**
> It means that you are now a grown-up and has to look after the server yourself...
:lolflag:

OP:  You will still be able to installer software, however, the repositories will stop being updated the latest versions.  You shouldn't worry about the EOL because you can always update to 11.04.

---

### Post by CatKiller on 2011-07-25
> **redss said:**
> Does this mean that if I use apt-get to install a software application today (like flashplugin-nonfree) that apt-get may not work to install it after April 2012 when 10.10 is desupported?

You'll need to point your sources.list to old-releases.ubuntu.com instead. You'll still be able to install software, just not updated software.

You don't have to install Maverick, though. Natty's out now.

---

### Post by redss on 2011-07-25
I just wanted to be sure that all the apt-get installs (that currently work) won't break after the EOL date, which sounds like the case, right?

I ask since I use the non-persistent liveUSB version and always reinstall via apt-get after rebooting.

---

### Post by CatKiller on 2011-07-25
Non-persistent means that you won't be able to change your sources.list. But you can use the current live version instead.

---

### Post by redss on 2011-07-25
Actually non-persistent means the apt-get installed packages have to be reinstalled after rebooting.  I can easily update my sources.list before using apt-get to reinstall.

---

### Post by CatKiller on 2011-07-25
You're quite right. Wasn't thinking.

And I guess it's not that much extra trouble given that you're installing stuff fresh each time anyway.

Is it a security thing that you're not running a persistent version?

---

