---
title: "cannot get php to pass a shell argument"
date: 2006-04-19
forum: General Help
---

### Post by thespinesplitter on 2006-04-19
hello to everyone, ive been banging my head on the table for quite some time now with the vlc HTTP interface, Apache and PHP

BTW i am not experienced with apache and its allready configured also, im no coder but i can interpret code very quickly with a bit of research.

this is part of my apaches server index page:

```
index.html
<html>
<center>
<br><br><br><FORM METHOD="LINK" ACTION="vlc.php">
<INPUT TYPE="submit" VALUE="Start VLC">
</FORM>
<FORM METHOD="LINK" ACTION="http://youll-never-know.org:4358">
<INPUT TYPE="submit" VALUE="Gotto Remote">
</FORM>
<FORM METHOD="LINK" ACTION="closevlc.php">
<INPUT TYPE="submit" VALUE="Close VLC">
</FORM>
</center>
</html>
```

php code to start vlc:

```
vlc.php
<?php
system("(/usr/bin/vlc /home/spine/video --intf=http --http-host 192.168.1.100:4358 --fullscreen) >nul");
?>

```

close vlc

```
closevlc.php
<?php
system("(killall vlc) >nul");
?>

```

bassically i cannot get php to pass a single shell argument,
i also tried exec() with no luck


any help - much appreciated

---

### Post by thespinesplitter on 2006-04-19
libdvdnav: Using dvdnav version 0.1.9 from [http://dvd.sf.net](http://dvd.sf.net) libdvdnav: Can't read name block. Probably not a DVD-ROM device.

i get this error without nul

---

### Post by TomB on 2006-04-21
Try the shell_exec(); function

---

### Post by thespinesplitter on 2006-04-22
bump!


i tried that.

---

### Post by FedeKrum on 2006-05-23
[http://ar2.php.net/manual/en/function.escapeshellarg.php](http://ar2.php.net/manual/en/function.escapeshellarg.php)
[http://ar2.php.net/manual/en/function.escapeshellcmd.php](http://ar2.php.net/manual/en/function.escapeshellcmd.php)

I hope it helps
FedeKrum

---

