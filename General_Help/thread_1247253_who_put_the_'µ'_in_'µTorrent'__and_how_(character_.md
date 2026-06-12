---
title: "who put the 'µ' in 'µTorrent'?  and how? (character code question)"
date: 2009-08-22
forum: General Help
---

### Post by greylander on 2009-08-22
Hi this is not a bug or problem I need to fix... but I am very curious about the µ character, where it comes from, and how to enter it manually.  Before you give a quick answer about fonts -- this is *not* a font question

I encountered this first in the code snippets here:  [http://blog.shadypixel.com/fixing-utorrent-file-associations-in-linux/](http://blog.shadypixel.com/fixing-utorrent-file-associations-in-linux/)

Apparently, at the very least gnome file-browser, terminal, gedit, and the linux filesystem all handle this µ character just fine.

However, it is not just an alternative font, as this is showing up in what is otherwise plain text, with no font-chaning codes.

If you look at the text (just cut & paste this post) with a hex editor, you will find a two byte code corresponding to µ: C2 B5 (hex).

But if you check an extended ascii table (such as here: [http://www.cdrummond.qc.ca/cegep/informat/Professeurs/Alain/files/ascii.htm](http://www.cdrummond.qc.ca/cegep/informat/Professeurs/Alain/files/ascii.htm)), neither C2 nor B5 correspond to greek µ.  And besides ascii and extended ascii involve single byte codes, not two byte codes.  Oddly enough, extended ascii does have codes for greek letters, but uses the single byte E6 for lowercase greek micro, but apparently that is not what is being used in this situation.

So my questions are:

1)  What character coding system is being used here -- it is appears to be fairly standard.

2)  Is there a straightforward (or not so straightforward) way to enter these characters from the keyboard in ordinary linux/ubuntu text input (terminal windows, gedit, etc.).  I have been entering the µ character here with cut/paste from the first link above).  Is there some combination of cntrl/alt/shift+other_key which gets the higher, 80..FF byte codes?

Sharing any explanatory insights, or links to same would be very welcome.

---

### Post by gldearman on 2009-08-22
The character is the micro sign.  The reason you won't find it in ASCII encoding tables is that ASCII does not support it.  Most character encoding these days is done with [Unicode]("http://en.wikipedia.org/wiki/Unicode"), not ASCII.

The Unicode designation for that character is U+00B5. You will note that it is similar to the lower case Greek letter *mu*, at U+03BC, but Unicode considers them to be distinct characters.

Yeah, there is a way to type Unicode characters in Ubuntu with the keyboard, but darned if I can remember it. I'm not at my own computer now, but I'll play around with it when I get home and add a new reply with the way to do it (unless someone beats me to it).

There are two other ways to enter the character, however.  

From the Ubuntu character map (found in the Applications > Accessories menu on Ubuntu, I don't know where on other desktop environments), you can select the font you want, select the character (if that font supports it), and then copy and paste.

Also, in Open Office, you can open the special characters window by selecting Insert > Special Character.

---

### Post by gldearman on 2009-08-22
OK, I figured it out.

Hold down <Ctrl>+<Shift> while typing the characters from the Unicode encoding.

So, to type

µ

like I just did, hold down <Ctrl>+<Shift> while typing u00b5.  "_u00B5_" will initially appear on the screen, but be replaced by "µ" when you release <Ctrl>+<Shift>.

µ µ µ µ µ µ!

Of course, that's not entirely "straightforward," since it involves memorizing the encoding for the character you want.  But that's how you do it.

---

### Post by greylander on 2009-08-23
Thanks for the great reply!  "unicode" is what I needed to know... google helps fill in the rest.

So C2 B5 is specifcially the UTF-8 byte coding of unicode character u00B5, the greek micro.

Now trying to enter it, and...  µ!!  voila!

I guess I haven't been paying attention to character coding for the past decade (or two?) of so... and looks like UTF-8 is the trend.  As it is backwards compatible with ascii, it was easy to think I was still living in an ascii world.  lol!

---

### Post by CatKiller on 2009-08-23
> **greylander said:**
>  Is there a straightforward (or not so straightforward) way to enter these characters from the keyboard in ordinary linux/ubuntu text input (terminal windows, gedit, etc.).

With the [Compose key]("http://en.wikipedia.org/wiki/Compose_key"). There are [Compose key combinations]("http://www.hermit.org/Linux/ComposeKeys.html") for most of the extended characters, and they're reasonably intuitive; Compose&#8594;"&#8594;a gets you ä, for example.

Compose&#8594;m&#8594;u is pretty easy. That's how you'd write a mu.

---

### Post by P4man on 2009-08-23
or get a french or belgian keyboard. We got a key for it :p
µ

---

### Post by gldearman on 2009-08-23
> **CatKiller said:**
> With the [Compose key]("http://en.wikipedia.org/wiki/Compose_key"). There are [Compose key combinations]("http://www.hermit.org/Linux/ComposeKeys.html") for most of the extended characters, and they're reasonably intuitive; Compose&#8594;"&#8594;a gets you ä, for example.

Compose&#8594;m&#8594;u is pretty easy. That's how you'd write a mu.

Is there a compose key on a standard US keyboard?  The bottom row on my keyboard is:

<Ctrl><Super (Windows symbol)><Alt><Spacebar><Alt><Super><Menu><Ctrl>

None of those seem to do it.

---

### Post by greylander on 2009-08-23
A quick google turned up this forum thread:  [http://ubuntuforums.org/showthread.php?t=222640](http://ubuntuforums.org/showthread.php?t=222640)

You can define the compose key in ubuntu in system-->preferences-->keyboard-->layouts-->layout options-->Compose Key Position

I just set mine to that otherwise useless Windows key:

µµµµµµ   weeeeeeee....!!!

Gotta love Ubuntu (& Linux in general)  feel like I actually *own* my own computer... instead of µSoft!  lol!

---

### Post by gldearman on 2009-08-23
> **greylander said:**
> A quick google turned up this forum thread:  [http://ubuntuforums.org/showthread.php?t=222640](http://ubuntuforums.org/showthread.php?t=222640)

You can define the compose key in ubuntu in system-->preferences-->keyboard-->layouts-->layout options-->Compose Key Position

I just set mine to that otherwise useless Windows key:

µµµµµµ   weeeeeeee....!!!

Gotta love Ubuntu (& Linux in general)  feel like I actually *own* my own computer... instead of µSoft!  lol!

Thanks!  That's great info.  I actually use my <"Windows"> key all the time (mostly with the Expo plugin for Compiz Fusion), but, if I'm reading that right, I can leave one as-is and map the other to the Compose key.  And that would be very useful.

If only Windows were this easy; I have to type the "µ" symbol (and other special characters) *all the time* at work (WinXP), and there is no easy way to do it.

---

### Post by CatKiller on 2009-08-23
> **gldearman said:**
>  If only Windows were this easy; I have to type the "µ" symbol (and other special characters) *all the time* at work (WinXP), and there is no easy way to do it.

Alt+0181 on the keypad ought to do it.

---

### Post by gldearman on 2009-08-23
> **CatKiller said:**
> Alt+0181 on the keypad ought to do it.

Yeah, but with all the special characters I have to remember, it's easier to open Character Map and copy & paste.  A Compose key for WinXP would be great.  I mean, <Compose>+mu?  I'd never forget that. Alt+0181?  Not exactly a mnemonic.

---

