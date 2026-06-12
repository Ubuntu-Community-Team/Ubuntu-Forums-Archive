---
title: "windows 7 entry gone from Grub.cfg"
date: 2010-11-15
forum: General Help
---

### Post by ParkyZA on 2010-11-15
Hi there, 

Need a little help plz.  I was cleaning old kernels from Grub menu, all sorted except for a vista entry that i could not delete.  Ran this line which I found,"sudo chmod -x /etc/grub.d/30_os-prober", to remove unwanted entries, now only the linux entry left in Grub menu, windows 7 entry gone.  The vista entry was from an old install which is not there anymore.  Running 10.10 at the moment which is dualbooted with win7.

thanks

---

### Post by Mark Phelps on 2010-11-15
Basically, you removed the execute "bit" from that file, so that now, when update-grub runs, it no longer executes that file.  Unless that was a hand-written file, you should have left it alone.

When it runs, it searches for other OSs on your drives -- it does a new search every time.  It's better to either (1) leave it alone and ignore extra entries in the generated menu, or (2) hand-write your own file, save off the original file, and replace it with yours.

What I recommend is to restore the execute bit to that file, run update-grub again, and report back regarding the "extra" entries.

Realize that, in some cases, the new GRUB sees Vista and Win7 as the same -- so just because an entry says Vista Loader, doesn't actually mean it is for Vista.  It could also be for Win7.

---

### Post by dino99 on 2010-11-15
so revert back:

sudo chmod +x /etc/grub.d/30_os-prober

sudo grub-mkconfig
sudo update-grub

---

### Post by ParkyZA on 2010-11-15
Got it back, thanks dino99.  Lesson learnt Mark.  Lastly, how do I get rid of the vista entry without recking anything else?

dave@dave-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found Windows 7 (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sdb1
done
dave@dave-desktop:~$

---

### Post by Quackers on 2010-11-15
This might give you some ideas :-)

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by ParkyZA on 2010-11-15
Thanks Quackers, was actually just browsing that same link you mentioned, but learnt enough for today, try tomorrow. Think I need to read up some more before anymore attempts are to be made at modifing the Grub menu :)

Thanks for all the help guys!

---

### Post by Quackers on 2010-11-15
Lol, it can look a bit daunting at first! It's not as bad as it seems, but you need to take your time and be careful. It's good practise to make backup copies of any file you are going to change. Then, at least, you can return things to how they were.

---

### Post by ParkyZA on 2010-11-15
hey Quackers

Couldn't wait for tomorrow, GOT IT! Grub now nice and clean. Must add though, NB to read instructions carefully, wrong letter in string removed win7 and not vista.  LOL, fixed now. 

dave@dave-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found Windows 7 (loader) on /dev/sda1
done
dave@dave-desktop:~$

---

