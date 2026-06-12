---
title: "Garmin sat nav and exe file"
date: 2010-08-24
forum: General Help
---

### Post by fidelandche on 2010-08-24
Hi all,

Just bought a Garmin 250W Sat Nav and I need to connect it to my laptop so I can update the maps and safety cameras. The problem is the plugin I need is an exe file:mad: is there any way I can install this so the Sat Nav and the Garmin website can communicate?? (I know that an exe file is for M$)

---

### Post by fidelandche on 2010-08-25
Ok after a bit of "Goggling" I installed Wine. I downloaded firefox for M$ and the communicator plugin from Garmin and tried to install but each time I tried to install with Wine I just get error messages and it appears that these exe files are non exe files? which appears odd as they are from Garmin and Mozilla so they are not going to have Malware or a virus in them. 

 So has any one any ideas of where I go now.

---

### Post by Vaphell on 2010-08-25
what does it say exactly when you try to install with wine?

---

### Post by fidelandche on 2010-08-25
This is what I get when I try and install Firefox for M$

[IMG]http://lh6.ggpht.com/_thhSoVyjMZ0/THVgLhyK_-I/AAAAAAAAAUQ/R-7wCSbGC3E/Screenshot.png[/IMG]

 And this what I get when I try to install the communicator plugin

[IMG]http://***************/_thhSoVyjMZ0/THVg3mLst7I/AAAAAAAAAUU/xwOWMJ5_40k/Screenshot2.png[/IMG]

---

### Post by Vaphell on 2010-08-25
right click and in properties tick 'mark as an executable'
you see, in linux files can be executed not because they have some defined extension like .exe in windows, but because they have have the executable flag set and files don't have that set by default - it's a security thing.

2nd embedded pic has domain name starred out by the forum for some reason, so the link is kinda useless :)

---

### Post by fidelandche on 2010-08-26
Sorry about that, the message is just the same but states that the communicator plugin is not marked as executable.

 On another point when I install Wine, do I just install from the repos? and then when it is installed do I have to do anything to configure it? Because as I am using Xubuntu it is in applications - other.  When I click on other it states configure Wine, when I click on that do I have to add Firefox and the communicator plugin?

---

### Post by fidelandche on 2010-08-26
This is what I get when I right click on properties, so not sure where to mark it executable.

[IMG]http://lh5.ggpht.com/_thhSoVyjMZ0/THZwSKC6z6I/AAAAAAAAAUc/vIspRfgxsYE/Screenshot.png[/IMG]

---

### Post by Vaphell on 2010-08-26
permissions tab

---

### Post by fidelandche on 2010-08-26
Ok, I have sorted that out, now the problem is the communicator plugin will not work! When I connect the Sat Nav the Garmin website/communicator does not find the Sat Nav. It appears that I need USB drivers installed. Is there any way of installing USB drivers (which are ones for M$) on Xbuntu?

---

