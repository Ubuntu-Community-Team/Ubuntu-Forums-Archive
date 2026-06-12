---
title: "Intermittent problem running Nail at boot"
date: 2011-03-31
forum: General Help
---

### Post by abeliever on 2011-03-31
Intermittent problem running Nail at boot.

New to Linux(but learning lots), I am running Ubuntu 10.04 LTS and have installed nail( and motion) on 2 machines( I will call A & B).  Nail is functioning sending e-mail form both A & B even when invoked from a script as below.

However, the nail command does not send e-mail on machine A whether launched directly from rc.local or from within a scrip launched from rc.local. The echo commands are working around nail.  Thus, I know that the script is working.  Both nail and the script work fine when launched from a terminal interactivley.  Is there a problem with .msmtprc or .mailrc( but they are the same in both machines)?  .msmtprc adn .mailrc work fine when nail is used in a terminal.  I can provide these files with privacy modifications if needed.  Please, give lots of detail as I am new to Linux.  I am greatful for any ideas.

#!/bin/sh
# Name of this file =           /etc/init.d/mydate.sh
sleep 15
echo "Time + 15sec = $( date +%Y%m%d%T)" > /home/john/date.txt
sleep 45
nail -A gmail -s "fdcc boot" [EMAIL="johndoe@gmail.com"]johndoe@gmail.com[/EMAIL] < /home/john/date.txt
sleep 30
echo "post delay." >> /home/john/date.txt

The sleep SEC commands were added to allow for complete boot before nail is invoked.  I even tried update-rc.d to add the script to the boot process.  I can tell that the mydate.sh ran as date.txt was created but nail did not.

Hard ware:
Machine A:
ASUS PTGD1-LA PufferM UL8E
512 meg ram
video HP 5187-6145

Machine B:
Grouper PTGD1-LA GL8E
256 meg ram
video: on board.

---

