---
title: "Confusion about the fglrx driver and Radeon 9200"
date: 2009-07-28
forum: General Help
---

### Post by Jeinhor on 2009-07-28
Hello,

I'm running Ubuntu Januty 9.04 (i686) with ATI Radeon 9200. Compiz and such runs just fine, but I'm having some small problems. For example, if I start glxgears and move the window around it leaves still images at previous locations. I can then "erase" these still images by moving another window over them.

Also, when I run XBMC in windowed mode, desktop windows "flickers" through. This, along with some other issues in XBMC, made me look for other drivers.

I read at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) that "The 'fglrx' driver does not support cards earlier than the 9500". Crap.

However, if I go to ati.com, choose drivers, then Linux, then Radeon and then Radeon 9200 I get this page: [http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx](http://support.amd.com/us/gpudownload/Pages/linux64-radeon-prer200.aspx).

1. Is this also fglrx drivers?
2. Why does drivers for my card exist at ATi's page when the BinaryDriverHowto/ATI says my card isn't supported?
3. How do I know which download link to pick? I tried running the check.sh script, but even when I ran it with sudo I got some message about me "not having console ownership".

Also, if I look at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI), it says "Enable the accelerated ATI graphics driver in the 'Hardware Drivers' (System->Hardware drivers)". If I go there I see no hardware driver. Does this mean I'm screwed?

Would really appreciate some inputs on this, it's quite confusing. Thanks in advance!

---

### Post by Jeinhor on 2009-07-31
I'll try to answer myself =)

1. Yes, it is, judging by [http://en.wikipedia.org/wiki/fglrx](http://en.wikipedia.org/wiki/fglrx) which shows a list of drivers released by ATi.
2. Probably because the BinaryDriverHowto/ATi is talking about the latest version of fglrx, as the support for Radeon 9200 is dropped in 8.29.6. When I choose drivers for Radeon 9200 on ati.com, I get to 8.28.8.
3. EDIT: Appears X.org is a fork of XFree86, and the one used by ubuntu is X.org: [http://ubuntuforums.org/archive/index.php/t-80156.html](http://ubuntuforums.org/archive/index.php/t-80156.html)

[COLOR="Red"]Will it work running those old fglrx drivers on new Ubuntu 9.04?[/COLOR] I'd rather not trash my system again...

---

### Post by 3rdalbum on 2009-07-31
The old drivers do not work with the newer version of Xorg that is included in Jaunty.

---

### Post by Jeinhor on 2009-07-31
Ok, thank you for clarifying this! Now I can look for a new graphic card without feeling bad =)

---

