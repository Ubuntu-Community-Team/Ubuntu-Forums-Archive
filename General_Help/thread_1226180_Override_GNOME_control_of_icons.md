---
title: "Override GNOME control of icons?"
date: 2009-07-29
forum: General Help
---

### Post by DGeeez on 2009-07-29
Neither KDE nor Windows does this, but GNOME assigns the same icon to each link based on broad system category, and the sorting doesn't get any finer than that - you can go and "customize" your "icon sets", but every program executeable will still look the same on your desktop. While GNOME still beats the pants off KDE for just doing it's job reliably and being easy to get around, I don't see what the icons have to do with this. I really would like to, and should be able to substitute my own unique icons for links to specific urls or files when they are opened by the same program, and then why not substitute a preferred icon for specific programs if I don't like the ones they ship with, OR I want my icons to distinguish one program or one file from another on my desktop and in my file browser? There are some very good reasons why I demand this sort of flexibility / functionality from Linux - it's because it's something which is very useful for productivity, is very easily done in Windows, Linux promoters are always scream'n that Linux, which is not Windows, is so much better than Windows, and that there isn't anything good in Windows which you can't do in their Linux distro! They keep on talking goods, but with a history which is as long as Windows, I'm still waiting for delivery of them. GNOME can do what it wants to as long as I can override it when I see the need - is there a way to do this?

---

### Post by CatKiller on 2009-07-29
> **DGeeez said:**
> I really would like to, and should be able to substitute my own unique icons for links to specific urls or files when they are opened by the same program, and then why not substitute a preferred icon for specific programs if I don't like the ones they ship with, OR I want my icons to distinguish one program or one file from another on my desktop and in my file browser?

Right-click on file. Select Properties. Click on the icon. Pick whatever image you like. This will work for any launcher.

Aside from files you've modified in this way, all others are theme-dependent. If you don't like a particular set of icons, you can use another. If you like the set but only want to change one, change the icon in the theme. The icon theme specification is [here]("http://www.freedesktop.org/wiki/Specifications/icon-theme-spec"), but you'll probably find out how to do what you want with an icon theme just by inspecting it.

---

### Post by DGeeez on 2009-07-29
> **CatKiller said:**
> Right-click on file. Select Properties. Click on the icon. Pick whatever image you like. This will work for any launcher.

Are you a GNOME user? It works just that way in Windows (I know all about that), and probably KDE, but if GNOME provides an editable item for icons associated with programs and files in their right-click -> Properties boxes (I've noticed there are fewer details displayed compared to Windows, and most of them cannot be edited in the Ubuntu GNOME box), then I've searched and missed it a hundred times. Which tab did you see it in?

---

### Post by CatKiller on 2009-07-29
> **DGeeez said:**
> Are you a GNOME user?

Yes.

> Which tab did you see it in?The Basic tab, the one that's first displayed when you select Properties. You just click on the icon.

It's not immediately obvious, but mouseover on the icon does highlight it, which is generally the feedback that something is an object you can click on to interact with. It took me quite a while to notice it the first time, too. Perhaps a tooltip saying something like "click to edit icon" would make it more obvious?

EDIT:

> **DGeeez said:**
> if GNOME provides an editable item for icons associated with programs and files in their right-click -> Properties boxes

It's not for all files of a type, it's for individual files, so that you can distinguish them from others of the same type. The "all files of a certain type" is theme-dependent. It's defined by the appropriate file in the mimetypes directories of the theme that you're using. I much prefer it this way. I used to hate it when a new application would change the icons of a whole bunch of files without asking (RealPlayer, I'm looking at you). This way, themes are consistent in how they show files regardless of which applications you happen to be using. And I'd hate for all the icons to change just because I've chosen to use VLC by default rather than Totem, for example.

---

### Post by Copernicus1234 on 2009-07-29
Ive been thinking of writing a program for this, but I never seem to get around to it. It would be very good to get all the theme icons you have on the system for a specific application to show up and allow easy selection of alternatives.

For example, you are using theme X but you want to see other themes alternative icons for Firefox in a easy to use GUI window. Of course you also want to select and apply changes to your theme.

So there's an idea for any of you that have the time and interest to do it. I think it would be a successful application.

---

### Post by DGeeez on 2009-07-29
> **CatKiller said:**
> Yes.

The Basic tab, the one that's first displayed when you select Properties. You just click on the icon.

It's not immediately obvious, but mouseover on the icon does highlight it, which is generally the feedback that something is an object you can click on to interact with. It took me quite a while to notice it the first time, too. Perhaps a tooltip saying something like "click to edit icon" would make it more obvious?

EDIT:



It's not for all files of a type, it's for individual files, so that you can distinguish them from others of the same type. 
That's what I'm looking to do now.

> **CatKiller said:**
> The "all files of a certain type" is theme-dependent. It's defined by the appropriate file in the mimetypes directories of the theme that you're using. I much prefer it this way. I used to hate it when a new application would change the icons of a whole bunch of files without asking (RealPlayer, I'm looking at you). This way, themes are consistent in how they show files regardless of which applications you happen to be using. And I'd hate for all the icons to change just because I've chosen to use VLC by default rather than Totem, for example.
I knew I'd probably find similar reasons to like that theme-based order in the long run, it's just my reference files and folder links would stand out better with my own icons.

Well, I'll be a monkey's distant ancestor - it turns out to be ridiculously easy, it just doesn't have that "click here" sign which recovering Windows users expect to see. What's really cool about this is that it will use almost any picture type (png and jpg both work) for an icon, even when they're kinda big, although my icon files are no good here (and I used to enjoy having to convert my jpgs and scale them down for fussy Windows). Thank you so very much!

---

### Post by CatKiller on 2009-07-29
> **DGeeez said:**
> my icon files are no good here

You can convert .ico files to other formats with ImageMagick (I can't remember if it's installed by default, but it's ridiculously useful, so it might well be). The syntax is something like ```
convert filename.ico filename.png
```You could probably do a for loop to do a whole bunch at once if wildcards don't work. Otherwise, I think GThumb will convert files in a batch process in a graphical tool.

EDIT:

> **DGeeez said:**
> it's just my reference files and folder links would stand out better with my own icons.

Another thing that you might want to consider is the use of Emblems. These are small additional images that are overlaid on the existing icon, without changing it. These are theme-dependent, too, so hopefully they will remain in keeping with the look of the rest of your Desktop. You select them from the Emblems tab of the Properties window.

---

### Post by DGeeez on 2009-07-30
> **CatKiller said:**
> You can convert .ico files to other formats with ImageMagick (I can't remember if it's installed by default, but it's ridiculously useful, so it might well be). The syntax is something like ```
convert filename.ico filename.png
```You could probably do a for loop to do a whole bunch at once if wildcards don't work. Otherwise, I think GThumb will convert files in a batch process in a graphical tool. 

It's no big deal, I still have the original files which they were scaled down and converted from. No need to do any conversions in most cases now, and that can't be beat! Anyway, I've found GIMP to be handy for dealing with .ico files in any direction.

> **CatKiller said:**
> EDIT:



Another thing that you might want to consider is the use of Emblems. These are small additional images that are overlaid on the existing icon, without changing it. These are theme-dependent, too, so hopefully they will remain in keeping with the look of the rest of your Desktop. You select them from the Emblems tab of the Properties window.

I've noticed those, so I've got more to keep me busy :)

One thing I'm not sure of, having found a real stunning theme, and changed the link folder icons on my desktop, is whether my custom icons would be overwritten by GNOME should I decide to try different themes. Is there something which I could do about this?

---

### Post by CatKiller on 2009-07-30
> **DGeeez said:**
>  One thing I'm not sure of, having found a real stunning theme, and changed the link folder icons on my desktop, is whether my custom icons would be overwritten by GNOME should I decide to try different themes.

I don't think so. If you switch to a different file manager I shouldn't imagine that the changes you've made will still be respected, but it's handled separately from the themes (through the XML files in ~/.nautilus/metafiles, I'd imagine). When you change themes, those icon settings should stay.

The easiest way to test it to your satisfaction is probably to create another user on your computer for guinea-pig purposes. Whenever you're curious about a per-user thing and you don't want to mess up your own settings, log into that one and try it. If you don't give that user admin privileges, they'll **only** be able to do per-user things.

---

