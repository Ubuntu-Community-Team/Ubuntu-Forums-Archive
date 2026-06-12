---
title: "Ubuntu 10.4 won't print, options grayed out, Cups not running"
date: 2010-05-10
forum: General Help
---

### Post by ronaldthomasjr on 2010-05-10
Very new to Ubuntu, and I'm not sure how it happened but recently when trying to print to a previously added printer, the printer does not show up. Most options are grayed out and clicking troubleshooter tells you that CUPS is not started.

Latest guide I could find is for Ubuntu 9.04, options for restarting cups in 10.4 are slightly different (see below)

**To restart cups from terminal window in Ubuntu 10.4:**
[INDENT]*sudo /etc/init.d/cups restart*[/INDENT]

I looks like in Ubuntu 9.04 the command was /etc/init.d/cupsys restart.

This should show the printer and open up the grayed out menu options, allowing you to print normally again.

---

### Post by nikhilbhardwaj on 2010-05-10
```

sudo service cups start/restart

```

---

### Post by jazeekat on 2010-05-16
> **nikhilbhardwaj said:**
> ```

sudo service cups start/restart

```
I am a very new Ubuntu user. My son gave me this computer and I am floundering on my own trying to figure it out! But I will.   Anyway, I have had problems with printers. My new Canon I250 did not work so I bought an HPF4480.  That did work before the 10.4 update. .Now I can't get it to work.  I did follow your instructions about and the printer is installed again but it will not print.  The test print worked but only the background prints, but not any words.

Can someone please help me???  Desparately seeking printer in Wisconsin

---

