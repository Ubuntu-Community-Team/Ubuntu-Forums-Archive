---
title: "Upgrade to 10.10 failed"
date: 2010-10-12
forum: General Help
---

### Post by zappadragon on 2010-10-12
So I have a netbook with the full 10.04 installed. It also has Windows 7 on it. Now the upgrade went fine at first but then it locked up. There was a window about grub in the background and the upgrade window with the terminal section open. The time remaining bar was at 28 minutes left. I was not able to click the grub window to bring it to the front and I was not able to move either window. I left it for over and hour after that and still had not moved. I rebooted and now of course Ubuntu does not work. Is there a way to fix it or do I need to just reinstall a fresh 10.10?

---

### Post by samr85 on 2010-10-13
I had exactly the same issue as this when upgrading.  When the grub message came up I could click on anything with the mouse, and could do anything with it even start other programs, except for move any windows around, so couldn't move update manager off the ok button...  The keyboard did nothing, even when I opened a new terminal window.  The keyboard worked if I switched to ctrl+alt+F1, but that didn't help as I couldn't work out how to interact with the grub window on tty7 from that prompt.  

I found that starting up using the recovery (or whatever it's called!) mode from grub let me repair all the packages and I managed to get back into ubuntu.  I think that I'm now stuck with some form of hybrid between versions and update manager is saying that there are no updates available, even though I know that there is at least an update for my browser available that should be showing up, and I suspect a lot of other things as well!

---

### Post by davidvandoren on 2010-10-13
MY upgrade crashed as well.

Try booting into an older kernel. I was lucky doing just that.
Move your data to an external hard drive or to windows 7.
boot from cd and fresh install. 
When partitioning the drive chose custom or advanced and delete all linux partitions.
Then create new once as you please. one /boot, one /, on swap, and then install. 
It takes only 20-40 minutes.
Why watching your drive ramble for hours and then end up with a Zombie?

---

### Post by zappadragon on 2010-10-14
I tried all that too and just had to end up doing a fresh install.

---

### Post by Swiftjay on 2010-10-14
> **zappadragon said:**
> I tried all that too and just had to end up doing a fresh install.


My upgrade seemed to work just fine, was it because your grub2 wasn't installed properly before hand?  This could've been an issue why.

---

### Post by bonkey on 2010-10-14
I just had this exact problem on the grub update. I couldn't click the buttons or move the windows and the keyboard shortcuts didn't work.

Looking for a workaround to fix this without re-installing. Anyone find a fix for this yet?

---

### Post by Tjofalt on 2011-04-05
Same thing happened to me.

Do a **compiz --replace** from the cli and you're set.

---

