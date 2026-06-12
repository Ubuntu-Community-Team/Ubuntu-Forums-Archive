---
title: "newbie needs helps setting up some servers"
date: 2010-03-20
forum: General Help
---

### Post by nerdy_kid on 2010-03-20
i have three pcs, a 3.6 ghz desktop running a http server and an openssh server, a dual core 1.4 ghz laptop, and a 1.6 ghz headless pc doing nothing whatsoever.

I am trying to learn more about server stuff, and the best way i learn is by doing.  I would like to turn the 1.6 ghz pc into a backup web server that automaticly hosts my files once the 3.6 ghz main server goes down.  How would i go about doing this?  any good sites for newbies on this general subject?  thanks!

---

### Post by joedoe47 on 2010-03-20
I think cron jobs might help, then again I'm a noob my self when it comes to ubuntu servers. any help?

---

### Post by eginon on 2010-03-20
Hi,

Maybe some information here would help:
[http://www.linux.org/docs/ldp/howto/DNS-HOWTO.html](http://www.linux.org/docs/ldp/howto/DNS-HOWTO.html)

There are probably way better, and more efficient, ways to do all this. But if I were to try it with what I know right now, today I would...

probably go in and turning off the dhcp (if I was using it) in my router and manually set the IP on the main server. Then have my backup just sit in an infinite loop and reach out and ping the main at some interval. If the main failed to respond then let that be a trigger to force the backup to (via a bash or a python script) to reconfigure itself and take over the main's IP address.

---

### Post by nerdy_kid on 2010-03-22
thanks for all the replies!
now about dhcp, if i turned it off then every pc that i connected i would have to assign a manual ip, correct?  cause that might suck.
This is gonna be fun hehe :)

---

### Post by john newbuntu on 2010-03-22
Assuming that you have all your web service data on the 3.6GHz PC, you might want to use something like rsync periodically to get the data over to the other box.  This way, your data stays in sync.  The rest is just adjusting your DNS and starting the appropriate web servers which has already been pointed out.  

But perhaps there are better automated options for failover implementations that I am unaware of.

---

### Post by nerdy_kid on 2010-03-24
ok, so i added a custom dns entry in my router called "web-server" with ip 192.168.1.6.  Then i wrote some probably horrible scripts:

this on will run on the backup server:
```

#!/bin/bash
#backup server script

HOSTNAME=`hostname` #pent4server

while ping -c 2 -i .2 -q -w 1 web-server
do
  if [[ `hostname` != $HOSTNAME ]] ; then
      echo "incorrect hostname, fixing"
      hostname $HOSTNAME
  fi

  sleep 10s
done

echo "server detected down, taking over"
hostname web-server
#restart the webserver
/etc/init.d/apache restart

while ! ping -c 2 -i .2 -q -w 1 jesse-desktop
do
  sleep 30s
done

echo "main server back up"
hostname $HOSTNAME
#restart the webserver
/etc/init.d/apache2 restart

```

and this will run on the main server:
```

#!/bin/bash
#main server script

HOSTNAME=jesse-desktop #should = jesse-desktop

while ping -c 2 -i .2 -q -w 1 web-server
do
#backup server is up, wait till it sees us
  if [[ `hostname` != $HOSTNAME ]] ; then
      echo "incorrect hostname, fixing"
      hostname $HOSTNAME
  fi

  sleep 10s
done

#server saw us, take over the hostname
hostname web-server
#restart the webserver
/etc/init.d/apache2 restart

```

they seem to work fine, but how do i get the router to reassign my ip once i change my hostname? or am i doing this totally wrong ?(probably lol but im new at this :D)

thanks :)

[edit] after i do hostname webserver then i ping web-server, i get one packet then nothin.
[edit2] ok i got it to change the hostname by running sudo dhpclient after, but the ip is still wrong.  the router makes a new entry for web-server with the same ip as the old hostname :( i might be able to get it to work anyway though.  apprecate any help! :)

---

### Post by nerdy_kid on 2010-03-24
nope...not working.  Is it possible that the router cant do what i need it to do?

---

### Post by nerdy_kid on 2010-03-25
help?

---

### Post by nerdy_kid on 2010-03-26
i can get the hostname to change with sudo hostname sudo dhclient -r sudo dhclient, and i can change my LAN IP with sudo ifconfig eth0 IP but that cuts my internet connection off so its kinda useless....cant figure out how to disable the DNS server on my router :(

---

