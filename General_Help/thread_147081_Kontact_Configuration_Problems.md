---
title: "Kontact Configuration Problems?"
date: 2006-03-19
forum: General Help
---

### Post by wpp42000 on 2006-03-19
I am running Breezy Badger and everything is working.  I am configuring Kontact for my personal use and the News icon does not load (library files for "libknodepart.la not found in paths).  So I configured some RSS feeds to get news, but I cannot get an RSS feed to appear on the Summary.  Can this be done?  How?

While I was surfing the RSS feeds, I got an error/warning screen showing "No plugin for 'Shockwave Flash Media' ".
I ran adept  and installed gstreamer0.8-swfdec and libswfdec0.3, but I still get the no plugin message.  What now?

Also the Agregator feed that is configured at install time is out-of-date (latest date is in 2005), and the ubuntu feed does not work.  I hope these are fixed in future releases.

---

### Post by Jucato on 2006-03-19
1. I'm trying to get the RSS feed to work in Summary View myself. Haven't gotten around how to do that.

2. The RSS feeds will use the KHTML KPart for viewing pages. So if Shockwave doesn't work in Konqueror, it won't work in RSS. I'm not sure if there's a shockwave plugin available for Linux. There's a flash plugin, though.

3. The Ubuntuforums RSS link at the bottom-right corner of Konqueror doesn't work. Instead, use this address: [http://ubuntuforums.org/external.php?type=RSS2](http://ubuntuforums.org/external.php?type=RSS2)
Also, there's a new feature in Ubuntuforums. Each section/sub-section now has it's own RSS link. You can find the RSS icon at the top-right corner above the first thread in the section/sub-section.
I don't think the Akregator feeds has been updated on the akregator side.

---

### Post by megadodo on 2006-05-13
I am also tying to get rss feeds in kontact summary page.
The kontact website says it is possible, ([http://www.kontact.org/components.php#summary]("http://www.kontact.org/components.php#summary")
But I have no option to add it in the summary settings. The website also says weather information can be added, but I cant do that either.
Did you manage to resolve this problem? Or does anyone know how? It would appear to be kubuntu specific.
Thanks
Richard

---

### Post by Mau on 2006-05-13
I had similar problems, but I believe I fixed it by installing KNode (sudo apt-get install knode).

---

### Post by megadodo on 2006-05-16
I have installed Knode, but there is still no option to add rss feeds to the summary pages. Any other ideas?

---

### Post by briguy on 2007-07-16
Install dcoprss
```

sudo apt-get install dcoprss
```

---

