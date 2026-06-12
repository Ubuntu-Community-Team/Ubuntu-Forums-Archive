---
title: "How to download an already upgraded Ubuntu iso-image?"
date: 2011-05-23
forum: General Help
---

### Post by HotForLinux on 2011-05-23
I would like to download an already upgraded Ubuntu Live-CD or upgraded alternate CD iso-image. 
Like an Ubuntu Hardy with all the package and safety upgrades up till  now so that I don't need to upgrade with a network connection.
Particularly the last two LTSs:  Hardy Heron and a Lucid Lynx

Does anyone know if it is possible?

[I think I posted this same question in the wrong place. in:
[http://ubuntuforums.org/showthread.php?p=10852927](http://ubuntuforums.org/showthread.php?p=10852927)
before.]

---

### Post by ajgreeny on 2011-05-23
Not possible in the way you describe, I'm afraid.  The nearest we get to that is the .point versions of the LTS ubuntu distros, eg 10.04.1 then 10.04.2.  The intervening versions of ubuntu do not have such a luxury, you simply get the iso of 11.04, and it will then be fixed.

---

### Post by HotForLinux on 2011-05-25
Thank you for your reply

What is the difference between what I say and what you say for the LTS releases? And how does one download those ".point" versions

---

### Post by LordNeo on 2011-05-25
Get the last LTS CDROM, install and then insert the newest CDROM (Natty) once inserted the autorun question will allow you to open synaptic and then you can just "upgrade" the packages from the cdrom

---

### Post by mikewhatever on 2011-05-25
If you download 10.04 and 8.04 now, you automatically get the 10.04.2 and 8.04.4, no need to do anything there for you.

---

### Post by HotForLinux on 2011-05-25
> **LordNeo said:**
> Get the last LTS CDROM, install and then insert the newest CDROM (Natty) once inserted the autorun question will allow you to open synaptic and then you can just "upgrade" the packages from the cdrom

What is the autorun question? I guess that after inserting the Live CDROM a question will be prompted asking what to do. But shouldn't the LTS CDROM and the packages in the "newest CD" be of the same release?. 
Let's say, I install Ubuntu Hardy and then use the newest CDROM (Natty), as you say, to upgrade the packages. If that is possible, wouldn't I end up with natty packages in a Hardy install?

---

### Post by HotForLinux on 2011-05-25
> **mikewhatever said:**
> If you download 10.04 and 8.04 now, you automatically get the 10.04.2 and 8.04.4, no need to do anything there for you.

Sure? There's no need to select which point version to download?
How come there's no info about that in the common download places?. It seems that you are going to download the same image as the first release.
But, well.... that sounds a good solution. It is simple, and even if the packages are not updated to the last second it would have a lot of upgrades and save a lot of time and work.

---

### Post by LordNeo on 2011-05-25
> **HotForLinux said:**
> What is the autorun question? I guess that after inserting the Live CDROM a question will be prompted asking what to do. But shouldn't the LTS CDROM and the packages in the "newest CD" be of the same release?. 
Let's say, I install Ubuntu Hardy and then use the newest CDROM (Natty), as you say, to upgrade the packages. If that is possible, wouldn't I end up with natty packages in a Hardy install?
Yes, you will end up with some packages upgraded to natty, but only those markes as "Security Fix" or alike, it will not upgrade your whole system to natty.
It also shouldn't install any new package, only upgrade already installed packages

---

### Post by mikewhatever on 2011-05-26
@HotForLinux
The file name you download clearly indicates that the ISO image had been updated.

@LordNeo
I'd mention that it's only possible to upgrade to 11.04 from 10.10. It wouldn't work with any older release. For example, the following wouldn't work:
> Let's say, I install Ubuntu Hardy and then use the newest CDROM (Natty), as you say, to upgrade the packages. If that is possible, wouldn't I end up with natty packages in a Hardy install?

See the upgrade howto:
[https://help.ubuntu.com/community/NattyUpgrades](https://help.ubuntu.com/community/NattyUpgrades)

---

### Post by HotForLinux on 2011-06-04
[QUOTE=mikewhatever;10864222]@HotForLinux
The file name you download clearly indicates that the ISO image had been updated.

I see. That's true, and it is ok. But you can only see that once you start the download. A brief, one line explanation, is missing somewhere or everywhere you download an updated old version.

For each release set of versions there should be the current (with all updates) and the old ones to choose.

---

