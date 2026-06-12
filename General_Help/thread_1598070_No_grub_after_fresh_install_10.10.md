---
title: "No grub after fresh install 10.10"
date: 2010-10-16
forum: General Help
---

### Post by TopGear on 2010-10-16
Hello people,

I just installed Kubuntu 10.10.
In Ubuntu 10.04, I used to have a GRUB2 bootloader, but with this install, it doesn't show up.

/dev/sda1 is the /boot partition
/dev/sda2 is the / partition
and there's another partition for SWAP.

I just don't know what to do actually... :(

---

### Post by JackNocturne on 2010-10-16
What **error** does it display when you boot? 


Also what method of installation did you use? Fresh-install or Upgrade?

---

### Post by TopGear on 2010-10-16
Well, there's no error. It just doesn't show up.
And I used a complete fresh install. First formatted my 10.04, and then installed 10.10 on it.

---

### Post by JackNocturne on 2010-10-16
Ok then all you have to do is boot from **Live Cd** and **install** Grub2 to /boot which is your boot partition

Type the following in Terminal from Live Cd
```
sudo grub-install --root-directory=/boot /dev/sda
```If you want more info;
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html)
>> Scroll to the bottom of the page <<

---

### Post by TopGear on 2010-10-16
Well, I can get into Ubuntu 10.10. I just don't see a grub. It's like 10 sec black, and then the kubuntu boot screen comes up, and I'm just able to login like normal.

---

### Post by JackNocturne on 2010-10-16
**Oh then disregard what i posted**



[LIST]
[*]Grub menu is "usually" not shown if you don't have more than 1 OS to boot
[*]If you would like to see it anyway,you have to edit the **/etc/default/grub** and/or **/etc/grub.d**   #I don't remember how,you'll just have to google for more information.
[/LIST]

---

### Post by mike2357 on 2010-10-16
This is how Ubuntu installs by default.  If you want to still see the grub menu, you have to do two things:

1.  In the file /etc/default/grub, comment out the line that reads "GRUB_HIDDEN_TIMEOUT=0".  You can do this by inserting a # (pound sign) at the beginning of the line.
2.  Recompile grub with the following command:
```
sudo update-grub
```

That should do it and you should see the grub menu the next time your computer boots.

---

### Post by wilee-nilee on 2010-10-16
If you just hold down the shift button the grub screen will show.

Also in the terminal run, and copy and paste what it says.
```
sudo fdisk -l
```

---

### Post by TopGear on 2010-10-16
Thank you guys. Uncommenting that line did it :D

---

