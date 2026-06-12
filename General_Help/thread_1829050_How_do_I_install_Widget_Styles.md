---
title: "How do I install Widget Styles??"
date: 2011-08-20
forum: General Help
---

### Post by sundy on 2011-08-20
Hi all,

I have just started my first real experience with KDE (Kubuntu Natty) after about 3 years with Gnome (Ubuntu). I like to customize my desktop as much as I can and am used to th ease at which you can install application themes in Gnome (using Appearances).

I have figured out how to install icon themes and plasma themes but cant seem to figure out how to install application themes (widget styles). I have found how to change the theme in Application appearance but can anyone tell me how to install new ones??

Thanks in advance for the help!!

---

### Post by ankspo71 on 2011-08-20
Hi,
There are a few  KDE styles that can be found in your package manager (synaptic, kpackagekit, etc) You should be able to find them by searching for "kde style". Once they are installed you can select them and configure them.

Unfortunately, KDE doesn't have as many Styles (in comparison to Gnome having many GTK themes and theme engines), but luckily some of the KDE Styles are very customizable (especially Qtcurve and Bespin)

Are you trying to import a Qtcurve theme? Or maybe a Bespin theme?

If you are trying to install a Qtcurve theme, first you need to install the meta-package called "qtcurve". This package will install the Qtcurve KDE Style for KDE applications, and the Qtcurve GTK theme engine for GTK applications.

Once Qtcurve is installed, go to System Settings > Application Appearance > Style, then Choose Qtcurve in the dropdown menu for  "Widget Style:".

Next, click on the "Configure" button. The Qtcurve settings window will open. 

Choose the "Presets and Preview" category on on the left, then click on the "Import" button towards the right. Now browse for theme file that you have downloaded called 'theme-name.qtcurve'. Once you have it imported click on the apply button. Now you can use the theme 'as is', or you can tweak it any way you like with the many configuration options. 

After you are done importing a qtcurve theme, be sure to enable the Qtcurve GTK theme engine at System Settings > Application Appearance > GTK+ Appearance, so your GTK applications will look like your KDE applications.

Qtcurve also includes a window border, and you can select that by going to System Settings > Workspace Appearance > Window Decorations. 

Bespin themes should have similar way to import themes, but bespin will have to be installed first too.

Hope this helps.

---

### Post by sundy on 2011-08-21
Fantastic!!

You sir, are a scholar and a gentleman!

Great explanation, worked a treat.

Thanks a lot!!

---

