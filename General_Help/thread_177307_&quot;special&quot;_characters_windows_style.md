---
title: "&quot;special&quot; characters windows style?"
date: 2006-05-16
forum: General Help
---

### Post by justleen on 2006-05-16
Hi People!

I got a quick question (and hopefully it has a quick answer).
Is it possible to get windows style special character input in Ubuntu?
For example the chars ö, î, ú i can get in windows (with US keyboard layout) by typing "o  ^i   and 'u . Is there a way in ubuntu to get these chars as easy as in windows?

(hope this is clear enough...)

---

### Post by Sutekh on 2006-05-16
Here are some ways, the difficulty you experience with each may vary though


 - Try the Character Map (Applications -> Accessories menu)
 - Go to View and change to By Unicode Block
 - The characters are represented by a code, for example the British pound sign (£) is ```
U + 00A3
``` meaning Ctrl + Shift + A + 3


 - You could also add a Character Palette to a Panel if you use GNOME, you just choose the character you want and middle-click (or paste) to pop it in where you need it

---

### Post by Sitix on 2006-05-17
I am experiencing the same problem, isn't there a 'real' solution for that. I mean, the system as Windows made it was ideal...

(I use Kubuntu, so can't do the Gnome thing)

---

### Post by Sutekh on 2006-05-17
[quote=Sitix]I am experiencing the same problem, isn't there a 'real' solution for that. I mean, the system as Windows made it was ideal...
[/quote] I don't understand. This is how I get special characters in Windows. Either I open the character map and copy it across, or look up the unicode value and type it in. Its exactly the same way.

[quote=Sitix]
(I use Kubuntu, so can't do the Gnome thing)[/quote] You might want this package (from the universe repository)

[Ubuntu Packages - kcharselect]("http://packages.ubuntu.com/breezy/utils/kcharselect")

If you enable the universe repository, all you need is
```
sudo apt-get install kcharselect
``` I haven't used this program though.

---

### Post by henriquemaia on 2006-05-17
[QUOTE=Sutekh]Here are some ways, the difficulty you experience with each may vary though


 - Try the Character Map (Applications -> Accessories menu)
 - Go to View and change to By Unicode Block
 - The characters are represented by a code, for example the British pound sign (£) is ```
U + 00A3
``` meaning Ctrl + Shift + A + 3

[...][/QUOTE]


Wow! Nice tip. This is really cool to know! Thanks a lot.

---

### Post by henriquemaia on 2006-05-17
[QUOTE=Sutekh]Here are some ways, the difficulty you experience with each may vary though


 - Try the Character Map (Applications -> Accessories menu)
 - Go to View and change to By Unicode Block
 - The characters are represented by a code, for example the British pound sign (£) is ```
U + 00A3
``` meaning Ctrl + Shift + A + 3


 - You could also add a Character Palette to a Panel if you use GNOME, you just choose the character you want and middle-click (or paste) to pop it in where you need it[/QUOTE]

How about when the code has letters, like **U+FEEC**?

---

### Post by henriquemaia on 2006-05-17
[QUOTE=henriquemaia]How about when the code has letters, like **U+FEEC**?[/QUOTE]

Ok, I got it right now. I just got too over excited and had my brain impaired for some moments. My appologies.

---

### Post by doclivingston on 2006-05-18
There is a much better way: using the Compose key.

Go to System->Preferences->Keyboard, then Layout Option->Compose Key Position, and set one of the keys to be Compose. The hold down the compose key, and type the characters you want composed together (you can release compose for the second character).

Compose + " + a  ->  ä
Compose + ` + e  ->  è
Compose + , + c  -> ç
Compose + ^ + i  ->  î
Compose + / + O  ->  Ø
Compose + * + a  -> å

---

### Post by Sutekh on 2006-05-18
Now that *is* a much better way!  Cheers!

---

### Post by doclivingston on 2006-05-18
The only downside is that there isn't a convenient list of all the composition mappings (aside from one of the source files for xorg). I've heard that the character map will be getting the ability to display composition-mappings for 2.16 though.

---

### Post by Sitix on 2006-05-18
[QUOTE=doclivingston]There is a much better way: using the Compose key.

Go to System->Preferences->Keyboard, then Layout Option->Compose Key Position, and set one of the keys to be Compose. The hold down the compose key, and type the characters you want composed together (you can release compose for the second character).

Compose + " + a  ->  ä
Compose + ` + e  ->  è
Compose + , + c  -> ç
Compose + ^ + i  ->  î
Compose + / + O  ->  Ø
Compose + * + a  -> å[/QUOTE]

This was exactly what I wanted, but I can't get it working. There isn't something like a compose key in my keyboard options. If I use the search option in the system settings I can't find anything even like it either...

---

### Post by davey.moore on 2008-07-07
> **doclivingston said:**
> There is a much better way: using the Compose key.

Go to System->Preferences->Keyboard, then Layout Option->Compose Key Position, and set one of the keys to be Compose. The hold down the compose key, and type the characters you want composed together (you can release compose for the second character).

Compose + " + a  ->  ä
Compose + ` + e  ->  è
Compose + , + c  -> ç
Compose + ^ + i  ->  î
Compose + / + O  ->  Ø
Compose + * + a  -> å

I was just looking for a quick way to do the £ symbol and I found it thanks to this.

Im letting others know in case you are looking for it:
Once you activate your Compose Key, you do:

Compose + minus symbol + L   = £

---

