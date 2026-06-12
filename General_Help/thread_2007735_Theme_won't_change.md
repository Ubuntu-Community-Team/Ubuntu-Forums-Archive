---
title: "Theme won't change"
date: 2012-06-21
forum: General Help
---

### Post by Earl_Maroon on 2012-06-21
(First of all, I'm using GNOME Shell, not Unity, and I am using the latest (12.04) Ubuntu release.)

I opened Appearance and set a new wallpaper. Then I changed the Theme from Adwaita to Ambience. Then I tried to change it back. When I try to select anything else from the drop down box the selection flickers for a milisecond or so then reverts to Ambience.

Then I tried changing my wallpaper back as I realised I had selected a file on an external drive rather than copying it to the internal HDD first. But I had the same problem.

Possibly related: text is showing up strangely in windows. (See attached image - the highlighting is the same in the menus)

Please can anybody suggest what might be wrong and how I might fix it?

---

### Post by Frogs Hair on 2012-06-21
Do you have the Gnome Tweak Tool / Advanced Settings from the software center and the user themes extension installed ?

---

### Post by Earl_Maroon on 2012-06-21
> **Frogs Hair said:**
> Do you have the Gnome Tweak Tool / Advanced Settings from the software center and the user themes extension installed ?

Yes.

---

### Post by Frogs Hair on 2012-06-22
Try restarting the shell. Alt + F2 ```
r
```
Check Looking Glass for errors. Alt + F2 ```
lg
```   
The Gmome shell does require 3D compatible graphics, so I don't know if that may be a factor. If you were able to use Unity 3D you should be able to run the Gnome Shell.

---

### Post by Earl_Maroon on 2012-06-24
> **Frogs Hair said:**
> Try restarting the shell. Alt + F2 ```
r
```
Check Looking Glass for errors. Alt + F2 ```
lg
```   
The Gmome shell does require 3D compatible graphics, so I don't know if that may be a factor. If you were able to use Unity 3D you should be able to run the Gnome Shell.

Thanks for your help, but that didn't reveal anything. I wasn't aware of Looking Glass before though, so thanks for bringing it to my attention. I'm sure I'll have use for it along the line.

I discovered the problem was something to do with a 3rd party repo package. I fixed it by downgrading using ppapurge but then GNOME Shell wouldn't start. Eventually I worked out there was a problem with gir1.2-gjsdbus-1.0, which I purged and reinstalled. After that everything seemed to be fine.

---

