---
title: "How to associate theme file type"
date: 2010-09-11
forum: General Help
---

### Post by Jeff Root on 2010-09-11
Ubuntu 9.10 Karmic Koala.
 
When I double-click any .theme file I get the error
message: "Could not display such-and-such.theme. the
location is not a folder."
 
When I right-click any .theme file there is no option
to "Open With", and no "Open With" tab in Properties.
 
When I create a text file and save it with a random
name, I can change the filename extension to wav, jpg,
png, txt, or theme, and Properties shows that the OS
thinks it is that filetype.  But all those filetypes except
theme give "Open With" options, and allow me to
change the extension again to anything.  Once a file
has been given the theme extension, it is stuck as a
theme file.
 
I want to associate theme files to GEdit. What can I do?
 
   -- Jeff, in Minneapolis

---

### Post by Frogs Hair on 2010-09-11
Hi, 

Just to try out your idea I downloaded a theme and left it in downloads and tried to open the theme with Gedit. I was given the option to open with by right clicking the package , but received an error . I then extracted the tar gz. and was still unable to open the package . This is the message returned.

---

### Post by Jeff Root on 2010-09-11
That is not the error message I got.
 
I forgot to say that I can drag and drop theme files into
GEdit without any problem.  The actual theme files I was
looking at are for icon themes, and they are plain text.
 
   -- Jeff, in Minneapolis

---

### Post by Jeff Root on 2010-09-17
Nobody knows?
 
   -- Jeff, in Minneapolis

---

### Post by leopardb on 2010-09-21
Well it's an old thing :
[https://launchpad.net/ubuntu/+source/nautilus/+bug/38434](https://launchpad.net/ubuntu/+source/nautilus/+bug/38434)
[https://bugzilla.gnome.org/show_bug.cgi?id=319981](https://bugzilla.gnome.org/show_bug.cgi?id=319981)

Drag & drop on gedit works, but if you want a solution, i'll give you an evil one :

```
sudo gedit /usr/share/mime/packages/freedesktop.org.xml
```Search for x-theme and replace :
```

    <sub-class-of type="application/x-desktop"/>
    <generic-icon name="package-x-generic"/>
```with :
```

    <!-- <sub-class-of type="application/x-desktop"/> -->
    <!-- <generic-icon name="package-x-generic"/> -->
    <sub-class-of type="text/plain"/>
```Then regenerate the mime cache :
```
sudo update-mime-database /usr/share/mime
```Now the .theme files will open with gedit (or any application set to open text files).

Did i mention that it is evil ? it's not a real solution because this file is an offical freedesktop file and the problem is how Nautilus handles .desktop files weirdly. That said, i don't even know why the .theme files should be a sub-class of the .desktop files (but i'm a lowly noob so it doesn't matter).

You could also try an 
```
/usr/share/mime/packages/Overrides.xml
```with something like
```
<?xml version="1.0" encoding="utf-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
    <mime-type type="application/x-theme">
        <comment>theme</comment>
        <sub-class-of type="text/plain"/>
        <generic-icon name="text-x-generic"/>
        <glob pattern="*.theme"/>
    </mime-type>
</mime-info>
```But don't bother ;) it just doesn't work... (although that would be the "right" way to do it).

I've done and tried it for you without noticing any side effect, *until now*. Still, once again, this is bad and i never told you that...

---

### Post by Jeff Root on 2010-09-24
Thanks, poster with even fewer posts than me!
It looks like I'll just get along with dragon
droppings.  Though evil isn't all *that* bad.
 
   -- Jeff, in Minneapolis

---

