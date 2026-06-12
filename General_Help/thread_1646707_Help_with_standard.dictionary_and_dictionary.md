---
title: "Help with standard.dictionary and dictionary"
date: 2010-12-16
forum: General Help
---

### Post by sn0m on 2010-12-16
Hi Guys
Does anybody know how to back up all changes that are made to standard dictionary in oowriter and the dictionary in mozilla web browser.
In other words I have added quite a few new medical terms to sd that it doesn't recognise when doing automatic spelling check.
Is there a way of saving them, so next time I do a fresh install they do not disappear and have to redo them all over again.
thanks
Sokol

---

### Post by gmargo on 2010-12-16
For mozilla/firefox, the personal dictionary is a text file in your profile directory named "persdict.dat".

[http://kb.mozillazine.org/Persdict.dat](http://kb.mozillazine.org/Persdict.dat)

---

### Post by gmargo on 2010-12-16
For openoffice, the standard place to put the list is

For OpenOffice 2 (as on 8.04 Hardy): $HOME/.openoffice.org2/user/wordbook/standard.dic

For OpenOffice 3 (as on 10.10 Maverick): $HOME/.openoffice.org/3/user/wordbook/standard.dic

It appears to be not-quite a text file, so you'd have to edit it through openoffice.

---

### Post by sn0m on 2010-12-16
thanx very much guys, I can backup my standard.dic now and replace in on a new insatall.
However I don't seem to find a persdict.dic in firefox, ?maybe cas is the 3.6 version...
this is the output from command line:
koli@koli-laptop:~$ find ~/ -name standard.dic
/home/koli/.openoffice.org/3/user/wordbook/standard.dic
koli@koli-laptop:~$ find ~/ -name persdict.dic
koli@koli-laptop:~$ find ~/ -iname persdict.dic
koli@koli-laptop:~$ find ~/ -iname persdict*.dic
koli@koli-laptop:~$ 

Could it be under a different name?
Thanx
Sokol

---

### Post by gmargo on 2010-12-16
Search for any .dic:
```

find $HOME -type f -iname '*.dic' -print

```or just use locate
```

locate .dic

```

---

### Post by sn0m on 2010-12-17
Hi Gmargo
Thanks for your help.
This is the output from find command as you adviced:
koli@koli-laptop:~$ find $HOME -type f -iname '*.dic' -print
/home/koli/Documents/MemoryCard042010/private/200002c1/dictionaries/English (US).dic
/home/koli/.mozilla/firefox/nurpy81w.default/extensions/sq-AL@dictionaries.addons.mozilla.org/dictionaries/sq.dic
/home/koli/.openoffice.org/3/user/wordbook/standard.dic
/home/koli/.config/enchant/en_GB.dic
/home/koli/.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/dictionaries/en-US.dic
koli@koli-laptop:~$ 

As you can see, the only one that comes up is an add on dictionary, the AL-Albanian one that I've added on already and I have checked it and it dosen't contain the words that I've already added on to standard english Dictionary.
A bit of mystery...
thanx
Sokol

---

