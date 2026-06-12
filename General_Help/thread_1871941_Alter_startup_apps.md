---
title: "Alter startup apps?"
date: 2011-10-29
forum: General Help
---

### Post by linuxuser12345 on 2011-10-29
Where do I go to alter all my startup applications in Ubuntu 11.10?

---

### Post by haqking on 2011-10-29
> **linuxuser12345 said:**
> Where do I go to alter all my startup applications in Ubuntu 11.10?

The top right cog you can see some however things have changed.



in some .desktop Part of the config is NoDisplay=true statement which you need to change to false if you want it listed.

Edit. Link for more information.[http://askubuntu.com/questions/66910/what-happened-to-to-the-startup-application-preferences](http://askubuntu.com/questions/66910/what-happened-to-to-the-startup-application-preferences)

---

### Post by linuxuser12345 on 2011-10-29
I am confused. What application do I type in the terminal that lets me alter my startup apps? I know there is one, I just forgot, and that link didn't help me :(

---

### Post by cbowman57 on 2011-10-29
gnome-session-properties

---

### Post by haqking on 2011-10-29
> **linuxuser12345 said:**
> I am confused. What application do I type in the terminal that lets me alter my startup apps? I know there is one, I just forgot, and that link didn't help me :(

you mean you want to add a new app to startup ?

The link i provided was so that you can re-populate the current list with the apps set to start up automatically as they no longer show by default.

if you want to add a new app to startup then like i said go to cog in top right corner and choose startup applications or click your dash icon and type startup and it will auto appear

edit: or yes as above if you want to launch it from terminal

---

### Post by linuxuser12345 on 2011-10-29
gnome-session-properties does not show all the actions that Ubuntu performs at startup.

---

### Post by haqking on 2011-10-29
> **linuxuser12345 said:**
> gnome-session-properties does not show all the actions that Ubuntu performs at startup.

I know which is what i said in my original post.

The apps do not show by default anymore.

If you want them to you need to change the .dekstop file properties to show NoDisplay=false

as outlined in the link i posted

or are you not talking about start up applications, because that was what you said.

---

### Post by linuxuser12345 on 2011-10-29
Okay. I will try to figure it out! lol
I will come back if I need any help! :)

---

### Post by haqking on 2011-10-29
> **linuxuser12345 said:**
> Okay. I will try to figure it out! lol
I will come back if I need any help! :)

if you look in

```
/etc/xdg/autostart
```

you will see a bunch of apps with a .desktop filename

if you

```
cat example.desktop
```

you will see a field that says NoDisplay=true

which means it is set to be hidden, if you change it to false then it will show in the startup applications applet

so for example to show the gnome startup sound

```
sudo nano /usr/share/gnome/autostart/libcanberra-login-sound.desktop
```

and change field from 

NoDisplay=true

to 

NoDisplay=false

---

