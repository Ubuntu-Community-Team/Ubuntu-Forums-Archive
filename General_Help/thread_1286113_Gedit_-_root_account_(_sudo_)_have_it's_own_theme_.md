---
title: "Gedit - root account ( sudo ) have it's own theme .. how to fix it ?"
date: 2009-10-08
forum: General Help
---

### Post by OpenGuard on 2009-10-08
Ok, this is weird ( at least in my eyes ) - if I launch gedit with root privileges, it uses different theme than if I use it in normal mode ( without root privileges ). Does anybody know how to fix this ( see attached screenshot ) ?

OS: Crunchbang 9.04 ( Openbox )

---

### Post by steeleyuk on 2009-10-08
[Use this guide.]("http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/")

You should really use gksu rather than sudo.

---

### Post by OpenGuard on 2009-10-08
> **steeleyuk said:**
> [Use this guide.]("http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/")

You should really use gksu rather than sudo.

Didn't helped - still 2 different themes.

---

### Post by fragos on 2009-10-08
All users have their own themes. Root is a user. If you want the same theme, change it when you've opened gedit as administrator.

---

### Post by Joeb454 on 2009-10-08
> **fragos said:**
> All users have their own themes. Root is a user. If you want the same theme, change it when you've opened gedit as administrator.

I think that would require opening gnome-appearance-properties as root, though I'm not 100% sure.

I like the change in theme, it lets me know which apps (if any) are running as root.

---

### Post by gali98 on 2009-10-08
I'm not exactly sure how openbox stores it theme settings, but it most likely saves them in ~.
Just find where the settings are and copy them to /root.
But really I would leave it like it is. That way you know when you are editing a file as root.
Kory

---

### Post by OpenGuard on 2009-10-08
> **fragos said:**
> All users have their own themes. Root is a user. If you want the same theme, change it when you've opened gedit as administrator.

Can't do that ( and I'm pretty sure it's not possible at all .. it would be way too insecure, as you could do the same for almost any application, which could result in permission issues, etc. ).

> **Joeb454 said:**
> I think that would require opening gnome-appearance-properties as root, though I'm not 100% sure.

I like the change in theme, it lets me know which apps (if any) are running as root.

I'm starting to think that I might leave it as it is. It could be easier to work if I could see in what state my file is, just by looking at it's theme 8-[

> **gali98 said:**
> I'm not exactly sure how openbox stores it theme settings, but it most likely saves them in ~.
Just find where the settings are and copy them to /root.
But really I would leave it like it is. That way you know when you are editing a file as root.
Kory

They are in /usr/share/themes ( ~/.themes is empty ).

---

### Post by fragos on 2009-10-08
Gedit, Terminal and Nautilus all have their own themes and can be changed within those applications for the user, you or root.

---

### Post by uylug on 2009-10-08
Exactly, root can have its own appearance settings just like any regular user.

Btw, you can link root settings to yours, so that root apps use the same appearance settings as yours.

```


sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts


```

Source: [http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/](http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/)

---

### Post by OpenGuard on 2009-10-08
> **uylug said:**
> Exactly, root can have its own appearance settings just like any regular user.

How could appearance settings application know that I want to configure gedit, not my overall desktops appearance ( and vice versa ) ? From what you said, I shouldn't be able to change my desktops theme while using gedit with root privileges ? :shock:

---

### Post by gali98 on 2009-10-08
> **OpenGuard said:**
> 
They are in /usr/share/themes ( ~/.themes is empty ).

Right. But the actual settings telling openbox what theme you are using should be in your home directory. ~/.themes is probably where you can put the actual theme files, not the settings. :)
Kory

---

### Post by uylug on 2009-10-08
> **OpenGuard said:**
> How could appearance settings application know that I want to configure gedit, not my overall desktops appearance ( and vice versa ) ? From what you said, I shouldn't be able to change my desktops theme while using gedit with root privileges ? :shock:

No wait. You can't set appearance settings to gedit, can you? I think you can change your overall desktop appearance. In that case, changing **root** settings would affect **all applications run as root.**

---

### Post by OpenGuard on 2009-10-08
> **uylug said:**
> No wait. You can't set appearance settings to gedit, can you? I think you can change your overall desktop appearance. In that case, changing **root** settings would affect **all applications run as root.**

Ok, well .. now the problem is that I can't seem to find a way to launch appearance settings manager ( as root ) - what's the name of it's executable ?

---

### Post by uylug on 2009-10-08
> **OpenGuard said:**
> Ok, well .. now the problem is that I can't seem to find a way to launch appearance settings manager ( as root ) - what's the name of it's executable ?

gnome-appearance-properties

---

### Post by gali98 on 2009-10-08
> **uylug said:**
> gnome-appearance-properties

Wait a second. I thought you are on OpenBox... What is theming gtk apps?
Kory

---

### Post by uylug on 2009-10-08
> **gali98 said:**
> Wait a second. I thought you are on OpenBox... What is theming gtk apps?
Kory

Oh. Lol. Sorry, just... thought you were using GTK.

Oh well...

---

### Post by gali98 on 2009-10-08
Just making sure ;)

To the original Poster, 
This might be what you are looking for:
[http://ubuntuforums.org/showthread.php?t=109298](http://ubuntuforums.org/showthread.php?t=109298)
Kory

---

### Post by OpenGuard on 2009-10-08
> **gali98 said:**
> Just making sure ;)

To the original Poster, 
This might be what you are looking for:
[http://ubuntuforums.org/showthread.php?t=109298](http://ubuntuforums.org/showthread.php?t=109298)
Kory

[IMG]http://forums.randi.org/images/smilies/signthankspin.gif[/IMG]

---

### Post by fragos on 2009-10-08
> **OpenGuard said:**
> How could appearance settings application know that I want to configure gedit, not my overall desktops appearance ( and vice versa ) ? From what you said, I shouldn't be able to change my desktops theme while using gedit with root privileges ? :shock:

Gedit themes are set in the Preferences function of Gedit not in the System Appearances.

---

### Post by OpenGuard on 2009-10-08
> **fragos said:**
> Gedit themes are set in the Preferences function of Gedit not in the System Appearances.

Heh, that would be a nice feature :) I think you meant color schemes, not themes ?

---

### Post by gali98 on 2009-10-09
> **OpenGuard said:**
> Heh, that would be a nice feature :) I think you meant color schemes, not themes ?

I think you're right. The actual windowing theme is set by gtk AFAIK.
Kory

---

