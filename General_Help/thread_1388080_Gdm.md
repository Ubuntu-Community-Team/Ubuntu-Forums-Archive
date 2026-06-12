---
title: "Gdm"
date: 2010-01-22
forum: General Help
---

### Post by Elfo33 on 2010-01-22
I have a boring, brown, GDM login screen.  I'm assuming this is what shows when there are no GDM themes.  I don't see any options in Administration -> Login Window, so what do I need to do to get the standard, Ubuntu GDM theme?  What package (asides from vanilla GDM) is required for this on Karmic?

---

### Post by VCoolio on 2010-01-22
Check [here]("http://ubuntuforums.org/showthread.php?t=1384578")

---

### Post by sisco311 on 2010-01-22
run your theme manager as user gdm:
```
sudo -u gdm dbus-launch gnome-appearance-properties
```
or set the theme in gconf editor:
```
sudo -u gdm dbus-launch gconf-editor
```
edit the value of the /desktop/gnome/interface/gtk_theme key

or use this python script: [thread=1358026]GDM2 Configuration Tool[/thread]

---

### Post by Elfo33 on 2010-01-22
Thanks for the help sisco, but those commands don't appear to solve my issue.  Maybe I need to clarify, I'm running 9.10, and my login has the geography of the default loging window shown [here](http://gadgetmix.com/index/wp-content/uploads/2009/09/ubuntu-10-04-karmic-koala-login-screen.JPG).

But all that eye candy?  Gone.  It's a very simple, ugly, light gray box with an even uglier solid brown background.  Think Windows 95 if they did brown, or of an Ubuntu minimal install before adding any desktop themes.

For whatever reason, the package "gdm" is not pulling in the default eye-candy, which is all I want.  I don't see what dependency it might be in the repository, either :/

---

### Post by JiuJitsu500 on 2010-01-22
To change your xsplash (splash screen with the ubuntu symbol and the loading animation) you can simply change the background, or put a whole new animation by downloading on in Gnome-look.org, or simply putting your own picture in the xsplash folder (when root). Also, this is a GUI way of doing this...

Set your root password (thoug hI don't even think this is completely necessary, I did it) open a terminal:

sudo passwd

Type your user password, then your UNIX (root) password (twice) and root is set.

Anywho though, the fun. Press ALT+F2 to open a run command without the terminal and type:

gksu nautilus

This opens the nautilus (your file manager in Gnome) after typing your password. You background will change to the default ubuntu orange thing, as you are now root. Navigate here:

File System > Usr > Share > Images

There is your xsplash folder, to get the image to change (and animations, etc) simply rename xsplash to something else (to preserve it) and create a new folder, call it xsplash, and put your image here (make sure the extension is changed to .png) and your colorful animations, or copy the ones in the original and put them here... 

EDIT* this is done best I think by opening the tar.gz if this is the downloaded file, dragging it in here from another window, and extracting it here.

Exit nautilus, now your xsplash is changed.

For the background of your login screen, to get it the same as the splash screens'... write this down and perform at the log in screen:

Press CTRL+ALT+F1 to open up a terminal at the log in screen.
Log in with your normal user name and password
Type: export DISPLAY=:0.0
Then type: sudo -u gdm gnome-control-center

Some crazy lines will pop up.... then the ability to type some more, but you don't have to, hit CTRL+ALT+F7 to close the terminal.... and you will notice now the control center is open. To modify the appearance, click on appearance and change what you want, even window colors (but I still haven't figured out how to move the box at all). Add a background image as you normally do, by clicking Backround > Add and find your picture and add it. Then.... viola!

Splash screens and Login Background are changed to your liking :)

---

### Post by Elfo33 on 2010-01-22
I've tried installing xsplash, and it changes the ugly brown background to a prettier background.  However, the login window, computer icon, and bottom bar remain old and ugly.

Plus, xsplash puts up an annoying splash screen which I don't want.  All I want is a pretty login window.

---

### Post by JiuJitsu500 on 2010-01-22
open the gnome control center like i described, and you can modify window appearance (changes the login window) as you see fit.... go to the colors tab after clicking "customize" in the theme portion.

---

### Post by JiuJitsu500 on 2010-01-22
to see the changes in real time i should add, just move the windows out of the way of the log in window to see them applied as you change them, to be sure you do exactly what you want to it.

The icon though is in the themes folder, and it's called "computer.png".... so if you want a new one you have to put your own icon in there called the same thing, and choose that theme in the control center.

The Icon is located here (for the default human login Icon): File System > Usr > Share > Icons > HumnLoginIcons > apps > 64

Change it's name to something else to preserve it, and put whatever small image you like in it's place (and rename it exactly how it the ubuntu symbol was), and it will appear.

---

### Post by growlf on 2010-01-22
Mmm... there is now a tool that helps in this scenario. GDM2 and Karmic - missing all options.  Yep.   Look at this post:

[http://ubuntuforums.org/showpost.php?p=8707543&postcount=55](http://ubuntuforums.org/showpost.php?p=8707543&postcount=55)

Allows many of the old settings again.

---

