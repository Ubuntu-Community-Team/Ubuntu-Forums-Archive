---
title: "Ubuntu host file to bloack ads help"
date: 2009-11-01
forum: General Help
---

### Post by dragon84 on 2009-11-01
Hi Ubuntu users,
i was wondering if anyone here knows how to modify the hosts file found in /etc/ to block ads. Back in the days when i was using windows i would go to the mvps, get the ad links nad paste it into the host file along with the ip 127.0.0.1.

i have read the threads before this, that teaches you how to modify ubuntu's hosts file but i have no success. i can still accesss adbrite. 

this is what i have done already. went to mvps to view the txt files with adlinks             (eg. 127.0.0.1            adbrite.com), put that into the hosts file using sudo gedit /etc/hosts, put it and the end of the file, and restarted the comp. after all that i can still access adbrite.com. 

can anyone tell me the proper step for this?

many thanks

---

### Post by sliketymo on 2009-11-01
Your on the right track.Place them right below:
127.0.0.1  local host
127.0.0.1  xxxxx-desktop
MVP'S HERE

above the loopback info.I just tried adbrite.com,got blank page.

---

### Post by 133794m3r on 2009-11-01
> **dragon84 said:**
> Hi Ubuntu users,
i was wondering if anyone here knows how to modify the hosts file found in /etc/ to block ads. Back in the days when i was using windows i would go to the mvps, get the ad links nad paste it into the host file along with the ip 127.0.0.1.

i have read the threads before this, that teaches you how to modify ubuntu's hosts file but i have no success. i can still accesss adbrite. 

this is what i have done already. went to mvps to view the txt files with adlinks             (eg. 127.0.0.1            adbrite.com), put that into the hosts file using sudo gedit /etc/hosts, put it and the end of the file, and restarted the comp. after all that i can still access adbrite.com. 

can anyone tell me the proper step for this?

many thanks
Are you using firefox? If so why not just get ADblock plus. It does exactly what your'e wanting to do except without having to worry about memorizing  all the random links and such. If you're using a different browser then i have no idea what to tell you.

---

### Post by dragon84 on 2009-11-02
wow thanks guys!!!!i put in teh mvps links into the host file and it works straight away. not too sure why it didnt work on my computer at work though. but thansk guys for helping out :D

---

