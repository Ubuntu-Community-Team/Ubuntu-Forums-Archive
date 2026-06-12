---
title: "Easy Guide to get new icons and stuff?"
date: 2010-01-28
forum: General Help
---

### Post by lucas777 on 2010-01-28
Just installed 9.10 and bloody loving it, Even though i love my Windows 7, This is just great learning all about Linux. Install was a breeze and installing normal apps are fine, but when we get to stuff like changing icons and stuff, this is just way over my head. All i want is icons that sort of look like MAC icons or Glass type icons, i downloaded a set from Deviantart and im that retarted i cant even follow the instructions...

[ReadMe to black-white 2 

1.Change your main menu icon
2.different folder icons

1.-add a "Main Menu" to your panel
 -run gconf-editor
 -navigate to /app/panel/objects
 -find a object_x with the "object_type=menu-object".
 - tick up "use_custom_icon"
 -type in "custom_icon" start-here1, start-here2, ... , start-here11
 - if you doesn't like any of this icons you can browse here to an image of your choice

2.In this version I add some different icons for your downloads, documents, music,... folder.  
 -To use them you must unpack the tar.gz package.
 -right click on the folder you wants to change and presspreference    
 -click on the folder icon and browse to the unpacked black-white2.tar.gz folder and go on to /  scalable/places (sometimes /scalable/places/256)    
 -choose your folder and press open.]


These kind of instructions are way to advanced for a everyday windows user.. Are there any other easier guides out there to do this kind of stuff?

Cheers

---

### Post by skymera on 2010-01-28
I generally download icons from Gnome-Look.

Extract the archive to my home then move it to /usr/share/icons

```
 sudo cp -R /home/$USER/iconfolder /usr/share/icons 
```

you can then choose the icons in System > Preferences > Appearence

---

### Post by vandorjw on 2010-01-28
I also download from gnome-look.
Save it anywhere on your computer and do not extract the .gz files, just keep them as they are.

Click System ---> preferences ---> Appearance.

Now, drag and drop the Icons themes or engines right on top of the Appearance Preferences and let go.

It will install automatically.

Hope this helps.

Cheers - CC7gir

PS: if you installed icons or window borders and cannot find them, click customize and look around:p

---

### Post by lucas777 on 2010-01-28
God you guys are fast thanks mates, il try it shorty and let you know the outcome

---

### Post by skymera on 2010-01-28
> **cc7gir said:**
> I also download from gnome-look.
Save it anywhere on your computer and do not extract the .gz files, just keep them as they are.

Click System ---> preferences ---> Appearance.

Now, drag and drop the Icons themes or engines right on top of the Appearance Preferences and let go.

It will install automatically.

Hope this helps.

Cheers - CC7gir

PS: if you installed icons or window borders and cannot find them, click customize and look around:p

This is indeed simpler than mine.
I drag and drop themes but i didn't know you could do the same for icons :D

Thanks.

---

### Post by lucas777 on 2010-01-28
Yes the drag and drop worked perfect. Okay now one more thing how do i get like a dock and stuff on the desktop going like cpu usage and stuff like that, ive seen some images around with that kind of stuff on it

---

### Post by skymera on 2010-01-28
For a dock check out Avant Window Navigator (AWN)and Screenlets for desktop widgets.

---

### Post by lucas777 on 2010-01-28
[http://gnome-look.org/content/show.php/lukas+desk_op-let?content=71314](http://gnome-look.org/content/show.php/lukas+desk_op-let?content=71314)

Now that is the type of desktop screen i want i just downloaded that but that doesnt seem to drag and drop.. i get an error..

---

