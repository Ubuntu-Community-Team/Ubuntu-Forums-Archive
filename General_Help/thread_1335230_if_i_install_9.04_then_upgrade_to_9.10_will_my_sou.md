---
title: "if i install 9.04 then upgrade to 9.10 will my sound work."
date: 2009-11-23
forum: General Help
---

### Post by elliotn on 2009-11-23
i havent manage to get sound to work in karmic am tired thus am returning back to jaunty. but will my sound work if i upgrade from 9.04 to 9.10 than having to fresh install 9.10

---

### Post by elliotn on 2009-11-23
any suggestion here

---

### Post by arubislander on 2009-11-23
My guess is, no it won't work if the trouble is with the Karmic drivers... but then again... who knows?

Do you have a spare partition on which you could install Jaunty and update to Karmic? I always do shadow upgrades and installs before committing my main partition.

---

### Post by kambrik on 2009-11-23
Does it work in 9.04?
What is the sound card? Make/Model?

Check out these two articles I wrote on upgrading Ubuntu (says server but works for desktop as well) and fixing sound problems in Ubuntu.

[http://www.compuhowto.com/linux/ubuntu/upgrade-ubuntu/]("http://www.compuhowto.com/linux/ubuntu/upgrade-ubuntu/")

[http://www.compuhowto.com/linux/ubuntu/ubuntu-no-sound/]("http://www.compuhowto.com/linux/ubuntu/ubuntu-no-sound/")

---

### Post by jadhav333 on 2009-11-23
I had sismilar issues earlier.. I followed these steps:

1) run the **System>Administration>SystemTesting**
2) Deselect all tests except the **audio test**
3) clicked **skip test** until I reached the test that plays a sound and ask you to verify
4) If you can hear the sound.. issue resolved..
5) if not.. rightclick on the audio icon in the system tray, in the top right hand corner of the desktop screen and open the **sound preferences**, try the various options available under the **Output panel**.. one at a time.. Test.. if no success, repeat with another output option..  

Worked in my case.. no need to re-install.. 

If this does not work.. maybe something else will.. do not lose hope :)

---

