---
title: "Using Putty"
date: 2010-08-27
forum: General Help
---

### Post by ptmuldoon on 2010-08-27
This is probably a dumb question, but I'm learning..

I have a headless Ubuntu Server setup going being used as a NAS box.  And I can use Putty to connect to the machine.

If i issue various commands via Putty, and than disconnect the connection, does the command continue to run and process until its finished? (ie, formatting drives, rebuilding arrays, etc)

---

### Post by Jose Catre-Vandis on 2010-08-27
In simple terms, no.

However, if you can use **screen** on your nas box, then you can issue most terminal commands, detach the screen and the process will continue to run, but not for processes such as the ones you mention, formatting, arrays and the like.

leave your putty session open for these - I guess you won't have to do it that often?

---

### Post by gdonwallace on 2010-08-27
if you have the screen utility installed then issue the command screen -d -RR; then issue whatever commands that you want, then they will continue to run even if you get disconnected.

However; this most likely wont work as you are on a NAS that does not have an actual running OS.  Therefore, any command that you issue to the NAS would stop running after you disconnect via putty.

---

### Post by ptmuldoon on 2010-08-27
I actually have Ubuntu Server installed onto an 8gb compact flash card for the Operating system, with an addition 4 1 TB drives in it, with the ability to expand up to 8 HDs. 

As I'm learning, I wasn't aware of Screen, which I just found is already installed on the OS, and should do the trick.

So I should just be able to run Screen, and grow my array remotely from another pc on the network.

---

