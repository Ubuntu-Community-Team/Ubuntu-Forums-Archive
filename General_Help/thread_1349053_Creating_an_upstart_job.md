---
title: "Creating an upstart job"
date: 2009-12-07
forum: General Help
---

### Post by wd5gnr on 2009-12-07
I wanted to run a service for my eyefi card when the machine starts up under my user ID but not associated with my login. 

Now, yes, I know I can use rc.local (and I have). But I wanted to be "modern" and use upstart. So I read the documentation. Nothing I do seems to work. 

Here's what I have (although I've tried lots of variations):
[PHP]
# Eye fi server run as user alw
description	"Receive network transmission from EyeFi"
start on filesystem
stop on runlevel [016]

expect fork
respawn

script
exec /usr/bin/sudo -u alw /usr/bin/python /usr/local/eyefi/EyeFiServer.py -c /usr/local/eyefi/DefaultSettings.ini
end script

[/PHP]

It seems like I either get a return saying it started (but it didn't) or it just hangs when I issue "sudo start eyefi".

For now I am back to using rc.local, but it bugs me when I can't figure something out.

Yes I have read the FAQ and WIKI at:
[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

### Post by wd5gnr on 2009-12-09
Actually that sudo should be:

su alw -c '---'

Still have not made this work except by putting it in rc.local.

---

