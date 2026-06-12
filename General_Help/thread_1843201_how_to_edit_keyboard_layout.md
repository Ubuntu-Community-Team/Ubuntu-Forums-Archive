---
title: "how to edit keyboard layout"
date: 2011-09-13
forum: General Help
---

### Post by mr.akik on 2011-09-13
I have already learned about how to change a keyboard layout modifying the xkb symbols.I edited the file located at /usr/share/X11/xkb/symbols to make my personal layout.
But when I use a layout with scim , that method does not work.Can you please tell me which file I should
edit in this case?

---

### Post by danpav2881 on 2011-12-13
I have a trouble like this.

I want to create a new custom layout because I want to use the Cirillic alphabet on an Italian keyboard changing less keys I can.

I made my file in /usr/share/X11/xkb/symbols directory and I changed evdev.xml and evdev.lst files in /usr/share/X11/xkb/rules.
Opening preferences keyboard setting window I can find my new layout but when I select it an error is notified to me:

> Errore nell'attivare la configurazione XKB.
Le cause di ciò potrebbero essere diverse.

Per segnalare questa situazione come bug, includere i risultati dei comandi:
 • xprop -root | grep XKB
 • gsettings get org.gnome.libgnomekbd.keyboard model
 • gsettings get org.gnome.libgnomekbd.keyboard layouts
 • gsettings get org.gnome.libgnomekbd.keyboard optionsExecuting the commands I obtain:
> 
xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "evdev", "pc105", "it", "", ""
_XKB_RULES_NAMES(STRING) = "evdev", "pc105", "it,ru", ",", "grp:shifts_toggle"

gsettings get org.gnome.libgnomekbd.keyboard model
''

gsettings get org.gnome.libgnomekbd.keyboard layouts
['it', 'ru', ' ru_it ']

gsettings get org.gnome.libgnomekbd.keyboard options
['grp\tgrp:shifts_toggle']

My layout file is this:
> partial alphanumeric_keys
xkb_symbols "ru_it" {
    
    include "latin(type4)"

    name[Group1]= “Russian (on Italian keyboard)”;
    
    //key.type[group1]="FOUR_LEVEL";
    
    key <AB01> { [ Cyrillic_ya, Cyrillic_YA, z, Z ] }; // &#1103; &#1071; z Z
    key <AB02> { [ Cyrillic_che, Cyrillic_CHE, x, X ] }; // &#1095; &#1063; x X
    key <AB03> { [ Cyrillic_es, Cyrillic_ES, c, C ] }; // &#1089; &#1057; c C
    key <AB04> { [ Cyrillic_em, Cyrillic_EM, v, V ] }; // &#1084; &#1052; v V
    key <AB05> { [ Cyrillic_i, Cyrillic_I, b, B ] }; // &#1080; &#1048; b B
    key <AB06> { [ Cyrillic_te, Cyrillic_TE, n, N ] }; // &#1090; &#1058; n N
    key <AB07> { [ Cyrillic_softsign, Cyrillic_SOFTSIGN, m, M ] }; // &#1100; &#1068; m M
    key <AB08> { [ Cyrillic_be, Cyrillic_BE, comma, semicolon ] }; // &#1073; &#1041; , ;
    key <AB09> { [ Cyrillic_yu, Cyrillic_YU, period, colon ] }; // &#1102; &#1070; . :
    key <AB10> { [ minus, underscore, dead_doubleacute, dead_doubleacute ] }; // - _
    key <AC01> { [ Cyrillic_ef, Cyrillic_EF, a, A ] }; // &#1092; &#1060; a A
    key <AC02> { [ Cyrillic_yeru, Cyrillic_YERU, s, S ] }; // &#1099; &#1067; s S
    key <AC03> { [ Cyrillic_ve, Cyrillic_VE, d, D ] }; // &#1074; &#1042; d D
    key <AC04> { [ Cyrillic_a, Cyrillic_A, f, F ] }; // &#1072; &#1040; f F
    key <AC05> { [ Cyrillic_pe, Cyrillic_PE, g, G ] }; // &#1087; &#1055; g G
    key <AC06> { [ Cyrillic_er, Cyrillic_ER, h, H ] }; // &#1088; &#1056; h H
    key <AC07> { [ Cyrillic_o, Cyrillic_O, j, J ] }; // &#1086; &#1054; j J
    key <AC08> { [ Cyrillic_el, Cyrillic_EL, k, K ] }; // &#1083; &#1051; k K
    key <AC09> { [ Cyrillic_de, Cyrillic_DE, l, L ] }; // &#1076; &#1044; l L
    key <AC10> { [ Cyrillic_zhe, Cyrillic_ZHE, at, EuroSign ] }; // &#1078; &#1046; @ €
    key <AC11> { [ Cyrillic_e, Cyrillic_E, numbersign, degree ] }; // &#1101; &#1069; # °
    key <AD01> { [ Cyrillic_shorti, Cyrillic_SHORTI, q, Q ] }; // &#1081; &#1049; q Q
    key <AD02> { [ Cyrillic_tse, Cyrillic_TSE, w, W ] }; // &#1094; &#1062; w W
    key <AD03> { [ Cyrillic_u, Cyrillic_U, e, E ] }; // &#1091; &#1059; e E
    key <AD04> { [ Cyrillic_ka, Cyrillic_KA, r, R ] }; // &#1082; &#1050; r R
    key <AD05> { [ Cyrillic_ie, Cyrillic_IE, t, T ] }; // &#1077; &#1045; t T
    key <AD06> { [ Cyrillic_en, Cyrillic_EN, y, Y ] }; // &#1085; &#1053; y Y
    key <AD07> { [ Cyrillic_ghe, Cyrillic_GHE, u, U ] }; // &#1075; &#1043; u U
    key <AD08> { [ Cyrillic_sha, Cyrillic_SHA, i, I ] }; // &#1096; &#1064; i I
    key <AD09> { [ Cyrillic_shcha, Cyrillic_SHCHA, o, O ] }; // &#1097; &#1065; o O
    key <AD10> { [ Cyrillic_ze, Cyrillic_ZE, p, P ] }; // &#1079; &#1047; p P
    key <AD11> { [ Cyrillic_ha, Cyrillic_HA, bracketleft, bracketright ] }; // &#1093; &#1061; [ ]
    key <AD12> { [ Cyrillic_hardsign, Cyrillic_HARDSIGN, plus, asterisk ] }; // &#1098; &#1066; + *
    key <AE01> { [ 1, exclam, dead_doubleacute, dead_doubleacute ] }; // 1 !
    key <AE02> { [ 2, quotedbl, dead_doubleacute, dead_doubleacute ] }; // 2 quotedbl
    key <AE03> { [ 3, sterling, dead_doubleacute, dead_doubleacute ] }; // 3 £
    key <AE04> { [ 4, dollar, dead_doubleacute, dead_doubleacute ] }; // 4 $
    key <AE05> { [ 5, percent, dead_doubleacute, dead_doubleacute ] }; // 5 %
    key <AE06> { [ 6, ampersand, dead_doubleacute, dead_doubleacute ] }; // 6 &
    key <AE07> { [ 7, slash, dead_doubleacute, dead_doubleacute ] }; // 7 /
    key <AE08> { [ 8, parenleft, dead_doubleacute, dead_doubleacute ] }; // 8 (
    key <AE09> { [ 9, parenright, dead_doubleacute, dead_doubleacute ] }; // 9 )
    key <AE10> { [ 0, equal, dead_doubleacute, dead_doubleacute ] }; // 0 =
    key <AE11> { [ apostrophe, question, dead_doubleacute, dead_doubleacute ] }; // ' ?
    key <AE12> { [ igrave, asciicircum, dead_doubleacute, dead_doubleacute ] }; // ì ^
    key <BKSL> { [ Cyrillic_io, Cyrillic_IO, braceleft, braceright ] }; // &#1105; &#1025; { }
    key <LSGT> { [ less, greater, dead_doubleacute, dead_doubleacute ] }; // < >
    key <TLDE> { [ backslash, bar, dead_doubleacute, dead_doubleacute ] }; // \ |

    include "level3(ralt_switch)"
    
};Lines from evdev.xml file are these:

> 
<layout>
      <configItem>
        <name> ru_it </name>
        <shortDescription> ruit </shortDescription>
        <description> "Russian (on Italian keyboard)" </description>
        <languagelist>
          <iso639Id> rus </iso639Id>
        </languagelist>
      </configItem>
    </layout>
Is there some one who can help me to understand how I can solve this thing? [-o<

---

