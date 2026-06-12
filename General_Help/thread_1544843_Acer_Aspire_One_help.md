---
title: "Acer Aspire One help"
date: 2010-08-03
forum: General Help
---

### Post by Twizlerr on 2010-08-03
Hello. I am currently using an Acer Aspire One 751h. I know this has been posted before, but I still can't seem to get this to work. 
First, the default resolution is not correct. My Aspire One's resoultion is 1366x768, and the only option available is 1024x768. How can I change the resolution to 1366x768 if it is not an option out-of-the-box? 
Also, when scrolling down web pages, I noticed that it is visually....awkward. When I scroll down, it seems laggy. It looks as if the whole web page refreshes every time I scroll down, or if it has a very low FPS. Can anyone help me with these issues?

Here's my specs:
Acer Aspire One (751h model)
Windows XP/Ubuntu 10.04 dual boot (Wubi)
Intel Atom Z520 / 1.33 GHz 
1GB RAM
11.6in (1366x768)
Intel GMA 500

I know I will be told to type a few commands into the terminal to give you some information, so just tell me what to type and I'll tell you what it gives me :)
Thanks in advance

---

### Post by JBAlaska on 2010-08-03
Try [This](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/) wiki page, And better still, [This](http://ubuntuforums.org/showpost.php?p=9587446&postcount=1406) Ubuntu Forum Thread

---

### Post by Twizlerr on 2010-08-03
> **JBAlaska said:**
> Try [This]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/") wiki page, And better still, [This]("http://ubuntuforums.org/showpost.php?p=9587446&postcount=1406") Ubuntu Forum Thread
Okay so I went to the wiki page and followed the instructions for 10.04. Everything went fine except for one command I was told to type. Here is the terminal log:
```
christian@ubuntu:~$ sudo apt-get install poulsbo-config poulsbo-driver-2d poulsbo-driver-3d psb-firmware psb-kernel-headers psb-kernel-source
[sudo] password for christian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package psb-kernel-headers
christian@ubuntu:~$ 


```I just copy/pasted the code from the wiki page and received this error. Anyways, I just continued following the instructions and then rebooted when I finished. I received a message notifying me that I would be running on a "low graphics mode for one session." I figure this happened because I received this error in the terminal?

edit: nothing has changed really. Still running on the wrong resolution, and scrolling down web pages is still laggy

---

### Post by Gaygerbil on 2010-08-03
You should mention what browser you're using cuz I do believe Chrome especially has a cruddy framerate when scrolling pages that's why people get the smooth scroll extension for Chrome. 

Basically it might be your browser not your OS so much.

---

### Post by Twizlerr on 2010-08-03
> **Gaygerbil said:**
> You should mention what browser you're using cuz I do believe Chrome especially has a cruddy framerate when scrolling pages that's why people get the smooth scroll extension for Chrome. 

Basically it might be your browser not your OS so much.
I'm using Firefox. It came with Ubuntu, and I use Firefox on all of my computers. Also, on my Windows XP half, Firefox works fine.

---

### Post by JBAlaska on 2010-08-03
> **Twizlerr said:**
> Okay so I went to the wiki page and followed the instructions for 10.04. Everything went fine except for one command I was told to type. Here is the terminal log:
```
christian@ubuntu:~$ sudo apt-get install poulsbo-config poulsbo-driver-2d poulsbo-driver-3d psb-firmware psb-kernel-headers psb-kernel-source
[sudo] password for christian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package psb-kernel-headers
christian@ubuntu:~$ 


```**I just copy/pasted the code from the wiki page and received this error.** Anyways, I just continued following the instructions and then rebooted when I finished. I received a message notifying me that I would be running on a "low graphics mode for one session." I figure this happened because I received this error in the terminal?

edit: nothing has changed really. Still running on the wrong resolution, and scrolling down web pages is still laggy

[B]You are running Ubuntu Lucid 10.04 correct? It seems you followed the instructions for Karmic 9.10.
[/B]
At this point you have 2 options, One would be to try and undo the instructions you followed (especially the changes to /etc/X11/xorg.conf and the PPA added to your sources) and start again with the Lucid 10.04 instructions.

 **I think the better and easier (at this point) option would be to follow the second [Link](http://ubuntuforums.org/showpost.php?p=9587446&postcount=1406) I gave you and download the custom Lucid 10.04 LiveCD with Intel GMA500 support built in. That page also addresses the other fixes for your 751h.**

Once you get the drivers with Hardware Video Acceleration, your netbook will act correctly. Good luck.

---

### Post by Twizlerr on 2010-08-03
> **JBAlaska said:**
> [B]You are running Ubuntu Lucid 10.04 correct? It seems you followed the instructions for Karmic 9.10.
[/B]
At this point you have 2 options, One would be to try and undo the instructions you followed (especially the changes to /etc/X11/xorg.conf and the PPA added to your sources) and start again with the Lucid 10.04 instructions.

 **I think the better and easier (at this point) option would be to follow the second [Link]("http://ubuntuforums.org/showpost.php?p=9587446&postcount=1406") I gave you and download the custom Lucid 10.04 LiveCD with Intel GMA500 support built in. That page also addresses the other fixes for your 751h.**

Once you get the drivers with Hardware Video Acceleration, your netbook will act correctly. Good luck.
This worked, thank you! I can't believe I followed the Karmic 9.10 instructions by accident >.<
Just in case anyone is wondering, I undid the changes I made when I followed the Karmic instructions, and then followed the Lucid 10.04 instructions. Now, the resolution is correct (1366x768) and scrolling down web pages is much smoother.
Thanks again for your help!

---

