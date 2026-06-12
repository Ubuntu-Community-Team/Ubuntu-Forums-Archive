---
title: "Can't get plain gnome back"
date: 2010-07-15
forum: General Help
---

### Post by ironhoof on 2010-07-15
I used synaptic package manager and downloaded E16 (enlightenment)

Then I found out I couldn't get back into gnome without it. It puts its little windows in gnome EVEN when I select session "GNOME" without the -E16 tagged on.

I tried to remove it but that removes all the window borders title and minimize, close, maximize buttons(When I log out and back in)

Then I tried restarting would not boot back into ubuntu until I reinstall E16 in a new created account in root. Its got me trapped and I really do not want to reinstall...

I just want rid of it and back where I was..

---

### Post by t.rei on 2010-07-15
might be a bit harsh, but if you do the following in terminal (strg+alt+f2 => login):

[color=red]This will move all gnome settings and those of several other apps to a backup directory! Be carefull![/color]

```

sudo service gdm stop

```to stop the login manager.
```

sudo apt-get remove --purge e16

```to completely remove enlightenment
```

sudo apt-get install --reinstall gdm ubuntu-desktop ubuntu-restricted-extras

```to make shure everything needed for the default ubuntu-gnome-desktop is there and correctly installed.

```

cd /home/<yourusername>
mkdir backups
mv .gnome2 backups/gnome2_backup
mv .gnome2_private backups/gnome2_private_backup 
mv .gconf backups/gconf_backup
mv .gconfd backups/gconfd_backup
mv .compiz backups/compiz_backup
mv .config backups/config_backup

```<yourusername> obviously being your username ;)
to move ALL configuration of gnome to their corresponding backup (and due to the .config directory some more apps!)

```

sudo dpkg-reconfigure gdm

```to make shure gdm is the login-manager of your choice.

```

reboot

```to reboot.

Now, once you get to the login - make shure to select a gnome-session from the menu AFTER you selected/confirmed your username and BEFORE entering and confirming the password.

You should end up in a default ubuntu-desktop.

---

### Post by sarim on 2010-07-15
remove E16 from synaptic.

if windows border disappears then run the following command's in terminal, of by Pressing ALT + F2

```
 metacity --replace &
gtk-window-decorator --replace &
```

---

### Post by ironhoof on 2010-07-15
I will try it right away!

---

### Post by ironhoof on 2010-07-15
It worked everything is back!! to default...
Both of you helped I couldn't use the terminal without 

Sarim's

metacity --replace &

Then T.Rei's fix did the job!

I have to rearrange everything again... (I customize my panels A LOT)

I thank you both very very very much! 

I thought I knew a lot but this was a new one for me.
I can now get to bed after wasting 3 hours..

---

