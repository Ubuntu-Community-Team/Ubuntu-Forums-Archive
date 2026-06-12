---
title: "Removing Firefox 4 language pack?"
date: 2011-04-02
forum: General Help
---

### Post by r1ft on 2011-04-02
How do I remove all the language packs installed with Firefox 4? I have  English US, English GB and English South Africa, and I don't need any of  them. As of now, I can only disable them.

I can't find any mention of them in Synaptic.

Firefox 4 on fully-updated Ubuntu 10.04 x86-64 here.

**EDIT:** I just saw that there is a FF4 'Mega Thread'; an admin may merge this thread with the former if he so desires. Thanks!
[B]
SOLUTION: They are in [COLOR=DarkOrange]*/usr/lib/firefox-extensions/*[/COLOR]. I deleted [COLOR=DarkOrange]**.xpi*[/COLOR] files and it worked without issues.[/B]

---

### Post by lithopsian on 2011-04-02
Language packs are add-ons.  Go to the add-ons manager from your tools menu and you should be able to find the packs listed in the Languages section.  Then click the disable or remove button and they will go away.  Disabled language packs will remain in your profile if you ever want to enable them again without downloading.

---

### Post by Krytarik on 2011-04-02
I just looked up the cause of that. The package "language-pack-en-base" included by the "firefox-stable" PPA is different in that aspect (also regarding the searchplugins) to those provided by the official Lucid repos. So, the next time the package gets upgraded, those language packs will 'return', unless you "force" a downgrade of the package to the official Lucid version.

Greetings.

---

### Post by Zeven on 2011-09-29
I have the English (South Africa) Language Pack installed as well and I really don't need it. When right clicking on a text field and selecting Languages, I see the following:

English / Australia
English / Australia
English / Canada
English / South Africa
English / United States

I don't need all of those, and I especially don't need English / Australia twice. Can this issue somehow be fixed?

---

### Post by Zeven on 2011-09-30
So can nobody offer any insight on the matter? Solutions would be preferable.

---

### Post by Krytarik on 2011-09-30
> **Zeven said:**
> Solutions would be preferable.
So, in short ;-) :
```
sudo apt-get purge hunspell-en-ca myspell-en-au myspell-en-za
```This should leave you with only "English / United States", and may remove the meta-packages "language-support-en" and "language-support-writing-en", if they are not already broken/removed, since I'm missing "English / United Kingdom" in your list, which is also listed twice in my list, as well as "English / United States".

Btw., we need to differentiate between "language packs" and "dictionaries", the first of which are for displaying the respective localized terms in the UI (like in menus and dialogs), and the latter are for spellchecking. And both are provided by different kind of packages or add-ons. Obviously, I wasn't too aware of the whole subject when I did my initial post in this thread.

Greetings.

---

### Post by Budchekov on 2012-02-04
> **r1ft said:**
> 
[B]
SOLUTION: They are in [COLOR=DarkOrange]*/usr/lib/firefox-extensions/*[/COLOR]. I deleted [COLOR=DarkOrange]**.xpi*[/COLOR] files and it worked without issues.[/B]

Old thread I know but it's always nice to find simple solutions here.
WFM Thanks  :)

---

### Post by Tzctlpc on 2012-04-10
The answer given above is not correct (at least not on my machine).

The problem is that some of the spelling support packages add too much rubbish and Firefox mixes that with the add-ons to create an unholy mess.

In my case the hunspell package loads dictionaries in the directory

/usr/share/myspell

and I have this there:


```
# ls -l
total 8060
-rw-r--r--. 1 root root   18607 Aug 19  2010 de_AT.aff
-rw-r--r--. 1 root root 1026892 Aug 19  2010 de_AT.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:24 de_BE.aff -> de_DE.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:24 de_BE.dic -> de_DE.dic
-rw-r--r--. 1 root root   18607 Aug 19  2010 de_CH.aff
-rw-r--r--. 1 root root 1025328 Aug 19  2010 de_CH.dic
-rw-r--r--. 1 root root   18607 Aug 19  2010 de_DE.aff
-rw-r--r--. 1 root root 1023076 Aug 19  2010 de_DE.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:24 de_LI.aff -> de_CH.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:24 de_LI.dic -> de_CH.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:24 de_LU.aff -> de_DE.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:24 de_LU.dic -> de_DE.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_AG.aff -> en_GB.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_AG.dic -> en_GB.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_AU.aff -> en_GB.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_AU.dic -> en_GB.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_BS.aff -> en_GB.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_BS.dic -> en_GB.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_BW.aff -> en_GB.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_BW.dic -> en_GB.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_BZ.aff -> en_GB.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_BZ.dic -> en_GB.dic
-rw-r--r--. 1 root root    3114 Aug 19  2010 en_CA.aff
-rw-r--r--. 1 root root  533931 Aug 19  2010 en_CA.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_DK.aff -> en_GB.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_DK.dic -> en_GB.dic
-rw-r--r--. 1 root root   27449 May 26  2005 en_GB.aff
-rw-r--r--. 1 root root  527349 Aug 19  2010 en_GB.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_GH.aff -> en_GB.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_GH.dic -> en_GB.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_HK.aff -> en_GB.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_HK.dic -> en_GB.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_IE.aff -> en_GB.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_IE.dic -> en_GB.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_IN.aff -> en_GB.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_IN.dic -> en_GB.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_JM.aff -> en_GB.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_JM.dic -> en_GB.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_NA.aff -> en_GB.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_NA.dic -> en_GB.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_NG.aff -> en_GB.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_NG.dic -> en_GB.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_NZ.aff -> en_GB.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_NZ.dic -> en_GB.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_PH.aff -> en_US.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_PH.dic -> en_US.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_SG.aff -> en_GB.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_SG.dic -> en_GB.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_TT.aff -> en_GB.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_TT.dic -> en_GB.dic
-rw-r--r--. 1 root root    3114 Aug 19  2010 en_US.aff
-rw-r--r--. 1 root root  532021 Aug 19  2010 en_US.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_ZA.aff -> en_GB.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_ZA.dic -> en_GB.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_ZW.aff -> en_GB.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:02 en_ZW.dic -> en_GB.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:24 fr_BE.aff -> fr_FR.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:24 fr_BE.dic -> fr_FR.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:24 fr_CA.aff -> fr_FR.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:24 fr_CA.dic -> fr_FR.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:24 fr_CH.aff -> fr_FR.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:24 fr_CH.dic -> fr_FR.dic
-rw-r--r--. 1 root root  362737 Sep 11  2009 fr_FR.aff
-rw-r--r--. 1 root root  886565 Sep 11  2009 fr_FR.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:24 fr_LU.aff -> fr_FR.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:24 fr_LU.dic -> fr_FR.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:24 fr_MC.aff -> fr_FR.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:24 fr_MC.dic -> fr_FR.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:24 nl_AW.aff -> nl_NL.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:24 nl_AW.dic -> nl_NL.dic
lrwxrwxrwx. 1 root root       9 Dec 16 05:24 nl_BE.aff -> nl_NL.aff
lrwxrwxrwx. 1 root root       9 Dec 16 05:24 nl_BE.dic -> nl_NL.dic
-rw-r--r--. 1 root root    7901 Jul 22  2009 nl_NL.aff
-rw-r--r--. 1 root root 2213427 Jul 22  2009 nl_NL.dic
```


check all those symbolic links. Nice to have I am sure, but in the case of Firefox a real pain, after all they all refer to the same dictionary data, so its just a case of fooling the user into believing they have lots of detailed choice.

I just removed all the links, and lo and behold, I am now only presented with the real dictionary available *plus* the Firefox add-ons.

Firefox makes all this unnecessarily confusing by mixing both sources of information needlessly, and Ubuntu( Debian?) does not help by allowing all those links (I am sure there is a good reason for them, but in Firefox they are just a hindrance, most people need to spell in 2 or 3 dictionaries at most, so being offered a list of 20 or 30 alternatives is most unhelpful).

---

### Post by dirtyblanket on 2013-01-16
> **r1ft said:**
> 
[B]
SOLUTION: They are in [COLOR=DarkOrange]*/usr/lib/firefox-extensions/*[/COLOR]. I deleted [COLOR=DarkOrange]**.xpi*[/COLOR] files and it worked without issues.[/B]


I couldn't remove chinese (and i really don't speak chinese, i have no clue why it was installed). I wasted so much time trying to get rid of it.

THANK YOU FOR THIS SOLUTION! I love you man.

---

