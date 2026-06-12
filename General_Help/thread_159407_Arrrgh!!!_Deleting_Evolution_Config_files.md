---
title: "Arrrgh!!! Deleting Evolution Config files"
date: 2006-04-12
forum: General Help
---

### Post by monomaniacpat on 2006-04-12
I'm having problems connecting to my university email account, so having deleted the account and started again and this making no difference, I thought I'd just uninstall and reinstall evo, but it still has all my settings - aaaaarrrrgh!

Please, someone, how do I factory reset evolution? I can't find the config.xmldb file, it's not under ~/.evolution, or anywhere according to the system search util.


Help!

mono.

---

### Post by Ramses de Norre on 2006-04-12
sudo apt-get remove --purge package_name && sudo apt-get install package_name
I'm not sure what the package name is.

---

### Post by monomaniacpat on 2006-04-12
Nope, the damn files are still there, somewhere....

---

### Post by nemequ on 2006-04-12
```
rm -rf ~/.evolution
```

I'd strongly suggest making a backup first, as the above will delete not only your settings, but all your mail as well:

```
tar jcf ~/evolution-data.tar.bz2 ~/.evolution
```

---

### Post by monomaniacpat on 2006-04-12
Nope, still got the same ol account and the same ol' certificates!

](*,) ](*,) ](*,)

---

### Post by Ramses de Norre on 2006-04-12
sudo updatedb && locate evolution
That'll show what remains on your system from evolution. I have no idea where to start searching though.

---

### Post by monomaniacpat on 2006-04-12
[QUOTE=arnieboy]remove the firestarter entry from System --> Preferences --> Sessions --> Startup programs[/QUOTE]
 
Halleluja! I fixed it! I searched all folders, deleting anything that was left over after an uninstallation, backing up and deleting them. Re-installed evo, finding, to my horror, it didn't work properly. Reinstated the missing files and BINGO! It works! 
:-D :-D :-D :-D :-D :-D

---

### Post by dunkirk on 2007-08-06
In case someone else runs across this thread from Google... I had the same problem. What I realized is that gconfd is caching these sorts of details. So, to really "clean out" the account info on Evo, you have to:

delete ~/.evolution/
delete ~/.gconf/apps/evolution/
evolution --force-shutdown
killall gconfd

---

### Post by drseuk on 2008-03-21
Under Gutsy, this needs to be:

rm -r ~/.evolution/
rm -r ~/.gconf/apps/evolution/
evolution --force-shutdown
killall gconfd-2

---

