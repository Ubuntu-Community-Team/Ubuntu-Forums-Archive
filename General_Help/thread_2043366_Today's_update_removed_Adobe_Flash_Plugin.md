---
title: "Today's update removed Adobe Flash Plugin"
date: 2012-08-16
forum: General Help
---

### Post by marin123 on 2012-08-16
I figured out what is the problem, but I don't know how to fix it.

So, I ran an update earlier today and it wanted to do "Partial Upgrade". OK, it was done and among other things, it installed libnspr4 and removed libnspr4-0d, on which flashplugin-installed was dependent.

Now I don't have Flash installed and I can't install it because apt-get says it has unmet dependencies, it depends on libnspr4-0d, and I have libnspr4.

How can I force the install of flashplugin?

---

### Post by Bertrand1771 on 2012-08-16
Hello, 

here is what worked for me :
sudo apt-get remove flashplugin-installer
sudo apt-get install flashplugin-installer

Cheers,

Bertrand

---

### Post by QIII on 2012-08-16
Lesson learned:  Just say no to partial upgrades.

---

### Post by LinkMJB on 2012-08-16
I ran into the same prompt today--what I did was cancel/say no, then just installed the updates using the update manager like normal (this in turn installed the new flash player and a bunch of other things). After that, it complained that a partial upgrade still needed to be done (leaving only the netscape libnspr crap to add, and oddly requiring removal of an english language support metadata pkg). I went ahead and allowed it to "partially update" at that point, removing the english language support metadata pkg and adding the netscape library pkgs. Haven't noticed any "bad behavior" since following that pattern, and flash still works :) ( now at version 11.2.202.238 )

---

### Post by marin123 on 2012-08-16
Oh well...
Partial upgrade loves to break things.

Bertrand's post didn't help me because I don't have Flash installed. But I installed Chrome (instead of Chromium) and now I have flash until flashplugin-installer gets dependencies corrected.

Actually, I know what to do, but I am too lazy to do it :)

If someone needs to do it, you need to download deb package, unpack it, edit the metadata file, update dependencies to libnspr4 (instead of libnspr4-0d), build that folder to package with dpkg and install it with USC or dpkg.

I hope someone finds this helpful :)

---

### Post by Rovano on 2012-08-16
Now is in main server situation ok :-)
sudo apt-get install flashplugin-installer really install....
> rovano@panter:~$ sudo apt-get install flashplugin-installer
&#268;tu seznamy balík&#367;… Hotovo
Vytvá&#345;ím strom závislostí       
&#268;tu stavové informace… Hotovo
Následující balík byl nainstalován automaticky a již není pot&#345;eba:
  libkutils4
Pro jejich odstran&#283;ní použijte „apt-get autoremove“.
Následující extra balíky budou instalovány:
  libnspr4-0d libnss3-1d
Navrhované balíky:
  x-ttcidfont-conf ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
Následující NOVÉ balíky budou nainstalovány:
  flashplugin-installer libnspr4-0d libnss3-1d
0 aktualizováno, 3 nov&#283; instalováno, 0 k odstran&#283;ní a 0 neaktualizováno.
Pot&#345;ebuji stáhnout 11,3 kB/32,8 kB archiv&#367;.
Po této operaci bude na disku použito dalších 302 kB.
Chcete pokra&#269;ovat [Y/n]? y
Mám:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/universe libnspr4-0d i386 4.8.9-1ubuntu2.2 [11,3 kB]
Staženo 11,3 kB za 0s (58,8 kB/s)       
P&#345;ednastavuji balíky...
Selecting previously unselected package libnss3-1d.
(&#268;tu databázi … nyní je nainstalováno 109108 soubor&#367; a adresá&#345;&#367;.)
Rozbaluji libnss3-1d (z …/libnss3-1d_3.13.1.with.ckbi.1.88-1ubuntu6_i386.deb) …
Selecting previously unselected package libnspr4-0d.
Rozbaluji libnspr4-0d (z …/libnspr4-0d_4.8.9-1ubuntu2.2_i386.deb) …
Selecting previously unselected package flashplugin-installer.
Rozbaluji flashplugin-installer (z …/flashplugin-installer_11.2.202.238ubuntu0.12.04.1_i386.deb) …
Zpracování spoušt&#283;&#269;&#367; pro balík update-notifier-common …
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.238.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.238.orig.tar.gz)
Installing from local file /tmp/tmpLQG0N9.gz
Flash Plugin installed.
Nastavuji balík libnss3-1d (3.13.1.with.ckbi.1.88-1ubuntu6) …
Nastavuji balík libnspr4-0d (4.8.9-1ubuntu2.2) …
Nastavuji balík flashplugin-installer (11.2.202.238ubuntu0.12.04.1) …


---

### Post by marin123 on 2012-08-17
> **Rovano said:**
> Now is in main server situation ok :-)
sudo apt-get install flashplugin-installer really install....

Yep, they fixed it. That was fast :)

---

