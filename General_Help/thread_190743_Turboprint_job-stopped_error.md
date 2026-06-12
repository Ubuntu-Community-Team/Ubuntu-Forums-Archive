---
title: "Turboprint job-stopped error"
date: 2006-06-06
forum: General Help
---

### Post by emlee5 on 2006-06-06
Hi all

I've installed Turboprint on Dapper 6.06 as I am trying to get better printing results with my Canon i560 printer. Cups has recognised the printer as the default and I can send a file for printing. The printer icon appears but all I get is stopped: job-stopped.

Do I need to redirect the print file somehow.

Any help would be much appreciated.

](*,)

---

### Post by helpme on 2006-06-06
[QUOTE=emlee5]Hi all

I've installed Turboprint on Dapper 6.06 as I am trying to get better printing results with my Canon i560 printer. Cups has recognised the printer as the default and I can send a file for printing. The printer icon appears but all I get is stopped: job-stopped.

Do I need to redirect the print file somehow.

Any help would be much appreciated.

](*,)[/QUOTE]
Just speculation, but make sure that the printer is actually started. You can do this from the gnome printing manager.

---

### Post by emlee5 on 2006-06-07
[QUOTE=helpme]Just speculation, but make sure that the printer is actually started. You can do this from the gnome printing manager.[/QUOTE]

Thanks for the reply.

I made sure that the printer was active in the gnome priting manager, but the job-stopped error came again.

I did change the following file: /etc/turboprint/system.cfg to look like this:

TP_CUPS=1
TP_LANGUAGE=en
TP_CHARSET=C
TP_INSTALLATIONSTATE=0
TPBIN_BROWSER=firefox
TPFILE_PRINTCAP=/etc/printcap
TPPATH_CONFIG=/etc/turboprint
TPPATH_SHARE=/usr/share/turboprint
TPPATH_SPOOL=/var/spool/lpd
TPPATH_BIN=/usr/bin
TPPATH_FILTERS=/usr/share/turboprint/lib
TPPATH_DOC=/usr/share/turboprint/doc
TPPATH_LOG=/var/log
TPPATH_TEMP=/tmp
TPPATH_MAN=/usr/share/man
TPPATH_CUPSDRIVER=/usr/share/cups/model
TPPATH_CUPSSETTINGS=/etc/cups/ppd
TPPATH_CUPSFILTER=/usr/lib/cups/filter
TPPATH_CUPSFILTER64=/usr/lib64/cups/filter
TPOWN_SPOOLDIR=lp
TPMOD_SPOOLDIR=0755
TPOWN_SPOOLFILE=lp
TPMOD_SPOOLFILE=0640

Perhaps there is something I should add here?

---

### Post by emlee5 on 2006-06-07
[QUOTE=helpme]Just speculation, but make sure that the printer is actually started. You can do this from the gnome printing manager.[/QUOTE]

Thanks for the reply.

I made sure that the printer was active in the gnome priting manager, but the job-stopped error came again.

I did change the following file: /etc/turboprint/system.cfg to look like this:

TP_CUPS=1
TP_LANGUAGE=en
TP_CHARSET=C
TP_INSTALLATIONSTATE=0
TPBIN_BROWSER=firefox
TPFILE_PRINTCAP=/etc/printcap
TPPATH_CONFIG=/etc/turboprint
TPPATH_SHARE=/usr/share/turboprint
TPPATH_SPOOL=/var/spool/lpd
TPPATH_BIN=/usr/bin
TPPATH_FILTERS=/usr/share/turboprint/lib
TPPATH_DOC=/usr/share/turboprint/doc
TPPATH_LOG=/var/log
TPPATH_TEMP=/tmp
TPPATH_MAN=/usr/share/man
TPPATH_CUPSDRIVER=/usr/share/cups/model
TPPATH_CUPSSETTINGS=/etc/cups/ppd
TPPATH_CUPSFILTER=/usr/lib/cups/filter
TPPATH_CUPSFILTER64=/usr/lib64/cups/filter
TPOWN_SPOOLDIR=lp
TPMOD_SPOOLDIR=0755
TPOWN_SPOOLFILE=lp
TPMOD_SPOOLFILE=0640

Perhaps there is something I should add here?

---

### Post by coolclassic on 2006-06-07
Have a look  at "xtpsetup" you should be able to start services from there. Also are you using the correct configuration file.

---

