---
title: "Amarok conky script not working"
date: 2010-03-15
forum: General Help
---

### Post by whiterabbit7500 on 2010-03-15
I'm trying to get my conky configuration to show the current track in amarok, using [this]("http://conky.sourceforge.net/amarok-ke49") script. After reading several forums and post about it, it should be working, but it's still not. related data from config file below.

```
$stippled_hr
${color}${alignc}Now Playing${color white}
${alignc}${execi 10 /home/whiterabbit/Desktop/Scripts/amarok_conky.sh artist}
${alignc}${execi 10 /home/whiterabbit/Desktop/Scripts/amarok_conky.sh title}
${execibar 1 /home/whiterabbit/Desktop/Scripts/amarok_conky.sh progress}
${alignc}"${execi 10 /home/whiterabbit/Desktop/Scripts/amarok_conky.sh album}"
```

When I run conky from a terminal, I get the output
```
ERROR: Couldn't attach to DCOP server!

```

Ok, so the problem seems to be coming from the fact that DCOP is no longer used on KDE4. How would I convert this script to work with DBUS?

The script has not been modified form the link posted...someone help please!! :-)

---

### Post by arbos on 2010-04-26
Use this script from [http://github.com/crshd/amarok-conky/blob/master/amarok-data]("http://github.com/crshd/amarok-conky/blob/master/amarok-data")

---

