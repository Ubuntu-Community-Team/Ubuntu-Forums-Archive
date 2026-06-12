---
title: "Evolution spell check broken"
date: 2011-01-12
forum: General Help
---

### Post by Rocket J Squirrel on 2011-01-12
Sometime earlier this week, after an Update Manager update, spell check in Evolution broke. 

It started underlining *all* words, even simple ones like "the".

I Googled around and found this article: [http://live.gnome.org/Evolution/FAQ#Why_does_Spellchecking_not_work.3F](http://live.gnome.org/Evolution/FAQ#Why_does_Spellchecking_not_work.3F)

First, I did as recommended: 'Then go to "Edit | Preferences | Composer Preferences | Spell Checking", and enable the available languages." I found a list of languages and found that the USA version of English was enabled. 

It then says, "You can also check gnome-enabled dictionaries by using gconf-editor. The  GConf key /GNOME/Spell/language should contain a space-separated list  of the languages you have enabled (i.e. en-US es for US english and  Spanish)."

No such key found in GConf.

I followed the next instruction ("you could also try the hard way: Shut Evolution down by closing  Evolution and then using the command evolution --force-shutdown. After  that, run gconftool-2 --unset /GNOME/Spell/mtime.") which I did, gfcontool-2  --unset /GNOME/Spell/mtime returned with no error or comment. 

But now, spell check isn't working at all, even misspelled words are not flagged, and "Edit | Preferences | Composer Preferences | Spell Checking" shows no languages to select from. 

Finally, the instructions say, "If all this does not help, remove the file  $HOME/.gconf/GNOME/Spell/%gconf.xml so all your spellchecking settings  get deleted. The file gets recreated and according to some users on the  Evolution mailing list, spellchecking should work again"

I found no "Spell" directory under "$HOME/.gconf"

I'm not a terrible speller, but do miss the okashunal werd, so having the spell checker working again would be useful.

Ideas?

---

### Post by Rocket J Squirrel on 2011-01-12
Solved. Needed to reinstall the needed dictionary: [https://wiki.ubuntu.com/Evolution](https://wiki.ubuntu.com/Evolution)

---

