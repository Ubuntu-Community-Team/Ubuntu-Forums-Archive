---
title: "Sticking program"
date: 2011-09-02
forum: General Help
---

### Post by Ted3929 on 2011-09-02
I keep receiving notifications that an update for a program called tvpvrd is awaiting me but it always fails.

I've tried uninstalling the program via synaptic and the remove command via terminal but it still remains and won't disappear and it resists all efforts to be uninstalled.

As a result I'm always getting notifications for this one update that can't be installed.

Like I said, I've tried uninstalling via Synaptic (it doesn't show in Ubuntu Software Center) and have used the ever-popular -f command via the terminal.

Anybody have an idea how to get rid of this bug?

---

### Post by ggeminii on 2011-09-02
check whether it has added any cron jobs.Check files in /etc/cron* for tvpvrd.
And if you want to remove the program run these commands.
1.updatedb
2.locate tvpvrd

and delete the files printed by locate command which you think may belong to the program

---

### Post by Ted3929 on 2011-09-02
Maybe I should clarify.  This is the error being posted.  It's asking for a reinstall before I can uninstall but neither process is working.  I can remove the program nor can I install it to remove it.


installArchives() failed: dpkg: error processing tvpvrd (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 tvpvrd
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

---

### Post by terrybbarton on 2012-01-05
Does anyone have a solution yet?

I am also having this exact same issue with tvpvrd in ArtistX Which is based on Ubuntu I think version 11. It is almost impossible to use the package managers because of the errors and hangups.

---

### Post by terrybbarton on 2012-01-05
Some Google searching and trying seemed to yield success:

I'm sure it was not all necessary, and there probably is a better way. However this seemed to fix mine.

[COLOR="Red"]Warning[/COLOR] - Running commands after the command "[FONT="Courier New"]sudo su[/FONT]" can be very dangerous especially ones like the "[FONT="Courier New"]rm[/FONT]" command below. My knowledge is limited and I don't know that I am not breaking tvpvrd or anything else.

I Launched Terminal under Accessories in the Ubuntu menu.

then typed in the following commands with enter at the end of each line.

[FONT="Courier New"]sudo su
apt-get -f install
apt-get upgrade
dpkg -i --force-all /var/cache/apt/archives/tvpvrd*[tab key]*
rm /etc/init.rd/tvpvrd
dpkg -i --force-all /var/cache/apt/archives/tvpvrd*[tab key]*
apt-get upgrade
apt-get -f install
exit
exit[/FONT]

Hopefully this information is helpful to somebody.

---

