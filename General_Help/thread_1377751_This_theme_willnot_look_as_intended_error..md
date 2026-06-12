---
title: "This theme willnot look as intended error."
date: 2010-01-10
forum: General Help
---

### Post by xXxDavyBoyxXx on 2010-01-10
Hi, this is my first post here, and I'm also an ubuntu noob to, so please be gentle on me!

I've recently installed Ubuntu 9.10 on an old system, and it's been great, however when I started trying to customize everything I ran into an issue with some themes I downloaded.

Everytime I try and apply the new themes in Appearance Preferences, I get this error:

[IMG]http://img96.imageshack.us/img96/4282/screenshotuj.png[/IMG]

As you can see from the screenshot, the themes haven't been applied properly neither, only certain parts of the taskbars and windows change so it just doesn't look right at all.

I've spent most of last night and today trying to find a fix for this, but I'm getting nowhere, I was hoping maybe someone here could help me fix this?

Thanks in advance.

---

### Post by xXxDavyBoyxXx on 2010-01-10
*bump*

Can't anyone help me out please? :(

---

### Post by xXxDavyBoyxXx on 2010-01-11
Surely someone here can assist me with this problem????

---

### Post by VCoolio on 2010-01-11
Themes consist of three elements: borders (metacity), controls (gtk2) and icon. Those can be defined in a index.theme file inside the theme folder in either ~/.theme or /usr/share/themes. If the author of a gtk-theme thinks it looks best with icontheme X and/or border theme Y, he defines that in the index.theme file, but doesn't necessarily include X and Y in his theme package. If you don't have those X and Y themes, it will throw this error, but it's not really broken. You can mix borders and gtk2 controls and icon themes at will, using the "custromize" button. Or you can check the index.theme file and search the missing parts on gnome-look.org, although there is no theme named 'default', so that's a bit odd.

If the error is about an engine, it's more serious. For example if engine "murrine" is missing, look for a package gtk2-engines-murrine in synaptic.

---

### Post by xXxDavyBoyxXx on 2010-01-11
Thanks for the reply, so it's just a case of me finding borders that match the themes I'm trying to use then?

---

### Post by VCoolio on 2010-01-11
Yep, and then just select your borders via the customize button. Have fun.
Btw, if you like green, check [here]("http://www.gnome-look.org/content/show.php/gruenstich?content=116380") and [here]("http://www.gnome-look.org/content/show.php/gruenstich2?content=116787").

---

