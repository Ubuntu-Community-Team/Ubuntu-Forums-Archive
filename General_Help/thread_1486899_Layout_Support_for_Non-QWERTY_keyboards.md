---
title: "Layout Support for Non-QWERTY keyboards"
date: 2010-05-18
forum: General Help
---

### Post by selevercin on 2010-05-18
Hello,

I physically have a Dvorak keyboard (i.e. not using the layout switch). I also occasionally type in Russian, using the software layout switch available in Ubuntu (I'm using Hardy Heron).

I am unable to switch layouts (correctly) unless I am using a QWERTY keyboard. Is there an easy way to tell Ubuntu that I am using a standard Dvorak keyboard and to adjust the layout maps appropriately? If this is unavailable, how can I make my own Russian keyboard layout to correct for this?

Thank you!

---

### Post by selevercin on 2010-05-18
For those who are interested, I created a Russian keyboard that is compatible with the Dvorak keyboard. I took the liberty of replacing '+' and '-' with '[' and ']' to be more Dvorak like, but this can easily be changed.

The same approach could be used for any other keymap. Follow the instructions found [http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html]("http://hektor.umcs.lublin.pl/%7Emikosmul/computing/articles/custom-keyboard-layouts-xkb.html") and [http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11]("http://people.uleth.ca/%7Edaniel.odonnell/Blog/custom-keyboard-in-linuxx11"). The same row "fixes" should be exactly applicable for a standard Dvorak keyboard.

Add the following to: /etc/X11/xkb/symbols/ru (supposedly this moved after Ubuntu 8.04). 

```
// Dvorak compatible layout
// For those using a physical Dvorak keyboard
// Nic Reveles <Nic.Reveles@gatech.edu>
// Last Changes 2010/05/18 by Nic Reveles

partial default alphanumeric_keys
xkb_symbols "dv" {

    name[Group1]= "Russia - Dvorak";

    key <AE01> {        [               1,          exclam      ]       };
    key <AE02> {        [               2,        quotedbl      ]       };
    key <AE03> {        [               3,      numbersign      ]       };
    key <AE04> {        [               4,        asterisk      ]       };
    key <AE05> {        [               5,           colon      ]       };
    key <AE06> {        [               6,           comma      ]       };
    key <AE07> {        [               7,          period      ]       };
    key <AE08> {        [               8,       semicolon      ]       };
    key <AE09> {        [               9,       parenleft      ]       };
    key <AE10> {        [               0,      parenright      ]       };
    key <AE12> {        [           equal,            plus      ]       };
    key <BKSL> {        [       backslash,             bar      ]       };
    key <LSGT> {        [           slash,             bar      ]       };
    key <TLDE> {        [     Cyrillic_io,     Cyrillic_IO      ]       };

    // top "E" row fix
    key <AE04> {        [               4,       semicolon      ]       };
    key <AE05> {        [               5,         percent      ]       };
    key <AE06> {        [               6,           colon      ]       };
    key <AE07> {        [               7,        question      ]       };
    key <AE08> {        [               8,        asterisk      ]       };
    key <AD11> {        [     bracketleft,       braceleft      ]       };
    key <AD12> {        [    bracketright,      braceright      ]       };

    // "D" row fix
    key <AC11> {        [ Cyrillic_shorti, Cyrillic_SHORTI      ]       };
    key <AB08> {        [    Cyrillic_tse,    Cyrillic_TSE      ]       };
    key <AB09> {        [      Cyrillic_u,      Cyrillic_U      ]       };
    key <AD10> {        [     Cyrillic_ka,     Cyrillic_KA      ]       };
    key <AD06> {        [     Cyrillic_ie,     Cyrillic_IE      ]       };
    key <AC04> {        [     Cyrillic_en,     Cyrillic_EN      ]       };
    key <AC05> {        [    Cyrillic_ghe,    Cyrillic_GHE      ]       };
    key <AB03> {        [    Cyrillic_sha,    Cyrillic_SHA      ]       };
    key <AD04> {        [  Cyrillic_shcha,  Cyrillic_SHCHA      ]       };
    key <AC09> {        [     Cyrillic_ze,     Cyrillic_ZE      ]       };
    key <AB10> {        [     Cyrillic_ha,     Cyrillic_HA      ]       };
    key <AE12> {        [Cyrillic_hardsign,Cyrillic_HARDSIGN    ]       };

    // "C" row fix
    key <AC01> {        [     Cyrillic_ef,     Cyrillic_EF      ]       };
    key <AD09> {        [   Cyrillic_yeru,   Cyrillic_YERU      ]       };
    key <AD03> {        [     Cyrillic_ve,     Cyrillic_VE      ]       };
    key <AD07> {        [      Cyrillic_a,      Cyrillic_A      ]       };
    key <AD08> {        [     Cyrillic_pe,     Cyrillic_PE      ]       };
    key <AC03> {        [     Cyrillic_er,     Cyrillic_ER      ]       };
    key <AC06> {        [      Cyrillic_o,      Cyrillic_O      ]       };
    key <AD05> {        [     Cyrillic_el,     Cyrillic_EL      ]       };
    key <AB06> {        [     Cyrillic_de,     Cyrillic_DE      ]       };
    key <AC02> {        [    Cyrillic_zhe,    Cyrillic_ZHE      ]       };
    key <AE11> {        [      Cyrillic_e,      Cyrillic_E      ]       };

    // "B" row fix
    key <AC10> {        [     Cyrillic_ya,     Cyrillic_YA      ]       };
    key <AD01> {        [    Cyrillic_che,    Cyrillic_CHE      ]       };
    key <AC07> {        [     Cyrillic_es,     Cyrillic_ES      ]       };
    key <AC08> {        [     Cyrillic_em,     Cyrillic_EM      ]       };
    key <AB02> {        [      Cyrillic_i,      Cyrillic_I      ]       };
    key <AB05> {        [     Cyrillic_te,     Cyrillic_TE      ]       };
    key <AB07> {        [Cyrillic_softsign,Cyrillic_SOFTSIGN    ]       };
    key <AD02> {        [     Cyrillic_be,     Cyrillic_BE      ]       };
    key <AB04> {        [     Cyrillic_yu,     Cyrillic_YU      ]       };
    key <AB01> {        [          period,           comma      ]       };

    key.type[group1]="TWO_LEVEL";

    include "kpdl(comma)"
}; 
```Finally, edit: /etc/X11/xkb/rules/xorg.xml
```
 <layout>
      <configItem>
        <name>ru</name>
        <shortDescription>Rus</shortDescription>
        <description>Russia</description>
      </configItem>
      <variantList>

      {... all the original variants are found here ... }

      <variant>
          <configItem>
          <name>dv</name>
          <description>Dvorak</description>
          </configItem>
        </variant>
      </variantList>
    </layout>

```

Now there should be a "Dvorak" listing under the Russian keyboards that is compatible with a Dvorak keyboard. This seems to work rather well, but I definitely believe a better fix is possible (for all Dvorak keyboards).

Hopefully this hack is useful to others in the meantime.

---

