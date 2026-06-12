---
title: "Metacity possible fixes"
date: 2010-06-06
forum: General Help
---

### Post by Bobulous on 2010-06-06
I finally seem to have Metacity loading on boot, without having to manually run `metacity --replace` (and without fudging it by adding that command to the session startup list). Without Metacity, all of the windows lack title bars, scroll bars, etc, making the desktop pretty much unusable.

The things I've done recently which may be responsible for fixing this are:

1) Giving up on the NVIDIA driver (because I cannot bear the garbled startup text any longer) even though it means xgamma forgets its value on every reboot.

2) Go through gconf-editor and making sure that all mentions of windowmanager point to Metacity. Also, setting Metacity to use act as a compositing manager by ticking the box in key /apps/metacity/general/compositing_manager.

3) Deleting the saved sessions by running `rm ~/.config/gnome-session/saved-session/*` (thanks to Bernhardt at launchpad for that tip).

I suspect it was actually action 3 that resolved the issue. I'm guessing the saved sessions should have been deleted by the upgrade to 10.04, but were overlooked.

---

### Post by Bobulous on 2010-06-06
Okay, I'm confused.

I'm sure I posted this in response to the Lucid fixes sticky thread, but it's appeared as a new thread altogether.

Still, it was very late/early. Guess I should just be glad I posted to the right forum.

---

### Post by Bobulous on 2010-06-10
Seems that step 3 is the magic step, as this has worked for someone else who had the same problem.

---

### Post by fragos on 2010-06-10
I may have had your problem and "metacity --replace" helped but left a terminal window open which when closed brought the problem back. After that my keyboard stopped sending characters so I decided to backup all data to a spare partition and to reinstall 10.04 from scratch. My original 10.04 install was an upgrade. I had been using using Chrome unstable and had been experimenting with settings like the one that removes the title bar from the chrome window only. When I reinstalled I went back to Chrome stable. So far so good.

---

