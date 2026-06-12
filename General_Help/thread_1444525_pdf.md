---
title: "pdf"
date: 2010-04-01
forum: General Help
---

### Post by nischalinn on 2010-04-01
how to *_**convert webpage to pdf?**_*

I've tried the command:

[U][B]$ wkhtmltopdf  linuxandfriends.com  linuxandfriends.pdf

[/B][/U]but it shows:

[U][B]xxx@xxx-desktop:~$ $ wkhtmltopdf  linuxandfriends.com  linuxandfriends.pdf
bash: $: command not found


[/B][/U]

---

### Post by Chemical Imbalance on 2010-04-01
In firefox:

File, Print, "Print to File", Output Format= pdf, 
Rename it and save it to the folder you want.

---

### Post by doas777 on 2010-04-01
have you actually installed 'wkhtmltopdf' [http://code.google.com/p/wkhtmltopdf/](http://code.google.com/p/wkhtmltopdf/)
?

I also see some hits on [s]google[/s] Topeka that lead me to believe that this will not work with all types of webpages (for instance PHP). your error message however indicates that you do not have it installed, or that it requires sudo (which would be stupid).

---

### Post by cjhabs on 2010-04-01
> **nischalinn said:**
> how to *_**convert webpage to pdf?**_*

I've tried the command:

[U][B]$ wkhtmltopdf  linuxandfriends.com  linuxandfriends.pdf

[/B][/U]but it shows:

[U][B]xxx@xxx-desktop:~$ $ wkhtmltopdf  linuxandfriends.com  linuxandfriends.pdf
bash: $: command not found


[/B][/U]

You can do this using open office - export as PDF.

---

### Post by Jive Turkey on 2010-04-01
I'm not familiar with wkhtmltopdf but you can verify that it is installed with the command ```
whereis wkhtmltopdf
``` It looks to be in the repositories but not installed by default so you can install it easily enough.

---

