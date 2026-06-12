---
title: "dual keyboard layout"
date: 2006-05-25
forum: General Help
---

### Post by ingo on 2006-05-25
Hi all,

I'm running Xubuntu on an old IBM laptop and need to have a dual keyboard layout (UK & DE). Problem is, I don't know how to! Searched the forum and googled but still no joy.

Can anybody point me in the right direction?

Cheers

---

### Post by Sef on 2006-05-25
I have set up dual keyboards under Gnome, so I will tell the basics.

1) Language support  

2) Keyboard layout

3) SCIM Input Method Setup

With those 3, I was able to have the choice of which langauge I wanted to boot my computer into, and switch between languages with pushing 2 buttons.  In Xubuntu, they made called something else, but the name should be similar.

---

### Post by ingo on 2006-05-25
Thanks Sef,

language support:  seems to me like the whole OS can be displayed in whatever language you choose but no keyboard switching option

keyboard layout: there is an applet under xfce, but first you have to tell the keyboard to have more than one language! This is my current problem.

SCIM: appears to support different writing systems but unfortunately not what I am looking for

Any other suggestions? I seem to recall something about manipulating the xorg.conf file, but cannot for my life remember how...

---

### Post by Lusse on 2006-11-21
xorg.conf?

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"Device"	"/dev/input/event0"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
**	Option		"XkbLayout"	"uk,de"**
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

---

### Post by ingo on 2006-11-25
that did it lusse!

thanks for your reply - how simple when you know how :)

---

### Post by MasterOfMuppets on 2007-02-11
Where can I find all the language acronyms?
I mean, so I would know what to write in the xorg.conf :)...

I added he (hebrew) in that line where you guys added de, and I still can't switch...
I can switch from English to Hebrew but not from Hebrew to english.

---

### Post by ingo on 2007-02-12
bit of googling came up with
[http://en.wikipedia.org/wiki/List_of_ISO_639-1_codes](http://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)
looks like heb is what you're after

hth

---

### Post by MasterOfMuppets on 2007-02-12
Didn't work :(...
I'm running kubuntu, in case that matters.
This is how my xorg.conf looks on that part:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us,heb"
	Option		"XkbOptions"	"lv3:alt_shift_toggle"
EndSection

```

I found the toggling key somewhere, can't remember exactly where...

---

### Post by ingo on 2007-02-12
Kubuntu? Well, in that case things are considerably easier :) Open System Settings, select Regional & Language, go to Keyboard Layout and go for Israel and Bob's your uncle :)

BTW, in the next tab along called switching options you can decide whether language options should be global, application or window specific - very useful! Also, standard keyboard switching between languages is ALT + CTRL + K, but you can change that to whatever you like.

HTH

---

### Post by MasterOfMuppets on 2007-02-12
Wish that would work... :(
I turned on sticky swirtching but it simply resets itself once I quit the Regional @ Language menus...

I found out about the ALT+CTRL+K option a while ago, but it switches only one way : form English to Hebrew.

And by the way, my grandpa's name's Bob, not my uncle's. Very close! :P
```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us,he"
        Option          "XkbOptions"    "grp:alt_shift_toggle"
EndSection

```

---

### Post by ingo on 2007-02-12
Hehe...

Ah, ok, you've changed it to ALT+SHIFT, makes sense. Try removing your second language from the XkbLayout line, restart kdm (sudo /etc/init.d/kdm restart) and give it another go.

---

### Post by MasterOfMuppets on 2007-02-12
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "grp:alt_shift_toggle"
EndSection

```

Restarted, nothing much resolved... I think it restarted successfully, can't know for sure since it popped me to nothing and I had to ALT+CTRL+F1 to log back in... TO GNOME :(.
Restarted and this is how xorg.conf looks now.
I can switch via ALT+CTRL+K to Hebrew from English, but not the other way around.
I'll make it:
```
        Option          "XkbLayout"     "us,he"

```
now and hope for the best. I've tried this before, but maybe the restart does it?

---

### Post by svetlin on 2007-02-13
Try switching languages with Ctrl+~

---

### Post by ingo on 2007-02-13
Out of interest, what - if anything - did you do to your kde that it didn't work? I've been using KDE for the last three years and this feature never once let me down. I even installed KDE on top of Ubuntu once (now using Kubuntu) and had no probs. 

Having said that, even though my languages can be switched at the mo I couldn't adjust it anymore if I wanted to 'cos all the settings in "System Settings" have gone blank!?

---

### Post by MasterOfMuppets on 2007-02-13
I removed the normal ubuntu desktop aka the gnome after I added KDE to the mix.
I don't know what's wrong... I already re-installed a pure kubuntum and I still have this problem. :(

I'll try CTRL+~ and get back to you guys, thanks for that bit.

---

### Post by yurukov on 2007-02-16
I have a similar problem - I am switching between an English and a Bulgarian kayboard layout. The problem is that Bulgarian means Cyrillic and then the common key combinations like Ctrl+C/V/X etc. don't work. Also I cannot set a key combination Ctrl+Shift ( the windows one ) to change the keyboard layout . Any idea how to fix any of this?

---

### Post by ingo on 2007-02-17
OK, the problem can't be as bad as all that, take that gun away :)

Seriously, there are two ways of defining the "switching" keys - via kde or gnome or directly on file level - /etc/X11/xorg.conf

Check MasterOfMuppets' xorg.conf extract
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "grp:alt_shift_toggle"
EndSectionThe last line but one tells xorg to change languages when alt and shift are pressed.

Doesn't that work for you?

---

### Post by svetlin on 2007-02-17
S Ctrl+~ triabva da stane, zashtoto "~" ne se promenia pri smiana na ezika. Pri men raboteshe predi izobshto da izchezne bulgarskia.

Smeni shortcut-a ot System settings -> Keyboard & Mouse -> Keyboard Shortcuts, naj-otdolu, ot Ctrl+Alt+K na Ctrl+~

---

### Post by yurukov on 2007-02-17
:) znam az go bqh napravil s Alt+1 no sym sviknal po na4ina v windows.


No it does not work. I restarted the system but no effect. I set it to Alt+1 from the settings. I cannot set it to Alt+A or any other letter, because when the layout is to Cyrillic, the shortct does not work.

---

### Post by MasterOfMuppets on 2007-02-19
I managed to fix my problem, simply overridden the KDE defaults and did it on X level like ingo suggested.
I would like to have an icon to tell me what language am I using at any given moment, but this has been enough of a headache anyways, so I'll let it be for a while :P...

---

### Post by ingo on 2007-02-19
Nice one. So what does your xorg.conf look like now?

---

### Post by yurukov on 2007-02-19
Mine goes like this:
```

...
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "grp:alt_shift_toggle"
EndSection
...

```

I guess that the secton about "xkblayout" should also include the bulgarian layout. How should I write it?

---

### Post by MasterOfMuppets on 2007-02-19
Option          "XkbLayout"     "us,bl"

I think that will do the trick, although "bl" might not be the correct abbreviation for Bulgarian.  Try looking for the correct abbreviation in the forums, I'm sure it's written here somewhere :).

---

### Post by yurukov on 2007-02-19
I'll see if that does the trick. Thanks.

---

### Post by ingo on 2007-02-20
> **ingo said:**
> bit of googling came up with
[http://en.wikipedia.org/wiki/List_of_ISO_639-1_codes](http://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)
looks like heb is what you're after

hth
I like quoting myself :)

---

### Post by MasterOfMuppets on 2007-02-20
That's not the place ingo... You can check what's your language abbreviation by looking in the language options in the menu.

---

