---
title: "photo management in Ubuntu 10.10 (missing features)"
date: 2010-10-26
forum: General Help
---

### Post by arpad9 on 2010-10-26
Maybe I don't pay enough attention.  I just know that whenever I've wanted to resize an image or email it, I've been able to do it pretty quickly.  It was usually a two step process of resizing with an editor and then sending from a menu.

Today, though, I went into the shiny new Shotwell and there appears to be no way to resize; or email.

OK.  Went back into F-Spot.  Surely there's an easy way to resize and/or email from there.  Nope.

Are we missing an easy way to do this or am I missing something?  I love Gimp but do I have to use that to resize an image?  Seems like overkill.

Ostensibly, there should be a one stop process - either from an app or from Nautilus - send image and a quick dialog to ask what size and GO!

---

### Post by coffeecat on 2010-10-26
> **arpad9 said:**
> Ostensibly, there should be a one stop process - either from an app or from Nautilus - send image and a quick dialog to ask what size and GO!

Indeed there is. Install the package nautilus-image-converter, restart nautilus by logging out and in again, and then right-click on image and 'Resize Images..' You can batch resize by selecting more than one.

And/or install Gthumb which I find very useful. You can find resize under Tools on the toolbar.

---

### Post by SeijiSensei on 2010-10-26
KDE's image manager, Gwenview, can do this if the kipi-plugins are installed as well.  You can install Gwenview into a GNOME system as well.

---

### Post by arpad9 on 2010-10-26
Sweet! thanks coffeecat!

I'm not so much of a KDE guy since I used it many, many years ago when it was bloated and slow.  Similar reasoning as to why I don't drink tequilla anymore.  I'm sure tequilla's fine but I had a bad experience with it a long time ago.

Still, for my personal convenience tastes, it would be nice to have a Publish to Email in Shotwell -  but that's something to bring up with the Shotwell folks.

Thanks again!

---

### Post by coffeecat on 2010-10-26
> **arpad9 said:**
> I'm not so much of a KDE guy since I used it many, many years ago when it was bloated and slow.

Talking of which... There's another nice feature in Gthumb. It has a simple-to-use but reasonably comprehensive rename facility. So much better to use than krename which, to my mind, is a typical KDE app in being - how shall I put this diplomatically? - perplexing. :wink:

---

### Post by SeijiSensei on 2010-10-27
The kipi-plugins for Gwenview do have the facility to email images; I don't know if the other tools mentioned do so.  It supports quite an array of email clients as well.

---

### Post by gradysghost on 2010-10-27
Also consider DigiKam.  I haven't used it myself, but I understand that it's pretty advanced in terms of features.

---

### Post by amjjawad on 2010-11-11
This thread was so helpful as I was just about to start a thread asking if there's any program/software in Ubuntu that is equivalent to Microsoft Photo Manager that comes with office (wasn't that the name? I didn't use Windows in long time :P )

I really care for Resizing all the images in the folder. Photo/Picture Manger in Microsoft was so helpful in that.

I'm going to try the tools that you guys suggested and hope to find them as helpful as Photo Manger :)

---

### Post by mcduck on 2010-11-11
You might want to try Phatch as well. At least if you just want a tool that can easily process a bunch of images, instead of looking for an *image viewer* that can process a bunch of images. :)

Personally, I just use Imagemagick. Much more powerful than any of the tools suggested in this thread but being a command-line app it also has a bit of a learning curve. ;)

---

### Post by amjjawad on 2010-11-11
> **mcduck said:**
> You might want to try Phatch as well. At least if you just want a tool that can easily process a bunch of images, instead of looking for an *image viewer* that can process a bunch of images. :)

Personally, I just use Imagemagick. Much more powerful than any of the tools suggested in this thread but being a command-line app it also has a bit of a learning curve. ;)

Thanks mcduck :)
I just installed Phatch but it seems it has more than what I really want :)
Perhaps I'm still new to Linux and still didn't get used to it yet. However, the best tool that meet my needs is: **nautilus-image-converter**.
That's all what I really need. I know I need crop sometimes but I care more about "resizing" images.

Even when I used Windows, I hated complicated stuff like ACD See and stuff like that. I used Microsoft Photo/Picture Manager which comes with Office and Photoshop (for editing, effects, etc) and of course the default image viewer for Windows. 3 applications only. No more, no less :)

However, to be fair to Linux and its softwares, I'll give these applications suggested here another chance even though some of these don't have "resize" feature or I have to click on the image that I want to resize but I might find some interested stuff :)

Thank you, guys!

---

### Post by Dragonbite on 2010-11-11
> **SeijiSensei said:**
> KDE's image manager, Gwenview, can do this if the kipi-plugins are installed as well.  You can install Gwenview into a GNOME system as well.

> **gradysghost said:**
> Also consider DigiKam.  I haven't used it myself, but I understand that it's pretty advanced in terms of features.

kipi-plugins are also available in DigiKam which will give you the catalog, tag and album management like F-spot (or better, in my opinion).

I haven't tried it for emailing, but when I get home I'll give it a try.  I use digikam on my Gnome Ubuntu installation and it works great.

Another option may be Picasa, but I try to shy away from it because of the reliance on Wine, and not a native Linux application like digiKam, F-Spot, et. al. are.

---

### Post by I'mGeorge on 2010-11-11
for resizing, viewing and doing some basic unpretentious image editing I use Mirage. I find it more than capable for all these simple tasks.

---

