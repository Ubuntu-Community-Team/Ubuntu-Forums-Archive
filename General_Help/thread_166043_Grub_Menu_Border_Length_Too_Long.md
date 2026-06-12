---
title: "Grub Menu Border Length Too Long"
date: 2006-04-25
forum: General Help
---

### Post by fallout75 on 2006-04-25
Is there any way to shorten the grub menu length?
I have 3 Entries, 

1.) Windows XP
2.) Ubuntu 6.0.6
3.) Ubuntu (Recovery Mode)

The border length is to long and interfering with my custom GRUB splash image.
There is a lot of blank space after my menu options.

Is there a way to change this?

TIA

---

### Post by rado_london on 2006-04-25
I have the same problem with having Ubuntu, Win and OSX and still got the big border. I actually want to remoe all borders nad additional text. How can  I do that?

---

### Post by testube_babies on 2006-04-25
EDIT:  sorry, wrong directory. Fixed now!

```
cd /boot/grub/
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst 
```

You can comment out or delete anything you don't want/need, but be careful.  If it causes a problem do this to restore the original:
```
cd /boot/grub/
sudo cp menu.lst_backup menu.lst
```

---

### Post by fallout75 on 2006-04-25
Yes you can comment out stuff by putting a # in front of a line. 
But still, is there any way to shorten the border or remove it all together?

---

### Post by tsrjzq on 2006-04-26
[QUOTE=testube_babies]```
cd /etc/grub/
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst 
```

You can comment out or delete anything you don't want/need, but be careful.  If it causes a problem do this to restore the original:
```
cd /etc/grub/
sudo cp menu.lst_backup menu.lst
```[/QUOTE]
if you would like to edit grub menu, edit the menu.lst is ok. but it's in /boot/grub not /etc/grub

---

### Post by rado_london on 2006-05-15
Does LILO provides more customizable boot loader such as no text or border, image and 3 entries?

---

### Post by Xceptiona1 on 2006-12-06
I too would like to know if removal or changing the size of the grub border is possible. I have a nice background image/splash that looks good, but the border overlaps some graphics and if I made the border shorter by a couple lines then it would be perfect...or if I just removed the border all together.

---

