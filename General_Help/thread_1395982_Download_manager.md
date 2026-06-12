---
title: "Download manager"
date: 2010-02-01
forum: General Help
---

### Post by sakundiak on 2010-02-01
Anyone know of a good download manager for ubuntu that will support multi thread as well as site logins. I do a lot of downloading from rapid share and all the download managers i've tried don't support site logins. thanks

---

### Post by t4thfavor on 2010-02-01
[http://www.linuxquestions.org/questions/linux-software-2/anyone-know-a-good-linux-download-manager-34810/](http://www.linuxquestions.org/questions/linux-software-2/anyone-know-a-good-linux-download-manager-34810/)

They mention a few here.

---

### Post by sakundiak on 2010-02-05
Okay so jdownloader is definitely the one for me since it support site logins such as rapidshare premium account. So i got it installed and it worked great for what i wanted it to do. The only problem i've ran into now is after a reboot jdownloader is gone from the taskbar and i don't know how to get it to run again. Anyone with some help on this please. Thanks

---

### Post by tlroche on 2010-02-05
> **sakundiak said:**
> after a reboot jdownloader is gone from the taskbar

I believe this is usually called the 'panel'.

> **sakundiak said:**
> and i don't know how to get it to run again. Anyone with some help on this please. Thanks

In GNOME karmic,
[LIST=1]
[*]Find where in the launchers it installed (maybe Applications>Internet ?)
[*]Right-click on its launcher, and choose ```
Add this launcher to panel
```
[/LIST]

---

### Post by sakundiak on 2010-02-05
Sorry about the panel / taskbar confusion, anyway this will make it run from the terminal
```
cd ~/.jd
java -jar JDownloader.jar
```

So any idea where i might find this installed so i can add this launcher to the panel? I did a search for JDownloader.jar but it comes up with nothing. Thanks

---

