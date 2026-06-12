---
title: "Firefox 3.5 not displaying some images properly"
date: 2009-07-07
forum: General Help
---

### Post by kallu_be on 2009-07-07
Firefox 3.5 is not displaying images properly. Below are some of the samples compared with firefox 3.0 (right window). Is there any build other than fta ppa that provides firefox 3.5 builds.

[[IMG]http://img199.imageshack.us/img199/3108/snapshot1c.th.png[/IMG]](http://img199.imageshack.us/i/snapshot1c.png/)

[[IMG]http://img9.imageshack.us/img9/4818/snapshot2vqd.th.png[/IMG]](http://img9.imageshack.us/i/snapshot2vqd.png/)

[[IMG]http://img145.imageshack.us/img145/6448/snapshot3.th.jpg[/IMG]](http://img145.imageshack.us/i/snapshot3.jpg/)

[[IMG]http://img13.imageshack.us/img13/4964/snapshot4d.th.jpg[/IMG]](http://img13.imageshack.us/i/snapshot4d.jpg/)

---

### Post by abhi_69 on 2009-07-07
there is another PPA for firefox 3.5. it is called "ubuntu-mozilla-security" PPA. u can enable this PPA & install firefox 3.5 from it according to this-
[http://www.ubuntusolutions.org/2009/07/ubuntu-firefox-3-5-install-use-ubuntu-mozilla-security.html](http://www.ubuntusolutions.org/2009/07/ubuntu-firefox-3-5-install-use-ubuntu-mozilla-security.html)
its much safer & easier than fta PPA. u can try it.
BTW, this tutorial is for ubuntu 9.04 jaunty. u should replace it with ur current ubuntu version.
try it........

---

### Post by H3g3m0n on 2009-07-07
This could be because the new Firefox has support for colour management enabled by default. It's possible the images are at fault with incorrect colour management information, or some bug in it still (even though its been in experimentally, but disabled since 3.0)

You could try disabling it: [http://www.robgalbraith.com/bins/content_page.asp?cid=7-9311-9478](http://www.robgalbraith.com/bins/content_page.asp?cid=7-9311-9478)

Those are instructions for enabling it, just change true to false, seems to be disabled by default for me though, but maybe its because I'm using an old profile.

---

### Post by kallu_be on 2009-07-07
> **H3g3m0n said:**
> This could be because the new Firefox has support for colour management enabled by default. It's possible the images are at fault with incorrect colour management information, or some bug in it still (even though its been in experimentally, but disabled since 3.0)

You could try disabling it: [http://www.robgalbraith.com/bins/content_page.asp?cid=7-9311-9478](http://www.robgalbraith.com/bins/content_page.asp?cid=7-9311-9478)

Those are instructions for enabling it, just change true to false, seems to be disabled by default for me though, but maybe its because I'm using an old profile.

Thanks for the link, its working fine now.

---

### Post by lovinglinux on 2009-07-07
> **H3g3m0n said:**
> This could be because the new Firefox has support for colour management enabled by default. It's possible the images are at fault with incorrect colour management information, or some bug in it still (even though its been in experimentally, but disabled since 3.0)

You could try disabling it: [http://www.robgalbraith.com/bins/content_page.asp?cid=7-9311-9478](http://www.robgalbraith.com/bins/content_page.asp?cid=7-9311-9478)

Those are instructions for enabling it, just change true to false, seems to be disabled by default for me though, but maybe its because I'm using an old profile.

Yes, it's color management, but most tutorials out there, including the one above, refer to **gfx.color_management.enabled** preference, which should not be present in Firefox 3.5. Maybe the problem is that those who are using old profiles still have this option. The current way of activating the color management can be found in the **Solution** [*[COLOR="Red"]**FOT007**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT007).

BTW, instead of deactivating it, you should enable color management for tagged graphics only, which means all images will display correctly, even if they don't have color profiles.

---

