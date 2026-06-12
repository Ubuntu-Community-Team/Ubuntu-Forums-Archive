---
title: "Xubuntu"
date: 2006-04-20
forum: General Help
---

### Post by Hoffmann on 2006-04-20
Hello;

By the way, does anyone here have experience with Xubuntu.  I am just curious about the available desktops. I have played with GNOME and KDE and, defenitely, up to now, I do prefer GNOME together with some KDE applications.

I hava a fast machine, with enough memory, etc., and I would like to know about XFCE on Ubuntu. Is it good? How do I install it. Is Synaptic the best option to install it? Can I have it in paralell to GNOME, etc?

Can I hear from you?

Thanks,
Hoffmann

---

### Post by K.Mandla on 2006-04-20
I've been tinkering with Xubuntu for about a week. I tried it some months ago when I was new to Ubuntu and didn't like it, because I only knew Gnome and couldn't find the things I wanted.

Now that I'm a teeny bit more proficient, I'm liking Xubuntu a lot better. I know how to get things to work outside of Gnome, and that helps me a lot. There are still some things I have to learn (like printer setup in Xubuntu), but for me, it's a cleaner, smoother interface.

Also, I started with the 5.10 Xubuntu, and the 6.06 version is MUCH nicer. If you decide to try it, I would suggest the newest one. It's an improvement, that's for sure.

The quickest way to install it is **sudo apt-get install xubuntu-desktop** in a terminal, and it will download and install automatically. When you log on to the computer, you can choose it via the "sessions" option (if you're installing it alongside Gnome; I don't know KDE). And if you don't like it, you can go back to Gnome.

Cheers! :D

---

### Post by dermotti on 2006-04-20
Dapper Xubuntu is friggen awesome........the older version in breezy isnt that great imho.

---

### Post by Hoffmann on 2006-04-20
[QUOTE=K.Mandla]I've been tinkering with Xubuntu for about a week. I tried it some months ago when I was new to Ubuntu and didn't like it, because I only knew Gnome and couldn't find the things I wanted.

Now that I'm a teeny bit more proficient, I'm liking Xubuntu a lot better. I know how to get things to work outside of Gnome, and that helps me a lot. There are still some things I have to learn (like printer setup in Xubuntu), but for me, it's a cleaner, smoother interface.

Also, I started with the 5.10 Xubuntu, and the 6.06 version is MUCH nicer. If you decide to try it, I would suggest the newest one. It's an improvement, that's for sure.

The quickest way to install it is **sudo apt-get install xubuntu-desktop** in a terminal, and it will download and install automatically. When you log on to the computer, you can choose it via the "sessions" option (if you're installing it alongside Gnome; I don't know KDE). And if you don't like it, you can go back to Gnome.

Cheers! :D[/QUOTE]

Hi K.Mandla,

Thanks for the prompt reply.
One more question: in the case I don't like Xubuntu, how could I uninstall it?

Cheers, :grin: 
Hoffmann

---

### Post by dermotti on 2006-04-20
**sudo apt-get remove xubuntu-desktop**

---

### Post by aysiu on 2006-04-20
Xubuntu on Breezy's okay.

Xubuntu on Dapper's great.

If you do this:

Applications > Accessories > Terminal ```
sudo aptitude update && sudo aptitude install xubuntu-desktop
``` You can try out Xubuntu, and if you don't like it ```
sudo aptitude remove xubuntu-desktop
``` will get rid of it.

**Note**: If you do ```
sudo apt-get install xubuntu-desktop
``` then ```
sudo apt-get remove xubuntu-desktop
``` will **not** remove Xubuntu. It will remove only the pointer to Xubuntu's packages, not the actual packages themselves.

---

### Post by Hoffmann on 2006-04-20
Hi aysiu,

Could you, please, explain better what do you mean by:

" Xubuntu on Breezy's okay. Xubuntu on Dapper's great."?

What differences have you noticed. I am just curious?

Hoffmann

---

### Post by aysiu on 2006-04-20
[QUOTE=Hoffmann]Hi aysiu,

Could you, please, explain better what do you mean by:

" Xubuntu on Breezy's okay. Xubuntu on Dapper's great."?

What differences have you noticed. I am just curious?

Hoffmann[/QUOTE] It just has better polish--feels more like a real desktop environment, not just a window manager (which it never was, technically, but that's how it felt in Breezy). Breezy's Xubuntu also includes GDM to manage the login screen, HAL to manage automounting, and Thunar to manage files (instead of Rox-Filer).

Best of all, the splash screen for Xubuntu Dapper is a little mouse running inside of the Ubuntu logo (as gerbils do). It's cute.

---

### Post by Hoffmann on 2006-04-20
[QUOTE=aysiu]It just has better polish--feels more like a real desktop environment, not just a window manager (which it never was, technically, but that's how it felt in Breezy). Breezy's Xubuntu also includes GDM to manage the login screen, HAL to manage automounting, and Thunar to manage files (instead of Rox-Filer).

Best of all, the splash screen for Xubuntu Dapper is a little mouse running inside of the Ubuntu logo (as gerbils do). It's cute.[/QUOTE]

After installing "additional" desktops on Breeze such as KDE of XFCE, when I upgrad to Dapper, will those "additionals" also be (automatically) upgraded? If not, what should be done?

Thanks,
Hoffmann

---

### Post by aysiu on 2006-04-20
[QUOTE=Hoffmann]After installing "additional" desktops on Breeze such as KDE of XFCE, when I upgrad to Dapper, will those "additionals" also be (automatically) upgraded? If not, what should be done?[/QUOTE] If you want to upgrade properly, you should make sure you have the appropriate metapackage installed *before* you dist-upgrade to Dapper.

For example, if you have KDE and XFCE, you should ```
sudo apt-get update
sudo apt-get install kubuntu-desktop xubuntu-desktop
``` *before* you change your /etc/apt/sources.list and ```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Hoffmann on 2006-04-20
[QUOTE=aysiu]If you want to upgrade properly, you should make sure you have the appropriate metapackage installed *before* you dist-upgrade to Dapper.

For example, if you have KDE and XFCE, you should ```
sudo apt-get update
sudo apt-get install kubuntu-desktop xubuntu-desktop
``` *before* you change your /etc/apt/sources.list and ```
sudo apt-get update
sudo apt-get dist-upgrade
```[/QUOTE]


Just to be sure that I understood your explanation:

(1) in order to upgrate Ubuntu to a new version (for example, from Breeze to Dapper), ALL I need to do is:

sudo apt-get update
sudo apt-get dist-upgrade

(2) However, if I have installed on Breeze KDE and XFCE desktops, before upgrading Ubuntu, I need to type:

sudo apt-get update
sudo apt-get install kubuntu-desktop xubuntu-desktop

And that is all. Is that correct?

Hoffmann

---

### Post by aysiu on 2006-04-20
[QUOTE=Hoffmann]
(1) in order to upgrate Ubuntu to a new version (for example, from Breeze to Dapper), ALL I need to do is:

sudo apt-get update
sudo apt-get dist-upgrade[/quote] Actually, before you do this, you should ```
sudo cp /etc/apt/sources.list /etc/apt/sources_breezy.list
sudo gedit /etc/apt/sources.list
``` and do a find/replace on the word *breezy* for the word *dapper*

> 
(2) However, if I have installed on Breeze KDE and XFCE desktops, before upgrading Ubuntu, I need to type:

sudo apt-get update
sudo apt-get install kubuntu-desktop xubuntu-desktop

And that is all. Is that correct?

Hoffmann Yes, this step needs to be done before the one I just outlined above--your sources.list should still be Breezy when you do this.

So to recap:

Step 1. Install Kubuntu and Xubuntu
Step 2. Change sources.list to Dapper
Step 3. dist-upgrade to Dapper

---

### Post by Hoffmann on 2006-04-20
aysiu:

Thanks for the prompt reply, and for the nice explanation!

Hoffmann

---

