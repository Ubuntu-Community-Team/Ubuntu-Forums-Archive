---
title: "Accented characters"
date: 2009-09-06
forum: General Help
---

### Post by ppb7 on 2009-09-06
hello,
I have just switched to jaunty and the best way to win over others is by proving that they can do the same things with jaunty as with xp. I´ve come across a problem with accented characters. While writing them in an Openoffice document is easy, the same key combinations I used then do not produce the same characters. i have a generic 105 key keyboard set to United Kingdom International (with dead keys). For instance, while in Openoffice the compose key + ` + a gives an a grave, this is not the case here as i am writing my question
LATEST
I am confused as what worked in OO this afternoon fails to do so now :?::?:

---

### Post by mike555 on 2009-09-06
Here is an old article that might help ...... there is a program to do what you want, but I can't remember the name,yet.

[http://www.debianadmin.com/special-characters-made-easier-in-ubuntu](http://www.debianadmin.com/special-characters-made-easier-in-ubuntu)


-- this link might help...   [https://help.ubuntu.com/community/GtkComposeTable](https://help.ubuntu.com/community/GtkComposeTable)

---

### Post by ppb7 on 2009-09-07
> **mike555 said:**
> Here is an old article that might help ...... there is a program to do what you want, but I can't remember the name,yet.

[http://www.debianadmin.com/special-characters-made-easier-in-ubuntu](http://www.debianadmin.com/special-characters-made-easier-in-ubuntu)
This link didn´t work but the following one did and I thank you for that:
> 
-- this link might help...   [https://help.ubuntu.com/community/GtkComposeTable](https://help.ubuntu.com/community/GtkComposeTable)however, things don´t seem to be working qute as they are supposed to. I have mapped the compose key to be both Win keys, yet some characters still work only with the default (shift+alt_gr together) and others behave very strangely i.e. they sometimes work but in an odd fashion (a grave requires Win+`+`+a) or don´t work at all. Also, as i am writing this, `, ´ and ¨ require 2 keystrokes. Some accented characters I can easily get through another keyboard layout then toggling between layouts, but not all characters can be had this way, so  I&#7743; welcoming other suggestions (if possible, I would like to avoid using the character palette as its use slows down things for me.

---

### Post by amauk on 2009-09-07
Right click on a Gnome panel (say, the top panel)
select "Add to Panel"
and add the "Character Palette" applet

Click the character you want, it'll be copied to your clipboard, then just paste into your application

simplest way to deal with foreign characters in any application

---

### Post by cholericfun on 2009-09-07
i extensively use the 3rd and 4th characters on the keyboard, (see attachment)

although at the beginning it seemed my settings were only held for
one login session until it magically ended up working the way i wanted.

under system - keyboard - Layout - layout options i have:

Third Level Chooser (some button) 

ô é ø ñ ß &#8542; ...

---

### Post by longtom on 2009-09-07
I have mine on South African setup.

Can do it all.

a ä á à 

the à I get by pressing 3rd party and hold it.  After that I press ` (next to the 1) and than a.

my third party knob is right Windows (must be useful for something)

You can set your third party knob at System > Preferences > Keyboard.

Go to Layout and press "Layout Options"  In "Third level Chooser" select what you want.
After that you can print your layout so you have a reference until you are familiar with all the shortcuts.

Good Luck!!

---

### Post by ppb7 on 2009-09-08
No luck anywhere. Whatever the keyboard configuration chosen, certain characters can only be obtained with the combination Alt_GR+Shift. As i use accented characters all the time, using the character palette is too cumbersome. I have now found out that à, ç, é, è and ù I can get most easily by switching keyboards and getting a French setup, but adding a third keyboard layout would be confusing and I would like to use the Win keys as they are otherwise redundant. i am mainly missing German characters (umlauts, that´s Alt_GR+shift then double quote then key) and other French vowels. There must be other parameters that I haven´t configured correctly (if you go to Keyboard layout, you´ve also got Alt/Win key behaviour, Compose key position and choice 3rd level key. And don forget that I still need to press twice the key that gives an apostrophe or a double quote. ](*,)

Also what are the Multi, Super, hyper and compose keys? :?:

---

### Post by bobince on 2009-09-08
You're nearly there!

> if you go to Keyboard layout, you´ve also got Alt/Win key behaviour, Compose key position and choice 3rd level key.

Go there and pick a compose key position. I use a Windows key, so I can type Win, then e, then ' to get é (there are many, many combinations).

Now you can forget the stuff with altgr and dead keys which I find much less convenient.

> And don forget that I still need to press twice the key that gives an apostrophe or a double quote.

Yes, that is why unalted-dead-keys layout like UK International are a total waste of time.

"Super" is another name for the Windows key (it actually predates Windows, the keycode was repurposed). The other others you are unlikely to see on a typical keyboard.

---

### Post by ppb7 on 2009-09-10
> **bobince said:**
> You're nearly there!
No, i´m afraid i´m not. i have now tried all the combinations possible (including many keyboard layout options) and here is what´s what:
- the options chosen are: Win key as compose key; menu key to switch keyboard layouts; scroll lock keyboard LED indicates that I have switched keyboard layouts
- i can get some less frequently used characters with the Win key (¥, € and ß for instance);
- I have to press any Alt key together with Shift, then the relevant keys to get most accented characters (î or ö for instance);
- to get é, è, ç, ù or à the easiest is to switch keyboard layouts (i opted for the menu key and France Alkternative, Latin-9 only keyboard) as only 1 keystroke is required (2 on the UK keyboard becomes é);
- I still need to press twice the apostrophe and quote key to get them to appear;

in short, I thought that using a single compose key would make it easier to produce accented characters (a different layout is problematic as other characters like the comma will be in another place thn the one you´re used to).
By the way, 4 characters are possible on most keys on the france alternative kbd but i can only  get them by pressing and holding the Alt_gr key. Any way of changing that?

---

### Post by cholericfun on 2009-09-10
i think youre not seeing the "third level chooser" option where you've been playing around with "compose key"  options

just as an e.g.:

i have gb-english, greek, german


Keyboard Layout options:

all off except:

Layout swiching: right Win key

Third Level Chooser: Alt_Gr

the LED option



...try that...

---

### Post by StuartN on 2009-09-10
> **ppb7 said:**
> I thought that using a single compose key would make it easier to produce accented characters

I have the right control key set as my compose key, although it should not make any difference to the following. The following works in most applications from Terminal upwards:

&#261; compose-;-a
á compose-'-a
à compose-`-a
ä compose-"-a

Some programs, like OpenOffice, have a language setting. This is stored as an OpenOffice setting and stored in individual documents, and it will change the keyboard locale when OpenOffice is running, and when documents are opened. It should be possible to get most characters without changing language.

---

### Post by bobince on 2009-09-11
> in short, I thought that using a single compose key would make it easier to produce accented characters (a different layout is problematic as other characters like the comma will be in another place thn the one you´re used to).Yes, that's exactly right. Do that.

Use the standard UK layout without dead keys; drop UK International ('cos the dead keys are annoying) and the other layouts; don't bother switch between layouts. Don't bother with the dead keys on the third-level chooser at this point. Just use purely the compose key to get a wide range of diacriticals.

(You can type the letter first too if you prefer. eg. compose-c-comma -> ç.)

---

### Post by StuartN on 2009-09-11
> **ppb7 said:**
> And don forget that I still need to press twice the key that gives an apostrophe or a double quote. ](*,)

I thought I had to press compose + the accent, and then the vowel, but actually it seems to be press and release compose, then press and release the accent, and finally press and release the vowel. You should only need to press the accent character once.

The third level chooser should also help - for instance I have the Win key set to third-level choose the euro sign on the 4 key, but it can select other decorations or other characters.

---

### Post by bobince on 2009-09-11
> **StuartN said:**
> I thought I had to press compose + the accent, and then the vowel, but actually it seems to be press and release compose, then press and release the accent, and finally press and release the vowel. You should only need to press the accent character once.

Heh. Yep. You can press the two keys (letter and accent) in any order, and there are other combinations. eg. compose-a-e=æ, m-u=µ. There are some longer combinations, too.

> The third level chooser should also help - for instance I have the Win key set to third-level choose the euro sign on the 4 key, but it can select other decorations or other characters.

Indeed. I use a custom layout to reassign 3rdlevel+punctuation to get “smart quotes” «and stuff» like that&#8201;—&#8201;rather than the kind-of-sucky dead-key accents.

---

### Post by ppb7 on 2009-09-12
everything works now satisfactorily for me. I changed keyboard layouts to what bobince advised me to use
> **bobince said:**
> Use the standard UK layout without dead keys
and followed what cholericfun said about which layout options to choose
> **cholericfun said:**
> Keyboard Layout options:

all off except:

Layout swiching: right Win keymenu key for me (for optional switch)

> Third Level Chooser: Alt_Grwin key for me

> the LED option

Thanks again to everybody for your suggestions:P:P

---

### Post by ppb7 on 2009-09-14
> **StuartN said:**
> > And don't forget that I still need to press twice the key that gives an apostrophe or a double quote.I thought I had to press compose + the accent, and then the vowel, but actually it seems to be press and release compose, then press and release the accent, and finally press and release the vowel. You should only need to press the accent character once.Sorry, I meant that i had to press the key twice in order to get an apostrophe on its own (or double quotes). But this also seems to have been resolved so thanks again to everybody who contributed and consider this thread closed.

---

