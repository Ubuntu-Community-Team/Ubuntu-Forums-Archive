---
title: "Laggy, choppy streaming videos on Ubuntu 11.04"
date: 2011-10-05
forum: General Help
---

### Post by Ulysses1994XF04 on 2011-10-05
So I installed Ubuntu last night. It seemed to be working fine, but when I go on websites that have streaming video (usually Adobe Flash) the video is really laggy and choppy, even when I set the setting to Lowest. 

Are there any easy fixes to this? I've tried looking for some, but they all seem to require long streams of commands and I don't know anything about programing. I'm afraid of screwing up and messing up my computer.

---

### Post by mikewhatever on 2011-10-05
You should post some more info:

What version of Adobe Flash did you install?

32bit or 64bit?

What are the specs of the computer?

---

### Post by Ulysses1994XF04 on 2011-10-05
It appears the version of Adobe Flash I installed was 10,3,183,10.

I have an Asus Eee PC 1001 PXD netbook; 1.66 GHz, 250 GB HD, 1 GB RAM.

What exactly do you mean by "32bit or 64bit?"

---

### Post by HermanAB on 2011-10-05
Howdy,

Use htop and ntop to figure out whether the problem is processor bound or network bound.

---

### Post by Ulysses1994XF04 on 2011-10-05
> **HermanAB said:**
> Howdy,

Use htop and ntop to figure out whether the problem is processor bound or network bound.

Sorry; what's htop and ntop?

I don't think it's network related; I have another, older laptop with Ubuntu 10.04 and the video streams fine.

---

### Post by Ulysses1994XF04 on 2011-10-05
bump

---

### Post by lovinglinux on 2011-10-05
Please wait at least 24 hours to bump a thread.

Unfortunately, flash doesn't perform well on Linux, due to various reasons. First, it doesn't play well with Compiz, which is the application responsible for all the cool 3D animations on your desktop. Also because, depending on your graphics card and video driver, sometimes it can't make use of hardware acceleration. Make sure you have the latest driver installed. You can do that through Jockey application, which is probably listed in your applications list as "Additional Drivers". If you have a recent nVidia card, you can also install vdpau through Software Center, which will allow the graphics card to do the hard work of decoding videos.

If your flash is stuttering, most likely it is using the CPU for processing. Try [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) extension for Firefox. It allows you to remove conflicting plugins, install the latest Beta flash version and apply some performance tweaks. For instructions see [http://www.webgapps.org/add-ons/flash-aid/documentation](http://www.webgapps.org/add-ons/flash-aid/documentation)

If that doesn't solve the problem see [http://www.webgapps.org/tutorials/firefox/optimization/flash-optimization](http://www.webgapps.org/tutorials/firefox/optimization/flash-optimization)

---

### Post by Ulysses1994XF04 on 2011-10-06
> **lovinglinux said:**
> Please wait at least 24 hours to bump a thread.

Unfortunately, flash doesn't perform well on Linux, due to various reasons. First, it doesn't play well with Compiz, which is the application responsible for all the cool 3D animations on your desktop. Also because, depending on your graphics card and video driver, sometimes it can't make use of hardware acceleration. Make sure you have the latest driver installed. You can do that through Jockey application, which is probably listed in your applications list as "Additional Drivers". If you have a recent nVidia card, you can also install vdpau through Software Center, which will allow the graphics card to do the hard work of decoding videos.

If your flash is stuttering, most likely it is using the CPU for processing. Try [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") extension for Firefox. It allows you to remove conflicting plugins, install the latest Beta flash version and apply some performance tweaks. For instructions see [http://www.webgapps.org/add-ons/flash-aid/documentation](http://www.webgapps.org/add-ons/flash-aid/documentation)

If that doesn't solve the problem see [http://www.webgapps.org/tutorials/firefox/optimization/flash-optimization](http://www.webgapps.org/tutorials/firefox/optimization/flash-optimization)

I tried Flash Aid, but when I installed it and ran it, all it seemed to do was remove Adobe Flash from my system. I couldn't watch flash videos. I had to reinstall it and now I'm back to square one.

---

