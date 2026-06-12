---
title: "Compiz autorestart - how?"
date: 2010-05-28
forum: General Help
---

### Post by Lockheed on 2010-05-28
Compiz often keels over and then I have to restart the comptuer because even though I made a special script to restart it, I am unable to invoke it as I cannot change active window.

However, since Metacity restarts itself, so should compiz. The question is - how?

---

### Post by blchinezu on 2010-05-28
run this script at startup:

```
#!/bin/bash
while [ "1" = "1" ]; do
compiz --replace
done
```

I don't know if there is a more elegant approach of the problem but this is how I 'solved' the compiz random die problem.

---

### Post by WorMzy on 2010-05-28
If you install compiz-fusion-plugins-extra, you get a crash handler plugin which you can configure.

[[img]http://www.ubuntu-pics.de/thumb/72555/compizconfig_settings_manager_038_dDV4Vv.png[/img]](http://www.ubuntu-pics.de/bild/72555/compizconfig_settings_manager_038_dDV4Vv.png)

Not only will this allow you to run metacity to take compiz's place in the event of a crash, it'll also create a crash log for you to examine and try to find out what's causing the crashes.

---

### Post by Lockheed on 2010-05-28
Thanks. I don't really want Metacity to kick in so I think I gonne go for a script. However, stupid question I have now - how do I make this script run at startup? Should I make the file executable and add to startup applications or in some other way?

---

### Post by blchinezu on 2010-05-29
in the gnome menu > preferences > startup applications
set whatever you want in the name and comment fields and:
```
bash **/path/to/script**
```in the command field
*/path/to/script* should obviously be the target script path


or you can do as WorMzy says... i never actually noticed that plugin... 
instead of **metacity** write **compiz --replace** and make sure that the plugin is activated and the *Start other window manager* option is checked
but it's not working as good as the script :) if i **killall compiz** it won't restart itself, while the upper script starts compiz

---

### Post by Lockheed on 2010-06-04
> **blchinezu said:**
> run this script at startup:

```
#!/bin/bash
while [ "1" = "1" ]; do
compiz --replace
done
```

I don't know if there is a more elegant approach of the problem but this is how I 'solved' the compiz random die problem.

Can this script be used for keeping other programs running as well?

---

