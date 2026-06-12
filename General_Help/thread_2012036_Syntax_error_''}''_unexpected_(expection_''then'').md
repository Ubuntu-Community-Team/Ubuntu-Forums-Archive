---
title: "Syntax error: ''}'' unexpected (expection ''then'')"
date: 2012-06-28
forum: General Help
---

### Post by KennerdsWayne on 2012-06-28
):P Hi guys... I'm newbie and I got a trouble when I'm set up a game server called Perfect World''...

But... at the last step to activate the server...
It showed an error...

[IMG]http://i1135.photobucket.com/albums/m625/KennerdsWayne/Problem.jpg[/IMG]

Inside common.inc.sh got these...
> #!/bin/sh

this_dir=/root

PwServer_Path=/usr/rain

Authd_Path=/usr/rain/ms_authd/build

Jetty_Path=/usr/rain/Jetty

Tomcat_path=/usr/local/jakarta-tomcat-5.5.9

Logs_Path=/usr/rain/logs

repairtime=5

DBTool_Path=/usr/rain/gamedbd

DB_Path=/usr/rain/gamedbd
UM_Path=/usr/rain/uniquenamed

Backup_Path=/root/backup
Romote_Backup_Path=/root/server/bk

DBRepair_Path=/root/repair/gamedbd/dbdata
UMRepair_Path=/root/repair/uniquenamed/dbdata

color_cyan="  [40;36m"
color_red="  [40;31m"
color_yellow="  [40;33m"
color_green="  [40;32m"
color_white="  [40;37m"
showmsg () {
	NO3_var=$3
	NO4_var=$4

	if [ ! "$NO3_var" ]; then
		NO3_var=$color_green
	fi

	if [ ! "$NO4_var" ]; then
		NO4_var=$color_white
	fi

	echo
	echo $NO3_var$1$NO4_var
	if [ "$2" ]; then
		echo $NO3_var$2$NO4_var
	fi
	echo
}

Original file...
[http://www.mediafire.com/?m4d7dzor8vn6reu](http://www.mediafire.com/?m4d7dzor8vn6reu)

I just a newbie without any knowledge to edit...
Please step by step to teach me if there is any idea to fix this.
Thank You.

---

### Post by dino99 on 2012-06-28
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9923](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9923)

---

### Post by KennerdsWayne on 2012-06-28
Sorry...
What were you giving...
Is an old version files and configs...
So~ That's nothing what I wanted inside that...

---

### Post by Vaphell on 2012-06-28
what does my_start look like?

---

### Post by KennerdsWayne on 2012-06-28
The original file of my_start:

[http://www.mediafire.com/?guam92ks5gwca5u](http://www.mediafire.com/?guam92ks5gwca5u)

---

