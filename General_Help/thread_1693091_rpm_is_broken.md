---
title: "rpm is broken?"
date: 2011-02-22
forum: General Help
---

### Post by Beowolf64 on 2011-02-22
I am currently reading a book about Linux commands. There is an example which shows how to print all installed packages. But on my PC is shows northing:

**rpm -qa**

I know it is supposed to print a long list of all installed packages. I tried to re-install rpm from the synaptic, but still it shows no output.

Any help is appreciated.

---

### Post by gandaran on 2011-02-22
ubuntu is based on debian .deb packages not .rpm so that command should work only on rpm systems like opensuse or fedora.

---

### Post by HermanAB on 2011-02-22
Howdy,

RPM stands for Red Hat Package Manager.  That should give you a clue...

Either change to Fedora, or find a book on Debian.

---

### Post by Beowolf64 on 2011-02-22
Ah, I see. Thanks for clarifying. 

Another relevant question. 

I manually installed GCC 4.52 (./configure; make; install) following the instructions from GNU website (don't ask why I didn't use synaptic). Now I have both gcc 4.4 and 4.52. Is it possible to remove the older version (synaptic installed 4.4) without braking the newer version (manually installed 4.52)?

Thank you!

P.S. I don't mind both versions to be present in my PC, as long as there is no conflict. Maybe I should remove manually installed version and reinstall it with synaptic?

---

### Post by gandaran on 2011-02-22
> **Beowolf64 said:**
> Ah, I see. Thanks for clarifying. 

Another relevant question. 

I manually installed GCC 4.52 (./configure; make; install) following the instructions from GNU website (don't ask why I didn't use synaptic). Now I have both gcc 4.4 and 4.52. Is it possible to remove the older version (synaptic installed 4.4) without braking the newer version (manually installed 4.52)?

Thank you!
yes you can safely remove 4.4 using synaptic without affecting 4.52, they are probably installed in deferent folders (you can check in file system where 4.52 is installed) but even if there was any conflict you can compile 4.52 again after removing the older one.

---

### Post by Stephen Morgan on 2011-02-22
dpkg --get-selections  Will print a list of installed packages, I believe.

---

### Post by Diametric on 2011-02-22
BTW - I just picked up a great book called:

[http://www.amazon.com/Ubuntu-Linux-Toolbox-Commands-Debian/dp/0470082933](http://www.amazon.com/Ubuntu-Linux-Toolbox-Commands-Debian/dp/0470082933)

It goes over Ubuntu (Debian based) installs and the various ways to accomplish that.  Lots of other cool stuff in it too.  Might be worth checking out.

Cheers.

---

### Post by Beowolf64 on 2011-03-05
SOLVED. [B]Debian uses dpkg, not rpm.
[/B]

---

