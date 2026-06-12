---
title: "Screen Resolution and boot problem with 9.10 upgrade"
date: 2010-01-17
forum: General Help
---

### Post by IDRACCA on 2010-01-17
I am running an older hp pavilion xt936 desktop. Was running ubuntu 8.10 everything was fine. I got a Upgrade pop up one day that I thought was for some security updates. I didn't realize that the pop up was also offering me to upgrade to 9.10. I clicked to accept upgrade and to my surprise got Version 9.10. 

The first problem that I experienced was that my screen resolution got changed from 1024x768 to 800x600. When I went to "preferences" and tried to change this the 1024x768 choice was not given as an option. I went to ubuntu help and different forums and saw somewhere that someone simply rebooted and fixed a similar problem. When I rebooted I got the screen to enter user name and password but when the ubuntu title screen appeared it immediately went into a mode that made my screen look like the horizontal adjustment was way off ( IE squiggly lines appeared across the screen that look like horizontal barber shop poles). At this point the computer tries to reboot on its own then comes back to the "log in screens" and does the same thing. I can't boot or get into the operating system at all now. Any help would be appreciated. I am considering starting all over again and re installing my copy of 8.10. But if I can get this working on this old machine I would like to try. Thanks in advance for any help any one might have.

IDRACCA

---

### Post by lidex on 2010-01-17
If you hold down the shift key after the bios screen you'll get the grub menu. Boot into the second option, which should be recovery mode. You'll come to a screen that give options for various functions. From that you'll want to get to a command line\shell\terminal with networking. Not sure of the exact wording but get to a prompt and run these commands as a start:
```
apt-get update
apt-get upgrade
update-grub
```
Now reboot. This is to ensure booting with the correct kernel. If there is an error try commands prefixing sudo.

---

### Post by lidex on 2010-01-17
From your current access point it would be helpful to download and burn a copy of Karmic LiveCD if possible.

---

### Post by IDRACCA on 2010-01-17
I think I have to hold down the escape key instead of shift as I do not have grub2. I did that and got a "grub" prompt. I believe that is what you meant by a "command line" I am a novice at this so please bear with me. I tried typing \shell\terminal with networking and got an "error 27" Unrecognized Command. I then tried to enter the other commands that you gave me with and without the "sudo" they all got the same response "unrecognized command." I must not be doing exactly what you were telling me to do. I can't get into my "ubuntu" machine to burn a "Karmic Live cd" but I can do it from another computer which is running win xp.  Where do I get this?

---

### Post by lidex on 2010-01-17
No. Sorry, I assumed you installed grub2 with karmic.

So you do get the grub screen on boot then? That's where you select the OS and kernel version. You want to select the second line from the top and hit enter. That should be a recovery option.
You'll see some stuff loading and then it will stop on a screen with various options. One of those options should be a terminal shell with networking. You select that and hit enter to get a command prompt.

Download ubuntu here:
[http://www.ubuntu.com/]("http://www.ubuntu.com/")

---

### Post by IDRACCA on 2010-01-18
> **lidex said:**
> No. Sorry, I assumed you installed grub2 with karmic.

So you do get the grub screen on boot then? That's where you select the OS and kernel version. You want to select the second line from the top and hit enter. That should be a recovery option.
You'll see some stuff loading and then it will stop on a screen with various options. One of those options should be a terminal shell with networking. You select that and hit enter to get a command prompt.

Download ubuntu here:
[http://www.ubuntu.com/](http://www.ubuntu.com/)

Thank you very  much for responding to my problem. I appreciate it very much. I "copped out" and reinstalled 8.10. Every thing seems fine so I will probably leave well enough alone for this OLD computer. I learned a whole lot about working with command lines etc. that I didn't previously know. Your comments encouraged me to look up more info on grub, grub2, bash, and the commands used to get things to work. My sphere of knowledge and info on the umbutu OS HAS BEEN GREATLY ENHANCED as a result of your correspondence! Thanks again for your kindness.

IDRACCA

---

