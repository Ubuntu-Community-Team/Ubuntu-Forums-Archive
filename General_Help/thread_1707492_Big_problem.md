---
title: "Big problem"
date: 2011-03-15
forum: General Help
---

### Post by getter on 2011-03-15
Hello: ):P

I'm from Spain and my english level is not very high so please, understand my poor post.

I'm posting here because in the oficial spanish ubuntu forum there are nobody that can help me. I'll try to resume my problem:

I try to use 10.04 when it was released. In 10 minutes, the system freezes. I try one more time but it still freezing. I take a look to the logs but there is not any information or any warning. When the 10.10 was launched i try it again but i had the same result: In random time the system freezes. Anytimes only the keyboard and mouse freezes but sometimes is the all system. I try Kubuntu too to see if the gnome system had the problem but it still freezing. Two weeks ago i try Opensuse, Mandriva, Debian and other OS and my surprise was very big: The problem of freezes exist in this OS too.

Anybody have any idea why it is happening? In 11.04 Beta 3 the system freezes too.

I try a lot of solutions that i see in the web but no one works.

My system info is:

ASUS P7P55 LX
Intel i5 750 @ 2.67
4Gb Ram
Nvidia GForce GTX 460
HDD ST3500418AS (500GB)

Thanks for any help :KS .

---

### Post by oldos2er on 2011-03-15
The fact that this is happening in every OS points to a possible hardware problem. From the grub boot menu, run memtest, and let it run overnight if you can. Also run fsck on your partitions, which is easiest to do from a LiveCD if you have one.

---

### Post by r-senior on 2011-03-15
To add to the suggestion about hardware problems: check all your fans are OK.

---

### Post by getter on 2011-03-15
> **oldos2er said:**
> The fact that this is happening in every OS points to a possible hardware problem. From the grub boot menu, run memtest, and let it run overnight if you can. Also run fsck on your partitions, which is easiest to do from a LiveCD if you have one.

Ok, i'll do this night while i study and i will post the results here.

[QUOTE=r-senior]To add to the suggestion about hardware problems: check all your fans are OK.[/quote]

I have a 35 cm fan and a 25 cm fan and it all ok. Also the graphic card and motherboard had a heat dissipator.

---

### Post by Script Warlock on 2011-03-15
i also suggest to check and clean your rams(you can use eraser) and detach some hardware leaving only motherboard, ram, keyboard, mouse and power supply.

---

### Post by getter on 2011-03-15
Script Warlock, i do that and nothing happens.

I forget to say that 9.10, 9.04 and older works perfect.

---

### Post by sdowney717 on 2011-03-15
as a test, you could try the latest ubuntu NN which will go into beta soon.

---

### Post by sdowney717 on 2011-03-15
as a test, you could try the latest ubuntu NN which will go into beta soon.
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

---

### Post by Script Warlock on 2011-03-15
> **getter said:**
> Script Warlock, i do that and nothing happens.

I forget to say that 9.10, 9.04 and older works perfect.

have you tried the live cd or usb? does it work flawless?

---

### Post by getter on 2011-03-15
> **Script Warlock said:**
> have you tried the live cd or usb? does it work flawless?

It freezes too. The first time i install 10.10 it freezes during installation.

---

### Post by r-senior on 2011-03-15
> **getter said:**
> I have a 35 cm fan and a 25 cm fan and it all ok. Also the graphic card and motherboard had a heat dissipator.
You have a 35cm (14") fan in your computer? :shock:

---

### Post by Script Warlock on 2011-03-15
did you tried removing the videocard and use the built-in vc of your mobo during installation? and also have you observed the vc fan if its running normally or something?...

i'm sure theres nothing wrong with the OS unless you have downloaded a faulty iso.

---

### Post by getter on 2011-03-15
> **Script Warlock said:**
> did you tried removing the videocard and use the built-in vc of your mobo during installation? and also have you observed the vc fan if its running normally or something?...

i'm sure theres nothing wrong with the OS unless you have downloaded a faulty iso.

But the VC works fine with windows xp and 9.XX. The VC have not fan, it have a heat dissipear.

> **r-senior said:**
> You have a 35cm (14") fan in your computer? :shock:

Yeah, it's a modding case.

---

