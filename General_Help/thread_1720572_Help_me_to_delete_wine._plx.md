---
title: "Help me to delete wine. plx"
date: 2011-04-03
forum: General Help
---

### Post by Julian Luna on 2011-04-03
Hello well, there's a lot of **** going around my wine... and I want to start from 0... so please tell me how to completely delete/purge it. Also winetricks, and please tell me a good ppa or something about wine and winetricks :( My wine is really sick it isn't working correctly I hate it

---

### Post by Anonymous is Incognito on 2011-04-03
[This](http://wiki.winehq.org/FAQ#head-ddc6f242056eb1a4fe566c9434d15fd8b64606aa) will get rid of Wine, I guess.

See if Winetricks is located in [FONT="Courier New"]/usr/local/bin/winetricks[/FONT] or [FONT="Courier New"]/usr/bin/winetricks[/FONT] and delete it with [FONT="Courier New"]rm -rf[/FONT].

I am no Wine user, two Google searches returned these. I think that in the future it is better to search first, it will also give you the answer quicker.

Sources:
[http://wiki.winehq.org/FAQ#head-ddc6f242056eb1a4fe566c9434d15fd8b64606aa](http://wiki.winehq.org/FAQ#head-ddc6f242056eb1a4fe566c9434d15fd8b64606aa)
[http://code.google.com/p/winetricks/wiki/Installing](http://code.google.com/p/winetricks/wiki/Installing)

---

### Post by Irony on 2011-04-03
To reset wine delete the home directory wine contents;

```
~/.wine
```

```
~/.winetrickscache
```

---

### Post by Julian Luna on 2011-04-03
Thanks :) I wasn't able to completely delete it, there were folders remaining :< But thanks ^^

---

### Post by techunit on 2011-04-03
Right Click on your menu and click edit menus

Go to the wine folder and under the menus section drag the wine section into any other section. Now you will have the option to uncheck and hide it away.

If you reinstall wine you should reverse this process.

Good Luck!

---

