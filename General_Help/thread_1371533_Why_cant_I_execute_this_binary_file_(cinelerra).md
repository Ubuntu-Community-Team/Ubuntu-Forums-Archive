---
title: "Why cant I execute this binary file (cinelerra)"
date: 2010-01-03
forum: General Help
---

### Post by linuxNewb on 2010-01-03
I am using Karmic.

I just downloaded Cinelerra from sourceforge. Apparently there is no installation, you just run the binary (according to the Readme). The binary is set to be executable (-rwxr-xr-x), but when I double click it in nautilus nothing happens. When I go to the app directory in the terminal and do:

 $ ./cinelerra

I get:

 bash: ./cinelerra: cannot execute binary file

What am I doing wrong? Thanks in advance.

---

### Post by oldos2er on 2010-01-03
Not sure about your problem, but you can download a *deb using the instructions here: [http://cinelerra.org/getting_cinelerra.php#karmic](http://cinelerra.org/getting_cinelerra.php#karmic)

---

### Post by Some Penguin on 2010-01-03
Try typing 'file cinelerra'.   Perhaps it's for the wrong architecture, such as you're trying to run a 64-bit binary on a 32-bit OS build.

---

### Post by linuxNewb on 2010-01-03
Thank you both. As it turns out Some Penguin was right. I had inadvertently downloaded the 64-bit app. I went ahead and used the deb posted by oldos2er in order to easily keep the app updated. Again, thank you both for your helpful responses.

---

