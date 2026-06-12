---
title: "Fresh 9.04 install is EXTREMELY slow"
date: 2009-10-28
forum: General Help
---

### Post by Goatie on 2009-10-28
Hi all.
I'm pretty new to Ubuntu so I haven't played around with it yet.

I've installed Jaunty on my old PC so I can learn Ubuntu better to know but it's extremely slow. Even opening the menus takes between 1 and 5 seconds... sometimes longer. I've activated the driver for my nVidia graphics card and installed all the updates from the update manager. I'm quite puzzled as to why it's so slow. At most times it runs at nearly 100% CPU usage.

I've tried searching the forums and I've read through some threads but didn't find any solutions to my problem.

Specs:
Intel Celeron 2.00GHz
768MB SDRAM
30GB HDD

---

### Post by jward3010 on 2009-10-28
Is all that RAM being seen by Ubuntu, go to a terminal and type:
```
free -m
```
Just check whether it shows it up as "768MB total" (or close enough).

---

### Post by P4man on 2009-10-28
open a terminal and run 

```
top
```

let us know which process is hogging your cpu. Also, which nvidia card and driver do you have?

---

### Post by Goatie on 2009-10-28
Sorry for the slow reply.. had to borrow a laptop so I could respond.

It shows 749 in total memory, but I don't believe that's the problem.

It's Xorg that hogs the CPU everytime I do anything on the computer so it's probably something with the driver for the graphics card. But this problem has been there even before I activated the driver.
The driver version is 173(.14.16) which is the recommended one. The graphics card is a Nvidida GeForce FX 5200 with umm, 128MB of memory I think.

---

### Post by lovinglinux on 2009-10-28
Go to "System >> Preferences >> Startup Applications", disable "Remote Desktop" and reboot. This should reduce CPU usage to normal levels.

---

### Post by lovinglinux on 2009-10-28
> **Goatie said:**
> Sorry for the slow reply.. had to borrow a laptop so I could respond.

It shows 749 in total memory, but I don't believe that's the problem.

It's Xorg that hogs the CPU everytime I do anything on the computer so it's probably something with the driver for the graphics card. But this problem has been there even before I activated the driver.
The driver version is 173(.14.16) which is the recommended one. The graphics card is a Nvidida GeForce FX 5200 with umm, 128MB of memory I think.

Also see this [http://ubuntuforums.org/showpost.php?p=7950332&postcount=2](http://ubuntuforums.org/showpost.php?p=7950332&postcount=2)

---

### Post by Goatie on 2009-10-28
That didn't work lovinglinux. It's still as slow as before.

---

### Post by Goatie on 2009-10-28
Don't know if this is allowed.. but here goes
**BUMP**

---

### Post by QIII on 2009-10-28
Generally, bumping so early is considered unsportsmanlike and may draw the ire of the moderators.

Two posters asked you to run commands.

If you would post the entire text of the results, it  would help in diagnosis.

---

### Post by P4man on 2009-10-28
How much memory is xorg using? And did you have this problem in the live cd as well?  Ive seen a few bugs about memory leaks in xorg which are meanwhile resolved, but even those usually take time before xorg starts using up all your ram and the system crawls to a halt.

Are you running any other background apps or something? Last point: did you install all updates?

(As for the bumping, considering the amount of posts here relative to the number of "helpers", Id say after 24 hours a bump would be okay. I subscribe to each thread I post in (as do most i suspect) so its not because its no longer on page 1 that we would miss it or forget it).

---

### Post by jward3010 on 2009-10-29
I've a slightly mad idea which will involve killing X (to some degree), well Gnome anyway and seeing what happens. Bearing mind you have an FX5200 you're X stuff should be pretty good.

Press Ctrl + Alt + F1 and you'll end up in the first console (tty1). Run "top" command in here and monitor whats eating CPU cycles and eating memory as well.

Now do Ctrl + Alt + F2, you'll end up in console 2 (tty2) and run:
```
sudo /etc/init.d/gdm stop
```
This will kill Gnome Desktop.

Head back to tty1 and monitor "top" command and whether CPU cycles have calmed or are still high.

---

### Post by Goatie on 2009-10-30
Hi again guys.
I've decided to shift over to the new Karmic Koala release instead of using Jaunty. I'll have to wait a week or longer with burning it to a CD because my DVD/burner drive on my main computer is busted... have to order a new one.

Is it better for me to use the alternate CD or the Live CD when I'm going to install 9.10 on the old computer?

---

### Post by P4man on 2009-10-30
> **Goatie said:**
> Hi again guys.
I've decided to shift over to the new Karmic Koala release instead of using Jaunty. I'll have to wait a week or longer with burning it to a CD because my DVD/burner drive on my main computer is busted... have to order a new one.

Is it better for me to use the alternate CD or the Live CD when I'm going to install 9.10 on the old computer?

Both should work. If the old machine can boot from USB, you could make a live usb stick and install from that.

---

### Post by Goatie on 2009-10-30
> **P4man said:**
> Both should work. If the old machine can boot from USB, you could make a live usb stick and install from that.

I've tried booting from a USB key, but Ol' Dusty(as I call it) is too stupid to recognize it even if I set it as the first bootable disk(?). I'll just wait a few days for the new DVD drive to arrive in the mail.

[EDIT]Bah, I just realized I have an old CD burner in another old computer I use for spare parts.

---

### Post by P4man on 2009-10-30
> **Goatie said:**
> I've tried booting from a USB key, but Ol' Dusty(as I call it) is too stupid to recognize it even if I set it as the first bootable disk(?). I'll just wait a few days for the new DVD drive to arrive in the mail.

[EDIT]Bah, I just realized I have an old CD burner in another old computer I use for spare parts.

If the machine has an option to boot from USB in the bios, then it probably can. It might be an issue with the usb stick. Perhaps its one of those [U3]("http://en.wikipedia.org/wiki/U3") enable sticks?

---

### Post by Goatie on 2009-10-30
Nope, it doesn't have U3. I'll try to format it and make a new one with the software called UNetbootin.
The one I have now was made manually with syslinux and works fine with LiveCD on this computer.

I'll be back later today after school and shopping. If not, I'll be back tomorrow some time... it's 08:40AM here in Denmark right now -.-

---

### Post by jward3010 on 2009-10-30
Old machines typically don't. Anything made in the last two to three years is probably full compatible.

Anyway in regards your other issue: "Alternate or Live?".

I'd go with Alternate for an old machine. The Live mode could blow up and run our of RAM before you get to the desktop and obviously with no swap being available then it will have no fallover. The alternate disk comes with a simple text based install (no you don't do anything by command line, you get options on screen which you select - it's very easy) that uses little RAM, a bit like a much improved Windows XP install.

---

