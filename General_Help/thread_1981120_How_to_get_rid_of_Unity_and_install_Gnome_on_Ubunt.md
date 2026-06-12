---
title: "How to get rid of Unity and install Gnome on Ubuntu 12?"
date: 2012-05-16
forum: General Help
---

### Post by Meadow of Flowers on 2012-05-16
I have just installed Ubuntu 12 and feel like hurling abuse at the development team!

Can even locate a command shell and no option to log into the classic desktop.

I tried to install Gnome Shell through the Software Centre only to get an error saying 'Requires installation of untrusted packages'. Clicking OK does nothing. Clicking Repair says 'Failed to download repository information'.

I can't launch the command shell (bash or sh) through the file system browser either.

Totally useless pile of ....!!! :mad:

If there is a way to get to a command shell or install Gnome then I would appreciate someone telling me how. Otherwise its another distro and I'm not looking back.

:(

---

### Post by evilsoup on 2012-05-16
When you say command shell, you mean a terminal right?
ctrl+alt+T should work. Alternatively, hit the windows key and type 'terminal'.

Oh, and if you are trying to get back to a traditional DE, you should install gnome-panel (it's nearly the same as gnome 2). Or maybe try XFCE4.

---

### Post by philinux on 2012-05-16
> **Meadow of Flowers said:**
> no option to log into the classic desktop.


:(

Install the package gnome-panel then the classic option will be in the login screen sessions option.

---

### Post by loklaan on 2012-05-16
You might want to check out **[Mate]("http://mate-desktop.org/about/")**, which is an active fork of Gnome 2.

Ubuntu developers don't deserve any kind of abuse, and I am sure they would appreciate it if you keep a cool head when arriving at the default desktop environment for new Ubuntu releases. It is very easy, in my opinion, to change the desktop environment to anything you prefer so I don't see the point of grumbling over this when you have the freedom to change anything you want; no one is stopping you.

---

### Post by forrestcupp on 2012-05-16
The question is, why does it tell you Gnome Shell will require untrusted packages? When you get to the terminal, in one of the ways already explained to you, type:
```
sudo apt-get update
sudo apt-get upgrade
```If you get any errors, post them here in code tags. If you don't get errors, try installing Gnome Shell again with
```
sudo apt-get install gnome-shell
```I don't think you can safely remove Unity, but Gnome Shell doesn't really take that much space, and you don't ever have to boot to Unity again. Installing that should also give you the Gnome Classic choice. It's not exactly the same, but close enough.

---

### Post by misterblobby on 2012-05-16
Take the time to learn how Unity works, it is very good once you get used to it. There has been many many posts on the pros and cons on this forum, so I won't try to start another one... just give it a fair chance!

---

### Post by bhunji on 2012-05-16
+1 for gnome-panel (classic).

If only the workspaces bug was fixed (and the software center would stop crashing) :P

---

### Post by Meadow of Flowers on 2012-05-16
> **BuNsiE said:**
> Ubuntu developers don't deserve any kind of abuse, and I am sure they would appreciate it if you keep a cool head when arriving at the default desktop environment for new Ubuntu releases. It is very easy, in my opinion, to change the desktop environment to anything you prefer so I don't see the point of grumbling over this when you have the freedom to change anything you want; no one is stopping you.

Well I haven't abused anyone just yet - just said I felt like it.....

Canonical seem to want to pressure everyone on to Unity. I have no problem with ongoing development and it is reasonable to assume that touch screen computers will be more common in future, but I do not agree with the tactic of deliberately obscuring things and making life more difficult for users.

If the items I turned up in Google search are to be believed (the odd article of denial notwithstanding), Ubuntu is dropping down the Linux distro league table. Despite Canonical's denial, I suspect Unity IS playing a part in this. By all means make improvements and develop new ideas, but let users have a choice and do NOT obstruct and frustrate them in making that choice.

---

### Post by Meadow of Flowers on 2012-05-16
> **evilsoup said:**
> When you say command shell, you mean a terminal right?
ctrl+alt+T should work. Alternatively, hit the windows key and type 'terminal'.

Oh, and if you are trying to get back to a traditional DE, you should install gnome-panel (it's nearly the same as gnome 2). Or maybe try XFCE4.

Thanks for this. Yes I did mean the terminal and Ctrl-Alt-T did work.  In the end though, I decided to give Xubuntu a try since it also has XFCE4 as well.

---

### Post by Meadow of Flowers on 2012-05-16
> **misterblobby said:**
> Take the time to learn how Unity works, it is very good once you get used to it. There has been many many posts on the pros and cons on this forum, so I won't try to start another one... just give it a fair chance!

Spent a little time looking around it on 11.04. For me, its designed for a touch environment and simply doesn't work in a non-touch environment.

---

### Post by loklaan on 2012-05-16
I am sorry you feel this way. :( I gave Unity a shot and so far it is doing a great job at keeping my desktop productive when I need it to be (So many keyboard-shortcuts!). If you are still using Unity, hold down the Super key (Windows key) to bring up shortcut-key references, it might change your mind on whether you think Unity was made for touchscreens. :P

But, it's not for everyone. Has any of the suggestion from above posts worked for you so far?

> Not really too happy with this so I'm going to give Xubuntu a try since it also has XFCE4 as well
You can try installing XFCE4 from the repositories.
```
sudo apt-get install xfce4
```

---

### Post by jerome1232 on 2012-05-16
> **Meadow of Flowers said:**
> Spent a little time looking around it on 11.04. For me, its designed for a touch environment and simply doesn't work in a non-touch environment.

Yeah, okay. Sure. I get it's not for everyone, but it does work in a non touch screen environment.


At any rate your running into two separate unrelated issues.

1) For some reason your repositories are missing gpg keys, unfortunately you didn't post the output requested which we need to diagnose that problem. Please post the requested output.

2) Utter refusal to attempt basic steps to learn a new interface, I mean couldn't find a terminal? You didn't try to open the dash and type 'terminal'? If you hold the super (windows) key it will give you a comprehensive list of keyboard shortcuts.

---

### Post by loklaan on 2012-05-16
> **Meadow of Flowers said:**
> Spent a little time looking around it on 11.04. For me, its designed for a touch environment and simply doesn't work in a non-touch environment.

Unity has come ***along way*** since 11.04! :)

---

### Post by nothingspecial on 2012-05-16
User has installed Xubuntu.

Threads like these are beyond old and we don't need another one.

Closed.

---

