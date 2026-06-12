---
title: "Custom Keyboard Map Probelm\Bug"
date: 2010-11-16
forum: General Help
---

### Post by Ari_Lari on 2010-11-16
Hey guys, I'm a new Ubuntu (version 10.10) user from Albania. Switched from W7 and I'm loving it so far. I only had one problem: creating a custom keyboard map for the Albanian language as the ones that usually come with the OS I don't like (they contain useless characters and everything is misplaced).

Following advice from a previous forum  this is what I did:
  sudo gedit /usr/share/X11/xkb/symbols/al (this is the default albanian language)(I backed it up just in case)

the file looked like this: (sorry if it's long)

> // $XKeyboardConfig$

// based on
// albanian keyboard layout
// done by Pablo Saratxaga <pablo@mandrakesoft.com>
//
// $XFree86: xc/programs/xkbcomp/symbols/al,v 1.2 2002/11/22 04:03:28 dawes Exp $

partial default alphanumeric_keys
xkb_symbols "basic" {
    include "latin(type3)"
    name[Group1]="Albania";

    key <AE01>	{ [         1,     exclam,   asciitilde,   dead_tilde ]	};
    key <AE02>	{ [         2,   quotedbl,   dead_caron,    oneeighth ]	};
    key <AE03>	{ [         3, numbersign, dead_circumflex,  sterling ]	};
    key <AE04>	{ [         4,     dollar,   dead_breve,       dollar ]	};
    key <AE05>	{ [         5,    percent, dead_abovering, threeeighths] };
    key <AE06>	{ [         6, asciicircum,  dead_ogonek, fiveeighths ]	};
    key <AE07>	{ [         7,  ampersand,        grave,   dead_grave ]	};
    key <AE08>	{ [         8,   asterisk, dead_abovedot,   trademark ]	};
    key <AE09>	{ [         9,  parenleft,   dead_acute,    plusminus ]	};
    key <AE10>	{ [         0, parenright, dead_doubleacute,   degree ]	};
    key <AE11>	{ [     minus, underscore, dead_diaeresis, questiondown] };

    key <AD03>	{ [         e,          E,     EuroSign,     EuroSign ]	};
    key <AD11>	{ [  ccedilla,   Ccedilla,     division, dead_abovering ] };
    key <AD12>	{ [        at, apostrophe,     multiply,  dead_macron ]	};

    key <AC02>	{ [         s,          S,      dstroke,      section ]	};
    key <AC03>	{ [         d,          D,      Dstroke,          ETH ]	};
    key <AC10>	{ [ediaeresis, Ediaeresis,   dollar, dead_doubleacute ]	};
    key <AC11>	{ [bracketleft,  braceleft,      ssharp,   dead_caron ]	};
    key <TLDE>	{ [ backslash,        bar,      notsign,      notsign ]	};

    key <BKSL>	{ [bracketright, braceright,   currency,   dead_breve ]	};
    key <AB08>	{ [     comma,  semicolon,         less,     multiply ]	};
    key <AB09>	{ [    period,      colon,      greater,     division ]	};
    key <AB10>	{ [     slash,   question, dead_belowdot, dead_abovedot ] };

    include "level3(ralt_switch)"
};

So this was based on the latin(type 3) keyboard. I wanted to change it to use the USA layout so these are the changes I did and how the file looked afterwards:


> //Albanian Layout
//For Ubuntu
partial default alphanumeric_keys
xkb_symbols "basic" {

    include "USA"
    name[Group1]="Albania";
 
    key <AD11> {	[ ccedilla,      Ccedilla,     braceright	]	};
    key <AD12> {	[ bracketright,  bracketleft,  braceleft	]	};
    key <AB10> {	[ ediaeresis,	 question,     Ediaeresis	]	};
    key <BKSL> {	[ slash,         backslash,    bar	        ]	};
    include "level3(ralt_switch)"
};

To work it required a restart upon restart the following error message came up:

> Error activating XKB configuration.It can happen under various circumstances: • a bug in libxklavier library • a bug in X server (xkbcomp, xmodmap utilities) • X server with incompatible libxkbfile implementationX server version data:The X.Org Foundation10900000If you report this situation as a bug, please include: • The result of xprop -root | grep XKB • The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

I have tried reverting back to the original and it worked fine, but even with smaller changes to the file the error kept popping up. Please someone tell me what I am doing wrong?!?!

Thanks a lot for your help :)

---

### Post by Andy Meier on 2011-01-03
Ubuntu 10.10 
I use a local keyboard with us and Thai layout.
The us layout is ok for me, but I like to have some
additional german characters like "äöü ÄÖÜ"
This can easy be implemented with xmodmap, but if 
you switch to the second layout, you will observe 
some strange results.

After plenty of  googling, I found an IMHO easy and 
perfect solution: create and use your custom keyboard!

1) /usr/share/X11/xkb/symbols/
   choose your nearest preference, in my case "us"
   and save it with a new name: "us-de" 

2) delete anything, which you don't need, and change, 
   what ever you like. My file for "us-de":
-----------
default
xkb_symbols "basic" {

    name[Group1]= "ASCII with german";

    // Alphanumeric section
    key <TLDE> {    [     grave,    asciitilde    ]    };
    key <AE01> {    [      1,    exclam         ]    };
    key <AE02> {    [ 2, at, twosuperior        ]    };
    key <AE03> {    [ 3, numbersign, threesuperior    ]    };
    key <AE04> {    [ 4, dollar, onequarter        ]    };
    key <AE05> {    [ 5, percent, onehalf        ]    };
    key <AE06> {    [ 6, asciicircum, threequarters    ]    };
    key <AE07> {    [      7,    ampersand    ]    };
    key <AE08> {    [ 8, asterisk, oneeighth    ]    };
    key <AE09> {    [      9,    parenleft    ]    };
    key <AE10> {    [ 0, parenright, degree            ]    };
    key <AE11> {    [     minus,    underscore    ]    };
    key <AE12> {    [     equal,    plus        ]    };

    key <AD01> {    [      q,    Q         ]    };
    key <AD02> {    [      w,    W        ]    };
    key <AD03> {    [ e, E, EuroSign, cent        ]    };
    key <AD04> {    [      r,    R        ]    };
    key <AD05> {    [      t,    T        ]    };
    key <AD06> {    [      y,    Y        ]    };
    key <AD07> {    [ u, U, udiaeresis, Udiaeresis    ]    };
    key <AD08> {    [      i,    I        ]    };
    key <AD09> {    [ o, O, odiaeresis, Odiaeresis    ]    };
    key <AD10> {    [      p,    P        ]    };
    key <AD11> {    [ bracketleft,    braceleft    ]    };
    key <AD12> {    [ bracketright,    braceright    ]    };

    key <AC01> {    [ a, A, adiaeresis, Adiaeresis    ]    };
    key <AC02> {    [      s,    S        ]    };
    key <AC03> {    [      d,    D        ]    };
    key <AC04> {    [      f,    F        ]    };
    key <AC05> {    [      g,    G        ]    };
    key <AC06> {    [      h,    H        ]    };
    key <AC07> {    [      j,    J        ]    };
    key <AC08> {    [      k,    K        ]    };
    key <AC09> {    [      l,    L        ]    };
    key <AC10> {    [ semicolon,    colon        ]    };
    key <AC11> {    [ apostrophe,    quotedbl    ]    };

    key <AB01> {    [      z,    Z         ]    };
    key <AB02> {    [      x,    X        ]    };
    key <AB03> {    [      c,    C        ]    };
    key <AB04> {    [      v,    V        ]    };
    key <AB05> {    [      b,    B        ]    };
    key <AB06> {    [      n,    N        ]    };
    key <AB07> {    [ m, M, mu              ]    };
    key <AB08> {    [     comma,    less        ]    };
    key <AB09> {    [    period,    greater        ]    };
    key <AB10> {    [     slash,    question    ]    };

    key <BKSL> {    [ backslash,         bar    ]    };
    key <CAPS> {        [ VoidSymbol            ]       };

    // End alphanumeric section
    include "level3(ralt_switch)"
};
-----------

3) /usr/share/X11/xkb/rules/evdev.xml
   Modify "evdev.xml" so your custom keyboard will be recognised:
   search for "</layoutList>" and 
   add the following just previous to "</layoutList>"  
-----------
    <layout>
      <configItem>
        <name>us-de</name>                                     <!-- 1) -->
        <shortDescription>US-DE</shortDescription>             <!-- 2) -->
        <description>ASCII with german</description>           <!-- 3) -->
        <languageList><iso639Id>eng</iso639Id></languageList>  <!-- 4) -->
      </configItem>
    </layout>
-----------
<!-- 1) --> "us-de"  is the filename of the new keyboard layout in X11/xkb/symbols
<!-- 2) --> "US-DE"  this will appear eg. in the indicator applet
<!-- 3) --> "ASCII with german" must coincide with the text at the begin of your file:
            name[Group1]= "ASCII with german";
            This text will also appear as comment under "Layouts"
<!-- 4) --> if you choose "eng" your layout will be shown in 
            System->Preferences->Keyboard->tab Layouts->Add->By Language->English
            under "Variants"

4) log out and log in again, and check 
   System->Preferences->Keyboard->tab Layouts->Add->By Language->English
   if you can find your custom layout, happy! You are ready to go!
   Select your first and second layou here. Add a keyboard switcher applet
   here under "options" you can also disable the CapsLock key.

5) the default keyboard will annoy you and sometime reappear... 
   If you like to get rid of this, edit
   /var/cache/gdm/$USER/dmrc
   and place anything existing as your new default: "Layout=us-de"
   then reboot..

I post this, as it is easy do do, but difficult to find out, and perhaps
this hint can make you happy too...

---

