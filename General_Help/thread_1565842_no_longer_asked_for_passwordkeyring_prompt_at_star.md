---
title: "no longer asked for password/keyring prompt at start-up?"
date: 2010-09-01
forum: General Help
---

### Post by jimstar79 on 2010-09-01
Hi all, 

something strange has happened with my system following an update today. 

Been having trouble connecting to the internet and i am no longer being asked for password/keyring prompt at start-up. Something the prompt comes up 5-15 minutes after start-up. 

I even manually set 'password at login' but it doesn't even ask me for that?

ps: over here [HTML]https://wiki.ubuntu.com/LucidLynx/ReleaseNotes[/HTML] i found something about Avahi potentially causing a conflict with network configuration - so i typed the following command and am now online at least:

sudo stop avahi-daemon
sudo sed -e '/^start/,+1s/^/#/' /etc/init/avahi-daemon.conf

hope that helps someone. 

But what about the other problem?

thanks in advance for any help!

---

### Post by jimstar79 on 2010-09-01
considering the amount of interest this thread is generating i thought i should post an update!

Internet connection remains sporadic and painful!

---

