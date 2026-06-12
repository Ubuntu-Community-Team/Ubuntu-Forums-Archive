---
title: "default temperature cutoffs for fan control on laptop?"
date: 2006-05-18
forum: General Help
---

### Post by nanotube on 2006-05-18
hey all
so on my laptop (dell inspiron 5150) the fan cuts on and off at certain temp cutoffs. specifically, at 50C, the fan turns off completely. 

i would like to keep my cpu a bit cooler than that, so i wonder how i can change that threshold to some other temperature. i thought it would be something to do with acpi, but could not find anything like that under /etc/acpi
i looked in the BIOS settings, and did not see anything there either. 

so, any help would be appreciated. thanks!

---

### Post by nanotube on 2006-05-18
bump? :)

---

### Post by hobbestec on 2006-05-18
There is a package called i8kutils that you can install with synaptic or apt-get.  It will let you control the fan on a dell laptop.  There is a readme about it available here: [http://people.debian.org/~dz//i8k/00-README](http://people.debian.org/~dz//i8k/00-README) - it looks like it does work on the 5150, but only ones with BIOS A24.

---

### Post by nanotube on 2006-05-19
[QUOTE=hobbestec]There is a package called i8kutils that you can install with synaptic or apt-get.  It will let you control the fan on a dell laptop.  There is a readme about it available here: [http://people.debian.org/~dz//i8k/00-README](http://people.debian.org/~dz//i8k/00-README) - it looks like it does work on the 5150, but only ones with BIOS A24.[/QUOTE]

hey hobbestec, 
thanks for your post - but i already have the i8kutils package, and it works just like advertised - i can manually tweak the status of the fans etc, and there is even a daemon-mode tool that can automatically turn the fan on/off for me. 
my question is specifically on where the /default/ ubuntu acpi temperature thresholds are, because i was thinking if i can tweak that, i can avoid running yet another daemon on top of everything else.

---

### Post by nanotube on 2006-05-22
bump.

---

### Post by s_h_a_d_o_w_s on 2006-05-22
Bump

---

### Post by karlseith on 2007-06-29
After running a Google search I came across this thread as I have the same concern about high temps on my Gateway 6510 Laptop. It appears that the fan is turned on at around 55C and off at 50C. I need to get the temp way down. There has to be a setting somewhere that can be adjusted I would think. Right?

---

### Post by nanotube on 2007-06-29
well, an update:
i have ended up just running the i8k daemon to set the custom temp controls.
the i8kutils package is for dell only, though, not sure if there's something similar for gateway, hp, etc...

---

### Post by zvadinov on 2007-09-16
Hello Nanotube,

I aktually have the Problem with the overheating of my Inspiron 5150
I have install all the i8k packeges but I dont know how to use them!
My Laptop is nonstop 55-70C° !
I've searched the Net but did not find any solution for me (im not a linux guru)
Would it be possible that you write i little How To .. the way you solved your problem!!

thanks in forward
zvadi

---

### Post by oilchangeguy on 2007-09-16
see this:
[http://www.roadtools.com/](http://www.roadtools.com/)
and this:
[http://www.amazon.com/Vantec-LapCool3-USB-Notebook-Cooling/dp/B000AGK8NI](http://www.amazon.com/Vantec-LapCool3-USB-Notebook-Cooling/dp/B000AGK8NI)

---

### Post by nanotube on 2007-09-16
> **zvadinov said:**
> Hello Nanotube,

I aktually have the Problem with the overheating of my Inspiron 5150
I have install all the i8k packeges but I dont know how to use them!
My Laptop is nonstop 55-70C° !
I've searched the Net but did not find any solution for me (im not a linux guru)
Would it be possible that you write i little How To .. the way you solved your problem!!

thanks in forward
zvadi

hi
read this, it will walk you through it: [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Temperature_and_Fan_Sensors](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Temperature_and_Fan_Sensors)

or this if you're using feisty:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles_Feisty#Temperature_and_Fan_Sensors](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles_Feisty#Temperature_and_Fan_Sensors)

---

