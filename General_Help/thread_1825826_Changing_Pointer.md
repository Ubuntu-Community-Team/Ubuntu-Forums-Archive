---
title: "Changing Pointer"
date: 2011-08-15
forum: General Help
---

### Post by Hosmion on 2011-08-15
Hello everyone.  

I'm just going to get right down to the point of this thread.  When I try and change my mouse pointer, it only works partially.  I made a video to try and explain the problem better.  Link below:

[http://www.youtube.com/watch?v=fh-SbxKQLok]("http://www.youtube.com/watch?v=fh-SbxKQLok")

As you see, the other pointer I chose only works over links and when I put it in a text box.  The default mouse is still always there and I don't know how to take it away so I just use the other one I want to use.

Thanks for the help,
Leonard

---

### Post by eawooten on 2011-08-15
Try this:

```
sudo gedit /usr/share/icons/default/index.theme
```
Change whatever it says to the EXACT pointer theme name.

If you open a blank file, make it look like this:

```
[Icon Theme]
Inherits=DMZ-Black
```

But "DMZ-Black" is your pointer theme name.

---

### Post by Frogs Hair on 2011-08-15
This happens with my Opera browser and not just on links . When I hover over the browser I see a plain white X cursor and when I move to an open area on the desktop the custom cursor appears . This only happens with cursors themes down loaded from Gnome Look . 

This has happened with the last two versions of Ubuntu and only with Opera . I have gone back to the default cursor themes because I use Opera more often than the Firefox development release I have installed . I will keep an eye on your thread .

---

### Post by Hosmion on 2011-08-15
> **eawooten said:**
> Try this:

```
sudo gedit /usr/share/icons/default/index.theme
```
Change whatever it says to the EXACT pointer theme name.

If you open a blank file, make it look like this:

```
[Icon Theme]
Inherits=DMZ-Black
```

But "DMZ-Black" is your pointer theme name.

I tried what you told me to, but it didn't work.  I gave the exact name, handhelds, but it didn't work.  I also tried it with the DMZ-Black and it didnt work either.

I got this error:

```
lenni@lenni-Aspire-6930:~$ sudo gedit /usr/share/icons/default/index.theme
[sudo] password for lenni: 

(gedit:15845): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.R9Y2ZV': No such file or directory

(gedit:15845): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:15845): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.GRCC0V': No such file or directory

(gedit:15845): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:15845): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.8EIE0V': No such file or directory

(gedit:15845): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```

---

### Post by Hosmion on 2011-08-15
> **Frogs Hair said:**
> This happens with my Opera browser and not just on links . When I hover over the browser I see a plain white X cursor and when I move to an open area on the desktop the custom cursor appears . This only happens with cursors themes down loaded from Gnome Look . 

This has happened with the last two versions of Ubuntu and only with Opera . I have gone back to the default cursor themes because I use Opera more often than the Firefox development release I have installed . I will keep an eye on your thread .

The cursor was not from Gnome Look, although the ones I have gotten from there have the same effect.  

Should I alert an Administrator about the problem, or what?

---

### Post by Frogs Hair on 2011-08-15
> **Hosmion said:**
> The cursor was not from Gnome Look, although the ones I have gotten from there have the same effect.  

Should I alert an Administrator about the problem, or what?

I don't think it is a forum problem , in my case it may be a setting in Opera I haven't found yet . I did have an issue that was forum related , see the link .  [http://ubuntuforums.org/showthread.php?t=1730035](http://ubuntuforums.org/showthread.php?t=1730035)

---

### Post by Hosmion on 2011-08-15
> **Frogs Hair said:**
> I don't think it is a forum problem , in my case it may be a setting in Opera I haven't found yet . I did have an issue that was forum related , see the link .  [http://ubuntuforums.org/showthread.php?t=1730035](http://ubuntuforums.org/showthread.php?t=1730035)

Is there anyone on the forums associated with the development of the Ubuntu Flavors?

---

### Post by Hosmion on 2011-08-16
Can anybody help?

---

### Post by AlphaLexman on 2011-08-16
I experienced this issue also. As eawooten pointed out, look at '/usr/share/icons/default/index.theme' for me it was a link to '/etc/alternatives/x-cursor-theme'

However, my file has **whitespace** around the equal sign, so that might make a difference.
```
cat /etc/alternatives/x-cursor-theme 
[Icon Theme]
Name = Oxygen Grey
Comment = Oxygen mouse theme. Oxygenize your desktop!
Inherits [COLOR="Red"]=[/COLOR] oxy-grey

```
Of course, change oxy-grey to your liking of DMZ-Black

---

### Post by Hosmion on 2011-08-21
> **AlphaLexman said:**
> I experienced this issue also. As eawooten pointed out, look at '/usr/share/icons/default/index.theme' for me it was a link to '/etc/alternatives/x-cursor-theme'

However, my file has **whitespace** around the equal sign, so that might make a difference.
```
cat /etc/alternatives/x-cursor-theme 
[Icon Theme]
Name = Oxygen Grey
Comment = Oxygen mouse theme. Oxygenize your desktop!
Inherits [COLOR="Red"]=[/COLOR] oxy-grey

```
Of course, change oxy-grey to your liking of DMZ-Black

I already tried that but it still didn't work.

Now I changed from 11.10 to 10.04 LTS.  So if that makes a difference, please help.

---

### Post by AlphaLexman on 2011-08-21
Look at...
```
cat /etc/alternatives/README
```
and...
```
man update-alternatives
```
Try...
```
update-alternatives --list x-cursor-theme
```
These codes are **NOT** the solution to your problem, but just might point you to a solution. I really think the answer is somewhere in '/etc/alternatives/' you may need to use your search skills on the files in that directory to find out where the replacement occurs.

Good Luck!

---

### Post by Hosmion on 2011-08-21
Thanks!

---

