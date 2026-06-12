---
title: "Editing Applications Menu"
date: 2009-11-05
forum: General Help
---

### Post by joelw135 on 2009-11-05
In the left hand corner is the Applications menu with its sub folders. How do I edit an application path in the sub folder? I have installed the latest versions of Firefox and Thunderbird and now the buttons for them in the Networks tab no longer work. I need to edit them. Thanks.

---

### Post by Giblet5 on 2009-11-05
Right-click the menu.

Select "Edit Menus..."

---

### Post by scouser73 on 2009-11-05
Right click on the ubuntu logo and edit the menus from that way.

---

### Post by Giblet5 on 2009-11-05
> **scouser73 said:**
> Right click on the ubuntu logo and edit the menus from that way.

Ever read much? ;)

---

### Post by joelw135 on 2009-11-05
> **scouser73 said:**
> Right click on the ubuntu logo and edit the menus from that way.

I tried what you said by right clicking and get no dialog to edit the menu.

---

### Post by joelw135 on 2009-11-05
> **Giblet5 said:**
> Right-click the menu.

Select "Edit Menus..."

When I right click there is no such item "Edit Menus"

---

### Post by MattM11 on 2009-11-05
I don't think there's any easy way to do this. It's one of the more annoying aspects of Xubuntu.

The following *might* work...

Go to usr/share/applications and copy/paste the Firefox and Thunderbird files there to your /home folder. 

Right-click, select "properties" and then edit the command line (from firefox to firefox3.5 - or whatever) under "launcher". 

Then use the terminal to copy the files back into the original directory (overwriting the existing ones).

I've not tried this myself - so you may want to wait for someone with more experience.

---

### Post by joelw135 on 2009-11-05
> **MattM11 said:**
> I don't think there's any easy way to do this. It's one of the more annoying aspects of Xubuntu.

The following *might* work...

Go to usr/share/applications and copy/paste the Firefox and Thunderbird files there to your /home folder. 

Right-click, select "properties" and then edit the command line (from firefox to firefox3.5 - or whatever) under "launcher". 

Then use the terminal to copy the files back into the original directory (overwriting the existing ones).

I've not tried this myself - so you may want to wait for someone with more experience.

I think that is way above my skill level. I guess I have to go back to Ubuntu.

---

### Post by MattM11 on 2009-11-05
It's probably a lot easier than I make it sound. I've never had to edit the menu, which is why I sound so reticent. I'd hate to think I screwed up someone else's system!

This may be a stupid question - but have you tried restarting the computer? I know that in the past I've installed apps that haven't shown up in the menu until I've done a restart.

---

### Post by Penguin Guy on 2009-11-05
> **joelw135 said:**
> When I right click there is no such item "Edit Menus"
Then try pressing [COLOR="Green"]Alt + F2[/COLOR] and typing [COLOR="green"]alacarte[/COLOR] (French for 'menu') into the box that appears.

---

### Post by joelw135 on 2009-11-05
> **Penguin Guy said:**
> Then try pressing [COLOR="Green"]Alt + F2[/COLOR] and typing [COLOR="green"]alacarte[/COLOR] (French for 'menu') into the box that appears.

I am going to reinstall as I think there is a problem. Thanks.

---

### Post by Marlonsm on 2009-11-05
Go to System > Preferences > Main Menu.
There you can edit the menus.

---

### Post by joelw135 on 2009-11-05
> **Marlonsm said:**
> Go to System > Preferences > Main Menu.
There you can edit the menus.

Main Menu is missing there to, I am going to reinstall now as I think something is screwed up. Better safe than sorry.

---

### Post by Giblet5 on 2009-11-05
> **joelw135 said:**
> Main Menu is missing there to, I am going to reinstall now as I think something is screwed up. Better safe than sorry.

That's not necessary.

Open a terminal window and copy/paste these commands. They will reset your login to all the default values, saving everything in case you ever want it back.

```
mkdir dotbackup
mv .gconf* .config* .kde* dotbackup
sudo /etc/init.d/gdm restart
```

Cool, huh? :)

---

### Post by joelw135 on 2009-11-05
> **Giblet5 said:**
> That's not necessary.

Open a terminal window and copy/paste these commands. They will reset your login to all the default values, saving everything in case you ever want it back.

```
mkdir dotbackup
mv .gconf* .config* .kde* dotbackup
sudo /etc/init.d/gdm restart
```

Cool, huh? :)

Thanks, but I already am reinstalling the system. Since all I did was install Thunderbird latest version and Firefox latest version I am not to far behind. If I still have problems I will get back. Thanks.

---

### Post by Giblet5 on 2009-11-05
> **joelw135 said:**
> Thanks, but I already am reinstalling the system. Since all I did was install Thunderbird latest version and Firefox latest version I am not to far behind. If I still have problems I will get back. Thanks.

It's your system!

(That will fix it though. In about 10 seconds.)

---

### Post by joelw135 on 2009-11-05
> **Giblet5 said:**
> It's your system!

(That will fix it though. In about 10 seconds.)

You are right, but I jumped the gun as I have worked on this since last night, and just got annoyed!

---

### Post by Giblet5 on 2009-11-05
> **joelw135 said:**
> You are right, but I jumped the gun as I have worked on this since last night, and just got annoyed!

We've all been there a time or ten.

Keep that trick in mind though. It's a great way to "start over" without losing your files, data, and installed packages.

---

### Post by joelw135 on 2009-11-05
> **Penguin Guy said:**
> Then try pressing [COLOR="Green"]Alt + F2[/COLOR] and typing [COLOR="green"]alacarte[/COLOR] (French for 'menu') into the box that appears.

OK I am back and still have no way to edit the menu. I find no menu editor anywhere.

---

### Post by demosthenese on 2009-11-05
You may have to wait for Xfce 4.8 for easily editable menus

[What-can-we-expect-in-Xfce-4.8-For-the-menu...]("http://jeromeg.blog.free.fr/index.php?post/2009/02/17/What-can-we-expect-in-Xfce-4.8-For-the-menu...")

---

### Post by joelw135 on 2009-11-05
> **demosthenese said:**
> You may have to wait for Xfce 4.8 for easily editable menus

[What-can-we-expect-in-Xfce-4.8-For-the-menu...]("http://jeromeg.blog.free.fr/index.php?post/2009/02/17/What-can-we-expect-in-Xfce-4.8-For-the-menu...")

Looks good, but how long before we have it?

---

