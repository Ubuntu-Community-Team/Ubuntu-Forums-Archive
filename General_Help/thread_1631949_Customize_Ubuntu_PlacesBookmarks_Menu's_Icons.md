---
title: "Customize Ubuntu Places/Bookmarks Menu's Icons"
date: 2010-11-27
forum: General Help
---

### Post by Matt G Dalian on 2010-11-27
I've searched around a lot but I haven't found an answer, but I'm sure this is something that can be done.

In the Ubuntu Places Menu (also known as the Bookmarks menu), the folders for Documents, Downloads, Musics, etc. have custom icons.
But every other folder that you have will only have the standard folder icon. 

This is true even if for the regular folder, you use a custom icon.

For example, I changed my Drupal folder's icon to the "Drupal Dude." But the Places version of the Drupal folder has a regular folder icon (see attached image).

[IMG]http://184.106.218.46/images/ubuntu-custom-places-icons.png[/IMG][IMG]http://www.jvinoles.com/images/ubuntu-custom-places-icons.png[/IMG]


Does anyone know of a way to manually change this?

Note that I'm no referring to how to change the icons on custom folders for Music or Documents to the Ubuntu standard icons. That's something I solved myself in another thread:[INDENT][http://ubuntuforums.org/showthread.php?p=9074493#post9074493](http://ubuntuforums.org/showthread.php?p=9074493#post9074493)[/INDENT]I've seen a lot of interest in custom places icons:
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=1448883](http://ubuntuforums.org/showthread.php?t=1448883)
[*][http://askubuntu.com/questions/5209/how-do-i-change-the-folder-icons-in-the-places-menu](http://askubuntu.com/questions/5209/how-do-i-change-the-folder-icons-in-the-places-menu)
[*][http://ubuntuforums.org/showthread.php?t=1458706](http://ubuntuforums.org/showthread.php?t=1458706)
[/LIST]

And on that last thread, it looks like someone was getting close to an answer (maybe), but I don't quite know:[INDENT][http://art.ubuntuforums.org/showpost.php?p=9537736&postcount=27](http://art.ubuntuforums.org/showpost.php?p=9537736&postcount=27)[/INDENT]> **PaLoBo said:**
> 

Normal Folder:
```
gvfs-info ~/Downloads/ | grep icon
  **standard::icon: folder-download, folder**

```Custom Folder:
```
gvfs-info ~/Dropbox/ | grep icon
  **standard::icon: inode-directory, gnome-mime-inode-directory, inode-x-generic, folder**
  metadata::nautilus-icon-view-auto-layout: true
  metadata::nautilus-icon-view-tighter-layout: false
  **metadata::custom-icon: Downloads/Icons/dropbox.svg**

```UInfortunately I haven't yet had success using gvfs-set-attribute to change the standard::icon attribute.

This would in theory use your custom icon everywhere (places, sidebar etc.)

If anybody knows better please chime in.


Another post implied that there might be a way to do this using gconf-editor:[INDENT][http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1608020](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1608020)[/INDENT]But I think the previous post quoted above is the more promising lead.

Any thoughts? It would be great to be able to do this in Ubuntu.

---

### Post by Matt G Dalian on 2010-12-19
*bump*

---

### Post by red72 on 2011-01-12
I am having the same problem. I searched a lot with no luck. Can anyone help?
Thanks!

---

### Post by Silv3ri on 2011-02-08
I have the same problem and have searched everywhere, and tried almost anything I could think of. It does seem that the icon used by **Places** is determined by the folder's **standard::icon** metadata tag, but I can't find any way to edit it. The **gvfs-set-attribute** command and the GIO library's _**[set_attribute()]("http://library.gnome.org/devel/glibmm/unstable/classGio_1_1File.html#a75fa7e1a44e97a910d232f2b4ab4bfdd")**_ function both give the same error, which is that they don't support setting that specific tag. 

Of course there has to be some way to do it, because whenever you login into a newly created user account for the first time, Ubuntu creates these folders with the tags set correctly. I just couldn't find anywhere yet that specifies which commands are used in that case.

Any help would be appreciated.

---

### Post by raen on 2011-07-05
Bump.

I'm having a similar issue.

---

### Post by braikar on 2011-09-25
Hi,

I wanted to change the icons in the places menus as well since a long time and I finally figured out how to do it, sadaly it's kind of a bad hack! It works but it will change the default paths of some apps that can use them.. bear with me it's kind of long to explain.
And it's kind of long to do aswell because you have to make your own icons, at each sizes, 8x8, 16x16, 22x22 etc. present in your choosen theme folder.
For the moment I'll use the gnome theme: /usr/share/icons/gnome/

DON'T TRY THE MODIFICATIONS EXPLAINED HERE UNTIL YOU READ THE WHOLE POST!

The icons for the places are located in /usr/share/icons/gnome/SIZES/places/
There are only 8 possible places you can make... in fact 7, because you'd better not play with the desktop default path!

So go in your home directory ~/.config/user-dirs.dirs
it will look something like:
```

XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Personals"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Software"
XDG_VIDEOS_DIR="$HOME/Videos"

```

That's my file, yours might be a bit different.
As you see I have for example one non default directory "$HOME/Software" which is assigned to XDG_PICTURES_DIR... (which f-spot and some photo programs use as default, so sometimes I have pictures that end up in my software folder because of the default path used, that's why I wouldn't try to mess with the most important one, e.g. XDG_DESKTOP_DIR... but you can change the default paths used by the applications so that's good!)

Anyway, normally XDG_PICTURES_DIR should be the pictures directory, but since I don't use that one I replaced it with whatever I wanted. For the "Drupal" folder for example you might assign it to XDG_TEMPLATES_DIR for example.
Then the next thing to know is that these special locations have each customized icons. Go look insinde the Humanity theme (/usr/share/icons/Humanity/places/SIZES/) to see the default Ubuntu ones...

I'll use the Humanity now, as you'll see the gnome theme has the folder order /usr/share/icons/gnome/SIZES/places/ whereas Humanity has the opposite order /usr/share/icons/Humanity/places/SIZES/
This doesn't really matter, because the paths to the folders are defined in /usr/share/icons/THEME/index.theme but it's just to let you know your own theme can have either of these orders of folders...

Soooo continuing, what's good with these places is that each have their own assigned icons, (based on the Humanity folder order here) we have:


XDG_DESKTOP_DIR ==> /usr/share/icons/THEME/places/SIZES/desktop.png
XDG_DOWNLOAD_DIR ==> /usr/share/icons/THEME/places/SIZES/folder-download.png
XDG_TEMPLATES_DIR ==> /usr/share/icons/THEME/places/SIZES/folder-templates.png
XDG_PUBLICSHARE_DIR ==> /usr/share/icons/THEME/places/SIZES/folder-publicshare.png
XDG_DOCUMENTS_DIR ==> /usr/share/icons/THEME/places/SIZES/folder-documents.png
XDG_MUSIC_DIR ==> /usr/share/icons/THEME/places/SIZES/folder-music.png
XDG_PICTURES_DIR ==> /usr/share/icons/THEME/places/SIZES/folder-pictures.png
XDG_VIDEOS_DIR ==> /usr/share/icons/THEME/places/SIZES/folder-videos.png

Evidently in the /usr/share/icons/THEME/places/scalable it would be folder-xxx.svg

So now you just need to assign your wanted folder to an XDG_ folder and make the icons for it.

Let's take the example of Drupal here, since I see you don't have the templates folder in your places, we'll use that one.

So modify:
~/.config/user-dirs.dirs with
```

XDG_TEMPLATES_DIR="$HOME/Drupal"

```
Then since you are using the Humanity theme (I don't know if it's Humaity or Humanity-Dark..., I'll assume Humanity), go to /usr/share/icons/Humanity/places/
and then in each folders 16, 22, 24, 32, 48, 64, 128 change the folder-templates.png icon with the correct size and the Drupal icon you want.
Then all you have to do is reload the icon-theme.cache.
Do: sudo gtk-update-icon-cache -f /usr/share/icons/Humanity/
-f is for 'force'.
That's it you'll have your icon in the places menu from now on :)

LoL it's a dirty try but it works absolutely fine, I would guess XDG_PUBLICSHARE_DIR is also a safe one to use since I've never seen it used in any ubuntu distribution..

Hope that helps, it took me a while to figure out a way to get my icons the way I wanted, I changed all the defaults icons on mine with that trick ;) As you can see in the attachement.

But I have to warn you, don't do the changes to the theme as I explained them here, because changing the theme files like that (because you have to change icon files that only root has access to) can mess up nautilus quite badly it seems, the best is to get the theme you use, modify it with your new icons and then install it as a new theme with whatever new name you want, so your theme will in fact end up in ~/.icons/NEW_THEME_NAME/. that will also avoid any updates problems in the future. because of all the checksums etc. no default root file should be modified like that!!
So for example for Humanity, just copy /usr/share/icons/Humanity/ to ~/.icons/Humanity/
and do the whole procedure above to the theme you copied in your home folder. Then just edit the ~/.icons/Humanity/index.theme file and give this duplicate theme a new name and update the icon cache in that specific theme... etc. and you're done in a proper way that won't mess up anything :)

And there are more things to be known, I just tested, and realised in fact DON'T USE XDG_TEMPLATES assigned to a big folder, because if you do that, you will have nautilus slowed down heavily because the whole folder will be displayer in  every context menu when you right click in nautilus in 'create Document' -> ...
I told you this is a very dirty hack :D :D

---

