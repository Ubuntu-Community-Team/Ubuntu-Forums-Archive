---
title: "Having major newbie problems with some packages I tried to install."
date: 2011-01-26
forum: General Help
---

### Post by grant_in_the_box on 2011-01-26
I attempted to install msttcorefonts using the command 'sudo apt-get install msttcorefonts' something happened during the process. To get to the point, all my fonts in firefox are messed up (to the point that i can't read them). In the terminal, i'm getting an error that says 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem

I don't really understand any of this yet. Can somebody please help me?:confused:

---

### Post by QLee on 2011-01-26
> **grant_in_the_box said:**
> I attempted to install msttcorefonts using the command 'sudo apt-get install msttcorefonts' something happened during the process. To get to the point, all my fonts in firefox are messed up (to the point that i can't read them). In the terminal, i'm getting an error that says 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem

I don't really understand any of this yet. Can somebody please help me?:confused:
What it means is that you must manually run 'sudo dpkg --configure -a'. In other words, open a terminal window and enter the given command.


[Edit] If it doesn't complete successfully, post any error message it gives.

---

### Post by rocthrttle on 2011-01-26
> **QLee said:**
> What it means is that you must manually run 'sudo dpkg --configure -a'. In other words, open a terminal window and enter the given command.

highlight and copy "sudo dpkg --configure -a"
open terminal under applications>accessories>terminal
right click menu paste the command
hit enter
should prompt for your password

or 

alt+F2 and paste the command there 
with the "run in terminal" box checked
should prompt for your password

---

### Post by grant_in_the_box on 2011-01-26
It ran the update but it took me to the same screen that it messed up at last time. Here is a screen shot

[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-ash1/hs897.ash1/180562_184629678237588_100000716711534_506077_6579125_n.jpg[/IMG]

Here is a shot of what it did to my Firefox


[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-snc6/hs272.snc6/180038_184629618237594_100000716711534_506076_971602_n.jpg[/IMG]

---

### Post by Vaphell on 2011-01-26
images are missing

---

### Post by grant_in_the_box on 2011-01-26
_the solution was to re-run the program and use the -tab- button to select <ok> at the end_[]("http://sphotos.ak.fbcdn.net/hphotos-ak-snc6/hs272.snc6/180038_184629618237594_100000716711534_506076_971602_n.jpg")

---

### Post by Krytarik on 2011-01-26
Run the same command again, press "Tab" to select <Ok>, then press enter, it should finish the configuration then.

---

### Post by grant_in_the_box on 2011-01-26
Thank You!! It's amazing how simple the solution can be sometimes.....

---

