---
title: "Issue with ubuntu tweak and login screen"
date: 2011-01-09
forum: General Help
---

### Post by LetsMugSanta on 2011-01-09
Yeah so I was trying to change the login screen using ubuntu tweak so that it was the same picture as my background but instead of using the background it is just flat purple. This is the same for two different computers. Anyone know how to fix this?

---

### Post by nomko on 2011-01-09
Forget Ubuntu tweak. use a tool called GDM2setup.

- Open a terminal
- type in: **sudo add-pt-repository ppa:gdm2setup/gdm2setup**
- type in: **sudo apt-get update**
- type in: **sudo apt-get install python-gdm2setup**

Now you can alter your login screen.

---

### Post by LetsMugSanta on 2011-01-09
[B]add-pt-repository

That command was not recognized.
[/B]

---

### Post by stinkeye on 2011-01-10
> **LetsMugSanta said:**
> [B]add-pt-repository

That command was not recognized.
[/B]
The correct command is 
```
add-apt-repository
```
but that ppa does not update for me.


You can change your login background, theme, etc by entering in the terminal
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```

Log out then select the style you want at the login from the Appearance window that pops up.
This will only affect the login appearance.


Then log in and execute 
```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```
to remove **gnome-appearance-properties** from the login window.

---

### Post by nomko on 2011-01-10
> **stinkeye said:**
> The correct command is 
```
add-apt-repository
```
but that ppa does not update for me.
 
 
You can change your login background, theme, etc by entering in the terminal
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```
 
Log out then select the style you want at the login from the Appearance window that pops up.
This will only affect the login appearance.
 
 
Then log in and execute 
```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```
to remove **gnome-appearance-properties** from the login window.
 
Correct, it's **add-apt-repsoitory**! 
 
But why doesn't it work for you?

---

### Post by stinkeye on 2011-01-10
> **nomko said:**
> Correct, it's **add-apt-repsoitory**! 
 
But why doesn't it work for you?
After adding the ppa with
```
sudo add-apt-repository ppa:gdm2setup/gdm2setup
```

When I run 
```
sudo apt-get update
```

I get this error...
```
W: Failed to fetch http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
```


Even though this is how the ppa says to install [**_[COLOR="DarkRed"]https://launchpad.net/gdm2setup[/COLOR]_**]("https://launchpad.net/gdm2setup")

---

### Post by Frogs Hair on 2011-01-10
Your problem may be more complicated , but when using the login settings in Ubuntu Tweak you must use Quit to apply changes or screen will default to Ubuntu purple.

---

### Post by LetsMugSanta on 2011-01-10
Yeah so I tried what you did nomko with the correct apt. and it seemed as everything worked well in the terminal but what do I do now. And I tried what you did frogs hair and that didn't work.

All I want to do is have my login screen as the same picture as my background. Should I try making a copy and placing it somewhere else and see if that works? Instead of having the same file access both?

---

### Post by stinkeye on 2011-01-10
Alt+F2 and run 
```
gksudo gdm2setup
```

or
Try what I said in post #4.
That works.

---

### Post by LetsMugSanta on 2011-01-10
Yeah that worked stinkeye. Thanks for the help

---

