---
title: "Disable the tilde key press-twice feature"
date: 2010-08-07
forum: General Help
---

### Post by ygoe on 2010-08-07
I have noticed quite often that the tilde key only works when I press it twice. I've searched a while and found out that it can be used for accented characters like with the n (can't do that on Windows here anyway). I only know of the tilde-n from Spanish, I've never seen all of the other tilde-characters. And I do not need any of then ever. But I do need to type in my home directory (~) quite often and I want that to work the first time I press that key. Especially when it works through a PuTTY/SSH shell from Windows, but not directly in Gnome Terminal. The system preferences for the keyboard mapping don't help me out.

So how can I disable that double-press feature for the tilde key? It's allright for the accent keys, the ´ and ` accents alone are invalid characters and should never be used anyway (there's real quotation characters for that) (except for shell backtick expressions) and I don't need the ^ symbol (for coding only) often on Linux.

Using Ubuntu 10.4 with German keyboard mapping (de), directly at the machine or via NX/VNC.

---

### Post by flanagan on 2010-08-07
Does it help if you set a compose key in your keyboard preferences?

Go to System --> Preferences --> Keyboard --Layouts --> Options
Under *Compose key position* choose one of the keys there.

This should override the use of the tilde key as the compose key. You can read more about the compose key and other possibilities where it may be being over-ridden at:

[https://help.ubuntu.com/community/ComposeKey]("https://help.ubuntu.com/community/ComposeKey")

---

### Post by ygoe on 2010-08-07
I've tried that already. It makes the compose key work as expected, but doesn't repair the tilde key. I then have two "compose keys" for tilde accents.

---

### Post by flanagan on 2010-08-07
Then see if it might be being set in a file called .Xmodmap in your home directory. Look for a line in that file with the word "Multi_key".

/etc/X11/xorg.conf might also setting it (per the [ComposeKey]("https://help.ubuntu.com/community/ComposeKey") page).

---

### Post by simosx on 2010-08-07
> **LonelyPixel said:**
> I have noticed quite often that the tilde key only works when I press it twice. I've searched a while and found out that it can be used for accented characters like with the n (can't do that on Windows here anyway). I only know of the tilde-n from Spanish, I've never seen all of the other tilde-characters. And I do not need any of then ever. But I do need to type in my home directory (~) quite often and I want that to work the first time I press that key. Especially when it works through a PuTTY/SSH shell from Windows, but not directly in Gnome Terminal. The system preferences for the keyboard mapping don't help me out.

So how can I disable that double-press feature for the tilde key? It's allright for the accent keys, the ´ and ` accents alone are invalid characters and should never be used anyway (there's real quotation characters for that) (except for shell backtick expressions) and I don't need the ^ symbol (for coding only) often on Linux.

Using Ubuntu 10.4 with German keyboard mapping (de), directly at the machine or via NX/VNC.

Some other members of this forum had this issue recently; the issue is that you use a keyboard layout that places the 'dead_tilde' dead key at the location of the key you expect to type ~. 

You need to look through the keyboard layouts under the Germany list and find one that suits you better.

For your layout you already are using you get ~ if you press AltGr + +.

---

### Post by ygoe on 2010-08-07
There is no .Xmodmap key in my home directory. There isn't even a *Xmodmap* file anywhere in the filesystem. There's only two xmodmap binaries and a bunch of directories and other stuff somewhere.

AltGr++ is the only way I know of to type the tilde character. It's printed on the key cap this way (it's the third glyph on that key). Do other keyboard layouts have alternative methods to enter that character?

Anyway, the best solution for now is to change the keyboard layout/mapping (how's it called in English?) from "Germany" ("Deutschland") to "Germany disable accent keys" ("Deutschland Akzenttasten deaktiveren"). It disables all accent keys, making ^, ´, ` and ~ appear the moment I press the key. To use any accented characters not on the keyboard I need to use a compose key now. That's not too bad. I guess it just doesn't work the Windows way out of the box.

---

### Post by simosx on 2010-08-07
> **LonelyPixel said:**
> There is no .Xmodmap key in my home directory. There isn't even a *Xmodmap* file anywhere in the filesystem. There's only two xmodmap binaries and a bunch of directories and other stuff somewhere.

See what the maintainer of X.org (the GUI server in each Linux distribution) has to say about this 'xmodmap',
[http://who-t.blogspot.com/2010/06/keyboard-configuration-its-complicated.html](http://who-t.blogspot.com/2010/06/keyboard-configuration-its-complicated.html)

> **LonelyPixel said:**
> AltGr++ is the only way I know of to type the tilde character. It's printed on the key cap this way (it's the third glyph on that key). Do other keyboard layouts have alternative methods to enter that character?

Anyway, the best solution for now is to change the keyboard layout/mapping (how's it called in English?) from "Germany" ("Deutschland") to "Germany disable accent keys" ("Deutschland Akzenttasten deaktiveren"). It disables all accent keys, making ^, ´, ` and ~ appear the moment I press the key. To use any accented characters not on the keyboard I need to use a compose key now. That's not too bad. I guess it just doesn't work the Windows way out of the box.

The way it works in open-source software is that people like you and me have a need to type in German. We are not happy with the existing keyboard layout set and we want a variant that matches was we used to get in Windows. German users have been quite prolific and there exist the following layouts,

[FONT="Courier New"]    name[Group1]="Germany";
    name[Group1]="Germany - Eliminate dead keys";
    name[Group1]="Germany - Dead grave acute";
    name[Group1]="Germany - Dead acute";
    name[Group1]="Germany - Romanian keyboard with German letters";
    name[Group1]="Germany - Romanian keyboard with German letters, eliminate dead keys";
    name[Group1]="Germany - Dvorak";
    name[Group1]="Germany - Sun dead keys";
    name[Group1]= "Germany - Neo 2";
    name[Group1]= "Germany - Macintosh";
    name[Group1]= "Germany - Macintosh, eliminate dead keys";
	name[Group1] = "Germany - Lower Sorbian";
	name[Group1] = "Germany - Lower Sorbian (qwertz)";
    name[Group1] = "Germany - qwerty";
[/FONT]

In the Keyboard preferences you can see visually what each layout is supposed to do, and even print it. Nice keyboard image with the characters on the keys and so on.

It is doable to modify an existing layout and create a 'Germany - Equivalent to Windows German layout'.

---

### Post by ygoe on 2010-09-06
It doesn't work anymore... :(
I have setup the system anew today just to see whether everything I've written down was correct so far. I went to System, Settings, Keyboard, added the "Germany eliminate dead keys" layout, removed the "Germany" layout - and the accent keys still do their thing. So the keyboard layout change didn't have any effect at all! I have logged out and tried again, no change. What other option setting did I miss to make this setting work?

---

### Post by ygoe on 2010-09-07
To be more precise: The keyboard layout is correctly selected for local interactive logins, but not for NX connections through FreeNX with the NoMachine client for windows.

---

### Post by ygoe on 2010-09-25
This also happened on OpenSUSE 10.3 so I started looking into fixing that manually. I resolved the issue by adding the command "setxkbmap de nodeadkeys" to the session start programmes. This sets the desired keyboard layout at login, which is then preserved after the NX session suspension. I believe this is an NX server issue.

---

### Post by ghost_zero on 2010-11-24
Actually the real problem here is that normally (even on Windwos where you don't need the tilde for home directory) you have all dead keys EXCEPT the tilde AND
there exists no such kayboard-layout by default on Ubuntu (or I think at any Linux distribution). 
This should definitely be changed. I don't want to give up all the dead keys but just the tilde which I more or less never need.

And I would prefer to do so (in the future) without thinking too much about the how... I mean it actually is quite simple, I just need to replace the dead_tilde with asciitilde in the 
"/usr/share/X11/xkb/symbols/de" file but still...

---

