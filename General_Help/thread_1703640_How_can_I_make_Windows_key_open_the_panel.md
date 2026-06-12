---
title: "How can I make Windows key open the panel?"
date: 2011-03-09
forum: General Help
---

### Post by jockopablo on 2011-03-09
Hi, all.  I'm trying to find a way to make my Windows key the shortcut to opening my start panel in Lubuntu.  I've found easy instructions for Ubuntu, but Lubuntu doesn't have the keyboard shortcuts utility that Ubuntu has (at least I can't find it).

I found some instructions for editing a config file but I can't find the command for opening the panel, and I've seen conflicting information about how the Windows key is written (some say W, some say Super_L), so I hesitate to start playing around with that file when I'm only guessing.

Thanks in advance for any suggestions.

---

### Post by kerry_s on 2011-03-09
lubuntu uses openbox for it's wm, so thats what you want to learn.
[https://help.ubuntu.com/community/Openbox](https://help.ubuntu.com/community/Openbox)

---

### Post by jockopablo on 2011-03-09
Haha.  Thanks, I guess.

"Hey, can anyone tell me the proper sparkplug gap for a '92 V8 Mustang?"

"Mustangs run on a combustion engine.  Read this."  /gives entire Chilton manual.

:confused:

---

### Post by kerry_s on 2011-03-09
> **jockopablo said:**
> Haha.  Thanks, I guess.

"Hey, can anyone tell me the proper sparkplug gap for a '92 V8 Mustang?"

"Mustangs run on a combustion engine.  Read this."  /gives entire Chilton manual.

:confused:

:lolflag: it don't say in the manual ?

open your home folder(file manager/pcmanfm), press ctrl+h to show the hidden files, go into .config, look for a folder named "openbox", go into that folder, there should be a custom *.xml file for lubuntu, open that with your text editor(mousepad), scroll down till you see the keyboard shortcuts section.
that is where you need to add to, then restart openbox.

lubuntu is made of bits & pieces, once you learn the different parts it's easy, the main part is openbox.

give me like 45min to download & burn to usb, then i can run it live & be more detailed.

---

### Post by jockopablo on 2011-03-09
Thanks, Kerry.  I got that far, believe it or not, but I could't find the specific key name for the Start/Open Panel button or what Lubuntu's name for the Windows key is.

---

### Post by kerry_s on 2011-03-09
> **jockopablo said:**
> Thanks, Kerry.  I got that far, believe it or not, but I could't find the specific key name for the Start/Open Panel button or what Lubuntu's name for the Windows key is.

i think default it's set to 1 of the f# keys, i think alt+f1, just a matter of changing it to the Super_L

i'm at 15 min's on the download, so as soon as i boot it up i can tell you what line number it's on in the file, just hang in there.

i haven't used lubuntu in at least a year, so it's due for some play time anyways.

---

### Post by kerry_s on 2011-03-09
alright, here we go. ;)

go into ~/.config/openbox
open lubuntu-rc.xml with leafpad
click options-> line numbers
scroll down to line 286 you should see this:
```
    <keybind key="C-Escape">
      <action name="Execute">
        <command>lxpanelctl menu</command>
      </action>
```

change "C-Escape" to "Super_L"
now save the file(file-> save)
now press alt+f2
type> openbox --restart

try it out, you should be good to go.

anything else ? i'm running live so hit me up now.

---

### Post by kerry_s on 2011-03-09
alright, i'm done with lubuntu, it's still as crashy as i remember.

what ya think, i gave it the gnome style make over. :lolflag:

---

### Post by jockopablo on 2011-03-10
> **kerry_s said:**
> alright, here we go. ;)

. . .

As the young'uns say these days:  w00t!  Thank you so much!

My appropriate keybinding line wasn't on 286 but I found it easily enough.  

I might try to submit that tip to the Lubuntu wiki.  

BTW:  Lubuntu crashes a lot for you?  I must be lucky.  I haven't had a crash yet (/knocks on wood).  Is there a light distro you like better?  The main reason I'm using this is because it's fast and light and seems perfect for my netbook.

Thanks again.

---

### Post by kerry_s on 2011-03-10
> BTW: Lubuntu crashes a lot for you? I must be lucky. I haven't had a crash yet (/knocks on wood). Is there a light distro you like better? The main reason I'm using this is because it's fast and light and seems perfect for my netbook.

it's the file manager that always acts up for me, first it started crashing, then it just wouldn't work no more. in the past when i installed lubuntu, i always ended up replacing it with thunar the xfce4 file manager.

my machines a nettop, same specs as a netbook. see pic
for a netbook i would probably go meego, i got a google notebook & love living in the cloud.
[http://meego.com/](http://meego.com/)

---

