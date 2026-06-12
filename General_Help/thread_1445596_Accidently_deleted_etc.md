---
title: "Accidently deleted /etc"
date: 2010-04-02
forum: General Help
---

### Post by PlatosGimp on 2010-04-02
In a made rush working on various things, I clicked the wrong folder to "Send to Trash" and sent /etc to Trash through Nautilus opened as root. However, the /etc folder IS NOT in Trash? Nor is there an "Under Move to Trash" or anything like that.

So is my Ubuntu install hooped? Running 9.10 x64

---

### Post by koolblue3 on 2010-04-02
Hi,

Can you open the trash bin from Nautilus as root?

---

### Post by srs5694 on 2010-04-02
From a text-mode console (Terminal, Konsole, xterm, or whatever), type:

```

sudo find /root -name etc

```

With any luck, you'll get a result, such as /root/.Trash/etc. If not, try again but type your home directory ("/home/{whatever}") instead of /root. If you find something with either search, type:

```

cp -a /root/.Trash/etc /

```

Change the path to etc as necessary. Note that there's a space between "etc" and "/" in this command. After you reboot to test it, you can safely delete the /root/.Trash/etc directory -- or better yet, move it into /root to serve as a backup should something like this ever happen again!

Good luck!

---

