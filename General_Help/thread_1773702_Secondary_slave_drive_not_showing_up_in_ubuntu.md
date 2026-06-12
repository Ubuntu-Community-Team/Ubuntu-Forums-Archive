---
title: "Secondary slave drive not showing up in ubuntu"
date: 2011-06-02
forum: General Help
---

### Post by Fouzan on 2011-06-02
Hello everyone, 

I just installed ubuntu, this is my first time with it so excuse my ignorance regarding it. My issue is that ubuntu does not show my secondary slave seagate hdd .. it only shows and installs on my western digital master primary one. I need to have access to my slave drive because it has data on it which i wanna use. 
My secondary slave shows up in my windows and bios just fine. So what gives?

Thank you for any help in advance.

---

### Post by SavageWolf on 2011-06-02
What is the output of "ls /dev/sd*"?

(Enter this in a terminal, I'm not sure how to get to it in Unity...)

---

### Post by jamesisin on 2011-06-02
SATE or IDE?  If it's IDE check your jumpers.

Have you mounted the drive?

[http://jamesisin.com/a_high-tech_blech/index.php/2009/01/ubuntu-gets-a-second-friend/](http://jamesisin.com/a_high-tech_blech/index.php/2009/01/ubuntu-gets-a-second-friend/)

(I need to rewrite that article so sorry if it's a bit confusing.)

---

### Post by Fouzan on 2011-06-02
It wasnt showing up in the terminal output i tried that. Its IDE and its properly connected and working in windows XP. 

I am reinstalling ubuntu atm ... via the windows installer once its finished i will go through the whole mounting thing then. However ubuntu never shows it as being connected to the PC so i doubt if mounting is an issue?

---

### Post by jamesisin on 2011-06-02
Are you using Wubi?

What do you mean when you write "ubuntu never shows it as being connected to the PC"?  It won't show in many respects without having been mounted.

Post the output that SavageWolf asks for above.

---

### Post by Fouzan on 2011-06-02
Yes i am using Wubi and now its stuck at creating virtual disks for the past 3 hours ... ??? This is turning out to be a big bother now. 

What i meant by "ubuntu never shows it as being connected to the PC" is that i got that output when ubuntu was installed that savagewolf asked for and it never listed my slave drive, so i'm assuming that its not recognizing it as being connected to the PC because it listed my other HDD and USB drives.

---

