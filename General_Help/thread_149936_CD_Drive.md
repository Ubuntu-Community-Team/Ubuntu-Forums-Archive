---
title: "CD Drive"
date: 2006-03-25
forum: General Help
---

### Post by DemonOfElru on 2006-03-25
Hello,

The button the front of my tower to open/close cd drive will operate when there is no cd in the drive.

:evil: But when there is a cd in the drive I am forced to use the eject command from within the right-click submenu instead....](*,) this is massivly annoying. 

Is there a way to fix it so that that button ejects the cd no matter what or when?:confused: 

Thank you.:mrgreen:

---

### Post by Mustard on 2006-03-25
[QUOTE=DemonOfElru]Hello,

The button the front of my tower to open/close cd drive will operate when there is no cd in the drive.

:evil: But when there is a cd in the drive I am forced to use the eject command from within the right-click submenu instead....](*,) this is massivly annoying. 

Is there a way to fix it so that that button ejects the cd no matter what or when?:confused: 

Thank you.:mrgreen:[/QUOTE]

I don't know of anyway to do it.  It's that way for a reason I believe.

---

### Post by trent dillman on 2006-03-25
I think Automatix 'fixes' this, but this has been this way in Linux for a while...

---

### Post by akiro.yamamoto on 2006-03-25
Use this trick...
```
 
sudo gedit /etc/sysctl.conf

```
Then enter this at the end of the file.....
[quote=akiro.yamamoto]
dev.cdrom.lock=0
[/quote]

Hope this info helps....
;)

---

### Post by Mustard on 2006-03-25
Ah interesting. :)  Well now I know how to do it too. ;)

---

### Post by DemonOfElru on 2006-03-25
[QUOTE=akiro.yamamoto]Use this trick...
```
 
sudo gedit /etc/sysctl.conf

```
Then enter this at the end of the file.....


Hope this info helps....
;)[/QUOTE]

Ok I'm an idiot how do you execute that script?:( 

new to ubuntu:???:

---

### Post by Mustard on 2006-03-25
Go to  Applications>>Accessories>>Terminal in your menu...open the terminal..copy and paste the command into the terminal..hit enter. Then enter your user password at the prompt.  This should open up the relevant file in the gedit text editor.  Find the line that needs to be changed.  Edit it. Save it.  Test that it works.

---

### Post by akiro.yamamoto on 2006-03-25
You may have to either re-boot or restart X ( [ALT]+[CTRL]+[BACK SPACE] ) to enable this trick... cant remember which right now. :oops:
LOL :)

---

### Post by DemonOfElru on 2006-03-25
[QUOTE=Mustard]Go to  Applications>>Accessories>>Terminal in your menu...open the terminal..copy and paste the command into the terminal..hit enter. Then enter your user password at the prompt.  This should open up the relevant file in the gedit text editor.  Find the line that needs to be changed.  Edit it. Save it.  Test that it works.[/QUOTE]

ok pasted the command and put in password, but nothing poped up.

(see image/attachment)[ATTACH]7595[/ATTACH]

---

