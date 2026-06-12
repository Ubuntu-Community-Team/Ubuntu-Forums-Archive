---
title: "how do I do it? (howto go to plugins folder)"
date: 2010-09-24
forum: General Help
---

### Post by ieBrazil on 2010-09-24
"Installation

Installation of the Flash preview has to be done manually – but this isn’t that difficult.

    * Unpackage the file.
    * Copy the libflashplayer.so file to the plugins folder of your browser:
          o /usr/lib/mozilla/plugins/"

I've already download the said file. It's on my desktop area. But I just dont know where to go in order to copy the file on the said folder.

So, where or how do I do it in order to finish the job???

My browser is M. Firefox.

Tnx in advance.

---

### Post by oldos2er on 2010-09-24
If libflashplayer.so is on your desktop, ```
cd Desktop
sudo cp libflashplayer.so /usr/lib/mozilla/plugins
```

---

### Post by lovinglinux on 2010-09-25
Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

It will keep your 64bit flash updated, as long as you regularly update your Firefox extensions.

---

### Post by ieBrazil on 2010-09-28
> **oldos2er said:**
> If libflashplayer.so is on your desktop, ```
cd Desktop
sudo cp libflashplayer.so /usr/lib/mozilla/plugins
```


hummm it says "Not found"! But i can it on my desktop!

---

### Post by lovinglinux on 2010-09-28
> **ieBrazil said:**
> hummm it says "Not found"! But i can it on my desktop!

Read my previous post. Can't get easier than that.

---

### Post by oldos2er on 2010-09-28
> **ieBrazil said:**
> hummm it says "Not found"! But i can it on my desktop!

Can you post the output of **ls ~/Desktop** ?

---

### Post by ieBrazil on 2010-09-28
Lovinglinux, have I ever told you 'you're the one'?

So here I go: you are the one... tu és o melhor!

Valeu, meu!

Warm hugs from RS... it's so nice to know you're Brazilian too :-)

Bye!



igc


> **lovinglinux said:**
> Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version accordaving to your browser architecture.

It will keep your 64bit flash updated, as long as you regularly update your Firefox extensions.

---

### Post by lovinglinux on 2010-09-28
> **ieBrazil said:**
> Lovinglinux, have I ever told you 'you're the one'?

So here I go: you are the one... tu és o melhor!

Valeu, meu!

Warm hugs from RS... it's so nice to know you're Brazilian too :-)

Bye!



igc

You are welcome :)

BTW, I just released version 1.0.14, which allows to install flash 64bit preview 2 (codename square).

---

### Post by ieBrazil on 2010-10-01
Hi. Tnx for the additional information.
You could very well be wondering 'why this gaucho fellow do not donate some bucks to Lovinglinux, anyway, through website?'

I just would like to inform you that my financial condition is not a good one nowadays :-(

But things will get better on my side. Sure! Then I'll remember you.

Ok. Bye!

ieBrazil

> **lovinglinux said:**
> You are welcome :)

BTW, I just released version 1.0.14, which allows to install flash 64bit preview 2 (codename square).

---

### Post by lovinglinux on 2010-10-01
> **ieBrazil said:**
> Hi. Tnx for the additional information.
You could very well be wondering 'why this gaucho fellow do not donate some bucks to Lovinglinux, anyway, through website?'

I just would like to inform you that my financial condition is not a good one nowadays :-(

But things will get better on my side. Sure! Then I'll remember you.

Ok. Bye!

ieBrazil

No problem at all. You don't need to justify yourself. Donations are nice, but not the primary motivation for creating those extensions. A nice feedback like you did or a good review is also very welcome and supportive.

---

