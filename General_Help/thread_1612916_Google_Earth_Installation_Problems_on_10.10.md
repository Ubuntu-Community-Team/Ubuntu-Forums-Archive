---
title: "Google Earth Installation Problems on 10.10"
date: 2010-11-03
forum: General Help
---

### Post by dondiego2 on 2010-11-03
I downloaded GoogleEarthLinux.bin from there website and tried to install it and got these errors

```
sh GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.2.1.1588..............................................................
setup.data/setup.xml:1: parser error : Document is empty

^
setup.data/setup.xml:1: parser error : Start tag expected, '<' not found

^
Couldn't load 'setup.data/setup.xml'
```

I deleted the bin file and downloaded it again and had the same problem.  Anybody else having issues?

---

### Post by wilee-nilee on 2010-11-03
Install this version it works, and is a deb does it get much easier I say.;)
[http://packages.medibuntu.org/lucid/googleearth.html](http://packages.medibuntu.org/lucid/googleearth.html)

From this thread #21 post.
[http://ubuntuforums.org/showthread.php?t=1595339&page=4](http://ubuntuforums.org/showthread.php?t=1595339&page=4)

I have it installed .

---

### Post by rasfl3 on 2010-11-03
Just open up terminal and type in:
[FONT=monospace]
[/FONT]sudo apt-get install googleearth

You may also visit [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth) for assistance if the above doesn't work.

---

### Post by dondiego2 on 2010-11-03
Thanks.  Now its running!

---

### Post by ThatBum on 2010-11-03
Isn't Google Earth itself not in the repos anymore? Something about Google not wanting to redistribute it. The thing there is now is googleearth-package, which just wgets the archive from Google, builds it, and puts it in a deb on the local machine. That's what I did.

---

### Post by wilee-nilee on 2010-11-03
> **ThatBum said:**
> Isn't Google Earth itself not in the repos anymore? Something about Google not wanting to redistribute it. The thing there is now is googleearth-package, which just wgets the archive from Google, builds it, and puts it in a deb on the local machine. That's what I did.

It is in the repos but the errors shown are what happens I think the link is a slightly earlier version.

---

### Post by jcolyn on 2010-11-03
> **ThatBum said:**
> Isn't Google Earth itself not in the repos anymore? 

Googleearth is not in the repos by default...just googleearth-package which has to be built.

You can enable Medibuntu which will show it in the repos or you can download the .deb file and install it..

---

### Post by ThatBum on 2010-11-03
Whoops, I just looked here and realized I got ninja'd by dondiego2.

I looked at packages.medibuntu.org. It seems there is no googleearth in maverick, but there is in lucid. Hmm.

[http://packages.medibuntu.org/maverick/index.html](http://packages.medibuntu.org/maverick/index.html)
[http://packages.medibuntu.org/lucid/index.html](http://packages.medibuntu.org/lucid/index.html)

---

### Post by wilee-nilee on 2010-11-03
> **ThatBum said:**
> Whoops, I just looked here and realized I got ninja'd by dondiego2.

I looked at packages.medibuntu.org. It seems there is no googleearth in maverick, but there is in lucid. Hmm.

[http://packages.medibuntu.org/maverick/index.html](http://packages.medibuntu.org/maverick/index.html)
[http://packages.medibuntu.org/lucid/index.html](http://packages.medibuntu.org/lucid/index.html)

Load the google earth package and down load the deb I linked.

Actually I'm not sure you even need the package, the deb will show if you do.

---

### Post by dondiego2 on 2010-11-04
> **ThatBum said:**
> Whoops, I just looked here and realized I got ninja'd by dondiego2.

I looked at packages.medibuntu.org. It seems there is no googleearth in maverick, but there is in lucid. Hmm.

[http://packages.medibuntu.org/maverick/index.html](http://packages.medibuntu.org/maverick/index.html)
[http://packages.medibuntu.org/lucid/index.html](http://packages.medibuntu.org/lucid/index.html)


I found google earth package in synaptic package manager and installed it but could not get it to work.  It would start and then shut down.  I also downloaded the bin file from the google earth site and it wouldn't install.

Getting the deb package from the site suggested earlier worked for me.

---

