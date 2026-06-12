---
title: "Scraping and automating installation"
date: 2011-11-09
forum: General Help
---

### Post by Dumbestcrayon on 2011-11-09
MakeMKV expires every 30 days once it's installed so I've written 75% of a shell script to scrape [their post]("http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224"), download the bin.tar.gz and oss.tar.gz files, extract them and install them.

I have run into a road block. When you download and extract the tar.gz files we're instructed to 

> Unpack both packages and starting from source package do the following steps for each package:
```
make -f makefile.linux
sudo make -f makefile.linux install
```

When you execute the make command it presents you with a license agreement where you have to push "q" to exit.

After it exits you have to type "yes" to agree to the terms of the license.

Is there any way to automate this or will this be the end of my little project?

---

