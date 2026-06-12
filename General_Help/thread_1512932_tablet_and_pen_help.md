---
title: "tablet and pen help"
date: 2010-06-18
forum: General Help
---

### Post by dbowlin17 on 2010-06-18
[http://www.gottabemobile.com/forum/other-os/963-ubuntu-tablet-sharing-my-experiences.html](http://www.gottabemobile.com/forum/other-os/963-ubuntu-tablet-sharing-my-experiences.html)

There I found information about trying to get my tablet screen to rotate and all. There was some stuff about installing Wacom drivers, but the pen already works right out of the box. I just need help making .bash files to rotate the screen and pen with the 3 functions if anyone is able to help, that would be great. I understand the provided link shows me how and all, but I didn't really know if I needed to follow all the instructions it gave me or anything, because the pen works already. I need to rotate the screen and pen to the right. help would be great. thanks!

---

### Post by dbowlin17 on 2010-06-18
alright, nevermind there. got issues with the fans not working properly. however using partedmagic or boot and nuke (clearing hard drive) have had no problems. i use ubuntu on my main machine and love it, what options do i have that are close?

---

### Post by Favux on 2010-06-18
Hi dbowlin17,

Really need to know what tablet pc and what ubuntu release.  I'll guess Lucid and stylus with two buttons and eraser.

That link is pretty old.  See methods 1 or 3 at the [rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").

Also with the model of tablet pc you can search the site for how to fix the fans.

---

### Post by dbowlin17 on 2010-06-19
fujitsu T4020D - and lucid. Yeah, i dunno whats goin on with that. someone posted on the bug report this past may (2010) saying it was still an issue. and i still have that issue too.

---

### Post by Favux on 2010-06-20
Hi dbowlin17,

I'd post on VXxed's bug report:  [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/461675](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/461675)  The more action there the more likely a response.

It looks like he tried a lot on his thread:  [http://ubuntuforums.org/showpost.php?p=8163031&postcount=1](http://ubuntuforums.org/showpost.php?p=8163031&postcount=1)

First thing I'd check is the bios at the Fujitsu site and make sure you're up to date.

Then I'd try one of the kernel line options like acpi_osi="force"" and see if you get lucky:  [http://swiss.ubuntuforums.org/showpost.php?p=9310596&postcount=8](http://swiss.ubuntuforums.org/showpost.php?p=9310596&postcount=8)

---

### Post by Mark Phelps on 2010-06-20
> **Favux said:**
>  ... First thing I'd check is the bios at the Fujitsu site and make sure you're up to date...

That machine is at least five years old and Fujitsu hasn't issued any updates in all that time.

Plus, I have one of those, and no version of Ubuntu since 8.04 has worked properly on it.  Pen detection works, but that's about it.

---

### Post by dbowlin17 on 2010-06-20
so basically run windows 7. its too much work to get 8.04 to like my pen. oh well.

---

