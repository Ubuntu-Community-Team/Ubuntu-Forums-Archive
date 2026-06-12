---
title: "How to install PDF firefox browser plugin"
date: 2011-07-01
forum: General Help
---

### Post by belltown on 2011-07-01
When I try to display a PDF file from within the Firefox browser, I get a  screen that says "Click here to download plugin." When I click there, the plugin finder service runs and displays a message that says: "No suitable plugins were found".

How do I find and install the Firefox browser plugin that lets me display PDF files?

---

### Post by haqking on 2011-07-01
> **belltown said:**
> When I try to display a PDF file from within the Firefox browser, I get a  screen that says "Click here to download plugin." When I click there, the plugin finder service runs and displays a message that says: "No suitable plugins were found".

How do I find and install the Firefox browser plugin that lets me display PDF files?

[https://addons.mozilla.org/en-US/firefox/addon/pdf-download/](https://addons.mozilla.org/en-US/firefox/addon/pdf-download/)

also there is acroread (adobe) available as a reader

i prefer PDF editor, you can read and edit with it.

---

### Post by belltown on 2011-07-01
> **haqking said:**
> [https://addons.mozilla.org/en-US/firefox/addon/pdf-download/](https://addons.mozilla.org/en-US/firefox/addon/pdf-download/)

also there is acroread (adobe) available as a reader

i prefer PDF editor, you can read and edit with it.


I tried installing PDF download. It says it installed, I restarted my browser, but I still get the same message as before (click here to download plugin).

---

### Post by haqking on 2011-07-01
try here

[http://ubuntuforums.org/showthread.php?t=1729462&highlight=pdf+firefox](http://ubuntuforums.org/showthread.php?t=1729462&highlight=pdf+firefox)

---

### Post by belltown on 2011-07-01
Thanks for the help. This is what worked for me:

```
sudo apt-get install mozplugger
```

---

### Post by pqwoerituytrueiwoq on 2011-07-01
you can install adobe reader from Canonical Partners in the software center if you enabled the repository in software sources (it is a check box)
then pdf files will open in firefox the built in pdf viewer open faster so i don't make it default

---

### Post by haqking on 2011-07-01
> **belltown said:**
> Thanks for the help. This is what worked for me:

```
sudo apt-get install mozplugger
```


cool, make sure you mark the thread as solved for others ;-)

peace

---

### Post by lovinglinux on 2011-07-01
> **haqking said:**
> [https://addons.mozilla.org/en-US/firefox/addon/pdf-download/](https://addons.mozilla.org/en-US/firefox/addon/pdf-download/)

also there is acroread (adobe) available as a reader

i prefer PDF editor, you can read and edit with it.

That add-on is very slow. Is better to use mozplugger with Evince/Okular or [gPDF]("https://addons.mozilla.org/en-US/firefox/addon/14814/").

BTW, Mozilla is working on a Firefox built-in PDF reader using HTML5. Which means no more plugins necessary. No idea when it will be released tho.

---

