---
title: "Change Cursor in 11.10?"
date: 2011-11-20
forum: General Help
---

### Post by Spyderkid on 2011-11-20
I've been wanting to customize my Ubuntu more but 11.10 doesn't make it easy for you...

Is there a way I can change the cursor without editing important files...


I've used Ubuntu Tweak to change the cursor but it doesn't seem to completely work 


thanks :)

---

### Post by Bobhuber on 2011-11-20
> **Spyderkid said:**
> I've been wanting to customize my Ubuntu more but 11.10 doesn't make it easy for you...

Is there a way I can change the cursor without editing important files...


I've used Ubuntu Tweak to change the cursor but it doesn't seem to completely work 


thanks :)
It's not just 11.10 . The problems been around for quite a while (as early as 9.04 I think). The cursor will change in apps (firefox etc.) but not on the desktop. I have no clue as to why the developers either refuse or can't fix the problem. I've done it for my visually impaired mother but it's been quite a while ago and was not an easy thing to do. May be someone else can shed a bit more light on the subject. I'd love to see some responses to this one.

---

### Post by Frogs Hair on 2011-11-20
I have only noticed this in Opera  since I started using it on 10.04 . Regardless of what cursor theme the system uses Opera appears to be using its own theme or it draws the cursor theme differently than other applications .  :confused:

---

### Post by Spyderkid on 2011-11-20
yeah, the icon theme works fine appart from the normal pointer, and the resize pointer...

---

### Post by Spyderkid on 2011-11-22
So any solutions anyone :)?

---

### Post by Spyderkid on 2011-11-25
*cheeky little bump*

---

### Post by stinkeye on 2011-12-04
I've been messing around with this and in 11.10 if I change the file at 
```
/usr/share/icons/DMZ-White/cursor.theme
```
The cursor theme will change correctly after log out/in.[COLOR="Red"]**[/COLOR]See below
The file seems to be linked in a roundabout way to the **/usr/share/icons/default/index.theme** file.

eg 
```
gksudo gedit /usr/share/icons/DMZ-White/cursor.theme
```
```
[Icon Theme]
Inherits=[COLOR="Magenta"]DMZ-White[/COLOR]
```
[COLOR="magenta"]Change to new cursor theme as shown in /usr/share/icons[/COLOR]


You can do this in terminal with
```
sudo sh -c "echo '[Icon Theme]\nInherits=[COLOR="magenta"]DMZ-White[/COLOR]' > /usr/share/icons/DMZ-White/cursor.theme"
```
[COLOR="magenta"]Name of new theme[/COLOR]

[COLOR="Red"]**[/COLOR]You also need to change the setting in dconf with
```
gsettings set org.gnome.desktop.interface cursor-theme "[COLOR="Magenta"]DMZ-White[/COLOR]"
```
[COLOR="magenta"]Name of theme[/COLOR]


Then
```
sudo service lightdm restart
```

---

### Post by stinkeye on 2011-12-04
Been playing around and made a script that will do this for you.
It will list files in /usr/share/icons
where you can copy/paste to an input line (not all files listed are cursor themes)
It will edit the /usr/share/icons/DMZ-White/cursor.theme file and
change the dconf setting.
Then it will ask if you want to restartx.
Save as **change_cursor.sh** in your home folder and make executable.
```
#!/bin/bash

ls -1 --color=auto /usr/share/icons
echo -e '\nCopy and paste cursor theme from above and press Enter.\n*All listings may not be cursor themes.'
read Theme
gsettings set org.gnome.desktop.interface cursor-theme "$Theme" &
sudo sh -c "echo '[Icon Theme]\nInherits=$Theme' > /usr/share/icons/DMZ-White/cursor.theme"

read -p "Do you wish to restartx?(y/n):"
      if  [ "$REPLY" != "y" ] 
      then echo "You need to log out to complete cursor change."
 else 
      sudo service lightdm restart
fi 
```

to run use
```
./change_cursor.sh
```

---

### Post by Spyderkid on 2011-12-04
thanks :)

---

### Post by Spyderkid on 2011-12-04
you seem to know what your doing bash wise,
could you look at my other thread... [http://ubuntuforums.org/showthread.php?t=1890860](http://ubuntuforums.org/showthread.php?t=1890860)

---

### Post by stinkeye on 2011-12-04
> **Spyderkid said:**
> you seem to know what your doing bash wise,
could you look at my other thread... [http://ubuntuforums.org/showthread.php?t=1890860](http://ubuntuforums.org/showthread.php?t=1890860)
Nah, fooled you there.
I just look at other scripts and mix and match until it works.
Don't know the nuts and bolts of scripting.

If I could help I would.
:-$;-)

---

### Post by Spyderkid on 2011-12-04
aah ;), Do you mind if I add that script too my HOW TO: thread?

the thread is about changeing the icon theme and general theme in ubuntu 11.10 and I thought adding in how to change cursors a good addition :D

---

### Post by Spyderkid on 2011-12-04
Added attachments with 5 cursors I really like, (the third one is my favourite, it's basically windows 7 cursor, but instead of the blue swirley thing for the loading cursor, it's a rotating ubuntu logo)... Very cool

---

### Post by stinkeye on 2011-12-04
> **Spyderkid said:**
> aah ;), Do you mind if I add that script too my HOW TO: thread?

the thread is about changeing the icon theme and general theme in ubuntu 11.10 and I thought adding in how to change cursors a good addition :D
Sure,no problem.

> **Spyderkid said:**
> Added attachments with 5 cursors I really like, (the third one is my favourite, it's basically windows 7 cursor, but instead of the blue swirley thing for the loading cursor, it's a rotating ubuntu logo)... Very cool
I just tried Ubuntaero.....Not bad...clean and simple
May stick with it.
I use the GartoonRedux icons and the ComixCursors go well with it.

---

### Post by Spyderkid on 2011-12-04
Cool :D

I also quite like the Oxygen cursors which are available from the software centre

---

