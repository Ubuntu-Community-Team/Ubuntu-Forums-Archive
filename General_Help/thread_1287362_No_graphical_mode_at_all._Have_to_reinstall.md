---
title: "No graphical mode at all. Have to reinstall?"
date: 2009-10-10
forum: General Help
---

### Post by sopadeajo on 2009-10-10
learning to use Compiz (dangerous program), when i was trying the plugin windows Blur, i used some keyboard keys accidentally and got the window of CCSM completely black followed by a blacking of most of the sceen.I had to ctrl alt supr, but when booting again the screen is absolutely and completely black with nothing in it. The only thing that can be done is ctrl alt F1 and get a kind of Terminal screen where i tried to killall the blur and compiz processes without success. I wonder if i could uninstall (or purge) compiz and so get rid of what causes the total blacking of the Ubuntu screen.  Any ideas and solutions to avoid a reinstall???  Edit: This has been written using Vista. I´ll  be out of this forum for 8 or 9 hours. And i have tried to boot in recovery mode  3 times trying the graphic-repair option and more options without any success.

---

### Post by kiridude on 2009-10-10
not sure how to recover, but you can recover your files with the live cd.

---

### Post by wojox on 2009-10-10
Boot into single user mode and drop to a root shell, navigate to:

```
/.gconf/desktop/gnome/applications/window_manager/%gconf.xml
```

```
sudo nano %gconf.xml
```

Replace this line with:

```
<stringvalue>/usr/bin/metacity</stringvalue>
```

---

