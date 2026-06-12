---
title: "Low graphics mode, can't progress"
date: 2010-03-15
forum: General Help
---

### Post by heittaa on 2010-03-15
Hi there, first post :)
Bit of a noob to linux, but I can work my way around the terminal and so on so hopefully any help given won't be totally lost on me.

My computer is set up with 2 hard drives. A Maxtor 320GB is split into two partitions, one for Ubuntu karmic and one for Windows 7. The second disk, a samsung 2TB stores all non-OS files. 
I am running karmic 9.10 64-bit, and it was working perfectly for a while now. Today i was installing the download manager u-get (1.5.9) and the dependencies that went along with it (GTK+, gstreamer, atk, so on). The installation(s) worked fine.

Afterwards, I accidentally removed my Global Menu bar from the top panel, and upon trying to re-add it I got a message about whether I wanted to confirm deleting it from my configuration. I needed to reboot anyway, and thought this was just another thing that would go away after a reboot.

Upon rebooting and selecting Ubuntu, the logo appears normally, but then I am faced with a message saying:

> Your screen, graphics card, and input device settings
could not be detected correctly. You will need to
configure these yourself.and I cannot click the OK button or use the keyboard (both USB devices), nor can I with a serial mouse/kb.

I tried booting into my Windows 7 partition, but got a Bad Signature error, which was fixed with:

```
sudo apt-get install os-prober
sudo os-prober
sudo mv /boot/grub/device.map /boot/grub/device.map.bak
sudo update-grub
sudo reboot -n
```Now I can access windows, but ubuntu still boots in Low graphics mode and I cannot click/do anything. Recovery mode still works, i can access the terminal there.

Any clues?

(My graphics card is a Radeon HD4850, using the fglrx drivers that ubuntu suggested)

---

