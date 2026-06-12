---
title: "wine not uninstalling"
date: 2010-02-12
forum: General Help
---

### Post by dzwestwindsor on 2010-02-12
I'm trying to uninstall wine. 

I did everything i could to get it uninstalled, and I think it really is unintsalled, but the problem is when I go to "Applications" the Wine tab is still there, just without the logo. 

I even deleted the whole .wine folder. now what? how do I get rid of everything?

oh and along the way I might have accidently deleted some web fonts? I was't even sure if i did, but more and more things are times new roman, and I know that they are not supposed to be. how do I restore that? 

Ok thanks

---

### Post by jken146 on 2010-02-12
```
sudo apt-get purge wine
```

As for those fonts, you could install **msttcorefonts**

---

### Post by Silvertones on 2010-02-20
I;m having the same issue. I had installed MS Office and didn't care for it. So I used the "uninstall wine program". It went through the uninstall but Office would still load. Ran the uninstaller twice. Still wouldn't uninstall office. I decided I didn't really want Wine anyway some from Synaptic I uninstalled Wine. It's uninstalled by under applications the wine icon and the MS icons are still there.
How do I get rid of this Some of the stuff is gone:
1. confiqure wine
2. notepad
3. uninstall wine programs
The rest and the Office stuff won't go.

---

### Post by Silvertones on 2010-02-20
When I clicked on the icons nothing happens so assume it's just an icon issue so I used ```
sudo alacarte
``` to just uncheck those icons and they're gone. Was this the right thing to do?

---

### Post by saturnblackhole on 2010-02-20
^^^ the icons are still there but are now just hidden. 

i've also had this wine problem it pissed my off i solved it but going to places-->home folder-->pressing ctrl+h to show hidden icons--->.config--> menus and deleting the files with wine in the name. if that doesnt work you can search those files without wine in them and remove any mention of wine and save them.

---

### Post by jken146 on 2010-02-22
First, completely uninstall wine:
```
sudo apt-get purge wine
```
Then remove the directory ~/.wine (this contains the fake Windows environment):
```
rm -r ~/.wine
```

---

