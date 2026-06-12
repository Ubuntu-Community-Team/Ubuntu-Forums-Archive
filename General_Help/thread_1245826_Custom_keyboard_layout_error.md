---
title: "Custom keyboard layout error"
date: 2009-08-21
forum: General Help
---

### Post by Kijuna on 2009-08-21
Made a new file "Twi" in my folder usr/share/X11/xkb/symbols. Here's what its innards look like.

> // $XKeyboardConfig: xkeyboard-config/symbols/us,v 1.45 2008-05-27 21:50:35 svu Exp $

//
// $XdotOrg: xc/programs/xkbcomp/symbols/us,v 1.1.4.3 2004/03/05 13:41:33 eich Exp $
// $XFree86: xc/programs/xkbcomp/symbols/us,v 1.6 2003/10/31 14:32:05 pascal Exp $

default
partial alphanumeric_keys modifier_keys 
xkb_symbols "basic", "mac" {

    include "us"
    include "gr(bare)"
    include "latin"
    
    name[Group1]= "Twili";

    // Alphanumeric section
    key <TLDE> {    [     grave,    asciitilde    ]    };
    key <AE01> {    [      1,    exclam         ]    };
    key <AE02> {    [      2,    at        ]    };
    key <AE03> {    [      3,    numbersign    ]    };
    key <AE04> {    [      4,    dollar        ]    };
    key <AE05> {    [      5,    percent        ]    };
    key <AE06> {    [      6,    asciicircum    ]    };
    key <AE07> {    [      7,    ampersand    ]    };
    key <AE08> {    [      8,    asterisk    ]    };
    key <AE09> {    [      9,    parenleft    ]    };
    key <AE10> {    [      0,    parenright    ]    };
    key <AE11> {    [     minus,    underscore    ]    };
    key <AE12> {    [     equal,    plus        ]    };

    key <AD01> {    [    eth,    Eth         ]    };
    key <AD02> {    [      w,    W        ]    };
    key <AD03> {    [      e,    E        ]    };
    key <AD04> {    [      r,    R        ]    };
    key <AD05> {    [      t,    T        ]    };
    key <AD06> {    [      y,    Y        ]    };
    key <AD07> {    [      u,    U        ]    };
    key <AD08> {    [      i,    Iabovedot    ]    };
    key <AD09> {    [      o,    O        ]    };
    key <AD10> {    [      p,    P        ]    };
    key <AD11> {    [    period,    period      ]    };
    key <AD12> {    [  question,    questiondown    ]    };

    key <AC01> {    [      a,    A         ]    };
    key <AC02> {    [      s,    S        ]    };
    key <AC03> {    [      d,    D        ]    };
    key <AC04> {    [      f,    F        ]    };
    key <AC05> {    [      g,    G        ]    };
    key <AC06> {    [ apostraphe,    apostraphe    ]    };
    key <AC07> {    [        ae,    AE        ]    };
    key <AC08> {    [      k,    K        ]    };
    key <AC09> {    [  idotless,    +I,        ]    };
    key <AC10> {    [ bracketleft,    bracketleft    ]    };
    key <AC11> {    [ bracketright,    bracketright    ]    };

    key <AB01> {    [     ohorn,    Ohorn         ]    };
    key <AB02> {    [ Greek_phi,    Greek_PHI    ]    };
    key <AB03> {    [   ccedilla,    Ccedilla        ]    };
    key <AB04> {    [ greek_omega,    Greek_OMEGA    ]    };
    key <AB05> {    [      b,    B        ]    };
    key <AB06> {    [      n,    N        ]    };
    key <AB07> {    [      m,    M        ]    };
    key <AB08> {    [     thorn,    Thorn        ]    };
    key <AB09> {    [ exclamdown,    exclamdown    ]    };
    key <AB10> {    [    exclam,    exclam       ]    };

    key <BKSL> {    [ backslash,         bar    ]    };
    key <CAPS> {    [ Caps_Lock    ]    };
    // End alphanumeric section
};

I get an error when I try to select it in Keyboard Preferences -> layout:

> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10402000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

halp

---

### Post by Kijuna on 2009-08-21
Bump

---

### Post by aldimond on 2009-08-21
Your file has some syntax errors and misspelled keysums in it.  I tried compiling it with xkbcomp and found:

Line 3: choose either "basic" or "mac", not both.
Line 44: "apostrophe", not "apostraphe"
Line 47: Looks like an extraneous "+" and an extraneous ","
Line 54: "greek_omega" needs to be "Greek_omega"

Hopefully fixing these things will make it work... I haven't tried loading the file because I don't really want to mess with my keyboard mappings, but at least xkbcomp doesn't give any errors with these changes made.

---

### Post by Kijuna on 2009-08-21
Did all that, still getting an error.

---

### Post by Kijuna on 2009-08-21
bump

---

### Post by Kijuna on 2009-08-21
bump :\

---

### Post by aldimond on 2009-08-21
Run xkbcomp on the corrected file.  What error messages do you get?

---

### Post by Kijuna on 2009-08-21
What is xkbcomp?

---

### Post by aldimond on 2009-08-21
xkbcomp compiles X keyboard descriptions.  Open a terminal, browse to the location of your file, and run 'xkbcomp Twi Twi.xkm'.  This compiles your source file Twi into the compiled file Twi.xkm.  If there are errors remaining in the file the output from this command should help identify them.

After making corrections I got it working with the following file:

```
default                        
partial alphanumeric_keys modifier_keys
xkb_symbols "basic"  {                 

include "us"
include "gr(bare)"
include "latin"   

name[Group1]= "Twili";

// Alphanumeric section
key <TLDE> { [ grave, asciitilde ] };
key <AE01> { [ 1, exclam ] };
key <AE02> { [ 2, at ] };
key <AE03> { [ 3, numbersign ] };
key <AE04> { [ 4, dollar ] };
key <AE05> { [ 5, percent ] };
key <AE06> { [ 6, asciicircum ] };
key <AE07> { [ 7, ampersand ] };
key <AE08> { [ 8, asterisk ] };
key <AE09> { [ 9, parenleft ] };
key <AE10> { [ 0, parenright ] };
key <AE11> { [ minus, underscore ] };
key <AE12> { [ equal, plus ] };

key <AD01> { [ eth, Eth ] };
key <AD02> { [ w, W ] };
key <AD03> { [ e, E ] };
key <AD04> { [ r, R ] };
key <AD05> { [ t, T ] };
key <AD06> { [ y, Y ] };
key <AD07> { [ u, U ] };
key <AD08> { [ i, Iabovedot ] };
key <AD09> { [ o, O ] };
key <AD10> { [ p, P ] };
key <AD11> { [ period, period ] };
key <AD12> { [ question, questiondown ] };

key <AC01> { [ a, A ] };
key <AC02> { [ s, S ] };
key <AC03> { [ d, D ] };
key <AC04> { [ f, F ] };
key <AC05> { [ g, G ] };
key <AC06> { [ apostrophe, apostrophe ] };
key <AC07> { [ ae, AE ] };
key <AC08> { [ k, K ] };
key <AC09> { [ idotless, I ] };
key <AC10> { [ bracketleft, bracketleft ] };
key <AC11> { [ bracketright, bracketright ] };

key <AB01> { [ ohorn, Ohorn ] };
key <AB02> { [ Greek_phi, Greek_PHI ] };
key <AB03> { [ ccedilla, Ccedilla ] };
key <AB04> { [ Greek_omega, Greek_OMEGA ] };
key <AB05> { [ b, B ] };
key <AB06> { [ n, N ] };
key <AB07> { [ m, M ] };
key <AB08> { [ thorn, Thorn ] };
key <AB09> { [ exclamdown, exclamdown ] };
key <AB10> { [ exclam, exclam ] };

key <BKSL> { [ backslash, bar ] };
key <CAPS> { [ Caps_Lock ] };
// End alphanumeric section
};

```

---

### Post by Kijuna on 2009-08-22
Maybe it's a problem in xorg.xml. I'm not completely sure what I should be typing here.

>     <layout>
       <layout>
         <configItem>
           <name>tw</name>
           <shortDescription>twi</shortDescription>
           <description>Twili</description>
           <languageList>
              <iso639Id>eng</iso639Id>
           </languageList>
         </configItem>
         <variantList/>
       </layout>

       </layout>

       </layout>

...is the section I've got tw in.

---

### Post by DeMus on 2009-08-22
> 
key <AD01> { [ eth, Eth ] };
key <AD02> { [ w, W ] };
key <AD03> { [ e, E ] };
key <AD04> { [ r, R ] };
key <AD05> { [ t, T ] };
key <AD06> { [ y, Y ] };
key <AD07> { [ u, U ] };
key <AD08> { [ i, Iabovedot ] };
key <AD09> { [ o, O ] };
key <AD10> { [ p, P ] };
key <AD11> { [ period, period ] };
key <AD12> { [ question, questiondown ] };
In this list I miss the letter Q. I suppose Eth stands for the tab-key. So where is the q-Q?

---

### Post by Kijuna on 2009-08-22
Eth is the Icelandic character for th that looks like a curled D with a line through the top.

[http://en.wikipedia.org/wiki/Eth](http://en.wikipedia.org/wiki/Eth)

---

### Post by Kijuna on 2009-08-22
Bump.

Ing my face on the keyboard because I have been doing this for three days

gjnyuggjhgfghfytrfduhjkm uhjkbm vb

---

### Post by Kijuna on 2009-08-22
bump

---

### Post by Kijuna on 2009-08-22
up

---

