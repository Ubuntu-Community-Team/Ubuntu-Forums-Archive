---
title: "Icons stuck as GNOME defaults."
date: 2010-05-16
forum: General Help
---

### Post by Llamarama on 2010-05-16
Hey all, I'm using Ubuntu 10.04 LTS and after recently changing a theme, all icons are stuck as GNOME defaults.

I read some threads where it's only the folder icon that's stuck but as it is every single icon then I decided I'd best just ask. Please help, many thanks in advance.

---

### Post by dv3500ea on 2010-05-16
Either the theme uses the GNOME defaults or it depends on an icon theme that is not installed

---

### Post by Llamarama on 2010-05-16
I created a custom theme from parts of the theme library, however no matter which theme I use, default or custom, the gnome default icons are there. Even with the sample window showing the different icon set.

Also if I try to go back to the default Humanity theme, it's still GNOME icons. I'm very confused :S

---

### Post by dv3500ea on 2010-05-16
Try reinstalling [ubuntu-artwork]("apt:ubuntu-artwork")

---

### Post by Llamarama on 2010-05-16
This is going to sound very noobish, but how would I go about this? Sorry, I'm quite new to using Linux.

---

### Post by dv3500ea on 2010-05-17
Go to System -> Administration -> Synaptic Package Manager
search for ubuntu-artwork
Click on the check box next to ubuntu-artwork and click mark for reinstallation and click the green tick in the menu bar.

or

Go to Applications -> Accessories -> Terminal
Enter:
```

sudo apt-get remove ubuntu-artwork
sudo apt-get install ubuntu-artwork

```

---

### Post by Llamarama on 2010-05-18
Thanks for that, I'll try that.

---

### Post by clockworkpc on 2010-08-08
Hi,

I'm finding this *very* frustrating.  I've reinstalled the ubuntu artwork already and the problem keeps on coming back every time I play around in Appearance settings.

Can someone please tell me what is causing Gnome to stubbornly default to the ugly Gnome icons, even when icons_theme in gconf-editor says otherwise?

Thanks

---

### Post by cecilrhayduke on 2010-11-28
Install lxappearance.  For some reason, that works to change the icon theme.

---

