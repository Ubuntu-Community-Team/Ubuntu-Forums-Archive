---
title: "cron.daily not running jobs"
date: 2012-09-20
forum: General Help
---

### Post by philled on 2012-09-20
I have recently created a 12.04 Mythbuntu machine (though I don't believe this is specific to Mythbuntu - I think it's a Ubuntu issue). I have some jobs in /etc/cron.daily but they're not running.

I get lines in /var/log/syslog such as:
[FONT=Courier New]Sep 19 07:54:47 mbe anacron[1824]: Job `cron.daily' terminated (mailing output)[/FONT]

And I get emails with cron.daily which say:
[FONT=Courier New]3 incorrect password attempts ; TTY=unknown;+PWD=/home/phill ; USER=root ; COMMAND=/usr/bin/software-center
[FONT=Arial]
The scripts I want to execute in /etc/cron.daily are executable and owned by root.

[/FONT][/FONT]I think it may be some sort of /etc/sudoers issue [FONT=Courier New][FONT=Arial]but I don't know how to fix it.[/FONT][/FONT] My /etc/sudoers file looks like this:

[FONT=Courier New]# This file MUST be edited with the 'visudo' command as root.
#
Defaults        env_reset
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
# Host alias specification
# User alias specification
# Cmnd alias specification
# User privilege specification
root    ALL=(ALL:ALL) ALL
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL
# See sudoers(5) for more information on "#include" directives:
#includedir /etc/sudoers.d

[FONT=Arial]Can anyone please advise what I need to do to fix this?[/FONT]
[/FONT]

---

### Post by f8l_0e on 2012-09-20
I think this link might help: [https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/996753]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/996753")

It is not actually a bug, but a security feature. If I am reading the report correct you would want the following line as the last line of your /etc/sudoers file:
```
phill mbe = NOPASSWD: /usr/bin/software-center
```

---

### Post by philled on 2012-09-20
> **f8l_0e said:**
> I think this link might help: [https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/996753](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/996753)
 
If I am reading the report correct you would want the following line as the last line of your /etc/sudoers file:
```
phill mbe = NOPASSWD: /usr/bin/software-center
```
 
Thank you. I did see that page but didn't understand it. Does it mean that every script that needs to run as part of cron.daily must have its own line in /etc/sudoers?

---

### Post by JKyleOKC on 2012-09-20
Since cron.daily runs as root, it should not need a password for any of its actions.

Did you write those scripts yourself, and add them to the cron.daily list?

If you did, did you prefix any commands (such as launching Software Center) with "sudo"? If you did, that's the cause of your problem. Sudo will ask for the password of the account under which it's run, and since "root" has no password, it will fail every time. Since the cron jobs run as root in the first place, they do not need sudo...

Hope this helps. If it doesn't, post one of the scripts here for us to examine. Surround it with code tags (click the "#" icon on the message editor toolbar and paste the script in between the two tags it will generate) so that it will be easy for us to read.

---

### Post by philled on 2012-09-21
> **JKyleOKC said:**
> Since cron.daily runs as root, it should not need a password for any of its actions.
Did you write those scripts yourself, and add them to the cron.daily list?
Hope this helps. If it doesn't, post one of the scripts here for us to examine. 

Hi, here's one of my scripts. It runs perfectly when I run it from the command line, but won't run from cron.daily.

```

#!/bin/bash
# -------------------------------------------------------------------------
# Script : get_xmltv.sh - Grab Australian TV listings
# Author : Phill Edwards
# Descn  : Ash downloads the listings and makes available on web server,
#          so get them from Ash over http.
# -------------------------------------------------------------------------

echo "" >> /tmp/get_xmltv.log
echo "get_xmltv started at `date`" >> /tmp/get_xmltv.log

# ---- Start config section -----------------------------------------------
FNAME=/home/phill/.xmltv/xmltvSydney.xml
RUN_MM=0                # Flag for whether to run moviematch.pl. 1=yes,0=no
# ---- End config section -------------------------------------------------

echo "Downloading TV listings from ash... at `date`" >> /tmp/get_xmltv.log

# Download TV listings from ash
wget http://ash.edwards.home/mythtv/xmltvSydney.xml --output-document=$FNAME

echo "Loading TV listings into MythTV DB... at `date`" >> /tmp/get_xmltv.log

# Load TV listings into mythtv database
### This is the command from vsn 0.25 onwards
mythfilldatabase --file --sourceid 1 --xmlfile $FNAME

# Get tv guide data from tvguide.org.au and then run moviematch.pl to update
# the DB with Movie categories.
if [ $RUN_MM -eq 1 ]
   then

   echo "Running moviematch.pl ..."

   wget --header="accept-encoding: gzip" --input-file=/home/mythtv/.xmltv/tv_gra
b_au_tvg.conf --output-document=- | gzip -d | sed 's/channel="SBS-NEWS"/channel=
"news\.sbs\.com\.au"/g ; s/channel="Seven-Syd"/channel="sydney\.seven\.com\.au"/
g ; s/channel="Ten-NSW"/channel="sydney\.ten\.com\.au"/g ; s/channel="SBS-NSW"/c
hannel="sydney\.sbs\.com\.au"/g ; s/channel="ABC2"/channel="abc2\.abc\.gov\.au"/
g ; s/channel="Nine-Syd"/channel="sydney\.nine\.com\.au"/g ; s/channel="ABC-NSW"
/channel="nsw\.abc\.gov\.au"/g' > /home/mythtv/.xmltv/xmltvSydney_tvg.xml

   chmod 777 /home/mythtv/.xmltv/xmltvSydney_tvg.xml

   /usr/local/bin/moviematch.pl
fi

echo "get_xmltv finished at `date`" >> /tmp/get_xmltv.log

```

---

### Post by philled on 2012-09-21
> **JKyleOKC said:**
> Since cron.daily runs as root, it should not need a password for any of its actions.
Did you write those scripts yourself, and add them to the cron.daily list?


Could the fact that cron.daily runs it as root be the problem? When I run it from the command line I run it from a non-root user and it all works fine. If I run it from the command line prefixed with sudo it, of course, asks for a password. If cron.daily causes it to require a password then it would fail. But how do you make cron.daily run it as non-root if this is the problem? 

Also, when you say "add them to the cron.daily list", I don't actually add them to any list. I just put them in /etc/cron.daily/ and they're supposed to execute automatically just by virtue of being in that dir, aren't they?

I'm coming from a CentOS background where these issues don't exist so this is new to me.

---

### Post by philled on 2012-09-21
I think I may have just found something relevant at [http://www.stereoplex.com/blog/etc-cron-daily-scripts-not-running-ubuntu](http://www.stereoplex.com/blog/etc-cron-daily-scripts-not-running-ubuntu)

The script I'm running has a dot in the filename. I then looked at the man page for run-parts and it says "If neither the --lsbsysinit option nor the --regex option is given then the names must consist entirely of ASCII upper- and lower-case letters, ASCII digits, ASCII underscores, and ASCII minus-hyphens".

I've changed the filename and I'll see whether it now runs in the morning. I don't remember that from CentOS so not sure if this is something to do with a new version of run-parts or some sort of Ubuntu configuration.

---

### Post by shreepads on 2012-09-21
What's in /usr/local/bin/moviematch.pl?

---

### Post by JKyleOKC on 2012-09-21
> **philled said:**
> I think I may have just found something relevant at [http://www.stereoplex.com/blog/etc-cron-daily-scripts-not-running-ubuntu](http://www.stereoplex.com/blog/etc-cron-daily-scripts-not-running-ubuntu)

The script I'm running has a dot in the filename. I then looked at the man page for run-parts and it says "If neither the --lsbsysinit option nor the --regex option is given then the names must consist entirely of ASCII upper- and lower-case letters, ASCII digits, ASCII underscores, and ASCII minus-hyphens".

I've changed the filename and I'll see whether it now runs in the morning. I don't remember that from CentOS so not sure if this is something to do with a new version of run-parts or some sort of Ubuntu configuration.That could be it. Apparently cron sorts the filenames before launching each in turn, and the dot would make the script hidden. It's possible that cron isn't picking up hidden files at all -- the remarks in "0anacron" sorta imply that could be the case, as does the man-page item you quoted.

If there's any sequencing requirement, you might precede the filenames with two-digit numbers (like the SysV /etc/rc* files do) to force the sequence you want. If you do, make certain to add another zero to "0anacron" to make sure it remains the first one executed.

As for cron requiring a password to run as root, it won't. It's already a child process of a root system and inherited its user ID from its parent. However it will NOT have your $PATH variable available, so commands and file names need to be absolute rather than relative. I don't think this is anything different from the RedHat/CentOS conventions, but it's been a few years since I abandoned Mandriva and came over to the Debian derivatives so I'm not certain of that.

EDIT--After studying the full man page for run-parts, I'm confident that it's the ".sh" part of the filename that's causing the problem. If cron used the --lsbsysinit switch to run-parts, it would probably work since the description of that namespace includes the dot, but by default it's forbidden and the description at the top of the man page explicitly says that such files are ignored. My presumption that you were using the dot to hide the file was totally wrong -- but had you done so, it would also have prevented the file from running.

---

### Post by kjohri on 2012-09-21
> # Script : get_xmltv.sh - Grab Australian TV listings

Try to rename your script as get_xmltv (leave out the .sh suffix) and see whether that makes a difference.

anacron and cron use run-parts to execute the scripts in cron.daily. run-parts does not execute scripts with names having special characters like ".". 

[http://www.softprayog.in/tutorials/anacron]("http://www.softprayog.in/tutorials/anacron")

---

