---
title: "help getting wubi working on windows 7 64bit"
date: 2009-09-09
forum: General Help
---

### Post by steve51184 on 2009-09-09
hey all i had windows xp and wubi install but i installed windows 7 64bit on a new drive and deleted windows xp but i saved my "ubuntu" folder from my wubi install but now i need to get it working again.. how do i do that?

i've tried to install wubi again with the intent to just copy the files from my old wubi folder but the installer failed with a permission error so can i simply just add wubi back to windows 7's boot loader? if so how?

---

### Post by privatejarhead on 2009-09-09
seeing that you've deleted xp and replaced it with 7, and how windows treats wubi as any other .exe, i'd imagine that you would have to reinstall wubi the same way you did on xp. if you have a backup with all of your desired data (config files, docs, etc), you should be fine by doing a fresh install.

---

### Post by steve51184 on 2009-09-09
thank you for the reply but i suggest you read my post again...

*"i've tried to install wubi again with the intent to just copy the files from my old wubi folder but the installer failed with a permission error"*

---

### Post by raymondh on 2009-09-09
Early this year (when I was experimenting with wubi), I had to run wubi in compatibility mode (as Vista) in order to install it in 7 and get ubuntu recognized on boot-up.

Rt. clk on wubi.exe > properties > compatibility tab > run for Vista > apply > ok > proceed with install.

Hope this can help.  I don't have windows anymore in this computer hence cannot duplicate/test for you.

Good luck.

---

### Post by steve51184 on 2009-09-09
tried that and i get the same error :(

---

### Post by steve51184 on 2009-09-17
any help people?

---

### Post by ram2008 on 2009-10-08
Steve,

Did you consider trying the installation again with a new Ubuntu CD?  I tried installing Wubi last night and got the same "Permission denied" error.  So this morning I burned a new CD and this time Wubi installed in Windows XP just fine.  However, once I ran Ubuntu there were other problems which I have posted about.  They may be more related to the Beta version than Wubi per se.  Not sure.

---

