---
title: "Easier way to check PPA and update URL?"
date: 2010-11-07
forum: General Help
---

### Post by afrodeity on 2010-11-07
In order to fix the errors below, after upgrading I would have to visit each ppa individually to determine if it supports my current release/distribution. Is there an easier way to accomplish this, am thinking of a script, but my skills are rudimentary.

```

Failed to fetch http://packages.geexbox.org/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://mentors.debian.net/debian/pool/main/b/bashish/dists/squeeze/main/source/Sources.gz  404  Not Found
Failed to fetch http://mentors.debian.net/debian/pool/main/b/bashish/dists/squeeze/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://www.getdeb.net/playdeb-mirror/dists/maverick/lucid/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://download.opensuse.org/repositories/home:/midgardproject/dists/maverick/universe/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://apt.boxee.tv/dists/jaunty/main/binary-i386/Packages.gz  403  Forbidden
Failed to fetch http://le-web.org/repository/dists/stable/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/breathe-dev/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/freshgames/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/freshgames/ppa/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/freshgames/ppa/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/freshgames/ppa/ubuntu/dists/maverick/universe/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/freenx-team/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/fta/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/coolwanglu/scanmem/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/coolwanglu/scanmem/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/coolwanglu/scanmem/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/coolwanglu/scanmem/ubuntu/dists/maverick/universe/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/ibid-core/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/loell/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/openmetaverse/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/openmetaverse/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/shankao/opensimulator/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/gezakovacs/pdfocr/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/cavedon/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/cavedon/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu/dists/maverick/universe/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/scrawl/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/scrawl/ppa/ubuntu/dists/lucid/main/source/Sources.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/subdownloader-developers/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/team-xbmc-lucid/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/corenominal/ubuntu/dists/dists/intrepid/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/acire-team/acire-releases/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/akirad/akirad/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/akirad/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/amandeepgrewal/notifyosdconfig/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/canola/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/cybolic/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/deb-thumbnailer-team/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/freenx-team/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/gericom/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/gm-notify-maintainers/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/gnac-team/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/lernid-devs/lernid-releases/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/mixxxdevelopers/app/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/python-snippets-drivers/python-snippets-daily/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/ronmi/wallbox/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/sevenmachines/tor/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/silverwave/one-daily-a-month-1/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/stiff.ru/qmmp-svn/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/troorl/pino/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/tualatrix/gloobus/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/tvst-hotmail/cardapio/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/wormux/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/zachanimerulz/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://launchpad.net/epidermis/dists/maverick/main/binary-i386/Packages.gz  Undetermined Error [IP: 91.189.89.223 80]
Failed to fetch http://launchpad.net/epidermis/dists/lucid/main/source/Sources.gz  Undetermined Error [IP: 91.189.89.223 80]
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by dino99 on 2010-11-07
there are not much trusted ppa, that should not be a so big deal :)

[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by afrodeity on 2010-11-07
the script only checks gpg keys, not if the address is correct for the distribution and so on, but thanks.

---

### Post by mc4man on 2010-11-07
This will ck. and report on most ppa's, up to you to fix and or disable

[http://ubuntuforums.org/showthread.php?t=1594757](http://ubuntuforums.org/showthread.php?t=1594757)

---

### Post by afrodeity on 2010-11-07
many thanks, just what the doctor ordered.

---

### Post by delas6 on 2010-12-26
You are the guy, definitively, but I still got some troubles in doing all of the updates. Its just the last one anyways for the Pidgin software. I got a message displayed saying that not all of the updates could be installed. Any idea? Thanks in advance

---

