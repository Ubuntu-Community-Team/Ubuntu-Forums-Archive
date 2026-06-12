---
title: "Kernel Update Breaks Installation"
date: 2010-03-05
forum: General Help
---

### Post by Jonah Bron on 2010-03-05
Hello, world!

It seems that updating the Kernel breaks my installation.  I've tried it twice, and both times it disabled my gui desktop.  I'm posting this with links2 in my terminal.  The terminal works perfectly.

This is really annoying, as I can't even use my computer.  What do you think is the problem?

Thanks,
Jonah Bron

---

### Post by patchwork on 2010-03-05
Are you using a proprietary driver not included with ubuntu?

I am using nvidia 195.30, and need to remove the nvidia 173.xx driver, reinstall the 195.30 and modprobe it in after every kernel update.  Could be that you are experiencing something similar.

---

### Post by Jonah Bron on 2010-03-05
Unless Ubuntu is installing them itself, there's no way I am using proprietary drivers (my grpahics are ATI).  After installation, I went straight to the update manager.  After it finished (Kernel and all) I rebooted, and my desktop didn't work.  The login screen works, though.  When it auto-logins, I get a black screen with a white square containing a terminal in the top-left corner.

---

### Post by patchwork on 2010-03-05
Ubuntu loads open source drivers by default, and the fact that your GDM is loading correctly leads me to believe that the video driver is not at fault.  If you drop to console using CTRL+ALT+F1, is there any information left on that screen indicating a problem with X?

EDIT:  Also check to see if you have a file named .xsession-errors (in your home directory)

---

### Post by Jonah Bron on 2010-03-05
Yes, I do have that file.  Here are the contents:
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinput/xinput.d/default.
xterm: fatal IO error 11 (Resource temporarily unavailable) or KillClient on X server ":0.0"
Xsession: X session started for jonah at Fri Mar 5 12:45:55 PST 2010
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinput/xinput.d/all_ALL linked to /etc/X11/xinput/xinput.d/default.
waitpid(): No child process

```

---

### Post by Jonah Bron on 2010-03-05
I realize bumping is generally frowned upon, but this is a really severe problem.  Does anyone know what is causing this problem?

---

### Post by patchwork on 2010-03-05
Your X server seems to be starting (because you can see the GDM login screen), and then malfunctioning ( I understand you see a graphical terminal window, as opposed to the console login?).  
Can you access your /var/log/Xorg.0.log?  
I saw the fatal error in your xsession.error log, but it didn't ring any bells with me.  Maybe there is something a bit more descriptive in your Xorg.0.log

EDIT:  and from the other thread, your x server is running, that is why that pid showed up.   To restart your server you would enter sudo service gdm restart, or sudo service gdm stop && sudo service gdm start.

---

