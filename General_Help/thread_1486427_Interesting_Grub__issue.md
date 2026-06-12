---
title: "Interesting Grub  issue"
date: 2010-05-17
forum: General Help
---

### Post by clgy15 on 2010-05-17
Hey everybody,
So heres whats going on. I have Win7 and Ubuntu all nice and working. 
What I want to do is to install another Ubuntu just for a short while. I want to have a fresh install of Ubuntu to do my own remaster of it so heres my question.
Since the fresh install will install its grub into the mbr, how do I reinstate the grub from the first ubuntu when Im done with the remaster?
Thanks

---

### Post by jbrown96 on 2010-05-17
What version of grub are you using on the existing install. Since you have Win7 installed, you should get a Grub menu when you boot that says something very close to 1.97. If so then as long as you don't change the partition number of your existing install when you do the new one, then you won't have any problems. 
When installing, on the last page before you install, there is an advanced menu. Open it and don't install Grub. Once you reboot, go into your existing Ubuntu install. Run ```
sudo update-grub
``` and that will find your new install and add it to the menus. 

After you get rid of the new install, just run ```
sudo update-grub
``` in the old install to remove the new entries.

---

