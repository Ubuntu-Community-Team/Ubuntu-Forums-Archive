---
title: "problem with desktop and delete user"
date: 2006-03-20
forum: General Help
---

### Post by harys on 2006-03-20
hi,i got ubuntu installed on my laptop but i could'nt run amministration tasks from   my desktop. when i click on my amministration networking i'm asked for the root password and when i enter it a message appear that it's wrong, i tried several times but the same matter. when i entered the password of my session user i didn't have anything and now whenever i click on for example system administration networking it run and then stops and disappear.
i used the command line userdel to delete all the user and i created a new one with adduser. when i wanted to login session with the new user i created i get this message in a wizard [your$home /.dmrc file has incorrect permissions and is being ignored. this prevents the default session and language from being saved.File should be owned user and have 644 permissions. ] i clicked ok and have this second wizard [your session has lasted less than 10 seconds.If you have not logged out your self this could mean that there is some installation problem or that you may be out of diskspace :try logging in with on of the failsafe sessions to see if you can fix the problem ;)there is a small box view details (x-/.xsession-errors file) on which when i click it showed :
. /etc/gdm/presession/default : registrering your session with wtmp and utmp
. /etc/gdm/presession/default : running /usr/bin/x11/sess reg -a -w /var/log/vtmp -u-/var/run/utmp -x "/var/lib/gdm/:0.xservers" -h""-L" :0" "michel
. /etc/gdm/xsession : beginning session setup could not set node 0700 on private per user gnome configuration directory /home/michel/gnome2_private/' :operation non permitted.

*[size=1]Locked due to double posting - Artificial Intelligence*[/size]

---

