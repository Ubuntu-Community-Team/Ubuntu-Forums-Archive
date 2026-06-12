---
title: "Trouble with hibernating"
date: 2012-01-02
forum: General Help
---

### Post by jdawgvh on 2012-01-02
I've got a server that I'm trying to set up with Ubuntu 11.10 server edition.  I'm trying to set it up to hibernate if it finds no other computers on the network.  I have installed pm-utils and it seems to be suspending properly.  When I issue the pm-hibernate command everything works fine...exactly once.  Ubuntu will hibernate and come out of the hibernation.  Then when I send it back in to hibernation the computer reboots.  I've gone through a couple of tutorials on how to set up hibernation, changed a couple of things in the /etc/default/grub file (I changed them back when the behavior didn't change.  Based on the last couple of lines from:

```
cat /var/log/syslog | grep PM:
```> 
                                  Jan  2 14:30:50 server kernel: [    1.490582] PM: Checking hibernation image partition /dev/sdb5 
 Jan  2 14:30:50 server kernel: [    1.685247] PM: Hibernation image partition 8:21 present 
 Jan  2 14:30:50 server kernel: [    1.685251] PM: Looking for hibernation image. 
 Jan  2 14:30:50 server kernel: [    1.685440] PM: Image not found (code -22) 
 Jan  2 14:30:50 server kernel: [    1.685443] PM: Hibernation image not present or could not be loaded. 
  it seems like there is some setting that is not persistent.  Any help would be greatly appreciated but I'm kinda stuck.

---

### Post by jdawgvh on 2012-01-02
update:  I was able to get hibernate working thanks to this website:

[http://chriseiffel.com/everything-linux/step-by-step-how-to-get-hibernate-working-for-linux-ubuntu-11-04-mint-11/](http://chriseiffel.com/everything-linux/step-by-step-how-to-get-hibernate-working-for-linux-ubuntu-11-04-mint-11/)

Now I have a new problem.  It only works when I have a keyboard and mouse attached.  Since this is a server I would like to run this headless but I cannot get it to work.  Any thoughts on this new problem?

---

