---
title: "Unetbootin unable to download"
date: 2010-10-07
forum: General Help
---

### Post by mikelaurenzana on 2010-10-07
So I ran the latest update and my system is up to date. I tried installing Unetbootin, but received this error message in terminal as well as package manager.

"E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory"

I am currently running 64 bit Unbuntu 10.04 on a Toshiba Qosmio X305-Q705.
Thanks.

---

### Post by e79 on 2010-10-07
Silly question probably, but in the terminal, have you typed 'sudo' before typing your commands ?
 
Example:
```
sudo apt-get update
```

---

### Post by Rubi1200 on 2010-10-07
> **mikelaurenzana said:**
> So I ran the latest update and my system is up to date. I tried installing Unetbootin, but received this error message in [COLOR=Red]terminal as well as package manager[/COLOR].

"E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory"

I am currently running 64 bit Unbuntu 10.04 on a Toshiba Qosmio X305-Q705.
Thanks.
This error message usually appears if you have more than one software package manager open. In other words, if you have the Software Center and Synaptic open or a terminal command and something it will fail. Close all instances and then try downloading and installing with just one package manager or only via the terminal.

---

### Post by e79 on 2010-10-07
> **Rubi1200 said:**
> This error message usually appears if you have more than one software package manager open. In other words, if you have the Software Center and Synaptic open or a terminal command and something it will fail. Close all instances and then try downloading and installing with just one package manager.
 
+1
I completely forgot about that one, good thing to remember  :P

---

### Post by mikelaurenzana on 2010-10-07
I wonder if I could be anymore of a Linux n00bie. Thanks guys.

---

