---
title: "Open Office"
date: 2009-11-09
forum: General Help
---

### Post by FransGabriel on 2009-11-09
Hi its me again this time I have mange to course open office not to open,I have uninstalled it and reinstalled it, all that happens is that it comes up with open office logo and then logo disappears and nothing else I have checked under system monitor but there is no indication that open office is running. Has any one had this before or do you have any suggestions I am run 910 have recently done a clean installtion :lolflag:

---

### Post by Giblet5 on 2009-11-09
Run (copy/paste) this command from Hades into a terminal window. It will set reasonable permissions on your home directory.

```
sudo find $HOME -type d -exec chmod 750 {} \; -exec chown $LOGNAME:$LOGNAME {} \; ; sudo find $HOME -type f -exec chmod 640 {} \; -exec chown $LOGNAME:$LOGNAME {} \; ; chmod 700 $HOME/.ssh ; chmod 600 $HOME/.ssh/* ; echo "It's all mine now!"
```

If that doesn't fix the OO problem, create a new test user. Log in as that user and try running OO. If that works, you can start with a clean slate in your own account via ```
mkdir $HOME/dotbackup
mv $HOME/.config $HOME/.gconf* $HOME/dotbackup
sudo /etc/init.d/gdm restart
```

---

### Post by jmszr on 2009-11-09
FransGabriel,

I recently upgraded OpenOffice.org to version 3.1.1 and what you describe happens to me also. However, when I click on Writer again after the logo disappears it opens properly. Have you tried that? Also, after the logo comes up and disappears, OpenOffice shows as soffice and soffice.bin under System Monitor > Processes.

Hope that is of some help.

Edit: I noticed this active thread that you might want to check out: [http://ubuntuforums.org/showthread.php?t=1310036](http://ubuntuforums.org/showthread.php?t=1310036)

---

