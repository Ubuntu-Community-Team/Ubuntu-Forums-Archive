---
title: "messed up LINUX"
date: 2012-02-14
forum: General Help
---

### Post by fra11 on 2012-02-14
Hi all!
I think I've made a mess on my LINUX computer. It was freezed so I tried to restart it, however then the mouse wasn't working so I tried some strange combination of keys like ctrl alt f4, but not sure about it, and it all went black like if I just had a terminal interface. If I try startx it goes to a kde interface but then I'm not able to shut it down and if I log off or try to rebooth it simply goes back to the all black interface that looks like a terminal. 
How can I go back to my GNOME interface?
Any help?

:confused:

---

### Post by winh8r on 2012-02-14
Press ctrl + alt + T

type in 

sudo shutdown -r now

enter you password and it will reboot

then we can see where the problem is

---

### Post by fra11 on 2012-02-14
it says I'm not allowed to run sudo on this computer and that will be reported. 
looking at LINUX shortcuts, I've discovered that if I type fgconsole I get 8 opened terminals and with [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]<Ctrl><Alt><Fn>           (n=1..6) I get to different terminals that I must have opened somehow...typing startx I end up in the KDE interface from which I cannot do the log out...
any help?
:confused:
[/SIZE][/FONT]

---

### Post by winh8r on 2012-02-14
If you can get to a terminal again type


```
killall gnome-panel
```

---

### Post by fra11 on 2012-02-14
it says, gnome-panel, no process found.
and now, fgconsole is 2. 
ideas?:confused:

---

### Post by winh8r on 2012-02-14
Which version of Ubuntu are you running?

---

### Post by fra11 on 2012-02-14
good question... I don't really know now, also because the computer which is completely dead is the one of the office which is turned of. I'll check it tomorrow and I'll tell you.
Thanks

---

### Post by fra11 on 2012-02-15
ok I'm using GNOME 2.30.2 kernel 2.6.32-5-amd64. Is that the information you were looking for? Anyway, the problem solved itself during the night while being shut down brutally. However I have another issue with my linux pc. it is speaking in german even though the language setting is in English. Any tips on that?

---

### Post by winh8r on 2012-02-15
Hi,

What I was looking for was the release of Ubuntu like Oneiric Ocelot 11.10 or whatever version you have , but you seem to be up and running again anyway.

You can remove unwanted locales/languages by opening a terminal and type

```
sudo apt-get install localepurge
```

then run it

```
 localepurge
```


and select the locales/languages which you wish to KEEP on your system, all other locales/languages will be purged from the system.

You will need to use the arrow keys on your keyboard to navigate in the menu and use the space bar to select/deselect locales/languages.


In your case , you were having issues with issuing the sudo command so make sure that you have been here:

[http://www.psychocats.net/ubuntu/fixsudo]("http://www.psychocats.net/ubuntu/fixsudo")

and resolve that issue before attempting to run a sudo command.

Hope this helps you.

---

### Post by fra11 on 2012-02-15
Thanks.
I've looked at the link you sent me, but considering that it is all in German, I'm having issues even with the basic things. Foe example I've tried to look at my sudoers.d file and I cannot either see the users or the other options. Anyway I guess that my problem with sudo is that I don't have permission to the admin group. However, being  this the office pc and me absolutely incapable with this stuff, I'm really afraid of messing it all up again if I try to change the code. 
Any other easier solution?

---

### Post by winh8r on 2012-02-15
open a terminal and type in


```
locale -a -v
```

this will show what is on the system and where it is located

---

### Post by fra11 on 2012-02-15
Done, and I get a terminal window where it is said a huge amount of stuff.... I paste it here, don't know if it helps....

```


locale: aa_DJ           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Afar language locale for Djibouti (CaduLaaqo Dialects).
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | aa
territory | DJ
 revision | 0.20
     date | 2003-07-05
  codeset | ISO-8859-1

locale: aa_DJ.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Afar language locale for Djibouti (CaduLaaqo Dialects).
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | aa
territory | DJ
 revision | 0.20
     date | 2003-07-05
  codeset | ISO-8859-1

locale: aa_DJ.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Afar language locale for Djibouti (CaduLaaqo Dialects).
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | aa
territory | DJ
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: aa_ER           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Afar language locale for Eritrea (CaduLaaqo Dialects).
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | aa
territory | ER
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: aa_ER@saaho     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Afar language locale for Eritrea (Saaho Dialect).
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | aa
territory | ER
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: aa_ER.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Afar language locale for Eritrea (CaduLaaqo Dialects).
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | aa
territory | ER
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: aa_ER.utf8@saah archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Afar language locale for Eritrea (Saaho Dialect).
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | aa
territory | ER
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: aa_ET           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Afar language locale for Ethiopia (CaduCarra Dialects).
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | aa
territory | ET
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: aa_ET.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Afar language locale for Ethiopia (CaduCarra Dialects).
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | aa
territory | ET
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: af_ZA           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Afrikaans locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Afrikaans
territory | South Africa
 revision | 1.2.1
     date | 2005-10-13
  codeset | ISO-8859-1

locale: af_ZA.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Afrikaans locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Afrikaans
territory | South Africa
 revision | 1.2.1
     date | 2005-10-13
  codeset | ISO-8859-1

locale: af_ZA.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Afrikaans locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Afrikaans
territory | South Africa
 revision | 1.2.1
     date | 2005-10-13
  codeset | UTF-8

locale: am_ET           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Amharic language locale for Ethiopia.
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | am
territory | ET
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: am_ET.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Amharic language locale for Ethiopia.
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | am
territory | ET
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: an_ES           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Aragonese locale for Spain
  contact | Jordi Mallach P?rez
    email | bug-glibc-locales@gnu.org
 language | Aragonese
territory | Spain
 revision | 1.1
     date | 2003-08-25
  codeset | ISO-8859-15

locale: an_ES.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Aragonese locale for Spain
  contact | Jordi Mallach P?rez
    email | bug-glibc-locales@gnu.org
 language | Aragonese
territory | Spain
 revision | 1.1
     date | 2003-08-25
  codeset | ISO-8859-15

locale: an_ES.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Aragonese locale for Spain
  contact | Jordi Mallach P?rez
    email | bug-glibc-locales@gnu.org
 language | Aragonese
territory | Spain
 revision | 1.1
     date | 2003-08-25
  codeset | UTF-8

locale: ar_AE           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for United Arab Emirates
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | United Arab Emirates
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_AE.iso88596  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for United Arab Emirates
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | United Arab Emirates
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_AE.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for United Arab Emirates
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | United Arab Emirates
 revision | 1.0
     date | 2000-07-20
  codeset | UTF-8

locale: ar_BH           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Bahrain
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Bahrain
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_BH.iso88596  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Bahrain
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Bahrain
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_BH.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Bahrain
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Bahrain
 revision | 1.0
     date | 2000-07-20
  codeset | UTF-8

locale: ar_DZ           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Algeria
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Algeria
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_DZ.iso88596  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Algeria
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Algeria
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_DZ.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Algeria
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Algeria
 revision | 1.0
     date | 2000-07-20
  codeset | UTF-8

locale: ar_EG           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Egypt
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Egypt
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_EG.iso88596  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Egypt
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Egypt
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_EG.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Egypt
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Egypt
 revision | 1.0
     date | 2000-07-20
  codeset | UTF-8

locale: ar_IN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for India
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | India
 revision | 1.0
     date | 2000,October,27 (XML source:2000,July,20)
  codeset | UTF-8

locale: ar_IN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for India
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | India
 revision | 1.0
     date | 2000,October,27 (XML source:2000,July,20)
  codeset | UTF-8

locale: ar_IQ           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Iraq
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Iraq
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_IQ.iso88596  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Iraq
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Iraq
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_IQ.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Iraq
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Iraq
 revision | 1.0
     date | 2000-07-20
  codeset | UTF-8

locale: ar_JO           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Jordan
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Jordan
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_JO.iso88596  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Jordan
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Jordan
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_JO.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Jordan
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Jordan
 revision | 1.0
     date | 2000-07-20
  codeset | UTF-8

locale: ar_KW           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Kuwait
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Kuwait
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_KW.iso88596  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Kuwait
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Kuwait
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_KW.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Kuwait
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Kuwait
 revision | 1.0
     date | 2000-07-20
  codeset | UTF-8

locale: ar_LB           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Lebanon
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Lebanon
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_LB.iso88596  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Lebanon
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Lebanon
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_LB.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Lebanon
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Lebanon
 revision | 1.0
     date | 2000-07-20
  codeset | UTF-8

locale: ar_LY           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Libyan Arab Jamahiriya
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Libyan Arab Jamahiriya
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_LY.iso88596  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Libyan Arab Jamahiriya
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Libyan Arab Jamahiriya
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_LY.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Libyan Arab Jamahiriya
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Libyan Arab Jamahiriya
 revision | 1.0
     date | 2000-07-20
  codeset | UTF-8

locale: ar_MA           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Morocco
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Morocco
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_MA.iso88596  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Morocco
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Morocco
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_MA.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Morocco
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Morocco
 revision | 1.0
     date | 2000-07-20
  codeset | UTF-8

locale: ar_OM           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Oman
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Oman
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_OM.iso88596  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Oman
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Oman
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_OM.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Oman
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Oman
 revision | 1.0
     date | 2000-07-20
  codeset | UTF-8

locale: ar_QA           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Qatar
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Qatar
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_QA.iso88596  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Qatar
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Qatar
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_QA.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Qatar
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Qatar
 revision | 1.0
     date | 2000-07-20
  codeset | UTF-8

locale: ar_SA           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic locale for Saudi Arabia
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Saudi Arabia
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-6

locale: ar_SA.iso88596  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic locale for Saudi Arabia
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Saudi Arabia
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-6

locale: ar_SA.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic locale for Saudi Arabia
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Saudi Arabia
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: ar_SD           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Sudan
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Sudan
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_SD.iso88596  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Sudan
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Sudan
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_SD.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Sudan
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Sudan
 revision | 1.0
     date | 2000-07-20
  codeset | UTF-8

locale: ar_SY           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Syrian Arab Republic
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Syrian Arab Republic
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_SY.iso88596  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Syrian Arab Republic
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Syrian Arab Republic
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_SY.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Syrian Arab Republic
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Syrian Arab Republic
 revision | 1.0
     date | 2000-07-20
  codeset | UTF-8

locale: ar_TN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Tunisia
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Tunisia
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_TN.iso88596  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Tunisia
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Tunisia
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_TN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Tunisia
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Tunisia
 revision | 1.0
     date | 2000-07-20
  codeset | UTF-8

locale: ar_YE           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Yemen
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Yemen
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_YE.iso88596  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Yemen
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Yemen
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-6

locale: ar_YE.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Arabic language locale for Yemen
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Arabic
territory | Yemen
 revision | 1.0
     date | 2000-07-20
  codeset | UTF-8

locale: as_IN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Assamese language locale for India
   source | Amitakhya Phukan, Red Hat
    email | bug-glibc@gnu.org
 language | Assamese
territory | India
 revision | 1.0
     date | 2006-05-25
  codeset | UTF-8

locale: ast_ES          archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Asturian locale for Spain
  contact | Jordi Mallach
    email | jordi@gnu.org
 language | Asturian
territory | Spain
 revision | 1.0
     date | 2005-08-26
  codeset | ISO-8859-15

locale: ast_ES.iso88591 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Asturian locale for Spain
  contact | Jordi Mallach
    email | jordi@gnu.org
 language | Asturian
territory | Spain
 revision | 1.0
     date | 2005-08-26
  codeset | ISO-8859-15

locale: ast_ES.utf8     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Asturian locale for Spain
  contact | Jordi Mallach
    email | jordi@gnu.org
 language | Asturian
territory | Spain
 revision | 1.0
     date | 2005-08-26
  codeset | UTF-8

locale: az_AZ.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Azeri language locale for Azerbaijan (latin)
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Azeri
territory | Azerbaijan
 revision | 0.4
     date | 2001-01-26
  codeset | UTF-8

locale: be_BY           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Belarusian locale for Belarus
    email | bug-glibc-locales@gnu.org
 language | Belarusian
territory | Belarus
 revision | 1.0
     date | 2000-06-29
  codeset | CP1251

locale: be_BY.cp1251    archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Belarusian locale for Belarus
    email | bug-glibc-locales@gnu.org
 language | Belarusian
territory | Belarus
 revision | 1.0
     date | 2000-06-29
  codeset | CP1251

locale: be_BY@latin     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Belarusian Latin-Script locale for Belarus
    email | bug-glibc-locales@gnu.org
 language | Belarusian
territory | Belarus
 revision | 1.0
     date | 2005-09-15
  codeset | UTF-8

locale: be_BY.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Belarusian locale for Belarus
    email | bug-glibc-locales@gnu.org
 language | Belarusian
territory | Belarus
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: be_BY.utf8@lati archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Belarusian Latin-Script locale for Belarus
    email | bug-glibc-locales@gnu.org
 language | Belarusian
territory | Belarus
 revision | 1.0
     date | 2005-09-15
  codeset | UTF-8

locale: ber_DZ          archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Amazigh language locale for Algeria (latin)
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Amazigh
territory | Algeria
 revision | 0.1
     date | 2002-04-16
  codeset | UTF-8

locale: ber_DZ.utf8     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Amazigh language locale for Algeria (latin)
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Amazigh
territory | Algeria
 revision | 0.1
     date | 2002-04-16
  codeset | UTF-8

locale: ber_MA          archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Amazigh language locale for Morocco (tifinagh)
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Amazigh
territory | Morocco
 revision | 0.1
     date | 2002-06-26
  codeset | UTF-8

locale: ber_MA.utf8     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Amazigh language locale for Morocco (tifinagh)
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Amazigh
territory | Morocco
 revision | 0.1
     date | 2002-06-26
  codeset | UTF-8

locale: bg_BG           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Bulgarian locale for Bulgaria
   source | Linux Society Bulgaria
  address | develop@linux.zonebg.com
  contact | Delyan Toshev
    email | delyant@yahoo.com
 language | Bulgarian
territory | Bulgaria
 revision | 2.0.1
     date | 2002-09-10
  codeset | CP1251

locale: bg_BG.cp1251    archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Bulgarian locale for Bulgaria
   source | Linux Society Bulgaria
  address | develop@linux.zonebg.com
  contact | Delyan Toshev
    email | delyant@yahoo.com
 language | Bulgarian
territory | Bulgaria
 revision | 2.0.1
     date | 2002-09-10
  codeset | CP1251

locale: bg_BG.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Bulgarian locale for Bulgaria
   source | Linux Society Bulgaria
  address | develop@linux.zonebg.com
  contact | Delyan Toshev
    email | delyant@yahoo.com
 language | Bulgarian
territory | Bulgaria
 revision | 2.0.1
     date | 2002-09-10
  codeset | UTF-8

locale: bn_BD           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | BengaliBangla language locale for Bangladesh
   source | Ankur Group, http:/www.ankurbangla.org, http:/www.bengalinux.org
  address | Dhaka, Bangladesh
  contact | Taneem Ahmed, Jamil Ahmed
    email | taneem@bengalinux.org, jamil@bengalinux.org
 language | BengaliBangla
territory | Bangladesh
 revision | 0.5
     date | 2007-01-10
  codeset | UTF-8

locale: bn_BD.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | BengaliBangla language locale for Bangladesh
   source | Ankur Group, http:/www.ankurbangla.org, http:/www.bengalinux.org
  address | Dhaka, Bangladesh
  contact | Taneem Ahmed, Jamil Ahmed
    email | taneem@bengalinux.org, jamil@bengalinux.org
 language | BengaliBangla
territory | Bangladesh
 revision | 0.5
     date | 2007-01-10
  codeset | UTF-8

locale: bn_IN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Bengali language locale for India
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Bengali
territory | India
 revision | 1.0
     date | 2006-05-29
  codeset | UTF-8

locale: bn_IN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Bengali language locale for India
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Bengali
territory | India
 revision | 1.0
     date | 2006-05-29
  codeset | UTF-8

locale: bo_CN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tibetan language locale for P.R. of China
    email | bug-glibc@gnu.org
 language | Tibetan
territory | P.R. of China
 revision | 0.1
     date | 2007-11-06
  codeset | UTF-8

locale: bo_CN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tibetan language locale for P.R. of China
    email | bug-glibc@gnu.org
 language | Tibetan
territory | P.R. of China
 revision | 0.1
     date | 2007-11-06
  codeset | UTF-8

locale: bo_IN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tibetan language locale for India
    email | bug-glibc@gnu.org
 language | Tibetan
territory | India
 revision | 0.1
     date | 2007-11-06
  codeset | UTF-8

locale: bo_IN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tibetan language locale for India
    email | bug-glibc@gnu.org
 language | Tibetan
territory | India
 revision | 0.1
     date | 2007-11-06
  codeset | UTF-8

locale: br_FR           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Breton language locale for France
   source | Denise.Peden@enst-bretagne.fr (Denise Derrien-Peden)
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Breton
territory | France
 revision | 0.54
     date | 2001-01-28
  codeset | ISO-8859-1

locale: br_FR@euro      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Breton locale for France with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Breton
territory | France
 revision | 1.0
     date | 2002-02-28
  codeset | ISO-8859-15

locale: br_FR.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Breton language locale for France
   source | Denise.Peden@enst-bretagne.fr (Denise Derrien-Peden)
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Breton
territory | France
 revision | 0.54
     date | 2001-01-28
  codeset | ISO-8859-1

locale: br_FR.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Breton locale for France with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Breton
territory | France
 revision | 1.0
     date | 2002-02-28
  codeset | ISO-8859-15

locale: br_FR.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Breton language locale for France
   source | Denise.Peden@enst-bretagne.fr (Denise Derrien-Peden)
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Breton
territory | France
 revision | 0.54
     date | 2001-01-28
  codeset | UTF-8

locale: bs_BA           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Bosnian language locale for Bosnia and Herzegowina
   source | adapted from Croatian locale
  contact | Tomislav Vujec
    email | tvujec@carnet.hr
 language | Bosnian
territory | Bosnia and Herzegowina
 revision | 0.4
     date | 2004-01-09
  codeset | ISO-8859-2

locale: bs_BA.iso88592  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Bosnian language locale for Bosnia and Herzegowina
   source | adapted from Croatian locale
  contact | Tomislav Vujec
    email | tvujec@carnet.hr
 language | Bosnian
territory | Bosnia and Herzegowina
 revision | 0.4
     date | 2004-01-09
  codeset | ISO-8859-2

locale: bs_BA.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Bosnian language locale for Bosnia and Herzegowina
   source | adapted from Croatian locale
  contact | Tomislav Vujec
    email | tvujec@carnet.hr
 language | Bosnian
territory | Bosnia and Herzegowina
 revision | 0.4
     date | 2004-01-09
  codeset | UTF-8

locale: byn_ER          archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Blin language locale for Eritrea
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | byn
territory | ER
 revision | 0.21
     date | 2003-11-01
  codeset | UTF-8

locale: byn_ER.utf8     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Blin language locale for Eritrea
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | byn
territory | ER
 revision | 0.21
     date | 2003-11-01
  codeset | UTF-8

locale: ca_AD           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Catalan locale for Andorra 
   source | Robert Millan
 language | Catalan
territory | Andorra
 revision | 1.0
     date | 2006-01-16
  codeset | ISO-8859-15

locale: ca_AD.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Catalan locale for Andorra 
   source | Robert Millan
 language | Catalan
territory | Andorra
 revision | 1.0
     date | 2006-01-16
  codeset | ISO-8859-15

locale: ca_AD.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Catalan locale for Andorra 
   source | Robert Millan
 language | Catalan
territory | Andorra
 revision | 1.0
     date | 2006-01-16
  codeset | UTF-8

locale: ca_ES           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Catalan locale for Spain
   source | RAP
    email | bug-glibc-locales@gnu.org
 language | Catalan
territory | Spain
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: ca_ES@euro      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Catalan locale for Catalonia with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Catalan
territory | Spain
 revision | 1.0
     date | 2000-08-20
  codeset | ISO-8859-15

locale: ca_ES.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Catalan locale for Spain
   source | RAP
    email | bug-glibc-locales@gnu.org
 language | Catalan
territory | Spain
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: ca_ES.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Catalan locale for Catalonia with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Catalan
territory | Spain
 revision | 1.0
     date | 2000-08-20
  codeset | ISO-8859-15

locale: ca_ES.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Valencian (southern Catalan) locale for Spain with Euro
  contact | Jordi Mallach
    email | jordi@gnu.org
 language | Catalan
territory | Spain
 revision | 1.0
     date | 2006-04-06
  codeset | ISO-8859-15

locale: ca_ES.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Catalan locale for Spain
   source | RAP
    email | bug-glibc-locales@gnu.org
 language | Catalan
territory | Spain
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: ca_ES.utf8@vale archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Valencian (southern Catalan) locale for Spain with Euro
  contact | Jordi Mallach
    email | jordi@gnu.org
 language | Catalan
territory | Spain
 revision | 1.0
     date | 2006-04-06
  codeset | UTF-8

locale: ca_ES@valencia  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Valencian (southern Catalan) locale for Spain with Euro
  contact | Jordi Mallach
    email | jordi@gnu.org
 language | Catalan
territory | Spain
 revision | 1.0
     date | 2006-04-06
  codeset | ISO-8859-15

locale: ca_FR           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Catalan locale for France 
   source | Robert Millan
 language | Catalan
territory | France
 revision | 1.0
     date | 2006-01-16
  codeset | ISO-8859-15

locale: ca_FR.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Catalan locale for France 
   source | Robert Millan
 language | Catalan
territory | France
 revision | 1.0
     date | 2006-01-16
  codeset | ISO-8859-15

locale: ca_FR.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Catalan locale for France 
   source | Robert Millan
 language | Catalan
territory | France
 revision | 1.0
     date | 2006-01-16
  codeset | UTF-8

locale: ca_IT           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Catalan locale for Italy (L'Alguer) 
   source | Robert Millan
 language | Catalan
territory | Italy (L'Alguer)
 revision | 1.0
     date | 2006-01-16
  codeset | ISO-8859-15

locale: ca_IT.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Catalan locale for Italy (L'Alguer) 
   source | Robert Millan
 language | Catalan
territory | Italy (L'Alguer)
 revision | 1.0
     date | 2006-01-16
  codeset | ISO-8859-15

locale: ca_IT.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Catalan locale for Italy (L'Alguer) 
   source | Robert Millan
 language | Catalan
territory | Italy (L'Alguer)
 revision | 1.0
     date | 2006-01-16
  codeset | UTF-8

locale: crh_UA          archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Crimean Tatar (Crimean Turkish) language locale for Ukraine
  contact | Re&#351;at SABIQ
    email | tilde.birlik@gmail.com
 language | Crimean Tatar
territory | Ukraine
 revision | 0.4
     date | 2009-08-16
  codeset | UTF-8

locale: crh_UA.utf8     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Crimean Tatar (Crimean Turkish) language locale for Ukraine
  contact | Re&#351;at SABIQ
    email | tilde.birlik@gmail.com
 language | Crimean Tatar
territory | Ukraine
 revision | 0.4
     date | 2009-08-16
  codeset | UTF-8

locale: csb_PL          archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Kashubian locale for Poland
   source | csb_PL locale
  contact | Michal Ostrowski
    email | bug-glibc-locales@gnu.org
 language | Kashubian
territory | Poland
 audience | general
application | GNU locale
 revision | 1.0
     date | 2006-07-25
  codeset | UTF-8

locale: csb_PL.utf8     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Kashubian locale for Poland
   source | csb_PL locale
  contact | Michal Ostrowski
    email | bug-glibc-locales@gnu.org
 language | Kashubian
territory | Poland
 audience | general
application | GNU locale
 revision | 1.0
     date | 2006-07-25
  codeset | UTF-8

locale: cs_CZ           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Czech locale for the Czech Republic
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Czech
territory | Czech Republic
 revision | 1.0
     date | 2000-06-28
  codeset | ISO-8859-2

locale: cs_CZ.iso88592  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Czech locale for the Czech Republic
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Czech
territory | Czech Republic
 revision | 1.0
     date | 2000-06-28
  codeset | ISO-8859-2

locale: cs_CZ.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Czech locale for the Czech Republic
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Czech
territory | Czech Republic
 revision | 1.0
     date | 2000-06-28
  codeset | UTF-8

locale: cy_GB           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Welsh language locale for Great Britain
   source | thanks to Dafydd Tomos (dafydd@imaginet.co.uk)
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Welsh
territory | Great Britain
 revision | 0.9
     date | 2004-09-27
  codeset | ISO-8859-14

locale: cy_GB.iso885914 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Welsh language locale for Great Britain
   source | thanks to Dafydd Tomos (dafydd@imaginet.co.uk)
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Welsh
territory | Great Britain
 revision | 0.9
     date | 2004-09-27
  codeset | ISO-8859-14

locale: cy_GB.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Welsh language locale for Great Britain
   source | thanks to Dafydd Tomos (dafydd@imaginet.co.uk)
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Welsh
territory | Great Britain
 revision | 0.9
     date | 2004-09-27
  codeset | UTF-8

locale: da_DK           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Danish locale for Denmark
   source | Danish Standards Association
  address | Kollegievej 6, DK-2920 Charlottenlund, Danmark
    email | bug-glibc-locales@gnu.org
 language | Danish
territory | Denmark
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: da_DK.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Danish locale for Denmark
   source | Danish Standards Association
  address | Kollegievej 6, DK-2920 Charlottenlund, Danmark
    email | bug-glibc-locales@gnu.org
 language | Danish
territory | Denmark
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: da_DK.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Danish locale for Denmark
   source | Danish Standards Association
  address | Kollegievej 6, DK-2920 Charlottenlund, Danmark
    email | bug-glibc-locales@gnu.org
 language | Danish
territory | Denmark
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: de_AT           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Austria
   source | O:sterreiches Normungsinstitut
  address | Postfach 130, A-1021 Wien
  contact | Gerhard Budin
    email | bug-glibc-locales@gnu.org
 language | German
territory | Austria
 revision | 1.0
     date | 2000-06-28
  codeset | ISO-8859-1

locale: de_AT@euro      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Austria with Euro
   source | O:sterreiches Normungsinstitut
  address | Postfach 130, A-1021 Wien
  contact | Gerhard Budin
    email | bug-glibc-locales@gnu.org
 language | German
territory | Austria
 revision | 1.0
     date | 2000-08-20
  codeset | ISO-8859-15

locale: de_AT.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Austria
   source | O:sterreiches Normungsinstitut
  address | Postfach 130, A-1021 Wien
  contact | Gerhard Budin
    email | bug-glibc-locales@gnu.org
 language | German
territory | Austria
 revision | 1.0
     date | 2000-06-28
  codeset | ISO-8859-1

locale: de_AT.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Austria with Euro
   source | O:sterreiches Normungsinstitut
  address | Postfach 130, A-1021 Wien
  contact | Gerhard Budin
    email | bug-glibc-locales@gnu.org
 language | German
territory | Austria
 revision | 1.0
     date | 2000-08-20
  codeset | ISO-8859-15

locale: de_AT.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Austria
   source | O:sterreiches Normungsinstitut
  address | Postfach 130, A-1021 Wien
  contact | Gerhard Budin
    email | bug-glibc-locales@gnu.org
 language | German
territory | Austria
 revision | 1.0
     date | 2000-06-28
  codeset | UTF-8

locale: de_BE           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Belgium
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | German
territory | Belgium
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: de_BE@euro      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Belgium with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | German
territory | Belgium
 revision | 1.0
     date | 2000-08-21
  codeset | ISO-8859-15

locale: de_BE.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Belgium
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | German
territory | Belgium
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: de_BE.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Belgium with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | German
territory | Belgium
 revision | 1.0
     date | 2000-08-21
  codeset | ISO-8859-15

locale: de_BE.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Belgium
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | German
territory | Belgium
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: de_CH           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Switzerland
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | German
territory | Switzerland
 revision | 1.0
     date | 2007-09-23
  codeset | ISO-8859-1

locale: de_CH.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Switzerland
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | German
territory | Switzerland
 revision | 1.0
     date | 2007-09-23
  codeset | ISO-8859-1

locale: de_CH.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Switzerland
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | German
territory | Switzerland
 revision | 1.0
     date | 2007-09-23
  codeset | UTF-8

locale: de_DE           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Germany
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | German
territory | Germany
 revision | 1.0
     date | 2000-06-24
  codeset | ISO-8859-1

locale: de_DE@euro      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Germany with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | German
territory | Germany
 revision | 1.0
     date | 2000-06-24
  codeset | ISO-8859-15

locale: de_DE.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Germany
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | German
territory | Germany
 revision | 1.0
     date | 2000-06-24
  codeset | ISO-8859-1

locale: de_DE.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Germany with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | German
territory | Germany
 revision | 1.0
     date | 2000-06-24
  codeset | ISO-8859-15

locale: de_DE.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Germany
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | German
territory | Germany
 revision | 1.0
     date | 2000-06-24
  codeset | UTF-8

locale: de_LI.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Liechtenstein
    email | bug-glibc-locales@gnu.org
 language | German
territory | Liechtenstein
 revision | 1.0
     date | 2007-11-27
  codeset | UTF-8

locale: de_LU           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Luxemburg
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | German
territory | Luxemburg
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: de_LU@euro      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Luxemburg with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | German
territory | Luxemburg
 revision | 1.0
     date | 2000-08-20
  codeset | ISO-8859-15

locale: de_LU.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Luxemburg
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | German
territory | Luxemburg
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: de_LU.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Luxemburg with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | German
territory | Luxemburg
 revision | 1.0
     date | 2000-08-20
  codeset | ISO-8859-15

locale: de_LU.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | German locale for Luxemburg
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | German
territory | Luxemburg
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: dv_MV           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Dhivehi Language Locale for Maldives
    email | sofwath@hotmail.com
 language | Divehi
territory | Maldives
 revision | 0.1
     date | 2006-05-13
  codeset | UTF-8

locale: dv_MV.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Dhivehi Language Locale for Maldives
    email | sofwath@hotmail.com
 language | Divehi
territory | Maldives
 revision | 0.1
     date | 2006-05-13
  codeset | UTF-8

locale: dz_BT           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Dzongkha language locale for Bhutan
   source | Sherubtse College
  address | Kanglung, Bhutan
    email | bug-glibc@gnu.org
 language | Dzongkha
territory | Bhutan
 revision | 0.3
     date | 2004-09-03
  codeset | UTF-8

locale: dz_BT.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Dzongkha language locale for Bhutan
   source | Sherubtse College
  address | Kanglung, Bhutan
    email | bug-glibc@gnu.org
 language | Dzongkha
territory | Bhutan
 revision | 0.3
     date | 2004-09-03
  codeset | UTF-8

locale: el_CY           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Greek locale for Cyprus
   source | Greek Debian Translation Team
  address | Konstantinos Margaritis, M. Asias 50, Nafplion 21100, Greece
    email | bug-glibc@gnu.org
 language | Greek
territory | Cyprus
 revision | 1.0
     date | 2004-10-20
  codeset | ISO-8859-7

locale: el_CY.iso88597  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Greek locale for Cyprus
   source | Greek Debian Translation Team
  address | Konstantinos Margaritis, M. Asias 50, Nafplion 21100, Greece
    email | bug-glibc@gnu.org
 language | Greek
territory | Cyprus
 revision | 1.0
     date | 2004-10-20
  codeset | ISO-8859-7

locale: el_CY.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Greek locale for Cyprus
   source | Greek Debian Translation Team
  address | Konstantinos Margaritis, M. Asias 50, Nafplion 21100, Greece
    email | bug-glibc@gnu.org
 language | Greek
territory | Cyprus
 revision | 1.0
     date | 2004-10-20
  codeset | UTF-8

locale: el_GR           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Greek locale for Greece
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Greek
territory | Greece
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-7

locale: el_GR.iso88597  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Greek locale for Greece
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Greek
territory | Greece
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-7

locale: el_GR.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Greek locale for Greece
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Greek
territory | Greece
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: en_AG           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English language locale for Antigua and Barbuda
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | English
territory | Antigua and Barbuda
 revision | 1.0
     date | 2008-09-16
  codeset | UTF-8

locale: en_AG.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English language locale for Antigua and Barbuda
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | English
territory | Antigua and Barbuda
 revision | 1.0
     date | 2008-09-16
  codeset | UTF-8

locale: en_AU           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Australia
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | English
territory | Australia
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: en_AU.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Australia
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | English
territory | Australia
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: en_AU.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Australia
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | English
territory | Australia
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: en_BW           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Botswana
   source | RAP
    email | bug-glibc-locales@gnu.org
 language | English
territory | Botswana
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: en_BW.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Botswana
   source | RAP
    email | bug-glibc-locales@gnu.org
 language | English
territory | Botswana
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: en_BW.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Botswana
   source | RAP
    email | bug-glibc-locales@gnu.org
 language | English
territory | Botswana
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: en_CA           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Canada
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | English
territory | Canada
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: en_CA.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Canada
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | English
territory | Canada
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: en_CA.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Canada
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | English
territory | Canada
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: en_DK           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Denmark
   source | Danish Standards Association
  address | Kollegievej 6, DK-2920 Charlottenlund, Danmark
    email | bug-glibc-locales@gnu.org
 language | English
territory | Denmark
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: en_DK.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Denmark
   source | Danish Standards Association
  address | Kollegievej 6, DK-2920 Charlottenlund, Danmark
    email | bug-glibc-locales@gnu.org
 language | English
territory | Denmark
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: en_DK.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Denmark
   source | Danish Standards Association
  address | Kollegievej 6, DK-2920 Charlottenlund, Danmark
    email | bug-glibc-locales@gnu.org
 language | English
territory | Denmark
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-15

locale: en_DK.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Denmark
   source | Danish Standards Association
  address | Kollegievej 6, DK-2920 Charlottenlund, Danmark
    email | bug-glibc-locales@gnu.org
 language | English
territory | Denmark
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: en_GB           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Britain
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
  contact | Keld Simonsen
    email | bug-glibc-locales@gnu.org
 language | English
territory | Great Britain
 revision | 1.0
     date | 2000-06-28
  codeset | ISO-8859-1

locale: en_GB.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Britain
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
  contact | Keld Simonsen
    email | bug-glibc-locales@gnu.org
 language | English
territory | Great Britain
 revision | 1.0
     date | 2000-06-28
  codeset | ISO-8859-1

locale: en_GB.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Britain
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
  contact | Keld Simonsen
    email | bug-glibc-locales@gnu.org
 language | English
territory | Great Britain
 revision | 1.0
     date | 2000-06-28
  codeset | ISO-8859-15

locale: en_GB.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Britain
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
  contact | Keld Simonsen
    email | bug-glibc-locales@gnu.org
 language | English
territory | Great Britain
 revision | 1.0
     date | 2000-06-28
  codeset | UTF-8

locale: en_HK           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Hong Kong
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | English
territory | Hong Kong
 revision | 1.0
     date | 2000,October,27 (XML source:2000,July,20)
  codeset | ISO-8859-1

locale: en_HK.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Hong Kong
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | English
territory | Hong Kong
 revision | 1.0
     date | 2000,October,27 (XML source:2000,July,20)
  codeset | ISO-8859-1

locale: en_HK.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Hong Kong
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | English
territory | Hong Kong
 revision | 1.0
     date | 2000,October,27 (XML source:2000,July,20)
  codeset | UTF-8

locale: en_IE           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Ireland
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | English
territory | Ireland
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: en_IE@euro      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Ireland with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | English
territory | Ireland
 revision | 1.0
     date | 2000-08-20
  codeset | ISO-8859-15

locale: en_IE.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Ireland
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | English
territory | Ireland
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: en_IE.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Ireland with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | English
territory | Ireland
 revision | 1.0
     date | 2000-08-20
  codeset | ISO-8859-15

locale: en_IE.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Ireland
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | English
territory | Ireland
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: en_IN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English language locale for India
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | English
territory | India
 revision | 1.0
     date | 2000,October,27 (XML source:2000,July,20)
  codeset | UTF-8

locale: en_IN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English language locale for India
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | English
territory | India
 revision | 1.0
     date | 2000,October,27 (XML source:2000,July,20)
  codeset | UTF-8

locale: en_NG           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Nigeria
 language | English
territory | Nigeria
 revision | 0.2
     date | 2006-02-01
  codeset | UTF-8

locale: en_NG.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Nigeria
 language | English
territory | Nigeria
 revision | 0.2
     date | 2006-02-01
  codeset | UTF-8

locale: en_NZ           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for New Zealand
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | English
territory | New Zealand
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: en_NZ.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for New Zealand
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | English
territory | New Zealand
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: en_NZ.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for New Zealand
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | English
territory | New Zealand
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: en_PH           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English language locale for Philippines
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | English
territory | Philippines
 revision | 1.0
     date | 2000,October,27 (XML source:2000,July,20)
  codeset | ISO-8859-1

locale: en_PH.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English language locale for Philippines
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | English
territory | Philippines
 revision | 1.0
     date | 2000,October,27 (XML source:2000,July,20)
  codeset | ISO-8859-1

locale: en_PH.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English language locale for Philippines
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | English
territory | Philippines
 revision | 1.0
     date | 2000,October,27 (XML source:2000,July,20)
  codeset | UTF-8

locale: en_SG           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English language locale for Singapore
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | English
territory | Singapore
 revision | 1.0
     date | 2000,October,27 (XML source:2000,July,20)
  codeset | ISO-8859-1

locale: en_SG.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English language locale for Singapore
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | English
territory | Singapore
 revision | 1.0
     date | 2000,October,27 (XML source:2000,July,20)
  codeset | ISO-8859-1

locale: en_SG.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English language locale for Singapore
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | English
territory | Singapore
 revision | 1.0
     date | 2000,October,27 (XML source:2000,July,20)
  codeset | UTF-8

locale: en_US           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for the USA
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | English
territory | USA
 revision | 1.0
     date | 2000-06-24
  codeset | ISO-8859-1

locale: en_US.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for the USA
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | English
territory | USA
 revision | 1.0
     date | 2000-06-24
  codeset | ISO-8859-1

locale: en_US.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for the USA
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | English
territory | USA
 revision | 1.0
     date | 2000-06-24
  codeset | ISO-8859-15

locale: en_US.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for the USA
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | English
territory | USA
 revision | 1.0
     date | 2000-06-24
  codeset | UTF-8

locale: en_ZA           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | English
territory | South Africa
abbreviation | Translate.org.za
 revision | 1.3
     date | 2007-04-19
  codeset | ISO-8859-1

locale: en_ZA.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | English
territory | South Africa
abbreviation | Translate.org.za
 revision | 1.3
     date | 2007-04-19
  codeset | ISO-8859-1

locale: en_ZA.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | English
territory | South Africa
abbreviation | Translate.org.za
 revision | 1.3
     date | 2007-04-19
  codeset | UTF-8

locale: en_ZW           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Zimbabwe
   source | RAP
    email | bug-glibc-locales@gnu.org
 language | English
territory | Zimbabwe
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: en_ZW.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Zimbabwe
   source | RAP
    email | bug-glibc-locales@gnu.org
 language | English
territory | Zimbabwe
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: en_ZW.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | English locale for Zimbabwe
   source | RAP
    email | bug-glibc-locales@gnu.org
 language | English
territory | Zimbabwe
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: eo              archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Esperanto locale
    email | debian-esperanto@lists.debian.org
 language | Esperanto
 revision | draft
     date | 2002-07-04
  codeset | ISO-8859-3

locale: eo.iso88593     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Esperanto locale
    email | debian-esperanto@lists.debian.org
 language | Esperanto
 revision | draft
     date | 2002-07-04
  codeset | ISO-8859-3

locale: eo.utf8         archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Esperanto locale
    email | debian-esperanto@lists.debian.org
 language | Esperanto
 revision | draft
     date | 2002-07-04
  codeset | UTF-8

locale: es_AR           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Argentina
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Argentina
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_AR.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Argentina
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Argentina
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_AR.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Argentina
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Argentina
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: es_BO           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Bolivia
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Bolivia
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_BO.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Bolivia
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Bolivia
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_BO.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Bolivia
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Bolivia
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: es_CL           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Chile
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Chile
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_CL.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Chile
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Chile
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_CL.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Chile
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Chile
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: es_CO           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Colombia
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Colombia
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_CO.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Colombia
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Colombia
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_CO.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Colombia
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Colombia
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: es_CR           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Costa Rica
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Costa Rica
 revision | 1.1
     date | 2009-12-23
  codeset | ISO-8859-1

locale: es_CR.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Costa Rica
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Costa Rica
 revision | 1.1
     date | 2009-12-23
  codeset | ISO-8859-1

locale: es_CR.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Costa Rica
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Costa Rica
 revision | 1.1
     date | 2009-12-23
  codeset | UTF-8

locale: es_DO           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Dominican Republic
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Dominican Republic
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_DO.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Dominican Republic
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Dominican Republic
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_DO.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Dominican Republic
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Dominican Republic
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: es_EC           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Ecuador
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Ecuador
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_EC.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Ecuador
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Ecuador
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_EC.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Ecuador
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Ecuador
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: es_ES           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Spain
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Spain
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_ES@euro      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Spain with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Spain
     date | 2000-06-29
  codeset | ISO-8859-15

locale: es_ES.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Spain
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Spain
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_ES.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Spain with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Spain
     date | 2000-06-29
  codeset | ISO-8859-15

locale: es_ES.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Spain
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Spain
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: es_GT           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Guatemala
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Guatemala
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_GT.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Guatemala
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Guatemala
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_GT.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Guatemala
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Guatemala
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: es_HN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Honduras
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Honduras
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_HN.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Honduras
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Honduras
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_HN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Honduras
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Honduras
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: es_MX           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Mexico
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Mexico
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_MX.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Mexico
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Mexico
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_MX.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Mexico
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Mexico
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: es_NI           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Nicaragua
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Nicaragua
 revision | 1.0
     date | 2000-08-21
  codeset | ISO-8859-1

locale: es_NI.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Nicaragua
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Nicaragua
 revision | 1.0
     date | 2000-08-21
  codeset | ISO-8859-1

locale: es_NI.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Nicaragua
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Nicaragua
 revision | 1.0
     date | 2000-08-21
  codeset | UTF-8

locale: es_PA           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Panama
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Panama
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_PA.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Panama
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Panama
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_PA.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Panama
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Panama
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: es_PE           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Peru
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Peru
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_PE.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Peru
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Peru
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_PE.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Peru
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Peru
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: es_PR           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Puerto Rico
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Puerto Rico
 revision | 1.0
     date | 2000-08-21
  codeset | ISO-8859-1

locale: es_PR.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Puerto Rico
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Puerto Rico
 revision | 1.0
     date | 2000-08-21
  codeset | ISO-8859-1

locale: es_PR.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Puerto Rico
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Puerto Rico
 revision | 1.0
     date | 2000-08-21
  codeset | UTF-8

locale: es_PY           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Paraguay
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Paraguay
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_PY.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Paraguay
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Paraguay
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_PY.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Paraguay
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Paraguay
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: es_SV           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for El Salvador
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | El Salvador
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_SV.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for El Salvador
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | El Salvador
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_SV.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for El Salvador
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | El Salvador
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: es_US           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for the USA
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | USA
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_US.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for the USA
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | USA
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_US.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for the USA
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | USA
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: es_UY           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Uruguay
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Uruguay
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_UY.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Uruguay
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Uruguay
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_UY.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Uruguay
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Uruguay
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: es_VE           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Venezuela
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Venezuela
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_VE.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Venezuela
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Venezuela
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: es_VE.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Spanish locale for Venezuela
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Spanish
territory | Venezuela
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: et_EE           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Estonian locale for Estonia
   source | Estonian Informatics Fund
  address | To-nisma:gi 8, Tallinn, EE0100 Estonia
    email | bug-glibc-locales@gnu.org
 language | Estonian
territory | Estonia
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: et_EE.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Estonian locale for Estonia
   source | Estonian Informatics Fund
  address | To-nisma:gi 8, Tallinn, EE0100 Estonia
    email | bug-glibc-locales@gnu.org
 language | Estonian
territory | Estonia
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: et_EE.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Estonian locale for Estonia
   source | Estonian Informatics Fund
  address | To-nisma:gi 8, Tallinn, EE0100 Estonia
    email | bug-glibc-locales@gnu.org
 language | Estonian
territory | Estonia
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-15

locale: et_EE.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Estonian locale for Estonia
   source | Estonian Informatics Fund
  address | To-nisma:gi 8, Tallinn, EE0100 Estonia
    email | bug-glibc-locales@gnu.org
 language | Estonian
territory | Estonia
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: eu_ES           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Basque locale for Spain
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Basque
territory | Spain
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: eu_ES@euro      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Basque language locale for Spain with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Basque
territory | Spain
 revision | 1.0
     date | 2000-08-21
  codeset | ISO-8859-15

locale: eu_ES.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Basque locale for Spain
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Basque
territory | Spain
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: eu_ES.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Basque language locale for Spain with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Basque
territory | Spain
 revision | 1.0
     date | 2000-08-21
  codeset | ISO-8859-15

locale: eu_ES.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Basque locale for Spain
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Basque
territory | Spain
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: eu_FR           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Basque locale for France
   source | Christian Perrier and the Debian Project
  contact | Christian Perrier
    email | bubulle@debian.org
 language | Basque
territory | France
 revision | 1.0
     date | 2004-06-24
  codeset | ISO-8859-1

locale: eu_FR@euro      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Basque locale for France
   source | Christian Perrier and the Debian Project
  contact | Christian Perrier
    email | bubulle@debian.org
 language | Basque
territory | France
 revision | 1.0
     date | 2004-06-24
  codeset | ISO-8859-15

locale: eu_FR.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Basque locale for France
   source | Christian Perrier and the Debian Project
  contact | Christian Perrier
    email | bubulle@debian.org
 language | Basque
territory | France
 revision | 1.0
     date | 2004-06-24
  codeset | ISO-8859-1

locale: eu_FR.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Basque locale for France
   source | Christian Perrier and the Debian Project
  contact | Christian Perrier
    email | bubulle@debian.org
 language | Basque
territory | France
 revision | 1.0
     date | 2004-06-24
  codeset | ISO-8859-15

locale: eu_FR.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Basque locale for France
   source | Christian Perrier and the Debian Project
  contact | Christian Perrier
    email | bubulle@debian.org
 language | Basque
territory | France
 revision | 1.0
     date | 2004-06-24
  codeset | UTF-8

locale: fa_IR           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Persian locale for Iran
   source | Sharif FarsiWeb, Inc.
  address | 5, Shahid Ghasemi Habibollah, Azadi Ave, Tehran, Iran
  contact | Roozbeh Pournader
    email | roozbeh@farsiweb.info
telephone | +98 21 6022372
      fax | +98 21 6019568
 language | Persian
territory | Iran
 revision | 3.0
     date | 2005-04-06
  codeset | UTF-8

locale: fa_IR.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Persian locale for Iran
   source | Sharif FarsiWeb, Inc.
  address | 5, Shahid Ghasemi Habibollah, Azadi Ave, Tehran, Iran
  contact | Roozbeh Pournader
    email | roozbeh@farsiweb.info
telephone | +98 21 6022372
      fax | +98 21 6019568
 language | Persian
territory | Iran
 revision | 3.0
     date | 2005-04-06
  codeset | UTF-8

locale: fi_FI           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Finnish locale for Finland
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Finnish
territory | Finland
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: fi_FI@euro      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Finnish locale for Finland with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Finnish
territory | Finland
 revision | 1.0
     date | 2000-08-20
  codeset | ISO-8859-15

locale: fi_FI.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Finnish locale for Finland
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Finnish
territory | Finland
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: fi_FI.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Finnish locale for Finland with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Finnish
territory | Finland
 revision | 1.0
     date | 2000-08-20
  codeset | ISO-8859-15

locale: fi_FI.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Finnish locale for Finland
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Finnish
territory | Finland
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: fil_PH          archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Filipino language locale for Philippines
   source | Rene Torres
  contact | Rene Torres, Pablo Saratxaga
    email | rgtorre@rocketmail.com, pablo@mandrakesoft.com
 language | Filipino
territory | Philippines
 revision | 0.5
     date | 2005-02-02
  codeset | UTF-8

locale: fil_PH.utf8     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Filipino language locale for Philippines
   source | Rene Torres
  contact | Rene Torres, Pablo Saratxaga
    email | rgtorre@rocketmail.com, pablo@mandrakesoft.com
 language | Filipino
territory | Philippines
 revision | 0.5
     date | 2005-02-02
  codeset | UTF-8

locale: fo_FO           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Faroese locale for Faroe Islands
   source | Danish Standards Association
  address | Kollegievej 6, DK-2920 Charlottenlund, Danmark
    email | bug-glibc-locales@gnu.org
 language | Faroese
territory | Faroe Islands
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: fo_FO.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Faroese locale for Faroe Islands
   source | Danish Standards Association
  address | Kollegievej 6, DK-2920 Charlottenlund, Danmark
    email | bug-glibc-locales@gnu.org
 language | Faroese
territory | Faroe Islands
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: fo_FO.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Faroese locale for Faroe Islands
   source | Danish Standards Association
  address | Kollegievej 6, DK-2920 Charlottenlund, Danmark
    email | bug-glibc-locales@gnu.org
 language | Faroese
territory | Faroe Islands
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: fr_BE           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | French locale for Belgium
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | French
territory | Belgium
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: fr_BE@euro      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | French locale for Belgium with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | French
territory | Belgium
 revision | 1.0
     date | 2000-08-20
  codeset | ISO-8859-15

locale: fr_BE.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | French locale for Belgium
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | French
territory | Belgium
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: fr_BE.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | French locale for Belgium with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | French
territory | Belgium
 revision | 1.0
     date | 2000-08-20
  codeset | ISO-8859-15

locale: fr_BE.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | French locale for Belgium
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | French
territory | Belgium
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: fr_CA           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | French locale for Canada
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | French
territory | Canada
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: fr_CA.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | French locale for Canada
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | French
territory | Canada
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: fr_CA.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | French locale for Canada
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | French
territory | Canada
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: fr_CH           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | French locale for Switzerland
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | French
territory | Switzerland
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: fr_CH.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | French locale for Switzerland
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | French
territory | Switzerland
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: fr_CH.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | French locale for Switzerland
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | French
territory | Switzerland
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: fr_FR           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | French locale for France
   source | RAP
  contact | Traduc.org
    email | bug-glibc-locales@gnu.org
 language | French
territory | France
 revision | 1.0
     date | 2008-03-15
  codeset | ISO-8859-1

locale: fr_FR@euro      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | French locale for France with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | French
territory | France
 revision | 1.0
     date | 2000-08-20
  codeset | ISO-8859-15

locale: fr_FR.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | French locale for France
   source | RAP
  contact | Traduc.org
    email | bug-glibc-locales@gnu.org
 language | French
territory | France
 revision | 1.0
     date | 2008-03-15
  codeset | ISO-8859-1

locale: fr_FR.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | French locale for France with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | French
territory | France
 revision | 1.0
     date | 2000-08-20
  codeset | ISO-8859-15

locale: fr_FR.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | French locale for France
   source | RAP
  contact | Traduc.org
    email | bug-glibc-locales@gnu.org
 language | French
territory | France
 revision | 1.0
     date | 2008-03-15
  codeset | UTF-8

locale: fr_LU           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | French locale for Luxemburg
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | French
territory | Luxemburg
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: fr_LU@euro      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | French locale for Luxemburg with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | French
territory | Luxemburg
 revision | 1.0
     date | 2000-08-20
  codeset | ISO-8859-15

locale: fr_LU.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | French locale for Luxemburg
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | French
territory | Luxemburg
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: fr_LU.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | French locale for Luxemburg with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | French
territory | Luxemburg
 revision | 1.0
     date | 2000-08-20
  codeset | ISO-8859-15

locale: fr_LU.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | French locale for Luxemburg
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | French
territory | Luxemburg
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: fur_IT          archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Furlan locale for Italy
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Furlan
territory | Italy
 revision | 0.3
     date | 2004-04-26
  codeset | UTF-8

locale: fur_IT.utf8     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Furlan locale for Italy
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Furlan
territory | Italy
 revision | 0.3
     date | 2004-04-26
  codeset | UTF-8

locale: fy_DE           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Sater Frisian and North Frisian Locale for Germany
   source | information from Kenneth Christiansen
  contact | Kenneth Christiansen, Pablo Saratxaga
    email | kenneth@gnu.org, pablo@mandriva.com
 language | fy
territory | DE
 revision | 0.1
     date | 2003-11-30
  codeset | UTF-8

locale: fy_DE.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Sater Frisian and North Frisian Locale for Germany
   source | information from Kenneth Christiansen
  contact | Kenneth Christiansen, Pablo Saratxaga
    email | kenneth@gnu.org, pablo@mandriva.com
 language | fy
territory | DE
 revision | 0.1
     date | 2003-11-30
  codeset | UTF-8

locale: fy_NL           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Frisian locale for the Netherlands
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Frisian
territory | Netherlands
 revision | 1.0
     date | 2006-08-13
  codeset | UTF-8

locale: fy_NL.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Frisian locale for the Netherlands
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Frisian
territory | Netherlands
 revision | 1.0
     date | 2006-08-13
  codeset | UTF-8

locale: ga_IE           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Irish locale for Ireland
   source | NSAI
  address | Glasnevin, Dublin 9, Ireland
    email | bug-glibc-locales@gnu.org
 language | Irish
territory | Ireland
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: ga_IE@euro      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Irish locale for Ireland with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Irish
territory | Ireland
 revision | 1.0
     date | 2000-08-21
  codeset | ISO-8859-15

locale: ga_IE.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Irish locale for Ireland
   source | NSAI
  address | Glasnevin, Dublin 9, Ireland
    email | bug-glibc-locales@gnu.org
 language | Irish
territory | Ireland
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: ga_IE.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Irish locale for Ireland with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Irish
territory | Ireland
 revision | 1.0
     date | 2000-08-21
  codeset | ISO-8859-15

locale: ga_IE.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Irish locale for Ireland
   source | NSAI
  address | Glasnevin, Dublin 9, Ireland
    email | bug-glibc-locales@gnu.org
 language | Irish
territory | Ireland
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: gd_GB           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Scots Gaelic language locale for Great Britain
   source | Alastair McKinstry
  address | Cro? L?r, Ballinahalla, Maigh Cuilinn, Co. Gaillimh, Ireland
  contact | Alastair McKinstry
    email | mckinstry@computer.org
telephone | +353 91 556177
 language | Scots Gaelic
territory | Great Britain
 revision | 1.1
     date | 2000-06-12
  codeset | ISO-8859-15

locale: gd_GB.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Scots Gaelic language locale for Great Britain
   source | Alastair McKinstry
  address | Cro? L?r, Ballinahalla, Maigh Cuilinn, Co. Gaillimh, Ireland
  contact | Alastair McKinstry
    email | mckinstry@computer.org
telephone | +353 91 556177
 language | Scots Gaelic
territory | Great Britain
 revision | 1.1
     date | 2000-06-12
  codeset | ISO-8859-15

locale: gd_GB.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Scots Gaelic language locale for Great Britain
   source | Alastair McKinstry
  address | Cro? L?r, Ballinahalla, Maigh Cuilinn, Co. Gaillimh, Ireland
  contact | Alastair McKinstry
    email | mckinstry@computer.org
telephone | +353 91 556177
 language | Scots Gaelic
territory | Great Britain
 revision | 1.1
     date | 2000-06-12
  codeset | UTF-8

locale: gez_ER          archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Ge'ez language locale for Eritrea.
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | gez
territory | ER
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: gez_ER@abegede  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Ge'ez language locale for Eritrea With Abegede Collation.
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | gez
territory | ER
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: gez_ER.utf8     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Ge'ez language locale for Eritrea.
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | gez
territory | ER
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: gez_ER.utf8@abe archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Ge'ez language locale for Eritrea With Abegede Collation.
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | gez
territory | ER
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: gez_ET          archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Ge'ez language locale for Ethiopia
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | gez
territory | ET
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: gez_ET@abegede  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Ge'ez language locale for Ethiopia With Abegede Collation
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | gez
territory | ET
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: gez_ET.utf8     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Ge'ez language locale for Ethiopia
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | gez
territory | ET
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: gez_ET.utf8@abe archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Ge'ez language locale for Ethiopia With Abegede Collation
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | gez
territory | ET
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: gl_ES           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Galician locale for Spain
   source | GPUL
  address | Facultade de Inform?tica, Campus de Elvin~a, sn, 15071 A Corun~a, Spain
    email | bug-glibc-locales@gnu.org
 language | Galician
territory | Spain
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: gl_ES@euro      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Galician locale for Spain with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Galician
territory | Spain
 revision | 1.0
     date | 2000-08-21
  codeset | ISO-8859-15

locale: gl_ES.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Galician locale for Spain
   source | GPUL
  address | Facultade de Inform?tica, Campus de Elvin~a, sn, 15071 A Corun~a, Spain
    email | bug-glibc-locales@gnu.org
 language | Galician
territory | Spain
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: gl_ES.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Galician locale for Spain with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Galician
territory | Spain
 revision | 1.0
     date | 2000-08-21
  codeset | ISO-8859-15

locale: gl_ES.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Galician locale for Spain
   source | GPUL
  address | Facultade de Inform?tica, Campus de Elvin~a, sn, 15071 A Corun~a, Spain
    email | bug-glibc-locales@gnu.org
 language | Galician
territory | Spain
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: gu_IN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Gujarati Language Locale For India
   source | IndLinux.org
    email | bug-glibc-locales@gnu.org
 language | Gujarati
territory | India
 revision | 0.2
     date | 2004-14-09
  codeset | UTF-8

locale: gu_IN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Gujarati Language Locale For India
   source | IndLinux.org
    email | bug-glibc-locales@gnu.org
 language | Gujarati
territory | India
 revision | 0.2
     date | 2004-14-09
  codeset | UTF-8

locale: gv_GB           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Manx Gaelic locale for Britain
   source | Alastair McKinstry
  address | Cro? L?r, Ballinahalla, Maigh Cuilinn,, Co. Gaillimh, Ireland
    email | bug-glibc-locales@gnu.org
 language | Manx Gaelic
territory | Britain
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: gv_GB.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Manx Gaelic locale for Britain
   source | Alastair McKinstry
  address | Cro? L?r, Ballinahalla, Maigh Cuilinn,, Co. Gaillimh, Ireland
    email | bug-glibc-locales@gnu.org
 language | Manx Gaelic
territory | Britain
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: gv_GB.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Manx Gaelic locale for Britain
   source | Alastair McKinstry
  address | Cro? L?r, Ballinahalla, Maigh Cuilinn,, Co. Gaillimh, Ireland
    email | bug-glibc-locales@gnu.org
 language | Manx Gaelic
territory | Britain
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: ha_NG           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Hausa locale for Nigeria
    email | pablo@mandriva.com
 language | Hausa
territory | Nigeria
 revision | 0.2
     date | 2006-02-01
  codeset | UTF-8

locale: ha_NG.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Hausa locale for Nigeria
    email | pablo@mandriva.com
 language | Hausa
territory | Nigeria
 revision | 0.2
     date | 2006-02-01
  codeset | UTF-8

locale: he_IL           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Hebrew locale for Israel
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Hebrew
territory | Israel
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-8

locale: he_IL.iso88598  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Hebrew locale for Israel
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Hebrew
territory | Israel
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-8

locale: he_IL.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Hebrew locale for Israel
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Hebrew
territory | Israel
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: hi_IN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Hindi language locale for India
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Hindi
territory | India
 revision | 1.0
     date | 2000-07-21
  codeset | UTF-8

locale: hi_IN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Hindi language locale for India
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Hindi
territory | India
 revision | 1.0
     date | 2000-07-21
  codeset | UTF-8

locale: hne_IN          archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Chhattisgarhi language locale for India
   source | Red Hat, Pune
  address | Marisfot III, Marigold Premises, East-Wing, Kalyaninagar, Pune, India-411014
    email | bug-glibc-locales@gnu.org
 language | Chhattisgarhi
territory | India
 revision | 1.0
     date | 2008-12-03
  codeset | UTF-8

locale: hne_IN.utf8     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Chhattisgarhi language locale for India
   source | Red Hat, Pune
  address | Marisfot III, Marigold Premises, East-Wing, Kalyaninagar, Pune, India-411014
    email | bug-glibc-locales@gnu.org
 language | Chhattisgarhi
territory | India
 revision | 1.0
     date | 2008-12-03
  codeset | UTF-8

locale: hr_HR           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Croatian locale for Croatia
   source | CARNetMZT
  address | Josipa Marohnica bb, Zagreb, Hrvatska
    email | bug-glibc-locales@gnu.org
 language | Croatian
territory | Croatia
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-2

locale: hr_HR.iso88592  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Croatian locale for Croatia
   source | CARNetMZT
  address | Josipa Marohnica bb, Zagreb, Hrvatska
    email | bug-glibc-locales@gnu.org
 language | Croatian
territory | Croatia
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-2

locale: hr_HR.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Croatian locale for Croatia
   source | CARNetMZT
  address | Josipa Marohnica bb, Zagreb, Hrvatska
    email | bug-glibc-locales@gnu.org
 language | Croatian
territory | Croatia
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: hsb_DE          archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Upper Sorbian locale for Germany
   source | Information from Michael Wolf
  contact | Andrzej Krzysztofowicz
    email | ankry@mif.pg.gda.pl
 language | Upper Sorbian
territory | Germany
 revision | 0.1
     date | 2004-09-09
  codeset | ISO-8859-2

locale: hsb_DE.iso88592 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Upper Sorbian locale for Germany
   source | Information from Michael Wolf
  contact | Andrzej Krzysztofowicz
    email | ankry@mif.pg.gda.pl
 language | Upper Sorbian
territory | Germany
 revision | 0.1
     date | 2004-09-09
  codeset | ISO-8859-2

locale: hsb_DE.utf8     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Upper Sorbian locale for Germany
   source | Information from Michael Wolf
  contact | Andrzej Krzysztofowicz
    email | ankry@mif.pg.gda.pl
 language | Upper Sorbian
territory | Germany
 revision | 0.1
     date | 2004-09-09
  codeset | UTF-8

locale: ht_HT           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Kreyol locale for Haiti
   source | OLPC
  contact | olpchaiti.org
    email | contact@olpchaiti.org
 language | U006Breyol
territory | Haiti
 revision | 1.0
     date | 2008-08-17
  codeset | UTF-8

locale: ht_HT.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Kreyol locale for Haiti
   source | OLPC
  contact | olpchaiti.org
    email | contact@olpchaiti.org
 language | U006Breyol
territory | Haiti
 revision | 1.0
     date | 2008-08-17
  codeset | UTF-8

locale: hu_HU           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Hungarian locale for Hungary
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Hungarian
territory | Hungary
 revision | 4.7
     date | 2001-01-29
  codeset | ISO-8859-2

locale: hu_HU.iso88592  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Hungarian locale for Hungary
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Hungarian
territory | Hungary
 revision | 4.7
     date | 2001-01-29
  codeset | ISO-8859-2

locale: hu_HU.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Hungarian locale for Hungary
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Hungarian
territory | Hungary
 revision | 4.7
     date | 2001-01-29
  codeset | UTF-8

locale: hy_AM           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Armenian language locale for Armenia
   source | http:/www.freenet.amarmscii
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Armenian
territory | Armenia
 revision | 0.4
     date | 2001-01-26
  codeset | UTF-8

locale: hy_AM.armscii8  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Armenian language locale for Armenia
   source | http:/www.freenet.amarmscii
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Armenian
territory | Armenia
 revision | 0.4
     date | 2001-01-26
  codeset | ARMSCII-8

locale: hy_AM.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Armenian language locale for Armenia
   source | http:/www.freenet.amarmscii
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Armenian
territory | Armenia
 revision | 0.4
     date | 2001-01-26
  codeset | UTF-8

locale: ia              archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Interlingua locale
    email | mardy@despammed.com
 language | Interlingua
 revision | 1.0
     date | 2003-11-25
  codeset | UTF-8

locale: ia.utf8         archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Interlingua locale
    email | mardy@despammed.com
 language | Interlingua
 revision | 1.0
     date | 2003-11-25
  codeset | UTF-8

locale: id_ID           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Indonesian locale for Indonesia
    email | bug-glibc-locales@gnu.org
 language | Indonesian
territory | Indonesia
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: id_ID.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Indonesian locale for Indonesia
    email | bug-glibc-locales@gnu.org
 language | Indonesian
territory | Indonesia
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: id_ID.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Indonesian locale for Indonesia
    email | bug-glibc-locales@gnu.org
 language | Indonesian
territory | Indonesia
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: ig_NG           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Igbo locale for Nigeria
    email | pablo@mandriva.com
 language | Igbo
territory | Nigeria
 revision | 0.2
     date | 2005-12-14
  codeset | UTF-8

locale: ig_NG.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Igbo locale for Nigeria
    email | pablo@mandriva.com
 language | Igbo
territory | Nigeria
 revision | 0.2
     date | 2005-12-14
  codeset | UTF-8

locale: ik_CA           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Inupiaq locale for Canada
    email | pablo@mandriva.com
 language | Inupiaq
territory | Canada
 revision | 0.2
     date | 2004-08-01
  codeset | UTF-8

locale: ik_CA.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Inupiaq locale for Canada
    email | pablo@mandriva.com
 language | Inupiaq
territory | Canada
 revision | 0.2
     date | 2004-08-01
  codeset | UTF-8

locale: is_IS           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Icelandic locale for Iceland
   source | Stadlarad I'slands
  address | Keldnaholt-ITI', IS-112 Reykjavi'k, Iceland
    email | bug-glibc-locales@gnu.org
 language | Icelandic
territory | Iceland
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: is_IS.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Icelandic locale for Iceland
   source | Stadlarad I'slands
  address | Keldnaholt-ITI', IS-112 Reykjavi'k, Iceland
    email | bug-glibc-locales@gnu.org
 language | Icelandic
territory | Iceland
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: is_IS.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Icelandic locale for Iceland
   source | Stadlarad I'slands
  address | Keldnaholt-ITI', IS-112 Reykjavi'k, Iceland
    email | bug-glibc-locales@gnu.org
 language | Icelandic
territory | Iceland
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: it_CH           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Italian locale for Switzerland
    email | bug-glibc-locales@gnu.org
 language | Italian
territory | Switzerland
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: it_CH.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Italian locale for Switzerland
    email | bug-glibc-locales@gnu.org
 language | Italian
territory | Switzerland
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: it_CH.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Italian locale for Switzerland
    email | bug-glibc-locales@gnu.org
 language | Italian
territory | Switzerland
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: it_IT           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Italian locale for Italy
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Italian
territory | Italy
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: it_IT@euro      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Italian locale for Italy with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Italian
territory | Italy
 revision | 1.0
     date | 2000-08-20
  codeset | ISO-8859-15

locale: it_IT.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Italian locale for Italy
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Italian
territory | Italy
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: it_IT.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Italian locale for Italy with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Italian
territory | Italy
 revision | 1.0
     date | 2000-08-20
  codeset | ISO-8859-15

locale: it_IT.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Italian locale for Italy
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Italian
territory | Italy
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: iu_CA           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Inuktitut language locale for Nunavut, Canada
  contact | Pablo Saratxaga
    email | pablo@mandriva.com
 language | Inuktitut
territory | CA
 revision | 0.1
     date | 2001-05-04
  codeset | UTF-8

locale: iu_CA.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Inuktitut language locale for Nunavut, Canada
  contact | Pablo Saratxaga
    email | pablo@mandriva.com
 language | Inuktitut
territory | CA
 revision | 0.1
     date | 2001-05-04
  codeset | UTF-8

locale: iw_IL           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Hebrew locale for Israel
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Hebrew
territory | Israel
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-8

locale: iw_IL.iso88598  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Hebrew locale for Israel
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Hebrew
territory | Israel
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-8

locale: iw_IL.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Hebrew locale for Israel
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Hebrew
territory | Israel
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: ja_JP.eucjp     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Japanese language locale for Japan
   source | HANATAKA, Shinya, hanataka@abyss.rim.or.jp
    email | bug-glibc-locales@gnu.org
 language | Japanese
territory | Japan
 revision | 1.0
     date | 2000-07-20
  codeset | EUC-JP

locale: ja_JP.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Japanese language locale for Japan
   source | HANATAKA, Shinya, hanataka@abyss.rim.or.jp
    email | bug-glibc-locales@gnu.org
 language | Japanese
territory | Japan
 revision | 1.0
     date | 2000-07-20
  codeset | UTF-8

locale: ka_GE           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Georgian language locale for Georgia
  contact | Pablo Saratxaga
    email | srtxg@chanae.alphanet.ch
 language | Georgian
territory | Georgia
 revision | 0.6
     date | 2001-01-26
  codeset | GEORGIAN-PS

locale: ka_GE.georgianp archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Georgian language locale for Georgia
  contact | Pablo Saratxaga
    email | srtxg@chanae.alphanet.ch
 language | Georgian
territory | Georgia
 revision | 0.6
     date | 2001-01-26
  codeset | GEORGIAN-PS

locale: ka_GE.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Georgian language locale for Georgia
  contact | Pablo Saratxaga
    email | srtxg@chanae.alphanet.ch
 language | Georgian
territory | Georgia
 revision | 0.6
     date | 2001-01-26
  codeset | UTF-8

locale: kk_KZ           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Kazakh locale for Kazakhstan
   source | NIPI, Kazakhstan Copper Corporation
    email | bug-glibc-locales@gnu.org
 language | Kazakh
territory | Kazakhstan
 revision | 1.0
     date | 2003-06-06
  codeset | RK1048

locale: kk_KZ.rk1048    archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Kazakh locale for Kazakhstan
   source | NIPI, Kazakhstan Copper Corporation
    email | bug-glibc-locales@gnu.org
 language | Kazakh
territory | Kazakhstan
 revision | 1.0
     date | 2003-06-06
  codeset | RK1048

locale: kk_KZ.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Kazakh locale for Kazakhstan
   source | NIPI, Kazakhstan Copper Corporation
    email | bug-glibc-locales@gnu.org
 language | Kazakh
territory | Kazakhstan
 revision | 1.0
     date | 2003-06-06
  codeset | UTF-8

locale: kl_GL           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Greenlandic locale for Greenland
   source | Danish Standards Association
  address | Kollegievej 6, DK-2920 Charlottenlund, Danmark
    email | bug-glibc-locales@gnu.org
 language | Greenlandic
territory | Greenland
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: kl_GL.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Greenlandic locale for Greenland
   source | Danish Standards Association
  address | Kollegievej 6, DK-2920 Charlottenlund, Danmark
    email | bug-glibc-locales@gnu.org
 language | Greenlandic
territory | Greenland
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: kl_GL.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Greenlandic locale for Greenland
   source | Danish Standards Association
  address | Kollegievej 6, DK-2920 Charlottenlund, Danmark
    email | bug-glibc-locales@gnu.org
 language | Greenlandic
territory | Greenland
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: km_KH           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Khmer locale for Cambodia
  contact | Jens Herden at: jens@khmeros.info
    email | bug-glibc-locales@gnu.org
 language | Khmer
territory | Cambodia
 revision | 1.0
     date | 2005-3-15
  codeset | UTF-8

locale: km_KH.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Khmer locale for Cambodia
  contact | Jens Herden at: jens@khmeros.info
    email | bug-glibc-locales@gnu.org
 language | Khmer
territory | Cambodia
 revision | 1.0
     date | 2005-3-15
  codeset | UTF-8

locale: kn_IN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Kannada language locale for India
   source | IndLinux.org
    email | bug-glibc-locales@gnu.org
 language | Kannada
territory | India
 revision | 0.1
     date | 2002-11-28
  codeset | UTF-8

locale: kn_IN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Kannada language locale for India
   source | IndLinux.org
    email | bug-glibc-locales@gnu.org
 language | Kannada
territory | India
 revision | 0.1
     date | 2002-11-28
  codeset | UTF-8

locale: ko_KR.euckr     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Korean locale for Republic of Korea
    email | bug-glibc-locales@gnu.org
 language | Korean
territory | Republic of Korea
 revision | 1.1
     date | 2000-11-09
  codeset | EUC-KR

locale: ko_KR.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Korean locale for Republic of Korea
    email | bug-glibc-locales@gnu.org
 language | Korean
territory | Republic of Korea
 revision | 1.1
     date | 2000-11-09
  codeset | UTF-8

locale: ks_IN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Kashmiri language locale for India
   source | Red Hat, Pune
  address | Marisfot III, Marigold Premises, East-Wing, Kalyaninagar, Pune, India-411014
    email | bug-glibc-locales@gnu.org
 language | Kashmiri
territory | India
 revision | 1.0
     date | 2009,April,06
  codeset | UTF-8

locale: ks_IN@devanagar archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Kashmiri(devanagari) language locale for India
    email | ks-gnome-trans-commits@lists.code.indlinux.net
 language | Kashmiri
territory | India
 revision | 0.1
     date | 2008-08-26
  codeset | UTF-8

locale: ks_IN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Kashmiri language locale for India
   source | Red Hat, Pune
  address | Marisfot III, Marigold Premises, East-Wing, Kalyaninagar, Pune, India-411014
    email | bug-glibc-locales@gnu.org
 language | Kashmiri
territory | India
 revision | 1.0
     date | 2009,April,06
  codeset | UTF-8

locale: ks_IN.utf8@deva archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Kashmiri(devanagari) language locale for India
    email | ks-gnome-trans-commits@lists.code.indlinux.net
 language | Kashmiri
territory | India
 revision | 0.1
     date | 2008-08-26
  codeset | UTF-8

locale: ku_TR           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Kurdish (latin) locale for Turkey
   source | Kader DILSIZ
  contact | Kader DILSIZ, Pablo Saratxaga
    email | kader@ikader.com, pablo@mandrakesoft.com
 language | Kurdish
territory | Turkey
 revision | 0.2
     date | 2005-04-24
  codeset | ISO-8859-9

locale: ku_TR.iso88599  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Kurdish (latin) locale for Turkey
   source | Kader DILSIZ
  contact | Kader DILSIZ, Pablo Saratxaga
    email | kader@ikader.com, pablo@mandrakesoft.com
 language | Kurdish
territory | Turkey
 revision | 0.2
     date | 2005-04-24
  codeset | ISO-8859-9

locale: ku_TR.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Kurdish (latin) locale for Turkey
   source | Kader DILSIZ
  contact | Kader DILSIZ, Pablo Saratxaga
    email | kader@ikader.com, pablo@mandrakesoft.com
 language | Kurdish
territory | Turkey
 revision | 0.2
     date | 2005-04-24
  codeset | UTF-8

locale: kw_GB           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Cornish locale for Britain
   source | Alastair McKinstry
  address | Cro? L?r, Ballinahalla, Maigh Cuilinn,, Co. Gaillimh, Ireland
    email | bug-glibc-locales@gnu.org
 language | Cornish
territory | Britain
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: kw_GB.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Cornish locale for Britain
   source | Alastair McKinstry
  address | Cro? L?r, Ballinahalla, Maigh Cuilinn,, Co. Gaillimh, Ireland
    email | bug-glibc-locales@gnu.org
 language | Cornish
territory | Britain
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: kw_GB.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Cornish locale for Britain
   source | Alastair McKinstry
  address | Cro? L?r, Ballinahalla, Maigh Cuilinn,, Co. Gaillimh, Ireland
    email | bug-glibc-locales@gnu.org
 language | Cornish
territory | Britain
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: ky_KG           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Kyrgyz Language Locale for Kyrgyzstan
   source | Timur Jamakeev
  contact | Pablo Saratxaga, Timur Jamakeev
    email | srtxg@mandrakesoft.com, ztimur@mail.ru
 language | Kyrgyz
territory | Kyrgyzstan
 revision | 0.2
     date | 2004-10-14
  codeset | UTF-8

locale: ky_KG.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Kyrgyz Language Locale for Kyrgyzstan
   source | Timur Jamakeev
  contact | Pablo Saratxaga, Timur Jamakeev
    email | srtxg@mandrakesoft.com, ztimur@mail.ru
 language | Kyrgyz
territory | Kyrgyzstan
 revision | 0.2
     date | 2004-10-14
  codeset | UTF-8

locale: lg_UG           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Luganda locale for Uganda
   source | Akademe ya Luganda
  address | co P.O. Box 5190 Kampala, Uganda
  contact | Kizito Birabwa
    email | kompyuta@kizito.uklinux.net
 language | Luganda
territory | Uganda
 revision | 1.0
     date | 2001-11-04
  codeset | ISO-8859-10

locale: lg_UG.iso885910 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Luganda locale for Uganda
   source | Akademe ya Luganda
  address | co P.O. Box 5190 Kampala, Uganda
  contact | Kizito Birabwa
    email | kompyuta@kizito.uklinux.net
 language | Luganda
territory | Uganda
 revision | 1.0
     date | 2001-11-04
  codeset | ISO-8859-10

locale: lg_UG.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Luganda locale for Uganda
   source | Akademe ya Luganda
  address | co P.O. Box 5190 Kampala, Uganda
  contact | Kizito Birabwa
    email | kompyuta@kizito.uklinux.net
 language | Luganda
territory | Uganda
 revision | 1.0
     date | 2001-11-04
  codeset | UTF-8

locale: li_BE           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Limburgish Language Locale for Belgium
   source | information from Kenneth Christiansen
  contact | Kenneth Christiansen, Pablo Saratxaga
    email | kenneth@gnu.org, pablo@mandriva.com
 language | li
territory | BE
 revision | 0.1
     date | 2003-11-30
  codeset | UTF-8

locale: li_BE.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Limburgish Language Locale for Belgium
   source | information from Kenneth Christiansen
  contact | Kenneth Christiansen, Pablo Saratxaga
    email | kenneth@gnu.org, pablo@mandriva.com
 language | li
territory | BE
 revision | 0.1
     date | 2003-11-30
  codeset | UTF-8

locale: li_NL           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Limburgish Language Locale for the Netherlands
   source | information from Kenneth Christiansen
  contact | Kenneth Christiansen, Pablo Saratxaga
    email | kenneth@gnu.org, pablo@mandriva.com
 language | li
territory | NL
 revision | 0.1
     date | 2003-11-30
  codeset | UTF-8

locale: li_NL.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Limburgish Language Locale for the Netherlands
   source | information from Kenneth Christiansen
  contact | Kenneth Christiansen, Pablo Saratxaga
    email | kenneth@gnu.org, pablo@mandriva.com
 language | li
territory | NL
 revision | 0.1
     date | 2003-11-30
  codeset | UTF-8

locale: lo_LA           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Lao locale for Laos
  contact | Anousak Souphavanh at: anousak@muanglao.com
    email | bug-glibc-locales@gnu.org
 language | Lao
territory | Laos
 revision | 1.0
     date | 2003-4-1
  codeset | UTF-8

locale: lo_LA.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Lao locale for Laos
  contact | Anousak Souphavanh at: anousak@muanglao.com
    email | bug-glibc-locales@gnu.org
 language | Lao
territory | Laos
 revision | 1.0
     date | 2003-4-1
  codeset | UTF-8

locale: lt_LT           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Lithuanian locale for Lithuania
   source | Lithuanian Computer Society and
  address | P.O Box 1147, Donelaicio 60, 3000 Kaunas, Lithuania
    email | bug-glibc-locales@gnu.org
 language | Lithuanian
territory | Lithuania
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-13

locale: lt_LT.iso885913 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Lithuanian locale for Lithuania
   source | Lithuanian Computer Society and
  address | P.O Box 1147, Donelaicio 60, 3000 Kaunas, Lithuania
    email | bug-glibc-locales@gnu.org
 language | Lithuanian
territory | Lithuania
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-13

locale: lt_LT.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Lithuanian locale for Lithuania
   source | Lithuanian Computer Society and
  address | P.O Box 1147, Donelaicio 60, 3000 Kaunas, Lithuania
    email | bug-glibc-locales@gnu.org
 language | Lithuanian
territory | Lithuania
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: lv_LV           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Latvian locale for Latvia
   source | Latvian Standard LVS 24-93
  address | LU MII, Rainis boul. 29, LV-1459 Riga, Latvia
    email | bug-glibc-locales@gnu.org
 language | Latvian
territory | Latvia
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-13

locale: lv_LV.iso885913 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Latvian locale for Latvia
   source | Latvian Standard LVS 24-93
  address | LU MII, Rainis boul. 29, LV-1459 Riga, Latvia
    email | bug-glibc-locales@gnu.org
 language | Latvian
territory | Latvia
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-13

locale: lv_LV.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Latvian locale for Latvia
   source | Latvian Standard LVS 24-93
  address | LU MII, Rainis boul. 29, LV-1459 Riga, Latvia
    email | bug-glibc-locales@gnu.org
 language | Latvian
territory | Latvia
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: mai_IN          archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Maithili language locale for India
   source | Maithili Computing Research Center, Pune, India
  address | B-3302, Lunkad Daffodills, Viman Nagar, Pune, India
    email | rajeshkajha@yahoo.com
 language | Maithili
territory | India
 revision | 1.0
     date | 2006-11-01
  codeset | UTF-8

locale: mai_IN.utf8     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Maithili language locale for India
   source | Maithili Computing Research Center, Pune, India
  address | B-3302, Lunkad Daffodills, Viman Nagar, Pune, India
    email | rajeshkajha@yahoo.com
 language | Maithili
territory | India
 revision | 1.0
     date | 2006-11-01
  codeset | UTF-8

locale: mg_MG           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Malagasy locale for Madagascar
   source | The Debian Project modified by GNULinux Malagasy
  contact | Rado Ramarotafika,Do-Risika RAFIEFERANTSIARONJY
    email | rado@linuxmg.org,dourix@free.fr
 language | Malagasy
territory | Madagascar
 revision | 1.1
     date | 2005-02-02
  codeset | ISO-8859-15

locale: mg_MG.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Malagasy locale for Madagascar
   source | The Debian Project modified by GNULinux Malagasy
  contact | Rado Ramarotafika,Do-Risika RAFIEFERANTSIARONJY
    email | rado@linuxmg.org,dourix@free.fr
 language | Malagasy
territory | Madagascar
 revision | 1.1
     date | 2005-02-02
  codeset | ISO-8859-15

locale: mg_MG.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Malagasy locale for Madagascar
   source | The Debian Project modified by GNULinux Malagasy
  contact | Rado Ramarotafika,Do-Risika RAFIEFERANTSIARONJY
    email | rado@linuxmg.org,dourix@free.fr
 language | Malagasy
territory | Madagascar
 revision | 1.1
     date | 2005-02-02
  codeset | UTF-8

locale: mi_NZ           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Maori language locale for New Zealand
   source | James Gasson
  contact | James Gasson, Pablo Saratxaga
    email | james.gasson@clear.net.nz, pablo@mandrakesoft.com
 language | Maori
territory | New Zealand
 revision | 0.3
     date | 2001-01-28
  codeset | ISO-8859-13

locale: mi_NZ.iso885913 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Maori language locale for New Zealand
   source | James Gasson
  contact | James Gasson, Pablo Saratxaga
    email | james.gasson@clear.net.nz, pablo@mandrakesoft.com
 language | Maori
territory | New Zealand
 revision | 0.3
     date | 2001-01-28
  codeset | ISO-8859-13

locale: mi_NZ.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Maori language locale for New Zealand
   source | James Gasson
  contact | James Gasson, Pablo Saratxaga
    email | james.gasson@clear.net.nz, pablo@mandrakesoft.com
 language | Maori
territory | New Zealand
 revision | 0.3
     date | 2001-01-28
  codeset | UTF-8

locale: mk_MK           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Macedonian locale for Macedonia
  contact | Damjan Georgievski
    email | bug-glibc-locales@gnu.org
 language | Macedonian
territory | Macedonia
 revision | 2.2
     date | 2006-09-12
  codeset | ISO-8859-5

locale: mk_MK.iso88595  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Macedonian locale for Macedonia
  contact | Damjan Georgievski
    email | bug-glibc-locales@gnu.org
 language | Macedonian
territory | Macedonia
 revision | 2.2
     date | 2006-09-12
  codeset | ISO-8859-5

locale: mk_MK.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Macedonian locale for Macedonia
  contact | Damjan Georgievski
    email | bug-glibc-locales@gnu.org
 language | Macedonian
territory | Macedonia
 revision | 2.2
     date | 2006-09-12
  codeset | UTF-8

locale: ml_IN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Malayalam language locale for India
   source | Free Software Foundation of India, Trivandrum
    email | bug-glibc-locales@gnu.org
 language | Malayalam
territory | India
 revision | 0.1
     date | 2003-February-01
  codeset | UTF-8

locale: ml_IN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Malayalam language locale for India
   source | Free Software Foundation of India, Trivandrum
    email | bug-glibc-locales@gnu.org
 language | Malayalam
territory | India
 revision | 0.1
     date | 2003-February-01
  codeset | UTF-8

locale: mn_MN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Mongolian locale for Mongolia
   source | Sanlig Badral
    email | badral@chinggis.com
 language | Mongolian
territory | Mongolia
 audience | general
application | GNU locale
 revision | 1.0
     date | 2005-05-21
  codeset | UTF-8

locale: mn_MN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Mongolian locale for Mongolia
   source | Sanlig Badral
    email | badral@chinggis.com
 language | Mongolian
territory | Mongolia
 audience | general
application | GNU locale
 revision | 1.0
     date | 2005-05-21
  codeset | UTF-8

locale: mr_IN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Marathi language locale for India
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Marathi
territory | India
 revision | 1.0
     date | 2000-07-21
  codeset | UTF-8

locale: mr_IN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Marathi language locale for India
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Marathi
territory | India
 revision | 1.0
     date | 2000-07-21
  codeset | UTF-8

locale: ms_MY           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Malay language locale for Malaysia
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org, sebol@ikhlas.com
 language | Malay
territory | Malaysia
 revision | 0.92b
     date | 2001, December, 10
  codeset | ISO-8859-1

locale: ms_MY.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Malay language locale for Malaysia
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org, sebol@ikhlas.com
 language | Malay
territory | Malaysia
 revision | 0.92b
     date | 2001, December, 10
  codeset | ISO-8859-1

locale: ms_MY.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Malay language locale for Malaysia
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org, sebol@ikhlas.com
 language | Malay
territory | Malaysia
 revision | 0.92b
     date | 2001, December, 10
  codeset | UTF-8

locale: mt_MT           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Maltese language locale for Malta
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Maltese
territory | malta
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-3

locale: mt_MT.iso88593  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Maltese language locale for Malta
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Maltese
territory | malta
 revision | 1.0
     date | 2000-07-20
  codeset | ISO-8859-3

locale: mt_MT.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Maltese language locale for Malta
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Maltese
territory | malta
 revision | 1.0
     date | 2000-07-20
  codeset | UTF-8

locale: my_MM           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Burmese language locale for Myanmar
   source | ThanLwinSoft http:/www.thanlwinsoft.org
  address | Yangon, Myanmar
  contact | Keith Stribley
    email | devel@thanlwinsoft.org
 language | Burmese
territory | Myanmar
 revision | 1.3
     date | 2009-10-02
  codeset | UTF-8

locale: my_MM.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Burmese language locale for Myanmar
   source | ThanLwinSoft http:/www.thanlwinsoft.org
  address | Yangon, Myanmar
  contact | Keith Stribley
    email | devel@thanlwinsoft.org
 language | Burmese
territory | Myanmar
 revision | 1.3
     date | 2009-10-02
  codeset | UTF-8

locale: nan_TW@latin    archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Minnan language locale for Taiwan
  contact | Arne Goetje
    email | arne@canonical.com
 language | Minnan
territory | Taiwan
 revision | 0.1
     date | 2008-06-16
  codeset | UTF-8

locale: nan_TW.utf8@lat archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Minnan language locale for Taiwan
  contact | Arne Goetje
    email | arne@canonical.com
 language | Minnan
territory | Taiwan
 revision | 0.1
     date | 2008-06-16
  codeset | UTF-8

locale: nb_NO           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Norwegian (Bokmal) locale for Norway
   source | Norsk Standardiseringsforbund
  address | University Library, Drammensveien 41, N-9242 Oslo, Norge
    email | bug-glibc-locales@gnu.org
 language | Norwegian, Bokm?l
territory | Norway
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: nb_NO.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Norwegian (Bokmal) locale for Norway
   source | Norsk Standardiseringsforbund
  address | University Library, Drammensveien 41, N-9242 Oslo, Norge
    email | bug-glibc-locales@gnu.org
 language | Norwegian, Bokm?l
territory | Norway
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: nb_NO.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Norwegian (Bokmal) locale for Norway
   source | Norsk Standardiseringsforbund
  address | University Library, Drammensveien 41, N-9242 Oslo, Norge
    email | bug-glibc-locales@gnu.org
 language | Norwegian, Bokmål
territory | Norway
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: nds_DE          archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Low(lands) Saxon Language Locale for Germany
   source | information from Kenneth Christiansen
  contact | Kenneth Christiansen, Pablo Saratxaga
    email | kenneth@gnu.org, pablo@mandrakesoft.com
 language | nds
territory | DE
 revision | 0.1
     date | 2003-11-30
  codeset | UTF-8

locale: nds_DE.utf8     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Low(lands) Saxon Language Locale for Germany
   source | information from Kenneth Christiansen
  contact | Kenneth Christiansen, Pablo Saratxaga
    email | kenneth@gnu.org, pablo@mandrakesoft.com
 language | nds
territory | DE
 revision | 0.1
     date | 2003-11-30
  codeset | UTF-8

locale: nds_NL          archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Low(lands) Saxon Language Locale for the Netherlands
   source | information from Kenneth Christiansen
  contact | Kenneth Christiansen, Pablo Saratxaga
    email | kenneth@gnu.org, pablo@mandrakesoft.com
 language | nds
territory | NL
 revision | 0.1
     date | 2003-11-30
  codeset | UTF-8

locale: nds_NL.utf8     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Low(lands) Saxon Language Locale for the Netherlands
   source | information from Kenneth Christiansen
  contact | Kenneth Christiansen, Pablo Saratxaga
    email | kenneth@gnu.org, pablo@mandrakesoft.com
 language | nds
territory | NL
 revision | 0.1
     date | 2003-11-30
  codeset | UTF-8

locale: ne_NP           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Nepali language locale for Nepal
   source | Madan Puraskar Pustakalaya
  address | Rato Bangala, Patan Dhoka,Lalitpur,Nepal
    email | info@mpp.org.np
telephone | 977-1-5521393
 language | Nepali
territory | Nepal
 revision | 1.1
     date | 2003-05-12
  codeset | UTF-8

locale: ne_NP.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Nepali language locale for Nepal
   source | Madan Puraskar Pustakalaya
  address | Rato Bangala, Patan Dhoka,Lalitpur,Nepal
    email | info@mpp.org.np
telephone | 977-1-5521393
 language | Nepali
territory | Nepal
 revision | 1.1
     date | 2003-05-12
  codeset | UTF-8

locale: nl_AW           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Dutch language locale for Aruba
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Dutch
territory | Aruba
 revision | 1.0
     date | 2008-09-16
  codeset | UTF-8

locale: nl_AW.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Dutch language locale for Aruba
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Dutch
territory | Aruba
 revision | 1.0
     date | 2008-09-16
  codeset | UTF-8

locale: nl_BE           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Dutch locale for Belgium
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Dutch
territory | Belgium
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: nl_BE@euro      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Dutch locale for Belgium with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Dutch
territory | Belgium
 revision | 1.0
     date | 2000-08-21
  codeset | ISO-8859-15

locale: nl_BE.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Dutch locale for Belgium
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Dutch
territory | Belgium
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: nl_BE.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Dutch locale for Belgium with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Dutch
territory | Belgium
 revision | 1.0
     date | 2000-08-21
  codeset | ISO-8859-15

locale: nl_BE.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Dutch locale for Belgium
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Dutch
territory | Belgium
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: nl_NL           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Dutch locale for the Netherlands
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Dutch
territory | Netherlands
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: nl_NL@euro      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Dutch locale for the Netherlands with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Dutch
territory | Netherlands
 revision | 1.0
     date | 2000-08-20
  codeset | ISO-8859-15

locale: nl_NL.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Dutch locale for the Netherlands
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Dutch
territory | Netherlands
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: nl_NL.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Dutch locale for the Netherlands with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Dutch
territory | Netherlands
 revision | 1.0
     date | 2000-08-20
  codeset | ISO-8859-15

locale: nl_NL.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Dutch locale for the Netherlands
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Dutch
territory | Netherlands
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: nn_NO           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Nynorsk language locale for Norway
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Norwegian, Nynorsk
territory | Norway
 revision | 1.0
     date | 2000-08-31
  codeset | ISO-8859-1

locale: nn_NO.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Nynorsk language locale for Norway
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Norwegian, Nynorsk
territory | Norway
 revision | 1.0
     date | 2000-08-31
  codeset | ISO-8859-1

locale: nn_NO.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Nynorsk language locale for Norway
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Norwegian, Nynorsk
territory | Norway
 revision | 1.0
     date | 2000-08-31
  codeset | UTF-8

locale: nr_ZA           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Southern Ndebele locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | PO Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Southern Ndebele
territory | South Africa
 revision | 0.3
     date | 2005-10-13
  codeset | UTF-8

locale: nr_ZA.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Southern Ndebele locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | PO Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Southern Ndebele
territory | South Africa
 revision | 0.3
     date | 2005-10-13
  codeset | UTF-8

locale: nso_ZA          archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Northern Sotho locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | PO Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Northern Sotho
territory | South Africa
 revision | 0.3
     date | 2005-10-13
  codeset | UTF-8

locale: nso_ZA.utf8     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Northern Sotho locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | PO Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Northern Sotho
territory | South Africa
 revision | 0.3
     date | 2005-10-13
  codeset | UTF-8

locale: oc_FR           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Occitan Language Locale for France
   source | RAP
  address | Los Genets, 12290 Pont de Salars
  contact | Jean-Paul Fraysse
    email | Jean-Paul.Fraysse@wanadoo.fr
telephone | +33 -565743131 
 language | Occitan
territory | France
 revision | 0.2
     date | 2000-11-15
  codeset | ISO-8859-1

locale: oc_FR.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Occitan Language Locale for France
   source | RAP
  address | Los Genets, 12290 Pont de Salars
  contact | Jean-Paul Fraysse
    email | Jean-Paul.Fraysse@wanadoo.fr
telephone | +33 -565743131 
 language | Occitan
territory | France
 revision | 0.2
     date | 2000-11-15
  codeset | ISO-8859-1

locale: oc_FR.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Occitan Language Locale for France
   source | RAP
  address | Los Genets, 12290 Pont de Salars
  contact | Jean-Paul Fraysse
    email | Jean-Paul.Fraysse@wanadoo.fr
telephone | +33 -565743131 
 language | Occitan
territory | France
 revision | 0.2
     date | 2000-11-15
  codeset | UTF-8

locale: om_ET           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Oromo language locale for Ethiopia.
   source | Ge'ez Frontier Foundation & Sagalee Oromoo Publishing Co. Inc.
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | om
territory | ET
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: om_ET.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Oromo language locale for Ethiopia.
   source | Ge'ez Frontier Foundation & Sagalee Oromoo Publishing Co. Inc.
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | om
territory | ET
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: om_KE           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Oromo language locale for Kenya.
   source | Ge'ez Frontier Foundation & Sagalee Oromoo Publishing Co. Inc.
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | om
territory | KE
 revision | 0.20
     date | 2003-07-05
  codeset | ISO-8859-1

locale: om_KE.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Oromo language locale for Kenya.
   source | Ge'ez Frontier Foundation & Sagalee Oromoo Publishing Co. Inc.
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | om
territory | KE
 revision | 0.20
     date | 2003-07-05
  codeset | ISO-8859-1

locale: om_KE.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Oromo language locale for Kenya.
   source | Ge'ez Frontier Foundation & Sagalee Oromoo Publishing Co. Inc.
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | om
territory | KE
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: or_IN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Oriya language locale for India
   source | IBM AP Linux Technology Center, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc@gnu.org
 language | Oriya
territory | India
 revision | 1.0
     date | 2006-05-25
  codeset | UTF-8

locale: or_IN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Oriya language locale for India
   source | IBM AP Linux Technology Center, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc@gnu.org
 language | Oriya
territory | India
 revision | 1.0
     date | 2006-05-25
  codeset | UTF-8

locale: pa_IN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Punjabi language locale for Indian Punjabi(Gurmukhi)
   source | IndLinux.org
    email | bug-glibc-locales@gnu.org
 language | Punjabi
territory | India
 revision | 0.2
     date | 2004-09-30
  codeset | UTF-8

locale: pa_IN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Punjabi language locale for Indian Punjabi(Gurmukhi)
   source | IndLinux.org
    email | bug-glibc-locales@gnu.org
 language | Punjabi
territory | India
 revision | 0.2
     date | 2004-09-30
  codeset | UTF-8

locale: pap_AN          archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Papiamento Language for the (Netherland) Antilles
   source | informations from native speaker
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | pap
territory | AN
 revision | 0.2
     date | 2000-11-15
  codeset | UTF-8

locale: pap_AN.utf8     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Papiamento Language for the (Netherland) Antilles
   source | informations from native speaker
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | pap
territory | AN
 revision | 0.2
     date | 2000-11-15
  codeset | UTF-8

locale: pa_PK           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Punjabi (Shahmukhi) Language Locale for Pakistan
    email | bug-glibc-locales@gnu.org
 language | Punjabi (Shahmukhi)
territory | Pakistan
 revision | 0.3
     date | 2000-07-11
  codeset | UTF-8

locale: pa_PK.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Punjabi (Shahmukhi) Language Locale for Pakistan
    email | bug-glibc-locales@gnu.org
 language | Punjabi (Shahmukhi)
territory | Pakistan
 revision | 0.3
     date | 2000-07-11
  codeset | UTF-8

locale: pl_PL           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Polish locale for Poland
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Polish
territory | Poland
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-2

locale: pl_PL.iso88592  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Polish locale for Poland
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Polish
territory | Poland
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-2

locale: pl_PL.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Polish locale for Poland
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Polish
territory | Poland
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: ps_AF           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Pashto locale for Afghanistan
   source | Nasir Gulzade
  address | see e-mail.
  contact | Nasir Gulzade
    email | nasirgulzade@hotmail.com
telephone | +93 700530286
 language | Pashto
territory | Afghanistan
 revision | 0.2
     date | 2009-01-16
  codeset | UTF-8

locale: ps_AF.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Pashto locale for Afghanistan
   source | Nasir Gulzade
  address | see e-mail.
  contact | Nasir Gulzade
    email | nasirgulzade@hotmail.com
telephone | +93 700530286
 language | Pashto
territory | Afghanistan
 revision | 0.2
     date | 2009-01-16
  codeset | UTF-8

locale: pt_BR           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Portuguese locale for Brasil
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Portuguese
territory | Brasil
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: pt_BR.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Portuguese locale for Brasil
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Portuguese
territory | Brasil
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: pt_BR.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Portuguese locale for Brasil
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Portuguese
territory | Brasil
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: pt_PT           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Portuguese locale for Portugal
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Portuguese
territory | Portugal
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: pt_PT@euro      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Portuguese locale for Portugal with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Portuguese
territory | Portugal
 revision | 1.0
     date | 2000-08-20
  codeset | ISO-8859-15

locale: pt_PT.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Portuguese locale for Portugal
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Portuguese
territory | Portugal
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: pt_PT.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Portuguese locale for Portugal with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Portuguese
territory | Portugal
 revision | 1.0
     date | 2000-08-20
  codeset | ISO-8859-15

locale: pt_PT.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Portuguese locale for Portugal
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Portuguese
territory | Portugal
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: ro_RO           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Romanian locale for Romania
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Romanian
territory | Romania
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-2

locale: ro_RO.iso88592  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Romanian locale for Romania
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Romanian
territory | Romania
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-2

locale: ro_RO.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Romanian locale for Romania
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Romanian
territory | Romania
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: ru_RU           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Russian locale for Russia
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Russian
territory | Russia
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-5

locale: ru_RU.cp1251    archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Russian locale for Russia
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Russian
territory | Russia
 revision | 1.0
     date | 2000-06-29
  codeset | CP1251

locale: ru_RU.iso88595  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Russian locale for Russia
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Russian
territory | Russia
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-5

locale: ru_RU.koi8r     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Russian locale for Russia
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Russian
territory | Russia
 revision | 1.0
     date | 2000-06-29
  codeset | KOI8-R

locale: ru_RU.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Russian locale for Russia
   source | RAP
  address | Sankt Jorgens Alle 8, DK-1615 Kobenhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Russian
territory | Russia
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: ru_UA           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Russian locale for Ukraine
   source | RFC 2319
    email | bug-glibc-locales@gnu.org
 language | Russian
territory | Ukraine
 revision | 1.0
     date | 2000-06-29
  codeset | KOI8-U

locale: ru_UA.koi8u     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Russian locale for Ukraine
   source | RFC 2319
    email | bug-glibc-locales@gnu.org
 language | Russian
territory | Ukraine
 revision | 1.0
     date | 2000-06-29
  codeset | KOI8-U

locale: ru_UA.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Russian locale for Ukraine
   source | RFC 2319
    email | bug-glibc-locales@gnu.org
 language | Russian
territory | Ukraine
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: rw_RW           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Kinyarwanda language locale for Rwanda
   source | Rwanda
  address | Rwanda, Africa
  contact | Steve Murphy
    email | murf@e-tools.com
telephone | 1-307-754-5675
      fax | 1-307-754-5675
 language | Kinyarwanda
territory | Rwanda
 revision | 1.0
     date | 2004-02-24
  codeset | UTF-8

locale: rw_RW.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Kinyarwanda language locale for Rwanda
   source | Rwanda
  address | Rwanda, Africa
  contact | Steve Murphy
    email | murf@e-tools.com
telephone | 1-307-754-5675
      fax | 1-307-754-5675
 language | Kinyarwanda
territory | Rwanda
 revision | 1.0
     date | 2004-02-24
  codeset | UTF-8

locale: sa_IN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Sanskrit language locale for India
   source | The Debian project
  contact | Christian Perrier
    email | bubulle@debian.org
 language | Sanskrit
territory | India
 revision | 1.0
     date | 2005-09-25
  codeset | UTF-8

locale: sa_IN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Sanskrit language locale for India
   source | The Debian project
  contact | Christian Perrier
    email | bubulle@debian.org
 language | Sanskrit
territory | India
 revision | 1.0
     date | 2005-09-25
  codeset | UTF-8

locale: sc_IT           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Sardinian locale for Italy
  contact | Pablo Saratxaga
    email | pablo@mandriva.com
 language | Sardinian
territory | Italy
 revision | 0.1
     date | 2004-05-26
  codeset | UTF-8

locale: sc_IT.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Sardinian locale for Italy
  contact | Pablo Saratxaga
    email | pablo@mandriva.com
 language | Sardinian
territory | Italy
 revision | 0.1
     date | 2004-05-26
  codeset | UTF-8

locale: sd_IN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Sindhi language locale for India
   source | Red Hat, Pune
  address | Marisfot III, Marigold Premises, East-Wing, Kalyaninagar, Pune, India-411014
    email | bug-glibc-locales@gnu.org
 language | Sindhi
territory | India
 revision | 1.0
     date | 2008,September,09
  codeset | UTF-8

locale: sd_IN@devanagar archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Sindhi language locale for India
   source | Red Hat, Pune
  address | Marisfot III, Marigold Premises, East-Wing, Kalyaninagar, Pune, India-411014
    email | bug-glibc-locales@gnu.org
 language | Sindhi
territory | India
 revision | 1.0
     date | 2008-08-26
  codeset | UTF-8

locale: sd_IN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Sindhi language locale for India
   source | Red Hat, Pune
  address | Marisfot III, Marigold Premises, East-Wing, Kalyaninagar, Pune, India-411014
    email | bug-glibc-locales@gnu.org
 language | Sindhi
territory | India
 revision | 1.0
     date | 2008,September,09
  codeset | UTF-8

locale: sd_IN.utf8@deva archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Sindhi language locale for India
   source | Red Hat, Pune
  address | Marisfot III, Marigold Premises, East-Wing, Kalyaninagar, Pune, India-411014
    email | bug-glibc-locales@gnu.org
 language | Sindhi
territory | India
 revision | 1.0
     date | 2008-08-26
  codeset | UTF-8

locale: se_NO           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Northern Saami language locale for Norway
   source | http:/www.hum.uit.noatrondloc.html
  contact | B?rre Gaup
    email | boerre.gaup@pc.nu
 language | Northern Saami
territory | Norway
 revision | 0.1
     date | 2001-11-09
  codeset | UTF-8

locale: se_NO.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Northern Saami language locale for Norway
   source | http:/www.hum.uit.noatrondloc.html
  contact | B?rre Gaup
    email | boerre.gaup@pc.nu
 language | Northern Saami
territory | Norway
 revision | 0.1
     date | 2001-11-09
  codeset | UTF-8

locale: shs_CA          archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Secwepemctsin locale for Canada
   source | Neskie Manuel
  address | 745 Ska-Hiish Dr, Chase BC V0E 1M3
    email | bug-glibc-locales@gnu.org
 language | Secwepemctsin
territory | Canada
 revision | 1.0
     date | 2008-01-15
  codeset | UTF-8

locale: shs_CA.utf8     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Secwepemctsin locale for Canada
   source | Neskie Manuel
  address | 745 Ska-Hiish Dr, Chase BC V0E 1M3
    email | bug-glibc-locales@gnu.org
 language | Secwepemctsin
territory | Canada
 revision | 1.0
     date | 2008-01-15
  codeset | UTF-8

locale: sid_ET          archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Sidama language locale for Ethiopia.
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | sid
territory | ET
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: sid_ET.utf8     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Sidama language locale for Ethiopia.
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | sid
territory | ET
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: si_LK           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Sinhala language locale for Sri Lanka
   source | Lanka Linux User Group (LKLUG) www.lug.lk, sinhala.linux.lk
    email | libc-locales@sources.redhat.com
 language | Sinhala
territory | Sri Lanka
 revision | 0.9
     date | 2004.10.01
  codeset | UTF-8

locale: si_LK.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Sinhala language locale for Sri Lanka
   source | Lanka Linux User Group (LKLUG) www.lug.lk, sinhala.linux.lk
    email | libc-locales@sources.redhat.com
 language | Sinhala
territory | Sri Lanka
 revision | 0.9
     date | 2004.10.01
  codeset | UTF-8

locale: sk_SK           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Slovak locale for Slovak
  address | Narcisov? 56, SK-821 01 Bratislava, Slovak Republic
    email | bug-glibc-locales@gnu.org
 language | Slovak
territory | Slovak
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-2

locale: sk_SK.iso88592  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Slovak locale for Slovak
  address | Narcisov? 56, SK-821 01 Bratislava, Slovak Republic
    email | bug-glibc-locales@gnu.org
 language | Slovak
territory | Slovak
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-2

locale: sk_SK.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Slovak locale for Slovak
  address | Narcisová 56, SK-821 01 Bratislava, Slovak Republic
    email | bug-glibc-locales@gnu.org
 language | Slovak
territory | Slovak
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: sl_SI           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Slovenian locale for Slovenia
   source | USMMZT
  address | Kotnikova 6,, Ljubljana, Slovenia
    email | bug-glibc-locales@gnu.org
 language | Slovenian
territory | Slovenia
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-2

locale: sl_SI.iso88592  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Slovenian locale for Slovenia
   source | USMMZT
  address | Kotnikova 6,, Ljubljana, Slovenia
    email | bug-glibc-locales@gnu.org
 language | Slovenian
territory | Slovenia
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-2

locale: sl_SI.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Slovenian locale for Slovenia
   source | USMMZT
  address | Kotnikova 6,, Ljubljana, Slovenia
    email | bug-glibc-locales@gnu.org
 language | Slovenian
territory | Slovenia
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: so_DJ           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Somali language locale for Djibouti.
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | so
territory | DJ
 revision | 0.20
     date | 2003-07-05
  codeset | ISO-8859-1

locale: so_DJ.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Somali language locale for Djibouti.
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | so
territory | DJ
 revision | 0.20
     date | 2003-07-05
  codeset | ISO-8859-1

locale: so_DJ.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Somali language locale for Djibouti.
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | so
territory | DJ
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: so_ET           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Somali language locale for Ethiopia
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | so
territory | ET
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: so_ET.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Somali language locale for Ethiopia
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | so
territory | ET
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: so_KE           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Somali language locale for Kenya
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | so
territory | KE
 revision | 0.20
     date | 2003-07-05
  codeset | ISO-8859-1

locale: so_KE.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Somali language locale for Kenya
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | so
territory | KE
 revision | 0.20
     date | 2003-07-05
  codeset | ISO-8859-1

locale: so_KE.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Somali language locale for Kenya
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | so
territory | KE
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: so_SO           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Somali language locale for Somalia
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | so
territory | SO
 revision | 0.20
     date | 2003-07-05
  codeset | ISO-8859-1

locale: so_SO.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Somali language locale for Somalia
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | so
territory | SO
 revision | 0.20
     date | 2003-07-05
  codeset | ISO-8859-1

locale: so_SO.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Somali language locale for Somalia
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | so
territory | SO
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: sq_AL           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Albanian language locale for Albania
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Albanian
territory | Albania
 revision | 1.1
     date | 2004-07-01
  codeset | ISO-8859-1

locale: sq_AL.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Albanian language locale for Albania
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Albanian
territory | Albania
 revision | 1.1
     date | 2004-07-01
  codeset | ISO-8859-1

locale: sq_AL.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Albanian language locale for Albania
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Albanian
territory | Albania
 revision | 1.1
     date | 2004-07-01
  codeset | UTF-8

locale: sr_ME           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Serbian locale for Montenegro
   source | sr_YU, sr_CS locale
  contact | Danilo Segan
    email | bug-glibc@gnu.org
 language | Serbian
territory | Montenegro
 audience | general
application | GNU locale
 revision | 1.2
     date | 2006-10-11
  codeset | UTF-8

locale: sr_ME.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Serbian locale for Montenegro
   source | sr_YU, sr_CS locale
  contact | Danilo Segan
    email | bug-glibc@gnu.org
 language | Serbian
territory | Montenegro
 audience | general
application | GNU locale
 revision | 1.2
     date | 2006-10-11
  codeset | UTF-8

locale: sr_RS           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Serbian locale for Serbia
   source | sr_YU, sr_CS locale
  contact | Danilo Segan
    email | bug-glibc-locales@gnu.org
 language | Serbian
territory | Serbia
 audience | general
application | GNU locale
 revision | 1.3
     date | 2006-10-09
  codeset | UTF-8

locale: sr_RS@latin     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Serbian Latin locale for Serbia
   source | sr_YU, sr_CS locale
  contact | Danilo Segan
    email | bug-glibc-locales@gnu.org
 language | Serbian
territory | Serbia
 audience | general
application | GNU locale
 revision | 1.3
     date | 2006-10-09
  codeset | UTF-8

locale: sr_RS.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Serbian locale for Serbia
   source | sr_YU, sr_CS locale
  contact | Danilo Segan
    email | bug-glibc-locales@gnu.org
 language | Serbian
territory | Serbia
 audience | general
application | GNU locale
 revision | 1.3
     date | 2006-10-09
  codeset | UTF-8

locale: sr_RS.utf8@lati archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Serbian Latin locale for Serbia
   source | sr_YU, sr_CS locale
  contact | Danilo Segan
    email | bug-glibc-locales@gnu.org
 language | Serbian
territory | Serbia
 audience | general
application | GNU locale
 revision | 1.3
     date | 2006-10-09
  codeset | UTF-8

locale: ss_ZA           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Swati locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | PO Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Swati
territory | South Africa
 revision | 0.3
     date | 2005-10-13
  codeset | UTF-8

locale: ss_ZA.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Swati locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | PO Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Swati
territory | South Africa
 revision | 0.3
     date | 2005-10-13
  codeset | UTF-8

locale: st_ZA           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Sotho locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | PO Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Sotho
territory | South Africa
 revision | 0.3
     date | 2005-10-13
  codeset | ISO-8859-1

locale: st_ZA.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Sotho locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | PO Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Sotho
territory | South Africa
 revision | 0.3
     date | 2005-10-13
  codeset | ISO-8859-1

locale: st_ZA.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Sotho locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | PO Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Sotho
territory | South Africa
 revision | 0.3
     date | 2005-10-13
  codeset | UTF-8

locale: sv_FI           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Swedish locale for Finland
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Swedish
territory | Finland
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: sv_FI@euro      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Swedish locale for Finland with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Swedish
territory | Finland
 revision | 1.0
     date | 2000-08-21
  codeset | ISO-8859-15

locale: sv_FI.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Swedish locale for Finland
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Swedish
territory | Finland
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: sv_FI.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Swedish locale for Finland with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Swedish
territory | Finland
 revision | 1.0
     date | 2000-08-21
  codeset | ISO-8859-15

locale: sv_FI.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Swedish locale for Finland
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Swedish
territory | Finland
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: sv_SE           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Swedish locale for Sweden
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Swedish
territory | Sweden
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: sv_SE.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Swedish locale for Sweden
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Swedish
territory | Sweden
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-1

locale: sv_SE.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Swedish locale for Sweden
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Swedish
territory | Sweden
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-15

locale: sv_SE.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Swedish locale for Sweden
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Swedish
territory | Sweden
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: ta_IN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tamil language locale for India
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Tamil
territory | India
 revision | 1.0
     date | 2000,October,27 (XML source:2000,July,20)
  codeset | UTF-8

locale: ta_IN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tamil language locale for India
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Tamil
territory | India
 revision | 1.0
     date | 2000,October,27 (XML source:2000,July,20)
  codeset | UTF-8

locale: te_IN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Telugu language locale for India
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Telugu
territory | India
 revision | 0.95
     date | 2004-10-05
  codeset | UTF-8

locale: te_IN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Telugu language locale for India
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Telugu
territory | India
 revision | 0.95
     date | 2004-10-05
  codeset | UTF-8

locale: tg_TJ           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tajik language locale for Tajikistan
   source | Roger Kovacs
  contact | Pablo Saratxaga, Roger Kovacs
    email | pablo@mandrakesoft.com, ROGERKO@micromotion.com
 language | Tajik
territory | Tajikistan
 revision | 0.4
     date | 2004-01-09
  codeset | KOI8-T

locale: tg_TJ.koi8t     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tajik language locale for Tajikistan
   source | Roger Kovacs
  contact | Pablo Saratxaga, Roger Kovacs
    email | pablo@mandrakesoft.com, ROGERKO@micromotion.com
 language | Tajik
territory | Tajikistan
 revision | 0.4
     date | 2004-01-09
  codeset | KOI8-T

locale: tg_TJ.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tajik language locale for Tajikistan
   source | Roger Kovacs
  contact | Pablo Saratxaga, Roger Kovacs
    email | pablo@mandrakesoft.com, ROGERKO@micromotion.com
 language | Tajik
territory | Tajikistan
 revision | 0.4
     date | 2004-01-09
  codeset | UTF-8

locale: th_TH           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Thai locale for Thailand
    email | bug-glibc-locales@gnu.org
 language | Thai
territory | Thailand
 revision | 1.0
     date | 2000-06-29
  codeset | TIS-620

locale: th_TH.tis620    archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Thai locale for Thailand
    email | bug-glibc-locales@gnu.org
 language | Thai
territory | Thailand
 revision | 1.0
     date | 2000-06-29
  codeset | TIS-620

locale: th_TH.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Thai locale for Thailand
    email | bug-glibc-locales@gnu.org
 language | Thai
territory | Thailand
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: ti_ER           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tigrigna language locale for Eritrea.
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | ti
territory | ER
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: ti_ER.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tigrigna language locale for Eritrea.
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | ti
territory | ER
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: ti_ET           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tigrigna language locale for Ethiopia.
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | ti
territory | ET
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: ti_ET.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tigrigna language locale for Ethiopia.
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | ti
territory | ET
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: tig_ER          archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tigre language locale for Eritrea
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | tig
territory | ER
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: tig_ER.utf8     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tigre language locale for Eritrea
   source | Ge'ez Frontier Foundation
  address | 7802 Solomon Seal Dr., Springfield, VA 22152, USA
    email | locales@geez.org
 language | tig
territory | ER
 revision | 0.20
     date | 2003-07-05
  codeset | UTF-8

locale: tk_TM           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Turkmen locale for Turkmenistan
   source | Gurban M. Tewekgeli
  contact | Pablo Saratxaga & Gurban M. Tewekgeli
    email | pablo@mandriva.com & gmtavakkoli@yahoo.com
 language | Turkmen
territory | Turkmenistan
 revision | 0.3
     date | 2004-06-08
  codeset | UTF-8

locale: tk_TM.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Turkmen locale for Turkmenistan
   source | Gurban M. Tewekgeli
  contact | Pablo Saratxaga & Gurban M. Tewekgeli
    email | pablo@mandriva.com & gmtavakkoli@yahoo.com
 language | Turkmen
territory | Turkmenistan
 revision | 0.3
     date | 2004-06-08
  codeset | UTF-8

locale: tl_PH           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tagalog language locale for Philippines
   source | Rene Torres
  contact | Rene Torres, Pablo Saratxaga
    email | rgtorre@rocketmail.com, pablo@mandrakesoft.com
 language | Tagalog
territory | Philippines
 revision | 0.2
     date | 2001-01-28
  codeset | ISO-8859-1

locale: tl_PH.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tagalog language locale for Philippines
   source | Rene Torres
  contact | Rene Torres, Pablo Saratxaga
    email | rgtorre@rocketmail.com, pablo@mandrakesoft.com
 language | Tagalog
territory | Philippines
 revision | 0.2
     date | 2001-01-28
  codeset | ISO-8859-1

locale: tl_PH.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tagalog language locale for Philippines
   source | Rene Torres
  contact | Rene Torres, Pablo Saratxaga
    email | rgtorre@rocketmail.com, pablo@mandrakesoft.com
 language | Tagalog
territory | Philippines
 revision | 0.2
     date | 2001-01-28
  codeset | UTF-8

locale: tn_ZA           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tswana locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | PO Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Tswana
territory | South Africa
 revision | 0.4
     date | 2005-10-13
  codeset | UTF-8

locale: tn_ZA.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tswana locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | PO Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Tswana
territory | South Africa
 revision | 0.4
     date | 2005-10-13
  codeset | UTF-8

locale: tr_CY           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Turkish language locale for Cyprus
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Turkish
territory | Cyprus
 revision | 1.0
     date | 2004-10-23
  codeset | ISO-8859-9

locale: tr_CY.iso88599  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Turkish language locale for Cyprus
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Turkish
territory | Cyprus
 revision | 1.0
     date | 2004-10-23
  codeset | ISO-8859-9

locale: tr_CY.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Turkish language locale for Cyprus
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Turkish
territory | Cyprus
 revision | 1.0
     date | 2004-10-23
  codeset | UTF-8

locale: tr_TR           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Turkish locale for Turkey
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Turkish
territory | Turkey
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-9

locale: tr_TR.iso88599  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Turkish locale for Turkey
   source | RAP
  address | Sankt J?rgens Alle 8, DK-1615 K?benhavn V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Turkish
territory | Turkey
 revision | 1.0
     date | 2000-06-29
  codeset | ISO-8859-9

locale: tr_TR.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Turkish locale for Turkey
   source | RAP
  address | Sankt Jørgens Alle 8, DK-1615 København V, Danmark
    email | bug-glibc-locales@gnu.org
 language | Turkish
territory | Turkey
 revision | 1.0
     date | 2000-06-29
  codeset | UTF-8

locale: ts_ZA           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tsonga locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | PO Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Tsonga
territory | South Africa
 revision | 0.3
     date | 2005-10-12
  codeset | UTF-8

locale: ts_ZA.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tsonga locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | PO Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Tsonga
territory | South Africa
 revision | 0.3
     date | 2005-10-12
  codeset | UTF-8

locale: tt_RU@iqtelif.U archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tatar language locale using IQTElif alphabet; for Tatarstan, Russian Federation
  contact | Reshat Sabiq
    email | tatar.iqtelif.i18n@gmail.com
 language | Tatar
territory | Tatarstan, Russian Federation
 revision | 0.1
     date | 2006-10-12
  codeset | UTF-8

locale: tt_RU.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tatar language locale for Russia
   source | Rinat Norkin
  contact | Pablo Saratxaga, Rinat Norkin
    email | pablo@mandrakesoft.com, rinat@taif.ru
 language | Tatar
territory | Russia
 revision | 0.4
     date | 2001-01-28
  codeset | UTF-8

locale: tt_RU.utf8@iqte archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Tatar language locale using IQTElif alphabet; for Tatarstan, Russian Federation
  contact | Reshat Sabiq
    email | tatar.iqtelif.i18n@gmail.com
 language | Tatar
territory | Tatarstan, Russian Federation
 revision | 0.1
     date | 2006-10-12
  codeset | UTF-8

locale: ug_CN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Uyghur locale for China
    email | pablo@mandriva.com
 language | Uyghur
territory | China
 revision | 0.1
     date | 2005-11-08
  codeset | UTF-8

locale: ug_CN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Uyghur locale for China
    email | pablo@mandriva.com
 language | Uyghur
territory | China
 revision | 0.1
     date | 2005-11-08
  codeset | UTF-8

locale: uk_UA           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Ukrainian Language Locale for Ukraine
  contact | GNU libc maintainers
    email | bug-glibc-locales@gnu.org
 language | uk
territory | UA
 audience | general
application | general
abbreviation | ULU-2.1.12
 revision | 2.1.12
     date | 2006-05-20
  codeset | KOI8-U

locale: uk_UA.koi8u     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Ukrainian Language Locale for Ukraine
  contact | GNU libc maintainers
    email | bug-glibc-locales@gnu.org
 language | uk
territory | UA
 audience | general
application | general
abbreviation | ULU-2.1.12
 revision | 2.1.12
     date | 2006-05-20
  codeset | KOI8-U

locale: uk_UA.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Ukrainian Language Locale for Ukraine
  contact | GNU libc maintainers
    email | bug-glibc-locales@gnu.org
 language | uk
territory | UA
 audience | general
application | general
abbreviation | ULU-2.1.12
 revision | 2.1.12
     date | 2006-05-20
  codeset | UTF-8

locale: ur_PK           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Urdu Language Locale for Pakistan
    email | bug-glibc-locales@gnu.org
 language | Urdu
territory | Pakistan
 revision | 0.3
     date | 2000-07-11
  codeset | UTF-8

locale: ur_PK.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Urdu Language Locale for Pakistan
    email | bug-glibc-locales@gnu.org
 language | Urdu
territory | Pakistan
 revision | 0.3
     date | 2000-07-11
  codeset | UTF-8

locale: uz_UZ           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Uzbek (latin) locale for Uzbekistan
   source | Bobir Ismailov
  contact | Bobir Ismailov, Pablo Saratxaga, Mashrab Kuvatov
    email | bobir_is@yahoo.com, pablo@mandrakesoft.com, kmashrab@uni-bremen.de
 language | Uzbek
territory | Uzbekistan
 revision | 0.5
     date | 2003-06-27
  codeset | ISO-8859-1

locale: uz_UZ@cyrillic  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Uzbek (cyrillic) locale for Uzbekistan
   source | Mashrab Kuvatov
  contact | Mashrab Kuvatov, Pablo Saratxaga
    email | kmashrab@uni-bremen.de, pablo@mandrakesoft.com
 language | Uzbek
territory | Uzbekistan
 revision | 0.1
     date | 2003-05-30
  codeset | UTF-8

locale: uz_UZ.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Uzbek (latin) locale for Uzbekistan
   source | Bobir Ismailov
  contact | Bobir Ismailov, Pablo Saratxaga, Mashrab Kuvatov
    email | bobir_is@yahoo.com, pablo@mandrakesoft.com, kmashrab@uni-bremen.de
 language | Uzbek
territory | Uzbekistan
 revision | 0.5
     date | 2003-06-27
  codeset | ISO-8859-1

locale: uz_UZ.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Uzbek (latin) locale for Uzbekistan
   source | Bobir Ismailov
  contact | Bobir Ismailov, Pablo Saratxaga, Mashrab Kuvatov
    email | bobir_is@yahoo.com, pablo@mandrakesoft.com, kmashrab@uni-bremen.de
 language | Uzbek
territory | Uzbekistan
 revision | 0.5
     date | 2003-06-27
  codeset | UTF-8

locale: uz_UZ.utf8@cyri archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Uzbek (cyrillic) locale for Uzbekistan
   source | Mashrab Kuvatov
  contact | Mashrab Kuvatov, Pablo Saratxaga
    email | kmashrab@uni-bremen.de, pablo@mandrakesoft.com
 language | Uzbek
territory | Uzbekistan
 revision | 0.1
     date | 2003-05-30
  codeset | UTF-8

locale: ve_ZA           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Venda locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | PO Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Venda
territory | South Africa
 revision | 0.3
     date | 2005-10-13
  codeset | UTF-8

locale: ve_ZA.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Venda locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | PO Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Venda
territory | South Africa
 revision | 0.3
     date | 2005-10-13
  codeset | UTF-8

locale: vi_VN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Vietnamese language locale for Vietnam
   source | glibc locale and info from vietnamese native speakers
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Vietnamese
territory | Vietnam
 revision | 1.1
     date | 2004-01-09
  codeset | UTF-8

locale: vi_VN.tcvn      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Vietnamese language locale for Vietnam
   source | glibc locale and info from vietnamese native speakers
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Vietnamese
territory | Vietnam
 revision | 1.1
     date | 2004-01-09
  codeset | TCVN5712-1

locale: vi_VN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Vietnamese language locale for Vietnam
   source | glibc locale and info from vietnamese native speakers
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Vietnamese
territory | Vietnam
 revision | 1.1
     date | 2004-01-09
  codeset | UTF-8

locale: wa_BE           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Walloon Language Locale for Belgium
   source | Djan SACRE
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Walloon
territory | Belgium
 revision | 0.9
     date | 2003-08-25
  codeset | ISO-8859-1

locale: wa_BE@euro      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Walloon locale for Belgium with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Walloon
territory | Belgium
 revision | 1.0
     date | 2002-02-23
  codeset | ISO-8859-15

locale: wa_BE.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Walloon Language Locale for Belgium
   source | Djan SACRE
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Walloon
territory | Belgium
 revision | 0.9
     date | 2003-08-25
  codeset | ISO-8859-1

locale: wa_BE.iso885915 archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Walloon locale for Belgium with Euro
   source | Free Software Foundation, Inc.
  address | 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA
    email | bug-glibc-locales@gnu.org
 language | Walloon
territory | Belgium
 revision | 1.0
     date | 2002-02-23
  codeset | ISO-8859-15

locale: wa_BE.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Walloon Language Locale for Belgium
   source | Djan SACRE
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Walloon
territory | Belgium
 revision | 0.9
     date | 2003-08-25
  codeset | UTF-8

locale: wo_SN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Wolof locale for Senegal
   source | The Debian Project
  contact | Christian Perrier
    email | bubulle@debian.org
 language | Wolof
territory | Senegal
 revision | 1.0
     date | 2004-09-08
  codeset | UTF-8

locale: wo_SN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Wolof locale for Senegal
   source | The Debian Project
  contact | Christian Perrier
    email | bubulle@debian.org
 language | Wolof
territory | Senegal
 revision | 1.0
     date | 2004-09-08
  codeset | UTF-8

locale: xh_ZA           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Xhosa locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | PO Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Xhosa
territory | South Africa
 revision | 0.3
     date | 2005-10-13
  codeset | ISO-8859-1

locale: xh_ZA.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Xhosa locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | PO Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Xhosa
territory | South Africa
 revision | 0.3
     date | 2005-10-13
  codeset | ISO-8859-1

locale: xh_ZA.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Xhosa locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | PO Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Xhosa
territory | South Africa
 revision | 0.3
     date | 2005-10-13
  codeset | UTF-8

locale: yi_US           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Yiddish Language locale for the USA
   source | http://www.uyip.org/
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Yiddish
territory | USA
 revision | 0.4
     date | 2003-08-16
  codeset | CP1255

locale: yi_US.cp1255    archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Yiddish Language locale for the USA
   source | http://www.uyip.org/
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Yiddish
territory | USA
 revision | 0.4
     date | 2003-08-16
  codeset | CP1255

locale: yi_US.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Yiddish Language locale for the USA
   source | http://www.uyip.org/
  contact | Pablo Saratxaga
    email | pablo@mandrakesoft.com
 language | Yiddish
territory | USA
 revision | 0.4
     date | 2003-08-16
  codeset | UTF-8

locale: yo_NG           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Yoruba locale for Nigeria
    email | pablo@mandriva.com
 language | Yoruba
territory | Nigeria
 revision | 0.2
     date | 2005-11-20
  codeset | UTF-8

locale: yo_NG.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Yoruba locale for Nigeria
    email | pablo@mandriva.com
 language | Yoruba
territory | Nigeria
 revision | 0.2
     date | 2005-11-20
  codeset | UTF-8

locale: zh_CN           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Chinese locale for Peoples Republic of China
    email | bug-glibc-locales@gnu.org
 language | Chinese
territory | P.R. of China
 revision | 0.1
     date | 2000-07-25
  codeset | GB2312

locale: zh_CN.gb18030   archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Chinese locale for Peoples Republic of China
    email | bug-glibc-locales@gnu.org
 language | Chinese
territory | P.R. of China
 revision | 0.1
     date | 2000-07-25
  codeset | GB18030

locale: zh_CN.gb2312    archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Chinese locale for Peoples Republic of China
    email | bug-glibc-locales@gnu.org
 language | Chinese
territory | P.R. of China
 revision | 0.1
     date | 2000-07-25
  codeset | GB2312

locale: zh_CN.gbk       archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Chinese locale for Peoples Republic of China
    email | bug-glibc-locales@gnu.org
 language | Chinese
territory | P.R. of China
 revision | 0.1
     date | 2000-07-25
  codeset | GBK

locale: zh_CN.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Chinese locale for Peoples Republic of China
    email | bug-glibc-locales@gnu.org
 language | Chinese
territory | P.R. of China
 revision | 0.1
     date | 2000-07-25
  codeset | UTF-8

locale: zh_HK           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Chinese language locale for Hong Kong
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Chinese
territory | Hong Kong
 revision | 1.0
     date | 2000-07-20
  codeset | BIG5-HKSCS

locale: zh_HK.big5hkscs archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Chinese language locale for Hong Kong
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Chinese
territory | Hong Kong
 revision | 1.0
     date | 2000-07-20
  codeset | BIG5-HKSCS

locale: zh_HK.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Chinese language locale for Hong Kong
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Chinese
territory | Hong Kong
 revision | 1.0
     date | 2000-07-20
  codeset | UTF-8

locale: zh_SG           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Chinese language locale for Singapore
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Chinese
territory | Singapore
 revision | 1.0
     date | 2000,October,27 (XML source:2000,July,20)
  codeset | GB2312

locale: zh_SG.gb2312    archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Chinese language locale for Singapore
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Chinese
territory | Singapore
 revision | 1.0
     date | 2000,October,27 (XML source:2000,July,20)
  codeset | GB2312

locale: zh_SG.gbk       archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Chinese language locale for Singapore
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Chinese
territory | Singapore
 revision | 1.0
     date | 2000,October,27 (XML source:2000,July,20)
  codeset | GBK

locale: zh_SG.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Chinese language locale for Singapore
   source | IBM Globalization Center of Competency, Yamato Software Laboratory
  address | 1623-14, Shimotsuruma, Yamato-shi, Kanagawa-ken, 242-8502, Japan
    email | bug-glibc-locales@gnu.org
 language | Chinese
territory | Singapore
 revision | 1.0
     date | 2000,October,27 (XML source:2000,July,20)
  codeset | UTF-8

locale: zh_TW           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Chinese locale for Taiwan R.O.C.
    email | bug-glibc-locales@gnu.org
 language | Chinese
territory | Taiwan R.O.C.
 revision | 0.2
     date | 2000-08-02
  codeset | BIG5

locale: zh_TW.big5      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Chinese locale for Taiwan R.O.C.
    email | bug-glibc-locales@gnu.org
 language | Chinese
territory | Taiwan R.O.C.
 revision | 0.2
     date | 2000-08-02
  codeset | BIG5

locale: zh_TW.euctw     archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Chinese locale for Taiwan R.O.C.
    email | bug-glibc-locales@gnu.org
 language | Chinese
territory | Taiwan R.O.C.
 revision | 0.2
     date | 2000-08-02
  codeset | EUC-TW

locale: zh_TW.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Chinese locale for Taiwan R.O.C.
    email | bug-glibc-locales@gnu.org
 language | Chinese
territory | Taiwan R.O.C.
 revision | 0.2
     date | 2000-08-02
  codeset | UTF-8

locale: zu_ZA           archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Zulu locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Zulu
territory | South Africa
 revision | 0.3
     date | 2005-10-13
  codeset | ISO-8859-1

locale: zu_ZA.iso88591  archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Zulu locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Zulu
territory | South Africa
 revision | 0.3
     date | 2005-10-13
  codeset | ISO-8859-1

locale: zu_ZA.utf8      archive: /usr/lib/locale/locale-archive
-------------------------------------------------------------------------------
    title | Zulu locale for South Africa
   source | Zuza Software Foundation (Translate.org.za)
  address | Box 28364, Sunnyside, 0132, South Africa
  contact | Dwayne Bailey
    email | dwayne@translate.org.za
telephone | +27 12 460 1095
      fax | +27 12 460 1095
 language | Zulu
territory | South Africa
 revision | 0.3
     date | 2005-10-13
  codeset | UTF-8


```

---

### Post by winh8r on 2012-02-15
> If you have a single-boot (Ubuntu is the only operating system on your computer), to get the boot menu to show, you have to hold down the Shift key during bootup.

If you have a dual-boot (Ubuntu is installed next to Windows, another Linux operating system, or Mac OS X; and you choose at boot time which operating system to boot into), the boot menu should appear without the need to hold down the Shift key.


From the boot menu, select recovery mode, which is usually the second boot option.


After you select recovery mode and wait for all the boot-up processes to finish, you'll be presented with a few options. In this case, you want the Drop to root shell prompt option so press the Down arrow to get to that option, and then press Enter to select it.

The root account is the ultimate administrator and can do anything to the Ubuntu installation (including erase it), so please be careful with what commands you enter in the root terminal.

Do the actual repair

Case 1: If you'd removed your last admin user from the admin group, then type
```
adduser username admin
```
where username is your actual username.

This information was found at [http://www.psychocats.net/ubuntu/fixsudo]("http://www.psychocats.net/ubuntu/fixsudo")


This should be the information you need to fix your problem with sudo, write it down or print it out and reboot into recovery mode as described and add your username to admin.

---

### Post by fra11 on 2012-02-15
source -psychocats is an invalid option apparently....

---

### Post by winh8r on 2012-02-15
The words "source - psychocats" are merely to show where i took the information from for others who may be reading this thread.

the only information you need is the following command to be run at the root prompt in recovery mode:

```
adduser username admin
```

where username is YOUR username on the machine

for example:       


```
adduser fra11 admin
```

hope this clears things up for you

---

