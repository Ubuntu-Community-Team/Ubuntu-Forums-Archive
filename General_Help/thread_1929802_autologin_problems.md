---
title: "autologin problems"
date: 2012-02-22
forum: General Help
---

### Post by MacHaddock on 2012-02-22
Ok so I've installed Lubuntu 11.10 and I'm trying to set autologin doing stuff like this:

[http://ubuntuforums.org/showthread.php?p=11709026#post11709026]("http://ubuntuforums.org/showthread.php?p=11709026#post11709026")

Now that doesn't work and I get an error message saying:

Xsession: unable to launch "gnome-falleback" X session -- "nome-fallback" not found; falling back to default session.

I click ok and some sort of skeletal lubuntu session starts.

Now here comes the strange part. When I change the lxdm back the new problem doesn't go away.

maybe worth mentioning is that I have my /home and my / on different partitions.

---

### Post by MacHaddock on 2012-03-02
bump ;(

---

### Post by ankspo71 on 2012-03-02
Hi,
Is gnome-fallback listed in /etc/lxdm/default.conf? If it is, then check to see if gnome-fallback still installed. If gnome-fallback doesn't exist anymore then "gnome-fallback" should be removed from /etc/lxdm/default.conf and replaced with something else.

Here is a copy of my /etc/lxdm/default.conf from Lubuntu 11.10. The only changes I have made was on the 3rd line to enable my autologin.
```
[base]
## uncomment and set autologin username to enable autologin
autologin=ankspo71

## uncomment and set timeout to enable timeout autologin,
## the value should >=5
# timeout=10

## default session or desktop used when no systemwide config
session=/usr/bin/startlubuntu

## uncomment and set to set numlock on your keyboard
# numlock=0

## set this if you don't want to put xauth file at ~/.Xauthority
# xauth_path=/tmp

## greeter used to welcome the user
greeter=/usr/lib/lxdm/lxdm-greeter-gtk

[server]
## arg used to start xserver, not fully function
# arg=/usr/bin/X -background vt1

[display]
## gtk theme used by greeter
gtk_theme=Clearlooks

## background of the greeter
bg=/usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png

## if show bottom pane
bottom_pane=1

## if show language select control
lang=1

## if show keyboard layout select control
keyboard=0

## the theme of greeter
theme=Lubuntu

[input]

[userlist]
## if disable the user list control at greeter
disable=0

## whitelist user
white=

## blacklist user
black=


```


Also, if you have installed Gnome at one time, then there is also a chance that you are not using LXDM as your default display manager anymore. Installing Gnome will install GDM, so GDM might be the display manager currently in use. This might explain why the changes made to /etc/lxdm/default.conf didn't help autologin or correct the problem afterwards.

To check your default display manager, you can use this command:
```
cat /etc/X11/default-display-manager
```

I only have one display manager installed and it says:
/usr/sbin/lxdm

To identify the skeletal looking Lubuntu desktop, you can use this command:
```
echo $DESKTOP_SESSION
```
You are probably looking at the plain LXDE desktop, the desktop which Lubuntu's desktop is based upon.

Hope this helps.

---

### Post by MacHaddock on 2012-03-04
thanks but none of that helped. Gnome fallback isn't listed.

---

