---
title: "How to change cursor theme"
date: 2012-07-31
forum: General Help
---

### Post by wilbso on 2012-07-31
Hi, i want to change my cursor theme to this theme: [http://gnome-look.org/content/show.php/Pulse+Glass?content=124442](http://gnome-look.org/content/show.php/Pulse+Glass?content=124442)

How do i do it. Im running ubuntu 12.04

thanks

---

### Post by wilbso on 2012-07-31
Is it possible?

---

### Post by Dawnbandit on 2012-07-31
> **wilbso said:**
> Is it possible?
It should give you a guide on how to do it.

---

### Post by wilbso on 2012-07-31
> **Dawnbandit said:**
> It should give you a guide on how to do it.

I cant see any instructions

---

### Post by Dennis N on 2012-07-31
I use this method to change the mouse pointer in Unity:

[http://ubuntuforums.org/showpost.php?p=11929215&postcount=17](http://ubuntuforums.org/showpost.php?p=11929215&postcount=17)

The cursor you mention should work - it says it was updated to be compatable with Unity in Jun 2012. Also, it already has the cursor.theme file mentioned in that post so you don't need to make that.

---

### Post by wilbso on 2012-07-31
> **Dennis N said:**
> I use this method to change the mouse pointer in Unity:

[http://ubuntuforums.org/showpost.php?p=11929215&postcount=17](http://ubuntuforums.org/showpost.php?p=11929215&postcount=17)

The cursor you mention should work - it says it was updated to be compatable with Unity in Jun 2012. Also, it already has the cursor.theme file mentioned in that post so you don't need to make that.
Thanks man :) Just, i dont get it. where am i ment to extract it to?

---

### Post by GreatDanton on 2012-07-31
> **wilbso said:**
> Thanks man :) Just, i dont get it. where am i ment to extract it to?

> Put new cursor folder in /usr/share/icons. 

Hope this helps.

---

### Post by wilbso on 2012-07-31
> **GreatDanton said:**
> Hope this helps.

Yea, but everytime i try doing that, it says permission denied....

thanks

---

### Post by Dennis N on 2012-07-31
> **wilbso said:**
> Yea, but everytime i try doing that, it says permission denied....

thanks

First, let the file download to the Downloads folder and then extract the folder there. Then, copy the extracted folder into /usr/share/icons/

You have to use sudo to do this since the destination is root territory.

Start terminal, and change directory to Downloads folder. 

Then,

```
sudo cp -r Pulse-Glass /usr/share/icons/

```

---

### Post by GreatDanton on 2012-08-01
There is also another way if you prefer GUI. 
Extract files in Downloads. Open Terminal and type: ```
gksudo open nautilus
``` Now grab the files you have extracted and copy and paste it into the appropriate folder (in your case /usr/share/icons).


Regards.

---

