---
title: "Battery Percentage"
date: 2011-12-22
forum: General Help
---

### Post by cbennett926 on 2011-12-22
How can I display the laptop battery life in the form of a percentage?

---

### Post by satanselbow on 2011-12-22
Making the wild assumption that you would like to display it on your desktop along with other fascinating snippets of system geekery...

install conky

```
sudo apt-get install conky
```

add one or some of the following line to your ~/.conkyrc

1st one gives an estimation of charge time remaining (or says charged if on mains power)
2nd line gives you a %
3rd line displays a percentage bar

```
$battery $battery_time 
$battery_percent
$battery_bar
```

---

### Post by cbennett926 on 2011-12-22
I want the top right of the global bar in 11.10 to display battery percentage.

But I do love Conky!

---

### Post by Ms. Daisy on 2011-12-22
Sounds like you want an applet.

I found [this]("http://www.omgubuntu.co.uk/2011/02/battery-applet-status-ubuntu/"), I'm anxious to try it as soon as I can get into my Ubuntu partition on my laptop.
[QUOTE=omgubuntu.co.uk]To run ‘Battery Status’ as an Indicator-applet  in Ubuntu – including  in Unity 2D) – you’ll need to deploy the following command in a  terminal: -
```
/usr/lib/battery-status/battery-status --indicator
```To launch the indicator mode on log-in add it to your ‘Start-up applications’ in *‘System > Preferences > Startup Applications’*, entering the command above in the command field.
[/QUOTE]

---

### Post by pretty_whistle on 2011-12-22
I have Lubuntu and don't know if this will be the same on yours, but here goes:

-right click the panel>add & remove items>battery monitor>add
Another small window comes up with several things you can add.  Pick battery monitor (again) and hit "add" (again).

That's it.  Hovering the cursor over it gives %.

Edited:

Fixed typo.

---

### Post by pretty_whistle on 2011-12-22
P.S.  I retyped the last post of mine because I wrote it wrong.  So if you read it before the edit you'll need to read it again.

---

### Post by aeronutt on 2011-12-22
If you're using gnome-shell, there's an extension to see battery % here:

[https://extensions.gnome.org/](https://extensions.gnome.org/)

---

### Post by BC59 on 2011-12-22
Here you go:
[http://www.webupd8.org/2010/05/battery-status-01-released-improved.html](http://www.webupd8.org/2010/05/battery-status-01-released-improved.html)

---

### Post by satanselbow on 2011-12-22
> **cbennett926 said:**
> I want the top right of the global bar in 11.10 to display battery percentage.

But I do love Conky!

That might have been useful info to include in your initial post ;)

---

### Post by cbennett926 on 2011-12-22
Are all of these options being ran under Gnome? I have Unity, so would I have to run the 2d version?

---

### Post by BC59 on 2011-12-22
The indicator I provided above, works at least on Ubuntu 11.04 with Unity, not sure for 11.10

---

### Post by Ms. Daisy on 2011-12-22
> **BC59 said:**
> Here you go:
[http://www.webupd8.org/2010/05/batte...-improved.html]("http://www.webupd8.org/2010/05/battery-status-01-released-improved.html")

The indicator I provided above, works at least on Ubuntu 11.04 with Unity, not sure for 11.10
Nope, it doesn't work in 11.10 unity. I gave it a shot.

edit: turns out the link I provided was for the same package as BC59 provided. :(

Hopefully someone else out there has found a battery indicator applet for Unity???

---

### Post by cbennett926 on 2011-12-22
Sad day :( Perhaps on 12.04!

---

