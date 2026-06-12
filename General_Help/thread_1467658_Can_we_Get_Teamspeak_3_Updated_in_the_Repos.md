---
title: "Can we Get Teamspeak 3 Updated in the Repos"
date: 2010-04-30
forum: General Help
---

### Post by ToxicBurn on 2010-04-30
Not sure where to ask but can we get teamspeak 3 in the repo ?

Version 2 is not used anymore and the people over at [www.teamspeak.com](www.teamspeak.com) said it was ok to add it to our repo as long as we do not modify it.

---

### Post by darkshines87 on 2010-06-07
I agree, it would be very convenient if TS3 was shipped in the repos, not only TS2.

---

### Post by arloth on 2010-10-19
I think the only way it's going to get put in is through a 3rd party.  Just like Wine is done through ubuntu-wine ppa.  Samba, parted, and bluez through polslinux ppa (many thanks for this one), and Audacious etc with webupd8.. Granted the ones I just listed may not be quite updated to maverick yet.

If you want working OpenMotif, you still have to do manually with the .deb unfortunately. Seriously, look at what version ubuntu comes with vs. the one currently available.  You'll cry when you figure out how old it is.

The best bet would be to see if it could be included in one of these 3rd party repositories, or make one for it ourselves.  The bug report on it has been open quite a while.  [https://bugs.launchpad.net/bugs/572853](https://bugs.launchpad.net/bugs/572853)

---

### Post by supermorph on 2011-03-23
they kinda did modify (mabye not the actual data) the teamspeak 2 install

its nowhere near like the "downloadable" teamspeak 2 installation


before i explain, i will admit my setup is kinda custom
but the extracted folders from teamspeak 2 and three is all within thier destined folders, and not scattered all over the place like
the teamspeak-server app (ts two at this moment of typing)

heres my setup:

im trying to build a catagorised foler

e.g

clients x86 & x64 = /teamspeak/client/x86/two
clients x86 & x64 = /teamspeak/client/x86/three
clients x86 & x64 = /teamspeak/client/x64/two
clients x86 & x64 = /teamspeak/client/x64/three


servers x86 & x64 = /teamspeak/server/x86/two
servers x86 & x64 = /teamspeak/server/x86/three
servers x86 & x64 = /teamspeak/server/x64/two
servers x86 & x64 = /teamspeak/server/x64/three

and i am trying to botch together a bunch of scripts for init.d folder

so i can do either of: 

32-bit:

update-rc.d -f ts2x86 defaults
update-rc.d -f ts3x86 defaults

64-bit:

update-rc.d -f ts2x64 defaults
update-rc.d -f ts3x64 defaults

this way i can literally make my OWN remastersys iso for each cpu type
and just literally run one of the commands above 
(or both if ts2 & 3 is wanted)

i did have a9.04 custom dvd i made
really i want to use that. (not because its old, but i like the way its more sharp and not shiny like new ubuntu versions)
and also because its customised by myself.

i am working on 10.04 (x86) and 11.04 (x64) on another partition
as i want it to be very strait forward and simple regardless of version.

i use dynamic dns, and up until recently i was able to use my router with a dedicated (virgin media) dsl modem (i moved up to 50Mb)
which required an all in one so i had to use inadyn (for anyone who doesnt know, its an open source / free software dynamic dns client)

i use my own setup inadyn.conf

(contents changed to hide my data)

--username username
--password password
--update_period 60000
--alias some-title.dyndns.org
--background

(eof)

so i can say it kinda works but im having a little difficulty getting a ts2 script to stop it or restart 
(only either a service level change or reboot does it)


i made a user called ts3s (very basic user, no admin anything)
and made all teamspeak folders ts3s owned 

init.d script

ts2x86
======

#! /bin/sh
### BEGIN INIT INFO
# Provides: teamspeak
# Required-Start: networking
# Required-Stop:
# Default-Start: 2 3 4 5
# Default-Stop: S 0 1 6
# Short-Description: TeamSpeak 3 Server Daemon
# Description: Starts/Stops/Restarts the TeamSpeak 2 Server Daemon
### END INIT INFO

set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="TeamSpeak 2 Server"
NAME=tss2server
USER=ts3s
DIR=/teamspeak/server/x86/two
DAEMON=$DIR/teamspeak2-server_startscript
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/ts2x86

# Gracefully exit if the package has been removed.
test -x $DAEMON || exit 0

cd $DIR
sudo -u $USER ./teamspeak2-server_startscript $1

(eof)

admittedly it doesnt have a stop command, because i have been messing around with scripts on the web to try and put one in, but to no avail.

it is the same for ts3 (which for some unknown reason DOES stop)

ts3x64
======
#! /bin/sh
### BEGIN INIT INFO
# Provides: teamspeak
# Required-Start: networking
# Required-Stop:
# Default-Start: 2 3 4 5
# Default-Stop: S 0 1 6
# Short-Description: TeamSpeak 3 Server Daemon
# Description: Starts/Stops/Restarts the TeamSpeak 3 Server Daemon
### END INIT INFO

set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="TeamSpeak 3 Server"
NAME=ts3server
USER=ts3s
DIR=/teamspeak/server/x64/three
DAEMON=$DIR/ts3server_startscript.sh
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/ts3x64

# Gracefully exit if the package has been removed.
test -x $DAEMON || exit 0

cd $DIR
sudo -u $USER ./ts3server_startscript.sh $1

(eof)

as you can see, no real changed apart from titles (scripts/pid names)

any help would be wonderful, but i am far from a programmer,
im not a copy and paster, more like a franken-stein tester lol

sorry for the long posting,
i wanted to share my findings/doings for others to help

i would like to GPL v2 this information (except any content of teamspeak)
which it is known to be propriatary software. :-)
and also to note, this is for my personal usage, 

what i shared here is more of "how i did it" than a "heres how, friend"
(just to cover my A$$ :-p)

kind regards,
supermorph

p.s my stance on the update ts3 instead of ts2 is not good
it should in my view have a seperate app e,g "teamspeak3-server"

then folks have a choice (e.g if they had a windows one and wanted to port it to linux by copying the database files)

question: does this class me as computer OCD with folders? lol

---

