---
title: "how do i 'upgrade' to ubuntu..."
date: 2006-04-09
forum: General Help
---

### Post by master5o1 on 2006-04-09
How do I Upgrade to Ubuntu instead of Fresh new Install...

I have already installed 5.10. but would like to know for dapper drake, or another future...

Is it boot parameters crap or what?


Thanks for help...

---

### Post by dcstar on 2006-04-09
[QUOTE=master5o1]How do I Upgrade to Ubuntu instead of Fresh new Install...

I have already installed 5.10. but would like to know for dapper drake, or another future...

Is it boot parameters crap or what?


Thanks for help...[/QUOTE]
You look in the appropriate place in the forums for instructions, for example:

[http://ubuntuforums.org/showthread.php?t=74990](http://ubuntuforums.org/showthread.php?t=74990)

---

### Post by 5-HT on 2006-04-09
If you want to upgrade to dapper, first make sure you have ubuntu-desktop installed

```
 sudo apt-get install ubuntu-desktop 
``` 
Then just change all instances of "Breezy" with "Dapper" in your /etc/apt/sources.list.

It would be a good idea to only have the official Ubuntu repositories enabled when you do the upgrade (all others should have a # before them).

Note that dapper is still in development, and as such things may break on it. It is not currently recommended for use on a primary system because of this.

Also, switching to tty1 and turning off GMD would be an additional precaution I would do. Just logout of GNOME, switch to tty1 by a ctrl + alt + F1 and type ```
 sudo /etc/init.d/gdm stop 
```

To upgrade:
```
sudo apt-get update
sudo apt-get dist-upgrade 
``` 

Hope this helps.

---

### Post by master5o1 on 2006-04-09
is that when dapper cd comes out (or burn iso) or just a download while update thing through apt sorta stuff?

---

### Post by 5-HT on 2006-04-09
[LEFT]It can be either upon release or now.
The Dapper .iso is available, it's just still in development (things will change).

If you have a CD done up, you could always just pop it in and it'll automatically ask you if you want to upgrade.

You could also add the CD as a source for apt, or just let apt download the packages.
[/LEFT]

---

### Post by master5o1 on 2006-04-09
how do i do it on cd...is dapper going to be easier (anyone?) or what..

---

### Post by master5o1 on 2006-04-09
right...cool

---

