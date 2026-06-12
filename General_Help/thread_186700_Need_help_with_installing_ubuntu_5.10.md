---
title: "Need help with installing ubuntu 5.10"
date: 2006-06-02
forum: General Help
---

### Post by sbu on 2006-06-02
Good day all!

I recently received version 5.10 cds which I've ordered earliers this year.

I followed the instructions up to the point where I was asked to remove the cd rom and reboot my system. I did reboot my system and I arrived at dos-like command screen.However I wasnt able to continue from there because I dont know what commands to use to get to the gui.Is there gui? I am asking this because when I ran the live cd it gave me the impression that this OS is user friendly](*,)

---

### Post by maxweld on 2006-06-02
Can you describe what you are seeing at the dos like screen.
Ideally if you could replicate it would be best.

---

### Post by AirRaven on 2006-06-02
Try typing "sudo gdm". 

Are you sure you didn't install the basic server install by mistake?

---

### Post by sbu on 2006-06-02
I am asked to enter my login id(Keith) and my password(****) which I do
and then I get the following:'keith@ubuntu$:'

---

### Post by eqisow on 2006-06-02
Try 'sudo gdm' or 'startx'. I shouldn't have dropped you at the command line though. Perhaps you accidently did a server install? If neither of the above commands work, that is likely. Solve it by typing in 'sudo apt-get install ubuntu-desktop'.

Note: All commands are w/o the quotes.

---

### Post by lettas on 2006-06-02
Try commands

sudo apt-get update
sudo apt-get upgrade

That will upgrade your installation to the latest possible

If the installer failed to install everything, try command:

sudo apt-get install ubuntu-desktop

---

### Post by maxweld on 2006-06-02
Sounds like you have selected a wrong option during the install, e.g. server option.

If you can, it is probably easiest to reinstall, carefully checking the options as you go through the install process. I cannot run an install of 5:10 to remind myself of the options, but it is probably something like a desktop option. (avoid server option). 

If you are not sure how to respond, read the help offered, or ask again in this thread.

---

