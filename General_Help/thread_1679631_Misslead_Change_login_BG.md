---
title: "Misslead? Change login BG"
date: 2011-02-01
forum: General Help
---

### Post by xic816 on 2011-02-01
[B]On this website; [http://www.multimediaboom.com/how-to-change-login-screen-in-ubuntu-10-1010-049-04/](http://www.multimediaboom.com/how-to-change-login-screen-in-ubuntu-10-1010-049-04/) (method 3)

It says 1. download ubuntu tweak
2. type in; [/B]**sudo add-apt-repository ppa:ubuntu-tweak-testing/ppa && sudo apt-get update**[B]
sudo apt-get install ubuntu-tweak[/B][B]&#65279;


Terminal respnds following; 
mss90@mss90-1015PEM:~$ sudo add-adp-repository ppa:ubuntu-tweak-testing/ppa && sudo apt-get update sudo apt get install ubuntu-tweak
[sudo] password for mss90: 
sudo: add-adp-repository: command not found
mss90@mss90-1015PEM:~$ sudo add-apt-repository ppa:ubuntu-tweak-testing/ppa && sudo apt-get update sudo apt-get install-tweak
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 71A3FBDD68CDF1BA1484F67A2E183FA1E260F5B0
gpg: requesting key E260F5B0 from hkp server keyserver.ubuntu.com
gpg: key E260F5B0: "Launchpad PPA for Ubuntu Tweak Testing Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
E: The update command takes no arguments
[/B][B]
What just happend when I entered the command, I hope I didn't get tricked here! ^^

Please advise 

R
[/B]

---

### Post by Krytarik on 2011-02-01
> **xic816 said:**
> [B]On this website; [http://www.multimediaboom.com/how-to-change-login-screen-in-ubuntu-10-1010-049-04/](http://www.multimediaboom.com/how-to-change-login-screen-in-ubuntu-10-1010-049-04/) (method 3)

It says 1. download ubuntu tweak
2. type in; [/B]**sudo add-apt-repository ppa:ubuntu-tweak-testing/ppa && sudo apt-get update**[B]
sudo apt-get install ubuntu-tweak[/B][B]&#65279;


Terminal respnds following; 
mss90@mss90-1015PEM:~$ sudo add-adp-repository ppa:ubuntu-tweak-testing/ppa && sudo apt-get [COLOR=Red]update sudo[/COLOR] apt get install ubuntu-tweak
[sudo] password for mss90: 
sudo: add-adp-repository: command not found
mss90@mss90-1015PEM:~$ sudo add-apt-repository ppa:ubuntu-tweak-testing/ppa && sudo apt-get update sudo apt-get install-tweak
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 71A3FBDD68CDF1BA1484F67A2E183FA1E260F5B0
gpg: requesting key E260F5B0 from hkp server keyserver.ubuntu.com
gpg: key E260F5B0: "Launchpad PPA for Ubuntu Tweak Testing Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
E: The update command takes no arguments
[/B][B]
What just happend when I entered the command, I hope I didn't get tricked here! ^^

Please advise 

R
[/B]
Notice, that since you most probably just did c&c the given commands into the console, the marked commands follow each other directly. Just enter one after the other:
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```You will find Ubuntu Tweak in "Applications -> System Tools" after the installation.

Greetings.

---

### Post by mikewhatever on 2011-02-01
Mislead, why? What did you expect to happen?
Generally speaking, adding third party repositories is a possible security risk, so if you think you might get tricked, don't do it.
Check out [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) for more info on Ubuntu Tweak.

---

### Post by xic816 on 2011-02-01
> **mikewhatever said:**
> Mislead, why? What did you expect to happen?
Generally speaking, adding third party repositories is a possible security risk, so if you think you might get tricked, don't do it.
Check out [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) for more info on Ubuntu Tweak.


Yeah ur right, I don't have much experience with terminal yett so I thaught I could make some sense out of the terminal response to the command. I didn't so I wanted to get an confimation by u guys that the command have any unknown effects. 

I have installed the programm, but don't understand what the deal with the command is, care to explain?

Thanks for reply

---

### Post by Krytarik on 2011-02-01
The commands just 

- add a software source for Ubuntu Tweak, you can handle them here: "System -> Administration -> Software Sources -> Other Software"

- update the package/software database

- install Ubuntu Tweak

---

### Post by stinkeye on 2011-02-01
The initial error of
```
sudo: add-[COLOR="Red"]adp[/COLOR]-repository: command not found
```

is because the correct command is
```
sudo add-[COLOR="Red"]apt[/COLOR]-repository
```

---

### Post by xic816 on 2011-02-01
> **stinkeye said:**
> The initial error of
```
sudo: add-[COLOR=Red]adp[/COLOR]-repository: command not found
```is because the correct command is
```
sudo add-[COLOR=Red]apt[/COLOR]-repository
```


aha, thanks a lot guys! ;)

---

### Post by uRock on 2011-02-01
If you are trying to change the login screen background, then use this strategy.> Open the terminal and run the following commands,
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```
Then logout, and you’ll see an Appearance window pop up. Change it to how you prefer it, then close it and login as usual.

When you have logged in after finishing the customizing, run this command to prevent the Appearance window from opening at the GDM screen every time,```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop


```Information found at [ubuntugeek.com]("http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html")

Cheers,
uRock

---

### Post by Krytarik on 2011-02-01
[COLOR=Black]I didn't notice that, but can even top it ;-):

issued:
[/COLOR]> sudo add-a[COLOR=Red]dp[/COLOR]-repository ppa:ubuntu-tweak-testing/ppa && sudo apt-get upda[COLOR=Red]te su[/COLOR]do ap[COLOR=Red]t g[/COLOR]et install ubuntu-tweak[COLOR=Black]
would be:
[/COLOR]```
sudo add-a[COLOR=Red]pt[/COLOR]-repository ppa:ubuntu-tweak-testing/ppa && sudo apt-get update [COLOR=Red]&&[/COLOR] sudo ap[COLOR=Red]t-g[/COLOR]et install ubuntu-tweak
```[COLOR=Black]
[/COLOR]

---

### Post by Krytarik on 2011-02-01
Probably the easiest way to change the look of GDM would be this one:
```
gksudo -u gdm dbus-launch gnome-appearance-properties
```

---

### Post by uRock on 2011-02-01
> **Krytarik said:**
> Probably the easiest way to change the look of GDM would be this one:
```
gksudo -u gdm dbus-launch gnome-appearance-properties
```
Gives this error,
```
urock@urock-desktop:~$ gksudo -u gdm dbus-launch gnome-appearance-properties
Cannot open display: 
No protocol specified

(gnome-appearance-properties:2625): Gtk-WARNING **: cannot open display: :0.0

```

---

### Post by Krytarik on 2011-02-01
> **uRock said:**
> Gives this error,
```
urock@urock-desktop:~$ gksudo -u gdm dbus-launch gnome-appearance-properties
Cannot open display: 
No protocol specified

(gnome-appearance-properties:2625): Gtk-WARNING **: cannot open display: :0.0

```
It works for me, tested it just yet again.

---

### Post by sisco311 on 2011-02-01
> **uRock said:**
> Gives this error,
```
urock@urock-desktop:~$ gksudo -u gdm dbus-launch gnome-appearance-properties
Cannot open display: 
No protocol specified

(gnome-appearance-properties:2625): Gtk-WARNING **: cannot open display: :0.0

```

Not the most elegant method... but it should work if you add gdm to the list of allowed users to make a connection to the X server:
```
xhost +SI:localuser:gdm
```

I would start a separate X session on vt8 or vt9:
```
gksudo -u gdm xinit /usr/bin/dbus-launch gnome-appearance-properties -- :3 vt9
```

---

### Post by Krytarik on 2011-02-01
> **Krytarik said:**
> It works for me, tested it just yet again.
But this has unfortunately a side-effect:

"System -> Preferences -> Keyboard -> Accessibility -> Accessibility features can be toggled by keypresses" gets set.

And an item calling "Universal Access Preferences" appears in the panel, but only for the running session.

---

### Post by uRock on 2011-02-01
> **sisco311 said:**
> Not the most elegant method... but it should work if you add gdm to the list of allowed users to make a connection to the X server:
```
xhost +SI:localuser:gdm
```

Thanks sisco. That worked.

Cheers,
uRock

---

### Post by xic816 on 2011-02-07
> **uRock said:**
> If you are trying to change the login screen background, then use this strategy.Information found at [ubuntugeek.com]("http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html")

Cheers,
uRock

Works like a charm, thx;)

---

