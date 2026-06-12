---
title: "Suspend returns from suspend without staying suspended (heh)"
date: 2009-07-16
forum: General Help
---

### Post by nemo81 on 2009-07-16
Ok, so i try suspending OR hibernating my computer.

It goes through whatever it is its doing and then promptly boots back up without staying in the choosen state.

Wondering if theres something i can do to fix this?

I tried installing uswsusp and running sudo s2ram --force, without luck, i get the same behaviour.

I should note that this is a clean install (only a few hours old) of 9.04

The computer in question is an ASUS Pundit P4-P5N9300 barebone system with an Intel C2DE5400 and 4gb Crucial ram.

I am using the restricted nvidia drivers version 180.


Very much looking forward to any replies!
Thanks for reading.


EDIT:

Syslog:
[http://pastebin.ca/1497569](http://pastebin.ca/1497569)

Its the same with Hibernation.

---

### Post by busyu on 2009-07-16
I've got the same problem.  Compaq Presario R3000 running Jaunty 64, Nvidia driver 96 for Geforce4 440 Go.  

I was having trouble with suspend/hibernate (blank screen and would not wake up), like plenty of others around the forum.  So I turned off Sync to VBLANK in the Nvidia x server settings.  Now I suspend or hibernate, I get a blinking cursor for a few secs then the lock screen.  

I guess not suspending is better than crashing, but the best would be to have everything working right.

---

### Post by nemo81 on 2009-07-16
Aha, yeah.

My problem is that im gonna use this box as a mediacenter and i want it to suspend properly to ram so that i can get an almost instant on/off feature on it.

Mine doesnt just show a blinking cursor tho, it gives an error message *i think*. But its way too fast to read.

If someone know how i can enable debugging so that i can give more info then please tell me. In baby steps.. :)

---

### Post by nemo81 on 2009-07-16
I also tried pulling the networkcable before suspending, and that didnt help.. Was thinking there might be some wake on lan thing waking it up..

---

### Post by nemo81 on 2009-07-18
Ah well.

Ended up installing Windows 7 and XBMC for windows.

I cba trying to find the fault preventing hibernation and suspend on a OS i dont know properly.

Its evident something is wrong tho, from the volume of threads regarding the issue. Just wish i was able to help, but alas, the task is too great for a newbie like me. :(

---

### Post by Belsebub on 2009-08-10
Just bought a this pundit and had the same problem. For me, it was an external IR-receiver attached to a USB-port that was the problem.

The solution was to set the USB device wake-up jumpers on the motherboard to +5VSB instead of the default +5V. Actually, the manual said one of the jumpers, probably corresponding to the back USB-ports, should have been set to +5VSB by default, but it was not! :roll:

See page 3-4 in the [manual]("http://dlcdnet.asus.com/pub/ASUS/Barebone/P-P5N9300/E4224_P-P5N9300_manual.zip").

Hope that solves your problem too. XBMC + linux with this hardware is just so good :)

---

### Post by sansut on 2009-10-16
> **Belsebub said:**
> Just bought a this pundit and had the same problem. For me, it was an external IR-receiver attached to a USB-port that was the problem.

The solution was to set the USB device wake-up jumpers on the motherboard to +5VSB instead of the default +5V. Actually, the manual said one of the jumpers, probably corresponding to the back USB-ports, should have been set to +5VSB by default, but it was not! :roll:

See page 3-4 in the [manual]("http://dlcdnet.asus.com/pub/ASUS/Barebone/P-P5N9300/E4224_P-P5N9300_manual.zip").

Hope that solves your problem too. XBMC + linux with this hardware is just so good :)

Oh man you saved my weekend, I been looking for this solution so long and it was in the manual thanks. Now I can relax. By the way why are you using an external IR, don't you have the Pundit P4 with the internal IR and Remote? If you do and would like to make it work take a look at the solution at this link: [http://www.xbmc.org/forum/showthread.php?t=47651&page=8](http://www.xbmc.org/forum/showthread.php?t=47651&page=8)

Cheers and thanks again :)

---

