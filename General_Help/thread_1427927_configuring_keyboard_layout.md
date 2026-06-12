---
title: "configuring keyboard layout"
date: 2010-03-12
forum: General Help
---

### Post by riomare1 on 2010-03-12
hi
this is my current layout

```
// $XConsortium: macintosh /main/10 1996/01/29 19:54:54 kaleb $
// based on $XFree86: xc/programs/xkbcomp/symbols/macintosh/us,v 1.8 2003/08/04 10:32:31 eich Exp $
// $XFree86: xc/programs/xkbcomp/symbols/mylayout,v 1.8 2003/08/04 10:32:31 eich Exp $

// symbols definition for a Macintosh "Extended" keyboard
// edited for umlauts, switched keys, and modifiers

partial default alphanumeric_keys
xkb_symbols "extended" {

    include "si" // this is what we will modify. choose the right one for your language.
    //"macintosh_vndr/us" 
    name[Group1]= "mylayout";

    // Alphanumeric section

            
    key <AE10> {        [         0,    parenright,     degree  ]       }; // add a ° to the zero

    key <AD03> {        [         e,    E, EuroSign               ]       }; // add a € to the e
    key <AD07> {        [         u,    U,      udiaeresis,     Udiaeresis              ]       }; // add üÜ
    key <AD09> {        [         o,    O,      odiaeresis,     Odiaeresis              ]       }; // add öÖ

    key <AC01> {        [         a,    A,      adiaeresis,     Adiaeresis              ]       }; // add äÄ
    key <AC02> {        [         s,    S,      ssharp, ssharp          ]       }; // add ß
    // End alphanumeric section

    // Begin "Modifier" section
    key <RWIN> {        [  Multi_key    ]       }; // this assigns the compose key to the key right of the space key
    // replace KP_ENTER
    replace key <KPEN> { [ ISO_Level3_Shift ] }; // this and the next line make the enter key next to the compose key 
    modifier_map Mod5  { ISO_Level3_Shift }; // switch to the above defined ä,€,...
    // End "Modifier" section
};
```i would like to add these two bindings
    key <AD11>    { [        š, Š, bracketleft,  braceleft ]    };
    key <AD12>    { [        &#273;, &#272;, bracketright,  braceright ]    };
i tried but i get an error
if i add bracket bindings like this
key <AD11>    { [       a, A, bracketleft,  braceleft ]    };
it works

so there must be a problem with š and &#273;

---

