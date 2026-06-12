---
title: "Compiz issues"
date: 2012-06-09
forum: General Help
---

### Post by Hiuhu on 2012-06-09
I recently installed compiz in PC & now when I startup compiz my desktop displays only the background. What could be the problem ?

---

### Post by deadflowr on 2012-06-09
Can you open a terminal by using ctrl+atl+T?
If so, compiz is probably broken.
What is your graphics card? As there are known issues ans bugs surrounding several graphics cards, and compiz.
If you can access a terminal, type lspci | grep VGA to find out what graphic card you have. Post back any relevant info as we can then proceed from there.

[http://ubuntuforums.org/showthread.php?t=1006656]("http://ubuntuforums.org/showthread.php?t=1006656")

This is a very good thread on how to post on the forums.

---

### Post by Hiuhu on 2012-06-09
Ok. Yeah I can access only the terminal. And when I run the command this is what I get:
hiuhu@AMG ~ $ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)

---

### Post by deadflowr on 2012-06-09
Silly question, but what system are running?(ie Ubuntu12.04)
And if Ubuntu, why did you install compiz? Compiz is built into Ubuntu by default.

---

### Post by thespi on 2012-06-09
I am having a similar problem. I just installed ubuntu 12.04LTS and it goes to a command prompt, but at first it said "compiz stopped working", and "internal problem".

also:
00:05.0 VGA compatible controller: NVIDIA Corporation C51 [GeForce 6150 LE] (rev a2)

---

### Post by Hiuhu on 2012-06-10
Am using linux mint 12. So I had to install it cz its not installed by default

---

### Post by deadflowr on 2012-06-10
> **thespi said:**
> I am having a similar problem. I just installed ubuntu 12.04LTS and it goes to a command prompt, but at first it said "compiz stopped working", and "internal problem".

also:
00:05.0 VGA compatible controller: NVIDIA Corporation C51 [GeForce 6150 LE] (rev a2)

There are bug reports for the issue you are facing

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/990730]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/990730")
Unfortunately, this bug is an nvidia bug and cannot be resolved by the Ubuntu developers.
There are workarounds, such as logging into unity2d(which doesn't use compiz)Simply click on the cog/ubuntu icon next to your login name in the login screen and select unity2d.
Another solution, which I personally don't recommend, is to purge the existing drivers and install an older version from the nvidia website(I know that version 249.20 works). I don't recommend this because doing so will mean you'll have to keep up and update the drivers yourself, where as installing from the repos will get the updates automatically. And the probability of messing up the installation is high.


> **Hiuhu said:**
> Am using linux mint 12. So I had to install it cz its not installed by default

You  must have a reason for installing compiz on a system that doesn't use it.What is it?
(There is solid reason why compiz isn't installed in mint, because it would cause conflicts with the existing windows manager)

---

