---
title: "Super-boot-manager not working? (burg)"
date: 2011-10-16
forum: General Help
---

### Post by woodyg on 2011-10-16
I have moved to burg on my Ubuntu 11.10 and managed to install super-boot-manager. But now I get no further... when trying to install a new theme I go to burg-manager -> themes, where I double click on a theme... it seems to be installed. I click "apply changes", and changes seems to be applied, close super-boot-manager and reboot... and burg looks just like it did before I tried to install a new theme. Nothing is changed! 

Do I need to do something else?

---

### Post by sirius329 on 2011-10-16
how to install burg and super boot manager on ubuntu 11.10, the old ppa doesn't work:(

---

### Post by woodyg on 2011-10-16
> **sirius329 said:**
> how to install burg and super boot manager on ubuntu 11.10, the old ppa doesn't work:(

I think I used ppa:ingalex/super-boot-manager

---

### Post by meconio on 2011-10-16
I haven't been able to run or install neither burg nor super boot manager in 11.10, apparently the people behind burg is not working on it anymore, But I did get to install grub customizer. :(

---

### Post by woodyg on 2011-10-18
> **meconio said:**
> I haven't been able to run or install neither burg nor super boot manager in 11.10, apparently the people behind burg is not working on it anymore, But I did get to install grub customizer. :(

As I managed to install it, you should somehow be able to as well. It was a bit tricky to install BUC, but eventually I managed to get it installed. After that however, functionality is a bit hit and miss.

Is it official that there is no more development on super-boot-manager?

---

### Post by SE7EN-LOCSTA on 2011-10-18
I believe you will want to go back to the first part of burg manager, "burg-installer" and click on burg-emu. while on that screen, press t to change themes, the last one picked will be your boot menu. I think you do need BUC for this.

---

### Post by meconio on 2011-10-18
> **woodyg said:**
> As I managed to install it, you should somehow be able to as well. It was a bit tricky to install BUC, but eventually I managed to get it installed. After that however, functionality is a bit hit and miss.

Is it official that there is no more development on super-boot-manager?

As far as I know (which clearly is very little :D ) BURG development is the one that's being dropped down, not super-boot-manager.

---

### Post by woodyg on 2011-10-19
> **SE7EN-LOCSTA said:**
> I believe you will want to go back to the first part of burg manager, "burg-installer" and click on burg-emu. while on that screen, press t to change themes, the last one picked will be your boot menu. I think you do need BUC for this.

Oh... that is how it is done. It works! :D I confused installing a theme with actually changing theme, that is what I was doing wrong.

On a side note... pressing F3 gives me the choice of a resolution of either 640x480 or 800x600. My screen is 1024x600, so is it possible to change the resolution to reflect that?

---

### Post by meconio on 2011-10-24
How come this is marked as solved, seriously doubt that the problem is gone.

I have installed super boot manager, but can't use burg, it only says in the screen that burg is loading but that's it I get the same DOS like menu to choose between win7 and Ubuntu.  On the emu for burg it says that there is an error because of a unknown command "initrd" but so far I haven't find a syntax error on burg.cfg file.

---

### Post by woodyg on 2011-10-25
> **meconio said:**
> How come this is marked as solved, seriously doubt that the problem is gone.

I have installed super boot manager, but can't use burg, it only says in the screen that burg is loading but that's it I get the same DOS like menu to choose between win7 and Ubuntu.  On the emu for burg it says that there is an error because of a unknown command "initrd" but so far I haven't find a syntax error on burg.cfg file.

In my case the problem was no bug or anything, just me not understanding the application. It works fine for me on 11.10, that is all I can say...

---

### Post by meconio on 2011-10-25
Hey did you do a clean install or an upgrade from 10.10 or 11.04?

---

### Post by woodyg on 2011-10-25
> **meconio said:**
> Hey did you do a clean install or an upgrade from 10.10 or 11.04?

After a clean install of 11.10.

---

### Post by meconio on 2011-10-25
> **woodyg said:**
> After a clean install of 11.10.

Well me too, I guess that I'll just have to wait for a proper oneiric ppa.  thanks dude.

---

### Post by meconio on 2011-10-26
Got it!!!, had to do a clean install though, but it worked well, first installed grub customizer, cleaned up my OS lists a little and then I installed super-boot-manager, from there I just installed BURG and choose a theme, it worked in my two PC's with 11.10.

Apparently I messed up some config file the first time. :D

---

### Post by thongstele on 2011-10-27
> **meconio said:**
> Got it!!!, had to do a clean install though, but it worked well, first installed grub customizer, cleaned up my OS lists a little and then I installed super-boot-manager, from there I just installed BURG and choose a theme, it worked in my two PC's with 11.10.

Apparently I messed up some config file the first time. :D

**Step 1: Install Grub customizer:**
[COLOR=Black][COLOR=blue]sudo add-apt-repository ppa:danielrichter2007/grub-customizer[/COLOR]
[COLOR=blue]sudo apt-get update[/COLOR]
[/COLOR][COLOR=blue][COLOR=Black]sudo apt-get install grub-customizer[/COLOR]
**Step 2: Install Super-boot-manager:**
[/COLOR]
[LIST]
[*]sudo add-apt-repository **ppa:ingalex/super-boot-manager**
[*]sudo apt-get update && sudo apt-get install buc &#65279;super-boot-manager
[/LIST]
(Omit the error message:"unlocate...")
**Step 3: Install BURG bootloader:**
sudo add-apt-repository ppa:n-muench/burg 
sudo apt-get update  sudo apt-get install burg burg-themes

sudo burg-install "(hd0)"
sudo update-burg
sudo burg-emu[B][B]

_more options with BURG:_

[/B][/B]Press F2 To change theme .
 Press F3 to change resolution
 If you want to use  another easy way to configue burg, you need to install Burg- manager, [for this check our previuos post.]("http://www.unixmen.com/software/1072-burg-manager-install-and-configure-burg-the-easy-way")
 Here are the hot-keys defined in the boot menu:
 
[LIST]
[*]t - Open theme selection menu
[*]f - Toggle between folding mode
[*]n - Jump to the next item with the same class
[*]w - Jump to the next Windows item
[*]u - Jump to the next Ubuntu item
[*]e - Edit the command of current boot item
[*]c - Open a terminal window
[*]2 - Open two terminal windows
[*]h - Display help dialog (only available in sora theme)
[*]i - Display about dialog (only available in sora theme)
[*]q - Return to old grub menu
[*]F5/ctrl-x - Finish edit
[*]F6 - Switch window in dual terminal mode
[*]F7 - List the folded boot items
[*]F8 - Toggle between graphic and text mode
[*]F9 - shutdown
[*]F10 - reboot
[*]ESC - quit from the current popup menu or dialog.
[/LIST]



[COLOR=blue]

[/COLOR]

---

