---
title: "changing the ubuntu icon next to &quot;applications&quot;?"
date: 2006-02-03
forum: General Help
---

### Post by nandasunu on 2006-02-03
Hi, I have been playing with a MacOS theme and have seen that many have the apple logo where the ubuntu logo normally resides up in the top left of the screen. I have seen the logo on this thread: [http://ubuntuforums.org/showpost.php?p=621308&postcount=26](http://ubuntuforums.org/showpost.php?p=621308&postcount=26)

How can I switch the logo from ubuntu to apple?

thanks! :D

---

### Post by tehwa on 2006-02-03
nandasunu,

Here's the location of the image you want to replace:
```
/usr/share/icons/hicolor/48x48/apps/distributor-logo.png
```
Back it up, and copy go.png to that location/filename.

Credit to vr6stress:

[http://ubuntuforums.org/showpost.php?p=389889&postcount=119](http://ubuntuforums.org/showpost.php?p=389889&postcount=119)

---

### Post by ESPOiG on 2006-02-03
good work... :D now i can change it to wateva i like

even windows:twisted:....... just jokin i wuld never deface linux like that

---

### Post by tehwa on 2006-02-04
> even windows.......

What a disturbing thought...

[IMG]http://www.tehwa.net/images/win_panel.png[/IMG]

:p

---

### Post by gamma on 2006-02-04
[QUOTE=tehwa]What a disturbing thought...

[IMG]http://www.tehwa.net/images/win_panel.png[/IMG]

:p[/QUOTE]
Nice! ;)

---

### Post by nandasunu on 2006-02-04
thanks, got it! :-D

---

### Post by Rontie on 2006-12-11
> **tehwa said:**
> nandasunu,

Here's the location of the image you want to replace:
```
/usr/share/icons/hicolor/48x48/apps/distributor-logo.png
```
Back it up, and copy go.png to that location/filename.

Credit to vr6stress:

[http://ubuntuforums.org/showpost.php?p=389889&postcount=119](http://ubuntuforums.org/showpost.php?p=389889&postcount=119)


I tried this and it changed the ubuntu icon in the systems menu next to the "About Ubuntu"

---

### Post by manny0 on 2006-12-16
> **tehwa said:**
> nandasunu,

Here's the location of the image you want to replace:
```
/usr/share/icons/hicolor/48x48/apps/distributor-logo.png
```
Back it up, and copy go.png to that location/filename.

Credit to vr6stress:

[http://ubuntuforums.org/showpost.php?p=389889&postcount=119](http://ubuntuforums.org/showpost.php?p=389889&postcount=119)

what do you mean by "copy go.png to that directory"? i replaced it with the apple icon named the same thing as the old ubuntu imagie and the ubuntu imagie is still showing up :(

---

### Post by hikaricore on 2006-12-16
> **manny0 said:**
> what do you mean by "copy go.png to that directory"? i replaced it with the apple icon named the same thing as the old ubuntu imagie and the ubuntu imagie is still showing up :(

did  you restart gnome after?

```

killall gnome
```

or just logout and log back in.

---

### Post by manny0 on 2006-12-17
When i did a killall gnome in terminal it says no processes killed . and when i restarted still has the ubuntu emblem there. i dont know where my system is pulling this image seeing is i replaced it with the apple emblem. :(

---

### Post by hikaricore on 2006-12-17
> **manny0 said:**
> When i did a killall gnome in terminal it says no processes killed . and when i restarted still has the ubuntu emblem there. i dont know where my system is pulling this image seeing is i replaced it with the apple emblem. :(

sorry I meant:

killall gnome-panel


my mistake but since you logged out and in it shouldn't matter at this point :/

sorry

---

### Post by manny0 on 2006-12-17
yea.. why am i not able to change the picture. what am i possibly doing wrong? :(

---

### Post by manny0 on 2007-01-07
I am still having trouble getting the new emblem to appear on my tool bar. its driving my crazy. i cant change it what am i doing wrong? should i be in admin or something?

---

### Post by LMP900 on 2007-01-07
Are you using the default Human theme/icons? I'm using a different icon set so I changed the file:

```
/usr/share/icons/gnome/scalable/places/start-here.svg
```

and it worked perfectly. Hope that helps :)

---

### Post by manny0 on 2007-01-07
that directory doesnt exist on my box. it stops at scalable no places folder. i have a mac icon theme. and i want that ubuntu emblem gone and i want the apple emblem there in its place. i donno whats going on.

---

### Post by Beretta_NZ on 2008-03-26
> **tehwa said:**
> nandasunu,

Here's the location of the image you want to replace:
```
/usr/share/icons/hicolor/48x48/apps/distributor-logo.png
```
Back it up, and copy go.png to that location/filename.

Here's where I run into problems, probably because I'm a noob. How do i overwrite or delete anything in that apps folder? I don't have permission.

---

### Post by Beretta_NZ on 2008-03-26
> **Beretta_NZ said:**
> Here's where I run into problems, probably because I'm a noob. How do i overwrite or delete anything in that apps folder? I don't have permission.
OK, so I figured out how to login as root and access that folder. But the same old Ubuntu icon is there in the top left after I restart.

Meh, I can't be bothered.

---

### Post by HunterK on 2008-03-26
> **ESPOiG said:**
> good work... :D now i can change it to wateva i like

even windows:twisted:....... just jokin i wuld never deface linux like that

Another disturbing thought is why people want to make Ubuntu look like other operating systems?  :confused:  There are so many variations on "Vista Themes" and "OSX themes"  I don't get it. 

I even saw a theme to make Ubuntu look exactly like XP with the blue bar and everything!!  ugh

---

