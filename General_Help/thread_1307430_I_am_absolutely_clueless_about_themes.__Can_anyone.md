---
title: "I am absolutely clueless about themes.  Can anyone help?"
date: 2009-10-31
forum: General Help
---

### Post by MonoMatt304 on 2009-10-31
Hopefully someone can dumb this down for me and explain it in simple terms.  I've looked everywhere for a comprehensive guide, etc. but have found nothing, so this is my last resort.

I cannot, for the life of me, figure out themes.

I've been getting them from gnome-look.org.  I know that, when I download some (a very small few) I'm able to install them and they work fine, right out of the box.  Others require "GTK Theme Engines", which I have no idea how to install.  Others aren't in "tar.gz" format, so Ubuntu doesn't recognize them and won't install them.

So, can anyone explain it to me?  How do I install required GTK Theme Engines?  How do I install themes that aren't in "tar.gz" form, but are in "zip" or "gz" form?

I got -some- of the GTK Engines installed (I think) by running this command I found somewhere: "sudo apt-get install gtk2-engines-*".  Still, a majority of themes either require engines that weren't found in the repositories (and, thus, not installed), or they still don't work properly for one reason or another.

Can someone please help me?  I feel like a total idiot and I'm sure I'm missing something blatantly obvious, but I'm at a loss...

---

### Post by misfitpierce on 2009-10-31
the ones not in tar.gz, look inside and usually there sometimes a tar.gz somewhere inside...

GTK2.X is for window theme - Use GTK 2.X one on left.
Metacity is border is GTK does not alrdy include... some do!
Icons for icons... 

Hit most popular to get ones that usually work better and are already tar.gz usually and work good. Then hit install in appearance and click the tar.gz and it should install... Hit customize to make sure it changed the border and GTK part or icon part correctly.

It's really just that simple... If you need any more help on specific theme or problem... please post link to theme you want and whats going wrong!

---

### Post by gradinaruvasile on 2009-10-31
There are 3 types of themes:

- Window border - thats only the borders of windows the upper bar - managed by the "window manager" - Metacity or Compiz if u have desktop effects activated. If the window manager (usually Compiz is the culprit here) crashes, you will have no window borders, access to alt-tab and other related shortcuts (install and launch at startup fusion-icon and u can easily reload the window manager in this case, be it Metacity or Compiz).

- Application - the rest of the windows components such as tab style, scrollbar style etc. U find them in the tar.gz format, drag and drop it on an open "Appeareance Preferences" window to install easily.
This i think is managed by the engine (the GTK engine/GTK window decorator in Gnome - dont know for KDE, but surely has its own). Thats the reason u have to install the engine first. This can be tedious cause not all engines are found in the repos. Google for the ubuntu .deb file (i found every engine after a bit of searching). When u d/l themes, usually the creators mention the engine is based on. But in most cases they are based on commonly used engines that u can find in the repos (Myst, Clearlooks etc).

- Icon - no comment here, they are easy to use (drag-drop on "Appeareance Preferences"). 
Something to look at: i tried to use Karmic (Ubuntu 9.10) icon sets on Jaunty (Ubuntu 9.04) and  i found that it doesnt work seemingly because they have different folder structures.

General things to observe: 
- Sometimes there u see the error message indicating a missing icon theme. Just go to settings and select ur favourite icon theme or search for the one reported missing.
- Not all themes support customisable colors.

---

### Post by Gatemaze on 2009-10-31
on your home directory create a directory .themes
you can put there all the unzipped/extracted in general themes...

for icons create a dir .icons and do the same.

---

