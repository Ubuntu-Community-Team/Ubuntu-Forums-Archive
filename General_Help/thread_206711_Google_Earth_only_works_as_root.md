---
title: "Google Earth only works as root"
date: 2006-06-30
forum: General Help
---

### Post by chrisccoulson on 2006-06-30
I've installed GE4 on my machine, but, when I run it as a normal user, it only displays a black screen. If I go to Tools => Options, all settings seem to be grayed out.

However, if I sudo googleearth, it runs fine and I have access to all of the options.

I know this seems like some sort of access problem, but I don't know what. Permissions on /usr/local/google-earth are set to 755. I've tried setting them to 777 but it made no difference. I have full access to the .googleearth profile folder within my home folder. My user account is set to be able to use video hardware accelaration (via System => Administration => Users and Groups in GNOME).

I'm not really sure what else to try. Does anyone else have a similar problem?

---

### Post by jstueve on 2006-06-30
sudo chmod -R username:username ~/.googleearth

('course use YOUR username... running google earth from the install script installs the .googleearch directory, which of course now has root privs, since you installed using sudo)

---

### Post by remarks on 2006-06-30
[QUOTE=jstueve]sudo chmod -R username:username ~/.googleearth

('course use YOUR username... running google earth from the install script installs the .googleearch directory, which of course now has root privs, since you installed using sudo)[/QUOTE]


sudo **chown** -R username:username ~/.googleearth/

---

### Post by chrisccoulson on 2006-07-01
Thanks for the help. I did a chown -R and a chmod -R on .googleearth and it seems to be working fine now:)

---

### Post by gmenezesg on 2008-04-29
Just remove the directories ".config/Google/" and ".googleearth" from your home dir and start the application again. Worked for me.

---

### Post by dmrazor on 2008-06-02
Can confirm that both the chown and gmenezsg's solutions are working. I checked the "~/.config/Google" dir on my setup and it was owned by root:root. chown-ing to my own useraccount made googleearth startup just fine, but to be on the safe side I removed both dir's mentioned to see them recreated with the correct permissions on first run.

Raz.

---

