---
title: "How do I make a terminal script?"
date: 2006-04-06
forum: General Help
---

### Post by Bonkerz on 2006-04-06
Everytime I reboot I have to reconfigure the Netgear MA111 v1 wireless USB adapter via linux-wlan-ng. Any idea how to set it so that it runs those terminal commands upon startup? Would be great help.

---

### Post by FryerFox on 2006-04-06
Create a text file using gedit or your favorite editor and start it with:
```
#!/bin/bash
```
The '#!' is sometimes called the she-bang and it denotes that the file is a script to be executed using /bin/bash (the bash shell).

Then put in the commands you want executed and make the file executible:
```
chmod 755 file.sh
```

If you want it executed whenever you boot up, you can put the file in the /etc/init.d directory. An example of a boot-up script is:
```
#! /bin/sh

case "$1" in
  start)
        startup_stuff
        ;;
  stop)
        shutdown_stuff
        ;;
esac

exit 0
```

---

### Post by John.Michael.Kane on 2006-04-06
@Bonkerz this may help.
[http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal)
[http://www.tldp.org/HOWTO/HOWTO-INDEX/howtos.html](http://www.tldp.org/HOWTO/HOWTO-INDEX/howtos.html)                                                  [http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)
[http://www.linuxprofilm.com/articles/linux-daemon-howto.html](http://www.linuxprofilm.com/articles/linux-daemon-howto.html)
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

