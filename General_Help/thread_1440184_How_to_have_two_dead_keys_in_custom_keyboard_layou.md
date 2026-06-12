---
title: "How to have two dead keys in custom keyboard layout"
date: 2010-03-27
forum: General Help
---

### Post by mfearby on 2010-03-27
I want to create a custom keyboard layout with two dead keys for entering Latin characters with accents and macrons. I can do this already with third-level compose keys, but they aren't fun if you're typing a lot. Having to press AltGr+Minus then a vowel is annoying compared to having my leftbracket/leftbrace key assigned as a dead key to turn the next letter into one with a macron.

I tried adding the following to my ~/.XCompose and logging off and on again, but leftbracket hasn't been thusly turned into a dead key, alas:

```
<bracketleft> <a>                	: "&#257;"   U0101 # LATIN SMALL LETTER A WITH MACRON
```

I also want to turn the tilde/backtick key into a dead key for accenting the following vowel. this is much easier, IMHO, than AltGr + Apostrophe + Vowel (which means if I want an apostrophe, I have to press and hold AltGr+Apostrophe together, rather than in sequence = major pain!).

Any ideas how I can define two dead keys with matching sequences?

---

### Post by mfearby on 2010-03-30
I found a thread that explains how to do what I want: [http://swiss.ubuntuforums.org/showthread.php?t=1387812]("http://swiss.ubuntuforums.org/showthread.php?t=1387812"). I basically created my own "mf" keyboard, with relevant changes as follows:

```
// $XKeyboardConfig$

//
// $XdotOrg: xc/programs/xkbcomp/symbols/us,v 1.1.4.3 2004/03/05 13:41:33 eich Exp $
// $XFree86: xc/programs/xkbcomp/symbols/us,v 1.6 2003/10/31 14:32:05 pascal Exp $

default
partial alphanumeric_keys modifier_keys 
xkb_symbols "basic" {

    name[Group1]= "mf";

    // Alphanumeric section
    key <TLDE> {	[dead_acute,	asciitilde	]	};
    key <AD11> {	[  dead_macron,	braceleft	]	};
    // End alphanumeric section
};
```

Unlike dead keys in windows, I do not get a backtick or a left-square-bracket by pressing the dead key a second time, but I haven't needed those characters when typing up Latin words with pronunciation markings (like aúdi&#333;) so I'll live for now :-) 

This is SO much more convenient than the digital gymnastics required of the third-level compose key (AltGr with another key).

---

