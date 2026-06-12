---
title: "scale plugin shortcut"
date: 2012-07-02
forum: General Help
---

### Post by typos1 on 2012-07-02
Up until I upgraded to Precise, I had a scale windows icon in unity, whenever I wanted to access others windows on the desktop I just clicked on it and it showed all open windows. 

It disappeared after I ugraded to Precise. It was invaluable, I m trying to re-instal it but I ve searched all over the net and I cant find anything other than pressing super + w or alt + shift + up. 

I much prefer clicking on an icon to do it, anyone know where I can get it now ?

---

### Post by typos1 on 2012-07-09
Anyone know what happened to this app?

---

### Post by stinkeye on 2012-07-10
Make your own launcher.

Install xdotool (Program to simulate keyboard input)
```
sudo apt-get install xdotool
```

Save this as **Scale.desktop** to **~/.local/share/applications**
```
[Desktop Entry]
Type=Application
Version=1.0
Hidden=false
Terminal=false
Icon=[COLOR="Magenta"]/usr/share/icons/hicolor/scalable/apps/nautilus.svg[/COLOR]
Name=Scale
Exec=xdotool key Super+w
```
[COLOR="magenta"]Choose an icon[/COLOR]
To edit **Scale.desktop**, open gedit and drag and drop the file into it.
or in the terminal
```
gedit ~/.local/share/applications/Scale.desktop
```


Then just drag the **~/.local/share/applications/Scale.desktop** to the launcher.

---

### Post by typos1 on 2012-07-10
Thanks for the reply!

I ve installed xdotool.

I ve coded the second bit :
```
[Desktop Entry] Type=Application Version=1.0 Hidden=false Terminal=false Icon=[COLOR=Magenta]/usr/share/icons/hicolor/scalable/apps/nautilus.svg[/COLOR] Name=Scale Exec=xdotool key Super+w
```but it then says :

 ```
The program 'key' is currently not installed.  You can install it by typing:
sudo apt-get install donkey
```DO I go ahead and install donkey ? Or should this code be in a gedit file n user/share/apps?

When I drag the icon to the file it says "there was an problem opening the file . . ."

What do you mean by "launcher" ? Nothing happens if I drag it to unity and cant drag it to dash cos dash disappears when  click on the file.

When I click on the scale icon file it says there was an error opening the application

---

### Post by typos1 on 2012-07-10
Ah, didnt get the meaning of the pink text, but now I realise it was for me to choose an icon, the one I choose first of all was a png, I ve now chosen an .svg and I dont get the error in gedit.

But its not working properly and cant get the icon to the launcher

---

### Post by stinkeye on 2012-07-10
In the terminal copy and paste the xdotool command and press Enter.
```
[COLOR="red"]xdotool key Super+w[/COLOR]
```
If that works check your **Scale.desktop** file has exactly the same command including the spacing.
ie
```
[Desktop Entry]
Type=Application
Version=1.0
Hidden=false
Terminal=false
Icon=/home/glen/Pictures/switch_windows.png
Name=Scale
Exec=[COLOR="red"]xdotool key Super+w[/COLOR]
```

Because of the way the launcher works you have to wait 8-10 secs before you can run again or
use the middle mouse button to click on the icon.

---

### Post by typos1 on 2012-07-10
It works if I type the super+w command in the terminal. But I m not sure where I should code "[Desktop Entry] . . .Exec xdotool key Super+w". Do you mean in a terminal or in a gedit ? 

In a terminal its still says that the program key is not installed I should install it by typing sudo apt-get install donkey.

I think you mean in a gedit, cos thats what I ve done and I m getting somewhere now - I ve got a blank icon in the launcher and it works if I click on it !! 

But even though I ve dragged and dropped the icon I want into the gedit (when I do it comes up in another gedit, not the one I dragged it to), I ve just got a blank icon with a question mark.

When I goto home/local/share/apps and clickon the gedit file it says that "Untrusted application launcher" and that it may be unsafe, but the only option is "ok" which closes the window.

---

### Post by stinkeye on 2012-07-10
You need to specify the path to the icon in the 
**~/.local/share/applications/Scale.desktop** file.
eg I searched in google images for **switch_windows.png**
and saved the image to my Pictures folder.

Then edited Scale.desktop to use that image.
Open Scale.desktop with gedit (copy and paste the following command in the terminal)...
```
gedit ~/.local/share/applications/Scale.desktop
```
eg my file with edited [COLOR="Magenta"]icon path[/COLOR]
```
[Desktop Entry]
Type=Application
Version=1.0
Hidden=false
Terminal=false
Icon=[COLOR="magenta"]/home/glen/Pictures/switch_windows.png[/COLOR]
Name=Scale
Exec=xdotool key Super+w
```


> **typos1 said:**
> 
When I goto home/local/share/apps and clickon the gedit file it says that "Untrusted application launcher" and that it may be unsafe, but the only option is "ok" which closes the window.
You can't open a .desktop file directly.
You have to open in the terminal with
```
gedit *[COLOR="DimGray"]/path/to/.desktop[/COLOR]* 
```
or drag and drop the .desktop file into a gedit window.

P.S
You don't need donkey.
Sounds like your entering the .desktop code in the terminal instead of saving in gedit.

---

### Post by typos1 on 2012-07-10
Lol, I had the path to your icon ! Clearly that wont work !

Now added the correct path to my icon, but nothing changes, do I need to reboot ? Or should the icon change as soon as I save the gedit ?

---

### Post by stinkeye on 2012-07-10
> **typos1 said:**
> Lol, I had the path to your icon ! Clearly that wont work !

Now added the correct path to my icon, but nothing changes, do I need to reboot ? Or should the icon change as soon as I save the gedit ?
logout/in
Does it work now?

---

### Post by mc4man on 2012-07-10
The code box in post 4 shows the .desktop (launcher), having everthing on one line.
Does your .desktop look like the ones stinkeye has posted, ie. each part of the .desktop is on a seperate line??

---

### Post by typos1 on 2012-07-10
Already tried that, no it doesnt :(

---

### Post by stinkeye on 2012-07-10
In the terminal run...
```
gedit ~/.local/share/applications/Scale.desktop
```
and post a screenshot of the file.
Alt+print should take a screenshot of the active window.

---

### Post by typos1 on 2012-07-10
Is this where I find out I ve made a basic error and look stupid ? !

---

### Post by mc4man on 2012-07-10
your path for Icon= is wrong
should be 
Icon=/home/Jason/switch-windows.png
or
Icon=/home/jason/switch-windows.png
(depends on whether your username is Jason or jason

Then just drag the .desktop from ~/.local/share/applications on to unity launcher

(if you wanted to test the .desktop in place (~/.local/share/applications), then right click on the .desktop > Properties > > Permissions > & enable -  Allow executing file as program, though this isn't needed to  use in launcher

---

### Post by stinkeye on 2012-07-10
> **typos1 said:**
> Is this where I find out I ve made a basic error and look stupid ? !
The path to the image is incorrect.
To get the correct path, right click on the switch_windows.png and select copy.
Always better this way.No typing mistakes. 
You can now paste the correct path in to gedit.

---

### Post by mc4man on 2012-07-10
Just as an aside for possible future use - 
myself always find that when using custom or icons in a non-standard locations it's easier to just place the icon in
/usr/share/pixmaps

Then one can just use the icon name (no extension) on the Icon= line

---

### Post by typos1 on 2012-07-10
Hmm, it was"home" initially, but I changed it to "Home" whith a capital after it didnt work because I noticed that "Home" was spelt with a capital in Nautilus. 

I fiddled about with it a few tmes, including swapping "home" and "jason", the order I posted the screen shot was just the last combo I tried. 

Anyway,  changed home back to lower case and swapped it with "jason" lower case and logged out then I noticed my username was with a capital on the login screen. But despite that, when I logged back in the icon appeared, even though it shouldnt really work cos the gedit has "jason" spelt with lower case. 

Still, thanks for the help !!

---

### Post by Kopkins on 2012-07-10
Ubuntu sets your username and your first name with a lowercase letter, as far as I know, unless you change it. On my login screen, it displays my full name, for example 'John Smith', but my username is simply 'john'. 

Glad you got everything working.

Kopkins

---

### Post by typos1 on 2012-07-10
Ah, well that explains it then !

---

