---
title: "Can't boot any ubuntu due to hdd, help."
date: 2011-07-13
forum: General Help
---

### Post by Timill on 2011-07-13
Hi there, I have a dead hdd in my laptop, so I thought i'd be able to at least run a ubuntu livecd but whenever I try to boot my ubuntu 10.04 cd it fails. What happens is the purple screen with two icons at the bottom shows up, (like usual) and then the little underscore flashes for a while, but the an @ sign shows up in the left corner and does nothing after that. While it's doing this it allows me to type. So I was wondering if there's any commands I can type to tell ubuntu to ignore the dead hdd and boot so I can get the live cd going? I also tried booting my 9.10 disc into livecd mode but it gives me an infinite cycle of 'dev/sda i/o error'. I also looked for a way to disable my hdd in the bios but there isn't one. So there are any commands I can use while 10.04 is booting that would be great. Sorry for paragraphs but i'm writing this on a PSP.

---

### Post by wildmanne39 on 2011-07-13
> **Timill said:**
> Hi there, I have a dead hdd in my laptop, so I thought i'd be able to at least run a ubuntu livecd but whenever I try to boot my ubuntu 10.04 cd it fails. What happens is the purple screen with two icons at the bottom shows up, (like usual) and then the little underscore flashes for a while, but the an @ sign shows up in the left corner and does nothing after that. While it's doing this it allows me to type. So I was wondering if there's any commands I can type to tell ubuntu to ignore the dead hdd and boot so I can get the live cd going? I also tried booting my 9.10 disc into livecd mode but it gives me an infinite cycle of 'dev/sda i/o error'. I also looked for a way to disable my hdd in the bios but there isn't one. So there are any commands I can use while 10.04 is booting that would be great. Sorry for paragraphs but i'm writing this on a PSP.Hi, here is a link that should get you into ubuntu with the livecd of 10.04, you will need to use one of the boot parameters like nomodeset.
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by Timill on 2011-07-13
But it doesn't even get far enough along in the boot process to display that screen.

---

### Post by wildmanne39 on 2011-07-13
> **Timill said:**
> But it doesn't even get far enough along in the boot process to display that screen.Hi, have a look at this link I think it explains it better, the first part is for booting from a livecd.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Timill on 2011-07-13
Thankyou that link explained things better now I know how to get onto that screen, but I still don't know which option/command will help me bypass the dead hdd.

---

### Post by wildmanne39 on 2011-07-13
> **Timill said:**
> Thankyou that link explained things better now I know how to get onto that screen, but I still don't know which option/command will help me bypass the dead hdd.
Hi, it is not a problem with by passing the hard drive it is probably a video card driver issue not letting the cd load all the way. You should start by trying nomodeset, if that does not work try another one of the options on that page.

---

### Post by Timill on 2011-07-13
It's not the video card ubuntu livecd was working till my hdd died.

---

### Post by wildmanne39 on 2011-07-13
> **Timill said:**
> It's not the video card ubuntu livecd was working till my hdd died.Hi, did you try what the link mentioned?

---

### Post by Timill on 2011-07-13
None of it helped I still need some boot parameter so that the boot process doesn't get stuck on the '_@' and hang.

---

