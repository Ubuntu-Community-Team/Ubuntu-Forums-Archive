---
title: "MS Fonts won't reinstall"
date: 2011-09-11
forum: General Help
---

### Post by Yeen125 on 2011-09-11
Hey, I just loaded ubuntu 11.04 on my laptop. Just lately, I installed Ubuntu restricted extras. One of the 'extras' was the MS Truetype fonts, but I accidentally forgot to click 'I agree' on the EULA before hitting continue and now I can't install MS fonts. I tried reinstalling Ubuntu restricted extras, but that didn't work. So I tried reinstalling MS Truetype fonts itself, but it still says I declined the EULA. Can someone help me!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!![IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

---

### Post by gmargo on 2011-09-11
Since the EULA question is posted by the "postinst" script, not the configure script, you must effectively reinstall either directly or by remove then install.

Using the command line, try this:
```

sudo apt-get --reinstall install ttf-mscorefonts-installer

```Alternatively, use your graphical package installer to first remove, and then install the **ttf-mscorefonts-installer** package.

[URL="http://ubuntuforums.org/showpost.php?p=10427959&postcount=5"]
[/URL]

---

### Post by garvinrick4 on 2011-09-11
Thread has been answered I just wanted to let you know to use the [COLOR=Red]tab[/COLOR] key to toggle when
using terminal to install package or reconfigure a package that wants you to answer questions such as accept a EULA and or make a selection of which package to use when
you have more than one package installed that does the same thing.

Microsoft fonts is one that requires toggle with tab at install.

Gdm and lightdm when both installed upgrading from 11.04 to 11.10 is another example
for the time being that requires a toggle with tab at reconfigure.

Do not feel bad yen125 we all at the beginning have had same problems. Stick with it and enjoy Ubuntu ask all the questions you need to, it is how you learn.

---

