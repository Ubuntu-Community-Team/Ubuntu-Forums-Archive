---
title: "Lightweight fast web browser"
date: 2010-08-11
forum: General Help
---

### Post by rmcellig on 2010-08-11
I have the latest version of Ubuntu. At the moment I am using Firefox and was wondering if there is a fast lightweight browser for Ubuntu that I can use instead. This goes for other apps as well. If someone can provide a list of lightweight alternatives or point me to a site that lists them, that would be great!!!

---

### Post by dv3500ea on 2010-08-11
Lightweight Browsers:
[LIST]
[*][chromium]("apt:chromium-browser")
[*][midori]("apt:midori")
[*][epiphany]("apt:epiphany-browser")
[/LIST]

Lightweight Desktop Environments/Window Managers:
[LIST]
[*][LXDE]("apt:lxde")
[*][openbox]("apt:openbox")
[*][fluxbox]("apt:fluxbox")
[*][icewm]("apt:icewm")
[*][XFCE]("apt:xfce")
[/LIST]

Lightweight Documents:
[LIST]
[*][LyX]("apt:lyx") (not sure how lightweight this is but it is very good; for extreme lightweight use plain latex.
[*][abiword]("apt:abiword")
[*][gnumeric]("apt:gnumeric")
[/LIST]

The LXDE apps are all lightweight; they include music player, file manager, text editor etc.

---

### Post by rmcellig on 2010-08-11
Thanks so much for the info!! Are there detailed instructions on how I can install LXDE on top of my Ubuntu 10.04? Can I switch between the LXDE distro and my current Ubuntu installation?

I am trying to find the easiest and most straight forward way to do this. Thanks again in advance!! Much appreciated!!

---

### Post by ubunterooster on 2010-08-11
First, the above mentioned Chromium-browser is Not, let me repeat NOT, lightweight.

to get lxde 

```
sudo apt-get install lubuntu-desktop
```Log out (not turn off) and when going to log back in, notice the menu titled "sessions". Click that, choose lubuntu (it might say lxde instead of lubuntu) and then log in

---

### Post by AlphaLexman on 2010-08-11
Well in System -> Administration -> 'Synaptic Package Manager'...
in the search box enter lxde, and click the checkbox next to the package named lxde where it says mark for installation. Then click the 'apply' button, synaptic will dowload all the dependencies you need.

At next login, when you click or enter or username, at the bottom of the login screen, is a box that says 'session' it may say 'gnome' or 'default' either way click on it and choose 'lxde' enter your user password and you're in lxde, a lightweight desktop environment!

---

### Post by Ozymandias_117 on 2010-08-11
> **ubunterooster said:**
> First, the above mentioned Chromium-browser is Not, let me repeat NOT, lightweight.

to get lxde 

```
sudo apt-get install-lubuntu-desktop
```

Log out (not turn off) and when going to log back in, notice the menu titled "sessions". Click that, choose lubuntu (it might say lxde instead of lubuntu) and then log in

That would be ```
sudo apt-get install lubuntu-desktop
```

---

### Post by ubunterooster on 2010-08-11
> **Ozymandias_117 said:**
> That would be ```
sudo apt-get install lubuntu-desktop
```
Thank-you for the correction; :D I have edited my above post.

---

### Post by dv3500ea on 2010-08-12
> **rmcellig said:**
> Thanks so much for the info!! Are there detailed instructions on how I can install LXDE on top of my Ubuntu 10.04? Can I switch between the LXDE distro and my current Ubuntu installation?

I am trying to find the easiest and most straight forward way to do this. Thanks again in advance!! Much appreciated!!

You can just click on the [LXDE]("apt:lxde") link above to install it. Once installed, you can choose your desktop environment from the login screen.

---

### Post by VCoolio on 2010-08-12
> **rmcellig said:**
> I have the latest version of Ubuntu. At the moment I am using Firefox and was wondering if there is a fast lightweight browser for Ubuntu that I can use instead. This goes for other apps as well. If someone can provide a list of lightweight alternatives or point me to a site that lists them, that would be great!!!

Here you go: [http://wiki.archlinux.org/index.php/Lightweight_Applications](http://wiki.archlinux.org/index.php/Lightweight_Applications)
Lxde is ok, but if you tweak the startup applications / daemons in ubuntu and then use whatever apps you like you have more or less the same result.

---

### Post by rmcellig on 2010-08-12
Thank you so much for all of your help!! I will try installing through the Synaptic Package Manager. This way if I want to delete it later on I can do so my using the SPM. I cannot get over all the options available! Even though I spend a lot of time with my Mac and to a certain degree my Mac running Windows 7 under VMware Fusion, Ubuntu and everything else that goes with it is pretty impressive!

---

