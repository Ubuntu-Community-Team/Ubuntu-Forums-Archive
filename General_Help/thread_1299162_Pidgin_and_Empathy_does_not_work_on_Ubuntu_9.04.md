---
title: "Pidgin and Empathy does not work on Ubuntu 9.04"
date: 2009-10-23
forum: General Help
---

### Post by muntasir_120 on 2009-10-23
I recently installed Ubuntu 9.04 (while keeping Ubuntu 7.04 and WinXP on separate partitions). In Ubuntu 9.04 Pidgin never successfully connects to the internet (I tried Yahoo, MSN and IRC accounts on Pidgin). It just stays in the 'waiting for connections' mode indefinitely. I tried upgarding to the latest version, but still the same result.

Someone suggested I try Empathy, so I installed it via Synaptic. Empathy does not even let me set my status to anything but offline. I have no idea why, but both Empathy and Pidgin seem to be convinced that I'm not connected to the internet.

My internet connection is a mobile broadband, which I have to access via wvdial (I had to get wvdial from the ubuntu package repository and install from the deb file) because my mobile provider is not in Ubuntu's list for my country. This works fine for Firefox, Evolution, Synaptic and I can ping/wget/run scripts that access the internet from the terminal.

BTW, Pidgin works fine in both WinXP and Ubuntu Feisty on the same machine using the same internet connection.

Can someone please help?

---

### Post by Marlon Catudio on 2009-10-24
I also encountered the same problem when I Downloaded new updates on my newly installed Hardy Heron Machine. But luckily I was able to Figure out and solve the problem by adding another account on pidgin.
Try it, works for me

---

### Post by muntasir_120 on 2009-10-26
Thanks, but Pidgin does not allow adding new accounts with the same data as older accounts. So, what I did was to delete all old accounts and add them afresh. This worked for a time, but as soon as I got offline and reconnected again, Pidgin was again 'waiting for connection'. What I did was to disable all accounts and then re-enable them. This works, and this is what I'm doing at the moment until I find a better solution. Thank you for suggesting that.

Nothing of the sort appears to work for Empathy though. Any ideas?

---

### Post by equusaustralus on 2010-06-18
The bug is still ongoing, but in case anyone needs it, there's a solution from [launchpad]("https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/200047/comments/11"): 

[INDENT]
There is a way, but it has become harder with every release.

- Intrepid: enter something in the "away cause" field, pidgin will
  connect
- Jaunty: stop NetworkManager while pidgin is running
- Karmic: /sbin/stop network-manager before pidgin is started[/INDENT]

Typing "sudo /sbin/stop network-manager" then starting pidgin also worked in Lucid!

---

