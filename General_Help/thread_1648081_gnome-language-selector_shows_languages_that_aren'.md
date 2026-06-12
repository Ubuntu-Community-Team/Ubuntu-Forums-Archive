---
title: "gnome-language-selector shows languages that aren't even installed"
date: 2010-12-18
forum: General Help
---

### Post by fflarex on 2010-12-18
Like the title says, when I go to System->Administration->Language Support after installation, the list of languages includes Interlingua, German, and Catalan. None of these are installed, but I can't get them to go away. It's annoying because every once in a while something will display in German, like items in my application menu or applications in the sound preferences window. But not every time... I've never been able to reproduce it when I wanted and never been able to figure out what's going on.

So please, help me get rid of these languages! Every time I try something another one gets added. At first I only had Interlingua. When I tried to get rid of it German came along, and when I tried to get rid of German all of a sudden Catalan joined the pack. I am positive that these language support packages are not installed!

---

### Post by sikander3786 on 2010-12-18
Did you try Install/Remove Languages button from Language Support?

---

### Post by fflarex on 2010-12-18
> **sikander3786 said:**
> Did you try Install/Remove Languages button from Language Support?

Yes. According to Ubuntu they are not even installed.

I have also tried localepurge or whatever it's called, as well as actually installing the languages just so that I can uninstall them.

---

### Post by sikander3786 on 2010-12-18
Search Software Center for whatever languages e.g, German, Catalan etc. Do they appear installed there?

---

### Post by susema on 2010-12-18
That's interesting. Can I look at that;
[FONT=Verdana]
[/FONT]```
sudo dpkg-reconfigure locales
```

This can show us what're installed.

---

### Post by fflarex on 2010-12-18
> **sikander3786 said:**
> Search Software Center for whatever languages e.g, German, Catalan etc. Do they appear installed there?

Nope, they really are not installed at all. I'm guessing there is a config or cache file somewhere on my system that didn't get updated properly. I've checked /var/lib/locales/supported.d/, /etc/default/locales, and a few others that I can't quite recall right now, but none of them mentioned these languages.

---

### Post by fflarex on 2010-12-18
> **susema said:**
> That's interesting. Can I look at that;
[FONT=Verdana]
[/FONT]```
sudo dpkg-reconfigure locales
```

This can show us what're installed.

```
$ sudo dpkg-reconfigure locales
[sudo] password for me: 
Generating locales...
  en_AG.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... hash collision (1688509771) en_HK.utf8, de_CH.utf8
failed
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NG.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZW.UTF-8... done
  zh_HK.UTF-8... done
  zh_TW.UTF-8... done
Generation complete.
```

---

### Post by susema on 2010-12-18
Look for in Synaptic about ** language-pack-gnome-zh** and then remove it.

---

### Post by fflarex on 2010-12-18
> **susema said:**
> Look for in Synaptic about ** language-pack-gnome-zh** and then remove it.

zh is Chinese. I probably should have been clearer... I want both English and Chinese on my machine, but nothing else.

---

### Post by susema on 2010-12-18
H&#305;mm.. Ok.. What's this in terminal;

```
locale -a
```

---

### Post by fflarex on 2010-12-18
```
$ locale -a
C
ca_ES.utf8@valencia
de_CH.utf8
en_AG
en_AG.utf8
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_IN.utf8
en_NG
en_NG.utf8
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
ia
POSIX
zh_CN.utf8
zh_HK.utf8
zh_SG.utf8
zh_TW.utf8
```

ia in this list is Interlingua, de_CH.utf8 is Swiss German, and ca_ES.utf8@valencia is Catalan... we might be getting somewhere now.

---

### Post by susema on 2010-12-18
Yes.. You can look for** de** and **ca **in Synaptic and remove them that's about language?

---

### Post by fflarex on 2010-12-18
I found a few hunspell dictionaries in German and removed them but it didn't really fix anything. I couldn't find anything else related to these languages.

---

### Post by susema on 2010-12-18
> **fflarex said:**
> I found a few hunspell dictionaries in German and removed them but it didn't really fix anything. I couldn't find anything else related to these languages.

Perhaps, dependency of a package that's used..

---

### Post by fflarex on 2010-12-18
> **susema said:**
> Perhaps, dependency of a package that's used..

I'm not following.

---

