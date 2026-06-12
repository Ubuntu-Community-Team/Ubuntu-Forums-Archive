---
title: "X11 keybrd layout: difficulty getting a diacritic."
date: 2010-07-04
forum: General Help
---

### Post by ninjaaron on 2010-07-04
Hey everyone, I do a lot of work on Ancient Near East Languages (Hebrew, Aramaic, Akkadian, Hittite, Ugaritic...), and I need a lot of diacritic marks. [Following these instructions]("http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11") and using the character map, I've managed to get everything I wanted. There's just one fly left in my ointment. There is a standard for transcribing aspirated Hebrew consonants which involves putting a line below the character. This line:    &#817;

I need these characters:
&#7687;, &#7695;, &#7733;, and &#7791;.

I can make them using a combining character (U0331), but this is the rub: with all the other diacritics, I have to add them before the character, and with this set, I have to add it afterwards. This doesn't seem like a big deal, but it's a huge pain in the butt when your actually using it. I tried using combining characters with all my diacritics, but they don't work right with capital letters, so that was a no-go The combining characters also do screwy things with formating and spacing sometimes.

For all the dead-keys, there is a normal kind of formating that X11 uses. A grave("`") is "grave", and a dead grave is "dead_grave". A macron ("¯") is "macron" and a dead macron is "dead_macron"... not rocket science. Anyway, I've tried all kinds of possible names for this character with the word "dead" in front of them, and no luck. I've tried a fair number of Unicode codes, and no luck with them either. I even tried "dead_U005F" (U005F the normal symbol). Nothing seems to work (except the really annoying solution already mentioned).

By the way, this is what the layout file looks like right now... don't know if that helps... I marked the problem character in red. It's almost at the bottom.
```


// Made for working with semitic diacritics.
//

partial alphanumeric_keys
xkb_symbols "Special" {

    include "us(basic)"
    name[Group1]= "Special";
    key.type[group1]="FOUR_LEVEL";

    // Modified from the standard Macintosh Layout
    key <LSGT> { [   section,  plusminus,       section,        plusminus ] };
    key <TLDE> { [ dead_grave, asciitilde,        grave,        dead_horn ] };
    key <AE01> { [	   1,     exclam,    exclamdown,            U2044 ] };
    key <AE02> { [	   2,         at,     trademark,         EuroSign ] };
    key <AE03> { [	   3, numbersign,      sterling,            U2039 ] };
    key <AE04> { [	   4,     dollar,          cent,            U203A ] };
    key <AE05> { [	   5,    percent,      infinity,            UFB01 ] };
    key <AE06> { [         6,asciicircum,       section,            UFB02 ] };
    key <AE07> { [	   7,  ampersand,     paragraph,     doubledagger ] };
    key <AE08> { [	   8,   asterisk, enfilledcircbullet,      degree ] };
    key <AE09> { [	   9,  parenleft,   ordfeminine,   periodcentered ] };
    key <AE10> { [	   0, parenright,     masculine,singlelowquotemark] };
    key <AE11> { [     minus, underscore,        endash,           emdash ] };
    key <AE12> { [     equal,       plus,      notequal,        plusminus ] };

    key <AD01> { [	   q,          Q,            oe,               OE ] };
    key <AD02> { [	   w,          W,         U2211,doublelowquotemark] };
    key <AD03> { [	   e,          E,    dead_acute,            schwa ] };
    key <AD04> { [	   r,          R,    registered,            U2030 ] };
    key <AD05> { [	   t,          T,    dead_caron,           dagger ] };
    key <AD06> { [	   y,          Y,           yen,       onequarter ] };
    key <AD07> { [	   u,        U,  dead_diaeresis,        diaeresis ] };
    key <AD08> { [	   i,        I, dead_circumflex,            U02C6 ] };
    key <AD09> { [	   o,          O,        oslash,         Ooblique ] };
    key <AD10> { [	   p,          P,      Greek_pi,            U220F ] };
    key <AD11> { [ bracketleft,  braceleft,   U02BF, rightdoublequotemark ] };
    key <AD12> { [bracketright, braceright,   U02BE, rightsinglequotemark ] };
    key <BKSL> { [ backslash,        bar, guillemotleft,   guillemotright ] };

    key <AC01> { [	   a,          A,         aring,            Aring ] };
    key <AC02> { [	   s,          S,        ssharp,      dead_stroke ] };
    key <AC03> { [	   d,          D, partialderivative,          eth ] };
    key <AC04> { [	   f,          F,      function,        dead_hook ] };
    key <AC05> { [	   g,          G, dead_belowdot,    dead_abovedot ] };
    key <AC06> { [	   h,          H,         U1E2B,            U1E2A ] };
    key <AC07> { [	   j,          J,         U2206,          onehalf ] };
    key <AC08> { [	   k,          K,dead_abovering,            UF8FF ] };

    key <AC09> { [	   l,          L,       notsign,            THORN ] };
    key <AC10> { [ semicolon,      colon,         U2026,            thorn ] };
    key <AC11> { [apostrophe,   quotedbl,            ae,               AE ] };

    key <AB01> { [	   z,          Z,   Greek_OMEGA,     dead_cedilla ] };
    key <AB02> { [	   x,          X,         U2248,      dead_ogonek ] };
				// unclear whether "approxeq" is 2248 or 2245
    key <AB03> { [	   c,          C,      ccedilla,         Ccedilla ] };
    key <AB04> { [	   v,          V,    squareroot,            U25CA ] };
    key <AB05> { [	   b,          B,      integral,         idotless ] };
    key <AB06> { [	   n,          N,    dead_tilde,    threequarters ] };
    key <AB07> { [	   m,          M,         [COLOR="Red"]U0331,[/COLOR]               mu ] };
    key <AB08> { [     comma,       less,   dead_macron,    lessthanequal ] };
    key <AB09> { [    period,    greater,    dead_breve, greaterthanequal ] };
    key <AB10> { [     slash,   question,      division,     questiondown ] };

    include "level3(ralt_switch)"
}; 

```

---

### Post by ninjaaron on 2010-07-04
also, didn't really know where to post this. If a mod knows a better board for this question, feel free to move it there.

---

### Post by simosx on 2010-07-05
First of all, the reason why characters like &#7733; do not work like other pre-composed Unicode characters is due to the fact that at some point, the Unicode foundation, decided to limit the number of pre-composed Unicode characters.

I can see two options.

Indeed, GNOME and the GTK+ library do not have a facility yet to support 'deadkey + letter = letter + combiningcharacter'. You can currently only go up to 'letter + combiningcharacter' = 'letter + combiningcharacter'.

What you can do is disable the processing that GNOME/GTK+ do with compose sequences, and use the mechanism that the X server provides. In doing this, you sadly lose 'Cltr+Shift+u+HEXNUMBER=unicode_character'.
So for testing purposes,
1. open a terminal window
2. type 
[INDENT]gedit ~/.XCompose[/INDENT]
3. In the file add
[INDENT]<dead_belowmacron>	<t>	: "&#7791;"[/INDENT]
and save, quit.
4. In the terminal window, run
[INDENT]export GTK_IM_MODULE=xim[/INDENT]
and then
[INDENT]gedit
[/INDENT]

Now, if you press dead_belowmacron and then t, you get &#7791;.
I forgot to mention that this requires to update your layout file so that instead of U0331 you put dead_belowmacron.

If that works for you, repeat for the rest of the combinations that are missing.

If you want to make this GTK_IM_MODULE=xim thing permanent, you can add it in /etc/environment and reboot. To do so, 
[INDENT]gksudo gedit /etc/environment[/INDENT]
and add in a new line

[INDENT]GTK_IM_MODULE=xim
[/INDENT]
save, quit and restart your computer

Your other option would be to create an IBus keyboard layout. However I see that you have already done the job for XKB, so IBus might be too big of an investment.

Good luck!:popcorn:

---

