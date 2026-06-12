---
title: "Kile configuration problem - does not remember previously set options"
date: 2011-09-06
forum: General Help
---

### Post by harlequin_ on 2011-09-06
[SOLVED, see second post]

Hi, 

I installed Kile 2.1 after a fresh ubuntu 11.04 installation. When I open the application I am welcomed with a message I've never seen before, saying

The standard tool list needs to be reloaded because of the switch from KDE3 to KDE4. This will overwrite any changes in the tools you have made. Do you want to reload the list now (recommended)?

When I click "Yes", without doing anything visible, it progresses to Tip of the Day startup screen. Even though I uncheck "Show tips on startup", whenever I launch Kile I go through these 2 steps.

When I change the default PDF viewer from okular to evince, if I do not close Kile it works perfect but when I close it and reopen, my default pdfviewer is okular again. 

Other than these I cannot find anything irregular about the app and I can build and view my .tex files.

---

### Post by harlequin_ on 2011-09-06
SOLVED.

I just needed to change the owner of Kile's config file (I have no idea why by default it is root !!!) and now it's perfectly fine.

```

/home/<username>/.kde/share/config/kilerc
```Just change the owner from *root* to *<username>* by 

[CODE]
sudo chown <username> /home/<username>/.kde/share/config/kilerc

---

### Post by Gilberoni on 2011-10-10
thanks :)

---

### Post by my_love_is_ on 2012-03-11
> **harlequin_ said:**
> SOLVED.

I just needed to change the owner of Kile's config file (I have no idea why by default it is root !!!) and now it's perfectly fine.

```

/home/<username>/.kde/share/config/kilerc
```Just change the owner from *root* to *<username>* by 

[CODE]
sudo chown <username> /home/<username>/.kde/share/config/kilerc

In my case even though I own the configuration file, it does not remember my PDF viewer configuration:(

---

