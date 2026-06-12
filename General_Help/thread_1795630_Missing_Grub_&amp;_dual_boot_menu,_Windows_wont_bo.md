---
title: "Missing Grub &amp; dual boot menu, Windows wont boot"
date: 2011-07-03
forum: General Help
---

### Post by Pen16 on 2011-07-03
Hello i am having a problem with my dual boot setup.  I originally installed windows XP on a 100gb hard drive, from there i downloaded and burnt ubuntu off so i could install it on my 200gb hard drive.

For a little bit i struggled to even get it to install because it wouldn't recognize my onboard nvidia graphics, i ended up having to get an alt boot disk and fix it with technique in this link: [http://ubuntuforums.org/showthread.php?t=1592763](http://ubuntuforums.org/showthread.php?t=1592763).

Now after the bios boot, my screen shuts off for awhile and takes me directly to the login screen for ubuntu.  No Grub, no windows boot options, nothing.  I tried booting windows by choosing it from the bios boot menu but all it does is hang at prompt and doesn't boot at all.

I tried the live cd fix and reinstalled grub but nothing changed.  What i think is happening is that it boots the Grub menu but it doesn't display it because of graphical confrontations. It hangs for about 10 seconds, the grub default time, and then turns my monitor back on to display the Ubuntu login screen.

I know I've seen similar problems but none of the answers i have found worked.  I was wondering if one of you guru's might be able to help me out?

---

### Post by dino99 on 2011-07-03
sudo gedit /etc/default/grub

and set the countdown timer greater than 0 (5 or 10 seconds)

at end of bios process, if you hold "shift" key down, you will see the grub menu.

---

### Post by Pen16 on 2011-07-03
My countdown timer has been set at 10, and when i hold shift, it says its loading grub but i dont see it.

There is a line that says:

#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=TRUE

Do i need to change the value, i thought # meant it didn't read that line?
Or do i need to set the hidden timeout quiet to false?

---

### Post by Pen16 on 2011-07-03
So since my GRUB doesn't want to show, is there a way windows dual boot screen to come back?

Do i need to reinstall windows?  I think im gonna try that.

---

### Post by drs305 on 2011-07-03
After it boots to Ubuntu, try running
```
sudo update-grub
```

If Grub isn't aware of Windows, it won't show the menu. Running the command above will 'force' grub to look for other OS's.

As the command runs in a terminal, watch for indications that it is searching your partitions. If it doesn't appear to, run the following commands:
```
sudo os-prober  # Does this produce results. If not:
sudo apt-get install os-prober # Ensure os-prober is installed
sudo chmod +x /etc/grub.d/30_os-prober # Ensure the os-prober script is executable
sudo update-grub # Try search again.

```

---

### Post by Pen16 on 2011-07-04
I updated grub like you said and it didn't have any problems listing my xp install under sdb1.

Im thinking its more of a graphical glitch cause even if i try to load grub by  holding shift, it shuts my monitor off like theres no signal and then after the grub timeout it brings up the login screen, which isn't even displayed right.

---

### Post by drs305 on 2011-07-04
You may need to tweak some graphics settings. One thing that you might try is to remove "quiet splash" from the linux options of your default menuentry. It's not going to solve the problem, but it may allow you to see commands as the system boots.

The current default, after automatic or manaul selection of a Grub menu item, is for the screen to blank for a while as the OS loads. So at least part of what you are describing sounds normal. If you remove the "quiet splash" you would be able to see if the system is indeed 'hanging', or if it is just exhibiting it's normal behavior.

To remove "quiet splash", open /etc/default/grub as root and remove those entries from the "GRUB_CMDLINE_LINUX_DEFAULT=" line.
```
gksu gedit /etc/default/grub
sudo update-grub # After editing and saving /etc/default/grub
```

---

### Post by meneope on 2011-08-13
> **drs305 said:**
> You may need to tweak some graphics settings. One thing that you might try is to remove "quiet splash" from the linux options of your default menuentry. It's not going to solve the problem, but it may allow you to see commands as the system boots.
 
The current default, after automatic or manaul selection of a Grub menu item, is for the screen to blank for a while as the OS loads. So at least part of what you are describing sounds normal. If you remove the "quiet splash" you would be able to see if the system is indeed 'hanging', or if it is just exhibiting it's normal behavior.
 
To remove "quiet splash", open /etc/default/grub as root and remove those entries from the "GRUB_CMDLINE_LINUX_DEFAULT=" line.
```
gksu gedit /etc/default/grub
sudo update-grub # After editing and saving /etc/default/grub
```
 
 
 
I'm so tired of trying, There's no solution to this problem. I've exactly the same issue as Pen16 and I've tried everything here, everythng by the book, Windows XP is found and recognised but no dual bootup menu. I even install Startup Manager, Boot Repair, I even burn a copy of Ubuntu Secured Remix, tried to reinstall Ubuntu a couple of times. NOTHING works - It's either Windows XP or Ubuntu 11.04.
My last hope now is to try to install an ancient version, say 09.04 or something and then see whether I get a dual boot-up menu at start-up and then painfully update my system up to 11.04 (might take days...).
I don't know what else to do, the first time I installed Ubuntu in 2009 I never had this issue (shrugs) -

---

### Post by drs305 on 2011-08-13
> **meneope said:**
> I'm so tired of trying, There's no solution to this problem. I've exactly the same issue as Pen16 and I've tried everything here, everythng by the book, Windows XP is found and recognised but no dual bootup menu. I even install Startup Manager, Boot Repair, I even burn a copy of Ubuntu Secured Remix, tried to reinstall Ubuntu a couple of times. NOTHING works - It's either Windows XP or Ubuntu 11.04.
My last hope now is to try to install an ancient version, say 09.04 or something and then see whether I get a dual boot-up menu at start-up and then painfully update my system up to 11.04 (might take days...).
I don't know what else to do, the first time I installed Ubuntu in 2009 I never had this issue (shrugs) -

I stumbled upon something for another user earlier in the week. I don't know if it is the same issue or not. When you boot, is your issue that you never see the menu and it boots directly into Ubuntu?

If that is the case, it could be that the menu *display* is not working but the Grub menu is waiting for the 10 second timeout before it boots to the default (Ubuntu). The next time you boot, if this is what is happening to you, wait a bit after you think BIOS has transferred control. You are trying to act while Grub is in the 10 second timeout. Cursor DN 4 times and press ENTER and see if Windows or another OS or memtest boots.

---

