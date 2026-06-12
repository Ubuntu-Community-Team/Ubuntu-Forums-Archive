---
title: "Run Level scripts do not start on startup"
date: 2010-02-03
forum: General Help
---

### Post by tayran on 2010-02-03
Hi all,

I am using a Kubuntu 9.10 as a server machine. I upgraded it from Kubuntu 9.04 Beta. My problem is that although all scripts are present and executable in /etc/init.d and all links are also present in rc*.d directories, when i restart the machine they are not started automatically.

When i run init 2 or init 5 command after the startup all the scripts load normally.

Scripts are mostly installed by apt-get but only one script for tomcat was installed by me manually using update-rc.d command.

What should i do to automate those scripts on startup?

Thanks

---

### Post by tayran on 2010-02-08
I found a clue that may help. When i run runlevel command it says unknown although /var/run/utmp file exists and i see $RUNLEVEL and $PREVLEVEL as empty. Also after running init command /var/run/utmp does not change but runlevel command gives "N 2" this time.

No runlevel is initialized until entering kde gui mode. How can that be possible?

If it may help the content of the /proc/cmdline is:

root=UUID=9ab91724-2277-47c5-8fa5-c967286b9542 ro quiet splash

---

