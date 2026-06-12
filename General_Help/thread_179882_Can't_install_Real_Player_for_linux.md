---
title: "Can't install Real Player for linux"
date: 2006-05-20
forum: General Help
---

### Post by bobby19 on 2006-05-20
I have ben trying and trying, but I can't Install realplayer for linux on ubunu 5.10. Does anyone know how to install it succesfully? Or maybey of a realplayer equivalent, because I really need to play movies off the internet. Any help would be greatly appreciated. Thanx!

---

### Post by bluevoodoo1 on 2006-05-20
How about this?
[https://wiki.ubuntu.com/RealplayerInstallationMethods](https://wiki.ubuntu.com/RealplayerInstallationMethods)

---

### Post by K.Mandla on 2006-05-20
The deb off the wiki works like magic for me.

EDIT: Darn. Beat me to it. I type too slow. :)

---

### Post by evaristegalois on 2006-05-24
I struggled with this as well and finally got it to work as follows,
although there might be simpler ways. Download rp8_linux20_libc6_i386_
cs1_rpm from [http://forms.real.com/real/player/blackjack.html](http://forms.real.com/real/player/blackjack.html) and rename the ``cs1'' to ``cs2''. Remember the directory in which you are keeping this file. Then on the command line: ``sudo apt-get install real'' You will probably get an error message about missing dependencies. Just ``sudo apt-get install whatever'' until you have everything in place. Some RealPlayer installer program will then take over and ask you for the directory where you are keeping the above file. Off you go. Worked for me. The icon is under Applications > Sound & Video. Good luck.

---

### Post by Isoss on 2006-05-24
Check this one here: [http://ubuntuforums.org/showpost.php?p=1037880&postcount=5](http://ubuntuforums.org/showpost.php?p=1037880&postcount=5)
Take my word, this one works!

---

### Post by mellibra on 2006-05-25
Thanks, it works

---

### Post by ThaDoctor99 on 2006-05-28
Anybody who have good tips on getting PHP to work in linux ?
I really would like to get it work.
Thanks.
Greetings Tobias.

---

