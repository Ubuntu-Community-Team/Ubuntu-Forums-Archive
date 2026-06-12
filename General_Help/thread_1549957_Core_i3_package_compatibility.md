---
title: "Core i3 package compatibility"
date: 2010-08-10
forum: General Help
---

### Post by varunmagical on 2010-08-10
Hello guys,

Are ubuntu- 64 bit packages I am using on my core 2 duo desktop compatible with core i3?
I am thinking of buying new core i3 laptop as I am moving to new city .. 

I will not be having fast Internet access ( GPRS ), So I will be using the downloaded deb packages (In var/cache/apt) to install softwares I need whenever I format my laptop ( I experiment a lot, So I format a lot )

Will it work?

---

### Post by Darkness Des on 2010-08-10
My laptop uses two i3 Processors (64 bit) and I have no issues. Just make sure that the computer with the i3 in it is 64 bit.

---

### Post by varunmagical on 2010-08-10
> **Darkness Des said:**
> My laptop uses two i3 Processors (64 bit) and I have no issues. Just make sure that the computer with the i3 in it is 64 bit.
I am using 64 bit lucid on my desktop ... all core i3 processors are 64-bit. Right?

---

### Post by TBABill on 2010-08-10
And if you plan to use the on-board graphics (GPU/CPU combo) don't you need kernel 2.6.33 or newer to support it? If it uses another graphics chip, not a big deal.

---

### Post by schwabdale on 2010-08-10
I have a Vaio with an I3. To get lucid to see all the hardware I had to install 2.6.34. Not sure if its 64 bit or not.

---

### Post by TBABill on 2010-08-10
I did try mine with kernel 2.6.32 and it kept freezing so I had to hard restart after about 20 seconds of operation. I knew what the cause was, just wanted to see what effect it would have trying to run the older kernel. I'm using PCLinuxOS till Ubuntu 10.10 with a later kernel on the machine with the i3.

---

### Post by mister_playboy on 2010-08-10
One thing to be aware of is that Core i3s all lack Intel's VT-x virtualization extensions.

---

