---
title: "Canon iP2600 won't print"
date: 2010-02-11
forum: General Help
---

### Post by ChuckT on 2010-02-11
Hi,

I searched for solutions for hours and yet can't manage to get my printer to work.

I downloaded (as it was suggested elsewhere) the "cnijfilter-common" and the "cnijfilter-ip2600" that I found on Canon website. However when I want to install the first package, it says : "Error : Failed to satisfy all dependencies (broken cache)". 

Can anyone please help? 

(I use Ubuntu 9.10)

Edit : I found that the missing dependency was "libcupsys2" but I can't find it on Synaptic...

---

### Post by kahumba on 2010-02-11
this is what aptitude is saying:
> 
aptitude show libcupsys2
No current or candidate version found for libcupsys2
Package: libcupsys2
State: not a real package
Provided by: libcups2
I don't know what's the matter, try installing libcups2 but it's probably installed already..

btw, when searching for a library issue "aptitude search libname", to show details issue "aptitude show libname".

---

### Post by ChuckT on 2010-02-11
Yeah, libcups2 is already installed.

---

### Post by kahumba on 2010-02-11
Have you tried the solution by [lubeck]("http://ubuntuforums.org/member.php?u=449956") at
[http://ubuntuforums.org/showthread.php?t=775368](http://ubuntuforums.org/showthread.php?t=775368)

---

### Post by ChuckT on 2010-02-11
[IMG]http://i45.tinypic.com/2j29d8j.png[/IMG]

That's by installing the .deb package after doing what he said : sudo aa-complain cupsd. It's the same message I got before, again it's not working.

---

### Post by collinge on 2010-02-16
I have a cannon ip2600 and had the same problem you have.. tried for months to get it to work... 

Until i found this 
[http://ubuntuforums.org/showthread.php?t=775368&highlight=cannon+ip2600&page=2](http://ubuntuforums.org/showthread.php?t=775368&highlight=cannon+ip2600&page=2)

Download the stuff almikul put up there. then look @ post numbers 18 & 20

Mine runs like a champ using 9.10

---

