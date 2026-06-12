---
title: "Resolution gets reset everytime on reboot after Nvidia."
date: 2010-03-23
forum: General Help
---

### Post by Laxman_prodigy on 2010-03-23
I installed Nvidia 195 version from their site and installed as per their instruction.

Now, on reboot the resolution gets "800*600" while it should be "1366*768".

What should I do?:(

---

### Post by Laxman_prodigy on 2010-03-23
Also, I am fed up with trying to enable vdpau support for enhanced playback.

How can I get vdpau support from this driver through Mplayer or VLC? 

My card is 8500GT and I have installed Ubuntu 9.10 64 bit.

Please guide me in detail wherever possible.

---

### Post by Laxman_prodigy on 2010-03-23
Please do reply soon.:)

---

### Post by linden940 on 2010-03-23
you need to update your graphics card and then USE the graphics card to make the resolution setting

do it in sudo with this

```
gksudo nvidia-settings
```

---

### Post by Laxman_prodigy on 2010-03-24
> **linden940 said:**
> you need to update your graphics card and then USE the graphics card to make the resolution setting

do it in sudo with this

```
gksudo nvidia-settings
```


Thank you linden940.

I did it and "Nvidia Xserver settings pops out.


How do I update now and set the resolution?

---

### Post by Laxman_prodigy on 2010-03-24
Anybody?

---

### Post by selfcommander on 2012-04-25
this post [http://ubuntuforums.org/showpost.php?p=7490352&postcount=2](http://ubuntuforums.org/showpost.php?p=7490352&postcount=2) fixed it for me

---

