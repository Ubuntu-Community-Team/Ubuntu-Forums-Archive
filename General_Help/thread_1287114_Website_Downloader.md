---
title: "Website Downloader"
date: 2009-10-09
forum: General Help
---

### Post by Majorflam on 2009-10-09
I'm looking for a program that will download an entire website to pdf.

TIA

---

### Post by aheckler on 2009-10-09
Do you mean just one single web page, or literally an *entire* website?

---

### Post by pilorama on 2009-10-09
_...deleted..._[COLOR=#ffffff][COLOR=#ffffff][[COLOR=#ffffff][COLOR=#ffffff].[/COLOR][/COLOR]]("http://doctorluiza.wordpress.com/")[/COLOR][/COLOR]

---

### Post by Majorflam on 2009-10-10
> **aheckler said:**
> Do you mean just one single web page, or literally an *entire* website?

Yeah, entire website. But I would settle for one page. I've tried the plugin for Firefox, but it doesn't work very well.

---

### Post by StuartN on 2009-10-10
> **Majorflam said:**
> Yeah, entire website. But I would settle for one page. I've tried the plugin for Firefox, but it doesn't work very well.

wget, should already be installed. Use -r for recursive and -l to set the maximum depth. -H will allow host-spanning, i.e. links from other domains within the site you are downloading.

---

### Post by Majorflam on 2009-10-10
> **StuartN said:**
> wget, should already be installed. Use -r for recursive and -l to set the maximum depth. -H will allow host-spanning, i.e. links from other domains within the site you are downloading.

Hi, sorry to be a pain but could you give me an example code. Also, I assume wget is command line only?

---

### Post by Korozu on 2009-10-10
You can use Adobe Acrobat to convert.:popcorn:

---

### Post by Shazaam on 2009-10-10
gwget is a gui version of wget that you can install from the repos.

---

### Post by StuartN on 2009-10-10
> **Majorflam said:**
> Hi, sorry to be a pain but could you give me an example code. Also, I assume wget is command line only?

Sure, the URL of this page on the forum is [http://ubuntuforums.org/showthread.php?t=1287114](http://ubuntuforums.org/showthread.php?t=1287114) and you can save a copy of this page (and nothing else but this page) in the current directory like this:

```
wget http://ubuntuforums.org/showthread.php?t=1287114
```

If you want to download this thread, and to recursively download every page linked to by this thread, then add **-r --level=1**. Increasing the level gives pages linked to linked pages, etc. But **level=0** means _infinite_ recursion.

Only pages from this exact domain are included. The **-H** option would cross boundaries from, for instance, [www.google.com](www.google.com) to news.google.com or from google to sites within search results.

Be ready to kill wget if it gets out of control, and **man wget** for more information. It is command-line, but has an amazing range of options.

---

