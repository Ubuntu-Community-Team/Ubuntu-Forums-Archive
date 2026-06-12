---
title: "GDM (login screen) does not appear in Ubuntu Karmic"
date: 2009-12-28
forum: General Help
---

### Post by villalcalde84 on 2009-12-28
I have installed Ubuntu 9.10 Karmik Koala along with Win XP; a few days ago I installed some updates in Ubuntu, but when they were being installed the computer turned off suddenly. Since then when I turn it on, select to start Ubuntu, the white Ubuntu logo shows but after that the GDM or login screen does not appear. All I see is the prompt asking for my user name and password, and when I type them I’m left with a command line interface.

I think some system file was affected when installing the updates and the computer was turned off before it finished. What can I do to start the graphical interface? All help is appreciated.

Thanks.

---

### Post by dcstar on 2009-12-28
> **villalcalde84 said:**
> I have installed Ubuntu 9.10 Karmik Koala along with Win XP; a few days ago I installed some updates in Ubuntu, but when they were being installed the computer turned off suddenly. Since then when I turn it on, select to start Ubuntu, the white Ubuntu logo shows but after that the GDM or login screen does not appear. All I see is the prompt asking for my user name and password, and when I type them I&#8217;m left with a command line interface.

I think some system file was affected when installing the updates and the computer was turned off before it finished. What can I do to start the graphical interface? All help is appreciated.

Thanks.

Log in on the command line and run this:

```
sudo apt-get update
startx
```

---

### Post by villalcalde84 on 2009-12-29
I tried what you told me, sudo apt-get update and then startx, but the graphical interface did not start. I got this message when entering the second command:
xauth:/home/fernando/.Xauthority not writable, changes will be ignored
xauth: error in locking authority file /home/fernando/.Xauthority

Any ideas about this, what could be the error? and maybe a way to fix it?

Thanks.

---

### Post by warfacegod on 2009-12-29
I had a similar issue when I tried using an older version of GDM.

Try using just startx

If that doesn't work

From Command line type: sudo apt-get remove gdm 

hit enter

After that: sudo apt-get install gdm

hit enter

Then reboot when done.

---

### Post by Endless_Nameless on 2010-03-31
I think the same is happening to me! :sad:

Karmic Koala 32 bits

The ubuntu loading screen appear, but when it goes to the login screen, there is no window, field, or button! The mouse cursor appears and works, the log in the screen (alt+crtl+F8 ) does not show any errors. Nothing in the dmesg also.

It begin when I tried to open firefox, and it did not work. I tried to open other program (i don't remeber now what program was), and then i reboot. After this the problem started! I thought it was a kernel issue, and tried other kernels, with no success. Fortunately I keep  an Ubuntu 64-bits also installed, in case of emergency!

I tried to reinstall gdm, or to install the upgrades, but the problem is the same! I imagined if this happens to someone who needs a GUI to connect to the internet in first place. Anyone have some idea to help?

I wonder why the OP had this problem 3 months ago, and I only had it now...

Thanks for any answer!

---

### Post by sany on 2010-04-16
Very same problem here too. Ubuntu's login screen appears, but without any buttons or anythig to interact with. From commandline I could start X (startx) after I stopped gdm (sudo gdm-stop).  However once in the GUI I couldn't solve my problem.
Reinstalling gdm didn't help either. 
Unfortunately I don't know what caused this problem to occure, and I hope I wont encounter it in the future. (It isn't solved, I just reinstalled the whole Ubuntu)

---

### Post by shaka_zulu on 2010-04-16
What is the last thing you have done to your system because this error occurred? What graphic card you are using? Did you recently update Kernel?

---

