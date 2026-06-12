---
title: "screen resolution and monitor plymouth prob??"
date: 2011-06-13
forum: General Help
---

### Post by gene simmons on 2011-06-13
hi all,i recently found a post that had the same plymouth booting to text only issue i was having so i folowed the instructions and loaded the script.when it got to the resolution part i put in 800x600 24bit as i have a acer netbook and i think the default is to large,when i rebooted my plymouth came up yaaaa prob solved but the plymouth was very wide and poor quality,also before the pymouth the screen turned pixely and when the desktop came on it was very poor qualilty,i went to system preference monitor and it says unknown and none of the opetions there are available to me,i used terminal and tryped x{somthing} for checking minimum and maximum and it said failed to load.what can i try,the resolution now is ugly and wayyyyyyy to big for my little netbook. thanx guys

---

### Post by gene simmons on 2011-06-13
ok i have been on the pc a bit this morning so i must add that it also has no effects,i had minimize and maximaize effects in cccm and thier not working,wow i dont know what i did but i screwed it up bad haha. heres a link to the script i got from a post on here

[Fix Plymouth on Ubuntu after installing NVIDIA or ATI proprietary drivers for Ubuntu 11.04 Natty | Paolo Bernardi’s Weblog]("http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/")

---

### Post by Ronalddig on 2011-06-13
> **gene simmons said:**
> ok i have been on the pc a bit this morning so i must add that it also has no effects,i had minimize and maximaize effects in cccm and thier not working,wow i dont know what i did but i screwed it up bad haha. heres a link to the script i got from a post on here

[Fix Plymouth on Ubuntu after installing NVIDIA or ATI proprietary drivers for Ubuntu 11.04 Natty | Paolo Bernardi’s Weblog]("http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/")

i did same but i still dont get boot splash

---

### Post by stinkeye on 2011-06-13
This fix worked for me on Natty after installing the nvidia driver.

[SIZE="2"]**_Fix for only showing briefly_**[/SIZE]

create this file.

```
gksudo gedit /etc/initramfs-tools/conf.d/splash
```
and add this option 
```
FRAMEBUFFER=y
```
save the file.

Then

Code:
```
sudo update-initramfs -u
```




[SIZE="2"]**_Fix for showing text instead of logo_**[/SIZE]

```
gksudo gedit /etc/default/grub
```

add 
```
GRUB_GFXPAYLOAD_LINUX="[COLOR="#ff00ff"]1680x1050[/COLOR]"
```

using your [COLOR="#ff00ff"]monitor's native resolution[/COLOR]
Save file.

then run
```
sudo update-grub
```

---

### Post by gene simmons on 2011-06-13
is there a way to undo the script that was posted,ive tried quite a few things and i cant get my resolution changed,my desktop looks awful and compiz effects are not working.i folowed the instructions for the script and yes my plymouth is working but at a steep cost,is there a way to undo scripts.i hope i dont have to do a complete uninstall and reinstall.well maybe thats an excuse to try easy bcd for dual booting instead of wubi haha

dave:(

---

### Post by gene simmons on 2011-06-13
any sugestions on this resolution issue,i hope to get this figured out,its so ugly haha

---

