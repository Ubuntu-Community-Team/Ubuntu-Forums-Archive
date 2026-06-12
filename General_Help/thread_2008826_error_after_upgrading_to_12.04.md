---
title: "error after upgrading to 12.04"
date: 2012-06-23
forum: General Help
---

### Post by austinino12 on 2012-06-23
Hello everybody I'm facing an error with ubuntu 12.04 which I recently upgraded to. Now just to let you know I have almost no idea on anything about linux its just what the computer I bought had on it. When I turn my computer on it goes to the start up screen the grub menu I believe its called. After that it goes to a black screen with white text flashing on it. I took a picture of it with my phone and I will attach It to the post. Basically the white text says something about ushare and checking battery state. But after sitting on that screen for a while it goes to a screen saying the system is running in low graphics mode. Your screen, graphics card, and unput device settings could not be detected correctly. You will need to configure these yourself. And there's an option for ok. I have been suffering this problem for about several hours. Sorry for the bad typing and grammar I'm posting this from my blackberry. Thanks for reading and trying to help

---

### Post by grahammechanical on 2012-06-23
Do you get to a desktop? If so open the Dash and search for Additional Drivers and see if it offers a proprietary driver for you to install.

It would also be useful if you told us the specification of your hardware.

Regards.

---

### Post by austinino12 on 2012-06-23
There's not much more I can tell you since I don't know much. But I can tell you that I can select run in low graphics mode for one session once I do that I get a black screen with the bar at the top with the time. Also a bunch of screens come up saying stuff about application errors and asking if I want to relaunch them. These programs are things like jockey and medacity. Also I can access the terminal is there any commands I can use to fix this. I just figure out I'm running itel corporation integrated graphics card. 
Thanks so much.

---

### Post by philinux on 2012-06-23
> **austinino12 said:**
> There's not much more I can tell you since I don't know much. But I can tell you that I can select run in low graphics mode for one session once I do that I get a black screen with the bar at the top with the time. Also a bunch of screens come up saying stuff about application errors and asking if I want to relaunch them. These programs are things like jockey and medacity. Also I can access the terminal is there any commands I can use to fix this. I just figure out I'm running itel corporation integrated graphics card. 
Thanks so much.

Open a terminal.

Do these one at a time and note any errors.

sudo apt-get update 

sudo apt-get upgrade

---

