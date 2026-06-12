---
title: "Keyboard Volume"
date: 2006-02-20
forum: General Help
---

### Post by thepocketdrummer on 2006-02-20
I have speakers that are controlled entirely by the computer. There is no external volume control. So, it gets kind of annoying to click on the little speaker icon and slide the volume where I want it. In Windows, I control this with the keyboard's volume keys. I have a Microsoft Multimedia keyboard.

If anyone knows how to make the keyboard control the volume, that would be awesome.

---

### Post by DigitalDuality on 2006-02-20
I too would love to know.  This worked beautifully in Ubuntu.. not so well in Kubuntu.  In fact.. all my multimedia keys worked in Ubuntu (internet button, chat button, e-mail button, audio controls --back stop pause play next eject)

---

### Post by thepocketdrummer on 2006-02-20
I just found this Wiki. I haven't tried it yet, but it may fix both of our problems.

---

### Post by thepocketdrummer on 2006-02-20
I tried following the instuctions... I made the file and tried typing the next command, and it can't read it. I don't know what the problem is. All the keys were exactly the same as his example, so I don't see why it didn't work.

---

### Post by Treviño on 2006-02-20
I've fixed this using xbindkeys: [http://hocwp.free.fr/xbindkeys/xbindkeys.html]("http://hocwp.free.fr/xbindkeys/xbindkeys.html")
There's no volume progress bar shown in the screen like in ubuntu (unless someone write a qt program) btw works well.

Install it from synaptics or adept, you can also add xbindkeys-config to configure it using a gtk front-end.

Anyway edit your /home/user/.xbindkeysrc following examples, to identify your key code use xbindkeys -k.

Now I can't post here my configuration file because I'm not using my PC, btw it's like this (this is only to change volume):

```
# Here's my ~/.xbindkeysrc
# Volume Up
"amixer set Master,0 5%+"
   m:0x0 + c:176

# Volume Down
"amixer set Master,0 5%-"
   m:0x0 + c:174

# Toggle Volume
"amixer set Master,0 toggle"
   m:0x0 + c:160

# Start P1 (Firefox)
"firefox"
   m:0x0 + c:236

# Start P2 (Thunderbird)
"thunderbird"
   m:0x0 + c:178
``` 
Remember to add xbindkeys to X (or KDM) startup.

BYE!

---

### Post by chevyou on 2006-02-20
I'm not sure if this will work in Kubuntu, but I'm pretty sure it's just a KDE thing, so give it a shot.  It worked for me in suse 10.  I have an HP zv5000 with external volume keys.

create a file in your home dir called .Xmodmap
within the file place the following commands
keycode 174 = XF86AudioLowerVolume
keycode 160 = XF86AudioMute
keycode 176 = XF86AudioRaiseVolume

Like I said worked for me...

GOOD LUCK!

---

### Post by thepocketdrummer on 2006-02-21
Can someone make some sense of this for me?
[https://wiki.ubuntu.com/KubuntuVolumeHotkeys?highlight=%28volume%29](https://wiki.ubuntu.com/KubuntuVolumeHotkeys?highlight=%28volume%29)

I tried that and got nowhere. I can't figure out exactly what needs to be done. I even copy and pasted it and it still didn't work. I also tried creating a folder, but if I name it .Xmodmap like the one guy said, it doesn't even show up.

HELP!

---

### Post by DigitalDuality on 2006-02-21
^
the folder is there.. just hidden.

GO to View in the parent directory and select SHow Hidden Files.

---

### Post by thepocketdrummer on 2006-02-22
Ok, well it works in Gnome, but it still doesn't work in KDE. How do I make it work in KDE?

---

### Post by Treviño on 2006-03-19
Look [my previous post]("http://www.ubuntuforums.org/showpost.php?p=755232&postcount=5"), it works well with me.
Instead use keytouch...

---

### Post by Sboulema on 2006-03-20
I use Keytouch [http://keytouch.sf.net/](http://keytouch.sf.net/)
Very helpfull app to get all your multimedia keys working...

---

### Post by Treviño on 2006-03-22
Keytouch create me some (big) problems... Are you using KDE?
Look here: [http://www.ubuntuforums.org/showthread.php?p=850346&posted=1#post850346](http://www.ubuntuforums.org/showthread.php?p=850346&posted=1#post850346)

---

