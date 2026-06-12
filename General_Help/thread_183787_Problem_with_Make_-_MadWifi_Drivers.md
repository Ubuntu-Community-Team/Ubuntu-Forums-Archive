---
title: "Problem with Make - MadWifi Drivers"
date: 2006-05-28
forum: General Help
---

### Post by evandec on 2006-05-28
I downloaded and unpacked all the drivers for madwifi. When I go to the directory and use the make comand I get the following error.

[quote] make: command not found [/quote}

Whats up with that?

I know I have a lot of questions but I am still making the transition and a lot of this stuff is new to me.

---

### Post by hw-tph on 2006-05-28
Is there any particular reason you need to install the madwifi drivers from source? They are included in the linux-restricted-modules package so for most cards it will not be necessary.

And to install the base development environment (compiler, make, C headers) simply type **sudo apt-get install build-essential**.

Håkan

---

### Post by evandec on 2006-05-28
[QUOTE=hw-tph]Is there any particular reason you need to install the madwifi drivers from source? They are included in the linux-restricted-modules package so for most cards it will not be necessary.

And to install the base development environment (compiler, make, C headers) simply type **sudo apt-get install build-essential**.

Håkan[/QUOTE]

Thanks, I will need the develpment to compile things anyway, but I thought I would need the drivers for my atheros card. How can I go about adding it if the drivers are already installed.

---

