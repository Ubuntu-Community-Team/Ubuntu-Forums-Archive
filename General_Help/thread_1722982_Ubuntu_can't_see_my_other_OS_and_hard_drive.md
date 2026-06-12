---
title: "Ubuntu can't see my other OS and hard drive"
date: 2011-04-06
forum: General Help
---

### Post by go_lanche on 2011-04-06
I have (had) a pretty unique setup. Three hard drives. One runs Ubuntu, one runs XP and one was just a media storage drive. Everything was working correctly until my crappy XP needed reformatting. I removed the media drive and the ubuntu drive and attempted to boot into XP directly instead of going through GRUB. It wouldn't boot, I hooked the other two drives back up and now Ubuntu works correctly but the other two drives are no where to be found, even when I get into the boot menu. How can I get Ubuntu to see them again? I realize this isn't a standard problem, so any ideas / spitballing would be helpful.

---

### Post by techunit on 2011-04-06
which drive is grub installed on? if you can boot your ubuntu drive open a terminal and type

sudo update-grub

your other drives need to be plugged in.

---

### Post by go_lanche on 2011-04-06
Ubuntu is installed on the master drive. I ran a grub update and nothing changed. I am starting to think that maybe I fried something on the MB when I tried this experiment. This seems like it might be a hardware problem since not even the BIOS can see the other two HDs. Thanks for the tip on update-grub though.

---

### Post by techunit on 2011-04-06
you may just need to reseat the drives.

---

### Post by go_lanche on 2011-04-06
Embarassing to have to ask this, but I am not sure what that means. Just unplug / replug them?

---

### Post by admkbc on 2011-04-06
You should check plugs of hard drive. Next to you can test this drive on other computer.

---

### Post by techunit on 2011-04-06
you understood what I meant yes. And there is nothing embarasing about double checking. yes you unplug them and replug them.

---

### Post by Quackers on 2011-04-06
If your bios can't see the other drives, it is unlikely that an operating system will :wink:

---

### Post by go_lanche on 2011-04-06
I have tried unplugging / replugging to no avail. The BIOS can't see these no matter what I do. I plugged them into the SATA slave drive slots on the MB and on the raid slots. Nothing. I can't imagine that I simultaneously fried both drives to death by unplugging them. I don't have another machine to test them on right now. Thanks for all the help everyone.

---

### Post by oldfred on 2011-04-06
Check power connections also.

I always hate going into my system. Every time I open it to change something I invariably have to go back into it to reseat something. The old IDE cables were the worst as they would look like they were in place, but when I pushed they seated. And sometimes they had just enough of a connection to partially work.  I have converted some of my SATA connections to a locking style which helps.  But check power as well.

You should try to reinstall to exactly the same hardware ports. So drives will be the same sda, sdb, sdc order.  Ubuntu is good about finding drives by UUID, but windows not so much.

But BIOS has to see drives for them to work in any system.

---

