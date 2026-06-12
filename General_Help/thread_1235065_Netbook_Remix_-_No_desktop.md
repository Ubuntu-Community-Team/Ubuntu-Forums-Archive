---
title: "Netbook Remix - No desktop"
date: 2009-08-08
forum: General Help
---

### Post by kamaji792 on 2009-08-08
My EEE PC 900A ran out of batteries and turned itself off (without shutting down).

When I tried to re-start it it gave me a not shutdown properly message and checked the disk.  Then told me I had to do it manually.  Which I did answering yes to all the questions without really understanding any of them.

Now it starts fine.  I get the graphical log-on screen where I can enter my user name and password.  However I then get a black screen with a pointer.  So I have no desktop.  Luckily when I press the on-off button it shuts down cleanly.

Any help gratefully received.

---

### Post by bandofmercy on 2009-08-08
have you tried restarting x at the black screen with ctrl-alt-backspace?

otherwise (i'm sure someone else could be more specific and helpful about this)

after logging in to the black screen,
Try ctrl-alt-f2 to bring up a terminal.  login and enter

```
sudo killall gdm
``` to quit gnome, then, i don't know, maybe ```
sudo gdm
``` to start it up again?  switch to your main gui console again with ctrl-alt-f7 and see what that does...

do you have compiz enabled?  A recent post of mine shows a problem I was able to correct with login by temporarily diabling compiz and correcting some effects my cpu wasn't prepared for, but you should search my history for that.

other possible problems: (oh, and i'm pretty nooby, so like i say, someone else might have better ideas)

reconfigure your xorg from the terminal: ```
 sudo dpkg-reconfigure xserver-xorg
```

--I'm guessing you should do this after killing gdm, and if you have any custom edits to your xorg.conf you might lose them--on my old laptop I had to change the default resolution on my login screen, for example, because it was super big.  a better tutorial is here: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760) that mentions little details like backing up your old xorg.

or perhaps your startup programs are messy.  I don't know where ubuntu's startup programs are managed from in the terminal, though.  It seems different from most console-based tutorials i can find.

Good luck!  I hope someone can correct whatever lies I just told so that you are fixed!

---

### Post by kamaji792 on 2009-08-26
Thanks for the replay **bandofmercy**.

Your suggestions sadly did not help.

I don't think there is anything wrong with X.  I just think it is not being told what to display on the desktop.  I get a black window with a mouse pointer that I can move.

Additionally at the log on screen there is an options menu.  If I select **Select Session** > **Failsafe GNOME** > **Change Session** I get a desktop I can use.  Along with a message about 'start-up scripts not being run'.

Will probably go for the re-install option once I have the data retrieved from it (not much as I have not been using it for long).

Thanks anyway

---

### Post by shae on 2009-08-26
Before trying to reinstall, back up your data and remove the hidden files from your home folder.  That might get it to start correctly again.

---

### Post by P4man on 2009-08-26
where you by any chance doing an updgrade or install when it ran out of batteries ?

If so (and even when not), try this:
```
sudo dpkg --configure -a
```

---

### Post by bodhi.zazen on 2009-08-26
I am guessing your configuration files are corrupted.

I have had this happen on a few occasions and to be honest, easiest thing to do iss to move your entire home directory.

Boot to recovery mode , run a root shell

```
mv /home/your_user /home/your_user.bak
mkdir /home/your_user
chown your_user:your_user /home/your_user
```

then exit and at the recovery menu continue booting.

You will loose your configuration for your desktop, but should be easy to fix.

If you need data or other files from your old home, move it from the back up (your_user.bak) to the new home.

Once you are happy your have moved everything you need, you can delete the old (or back it up off your hard drive).

IMO this is easier then attempting to restore corrupt config files.

The one file you might want is /home/your_user_bak/.mozilla 

Good luck.

---

### Post by WalkerInTheWoods on 2009-08-26
I am having a similar problem, except when I logged in the background did show up but that was all. I am able to get the netbook desktop to show up now except the top panel will not come up and the program windows are not the right size and I cannot resize them. You can read about it here [http://ubuntuforums.org/showthread.php?t=1249872](http://ubuntuforums.org/showthread.php?t=1249872)

I suspect bodhi.zazen is right and the configuration files are messed up. I will try your suggestion. I wonder if kamaji792 has had any luck with it.

---

### Post by WalkerInTheWoods on 2009-08-26
This worked for me. Thank you!

> **bodhi.zazen said:**
> I am guessing your configuration files are corrupted.

I have had this happen on a few occasions and to be honest, easiest thing to do iss to move your entire home directory.

Boot to recovery mode , run a root shell

```
mv /home/your_user /home/your_user.bak
mkdir /home/your_user
chown your_user:your_user /home/your_user
```

then exit and at the recovery menu continue booting.

You will loose your configuration for your desktop, but should be easy to fix.

If you need data or other files from your old home, move it from the back up (your_user.bak) to the new home.

Once you are happy your have moved everything you need, you can delete the old (or back it up off your hard drive).

IMO this is easier then attempting to restore corrupt config files.

The one file you might want is /home/your_user_bak/.mozilla 

Good luck.

---

### Post by bodhi.zazen on 2009-08-27
glad it worked. As I indicated, after going through this myself, it is easier then trying to work through the config files and faster then re-installing.

---

