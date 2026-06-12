---
title: "Grub(i think) Error"
date: 2010-11-15
forum: General Help
---

### Post by Zachist on 2010-11-15
SOLVED




Ok, so normally when i start my computer it says "CD-Rom Boot: No medium" or something very similar. 
yesterday i installed a Dual-Boot linux set with ubuntu and windows vista.

The first time i did it it booted into the GRUB menu just fine, i selected ubuntu , it loaded and worked just fine.

Today i needed to load into vista, so i was in the GRUB menu and selected "Windows Vista (LOADER)"

and it came up to a loading screen (that i have never seen) saying Please wait while windows loads files. and it had a gray bar. then it went to the normal windows vista loading screen, so im like ok were all good.

Then it came up with  gray screen and the words PLEASE WAIT

and it came up with EMACHINES RECORVERY MANAGEMENT or something.

it gave me 2 options but the only selectable one was EXIT.


i clicked it and restarted my computer

Now it says the whole"No medium" thing but it also says


"Error: No such partition
Grub Rescue>"


I HAVE NO IDEA WHAT TO DO.

its my parents computer and i need a fix or atleast need to know something about it fast (prefrebaly in the next 1hr and a half (comptuer app class)

Please help me out here
thnx

---

### Post by drs305 on 2010-11-15
Zachist

Welcome to the Ubuntu forums.

Boot an Ubuntu LiveCD and go to this site and download/run the boot info script. The instructions are on the page:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Copy the contents of RESULTS.txt, then paste them between "code" tags, which you generate by pressing the # icon in the post's menubar.

The script will tell us how your boot files are set up and should allow us to restore your system fairly quickly.

---

### Post by Zachist on 2010-11-15
I dont have internet  on the comptuer that this is happening on, and im in a computer app class right now at school, i still have the rest of the day, :/

---

### Post by mr clark25 on 2010-11-15
> **Zachist said:**
> I dont have internet  on the comptuer that this is happening on, and im in a computer app class right now at school, i still have the rest of the day, :/

unless you want to take the hard way, we are going to need a way to get files on that computer.

the grub fixing script in my signature should work if you know the answers to the questions it asks. (if you run that boot-info script, we can help you answer them)

---

### Post by Zachist on 2010-11-15
The only Operating system i can boot into is ubuntu, but the only internet i have is a verizon aircard, and i cant do anything becasue u need a cd to install it, my sister has the CD, so i dont have any internet..... ughh.... i cant think of any other way, until i get internet...?

:/ i have a feeling im making this difficult

---

### Post by Hippytaff on 2010-11-15
Can't you use a usb pendrive to transfer the script to the ubuntu box, run the script, save the RESULTS.TXT to the pendrive and post it here on from the box that does have access.

---

### Post by matt_symes on 2010-11-15
Hi

> im in a computer app class right now at school.Cant you use another computer at school at download the script and instructions? Or a friend?

Copy to a USB stick and mount from the liveCD?

EDIT: HappyTaff you beat me to it :)

Kind regards

---

### Post by Zachist on 2010-11-15
> **Hippytaff said:**
> Can't you use a usb pendrive to transfer the script to the ubuntu box, run the script, save the RESULTS.TXT to the pendrive and post it here on from the box that does have access.


I didnt even think of that, i have to do it tomorrow, i dont have my pendrive with me right now, ill get that tomorrow or later today and then ill report back what happens.. Thanks if it works and if it dosent atleast u tryed. :/

---

### Post by Zachist on 2010-11-16
Solved, what happened was that GRUB named my partitions wrong and it named my VISTA partition as my recovery, so when i booted vista it really booted my recovery and this deleted my ubuntu drive, so now i know which one to boot and every thing is rtunning smoothly, thanks for the help!

---

### Post by Hippytaff on 2010-11-16
Glad its sorted - just in case you were wondering you can mark the thread as solved in the Thread tools at the top of the page. :-)

---

