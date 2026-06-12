---
title: "Ubuntu 10.04 Blank screen on Start-up"
date: 2010-05-22
forum: General Help
---

### Post by erusso0001 on 2010-05-22
Hello everyone,

I just bought a new Lenovo Y550P Laptop. Originally had Win7 on it, didnt care much for it so I thought I would be crazy and do a full install of the new Ubuntu 10.04.

Things have been working really nice until the past couple hours. If I restart the laptop, Ill get past the post but the laptop will get stuck on a black screen with the _ flashing, and will not move on from that point.

i was able to get my Intel Wifi 5300 agn working, and everything else seems to be working as well. The GPU is a Nvidia 240m, which Ubuntu was able to find the driver for with no problems. All in all it was running great all day until I did some restarts and now it's not moving past the black screen.

Any ideas?

Thanks

Ed


EDIT:

One quick note. Ubuntu will start up and move past the black screen with the flashing _  if i do a hard shutdown, and turn the laptop back on. Not sure if thats important info or not.

---

### Post by erusso0001 on 2010-05-23
bump for the linux noob :(

---

### Post by -humanaut- on 2010-05-23
Try hitting ctrl+alt+f1 when the cursor is flashing and see if you can get to a TTY console and login in from there once logged in type startx This is generally a problem with Plymouth (don't get me started on Plymouth I hate it and it should have never been included in an LTS) and Nvidia cards.

---

### Post by masque7 on 2010-11-27
Ironically this seems to be happening more and more. In the GRUB2 menu with Ubuntu highlighted if you press "E" to edit, and delete the words "quiet splash" and then boot with ctrl+x, it boots fine.

However, I have no idea how to rectify this as a permanent fix

---

