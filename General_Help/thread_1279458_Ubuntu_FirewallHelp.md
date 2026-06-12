---
title: "Ubuntu FirewallHelp?"
date: 2009-09-30
forum: General Help
---

### Post by scottishbloke on 2009-09-30
[SIZE=4]Hi,im new to ubuntu and im just wondering how i go about setting up the ufw firewall?any help will be much appreciated:guitar:[/SIZE]

---

### Post by credobyte on 2009-09-30
What do you mean by "setting it up" ?

```
sudo ufw enable
sudo ufw default deny
```

After that, just follow the guide: [http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html](http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html)

---

### Post by scottishbloke on 2009-09-30
[SIZE=3]Thanks vey much for that so with them commands you gave is that all i need to do,im looking through the link you gave me but i dont understand it at the moment,thanks:guitar:[/SIZE]

---

### Post by akakingess on 2009-09-30
I thought that UFW was on by default, but I have been known to be wrong more than once:) , but even if it not on automatically, all credobyte stated should do you just fine.

---

### Post by credobyte on 2009-09-30
> **akakingess said:**
> I thought that UFW was on by default, but I have been known to be wrong more than once:) , but even if it not on automatically, all credobyte stated should do you just fine.

Once you finish installing Ubuntu, first reboot will result in "ufw disabled - skipping".

---

### Post by scottishbloke on 2009-09-30
[SIZE=3]thanks,yeah it was not on by default,ive been browsing the net the last few days just hiding behind my router firewall,i went and fetched gufw from the synaptic manager after doing the terminal commands and now i have something to look at that says enabled haha,thanks for the help,much appreciated:)[/SIZE]

---

### Post by akakingess on 2009-09-30
Thanks, that's good to know, I didn't know that, just had read it somewhere else, just goes to show you, don't believe everything you read;)

---

### Post by 3rdalbum on 2009-09-30
> **scottishbloke said:**
> thanks,yeah it was not on by default,ive been browsing the net the last few days just hiding behind my router firewall

Well it's good that you solved your immediate question, but if you're behind a firewall on your router then there's no need to have a personal firewall on your computer too. If the router's firewall is blocking incoming connections, then the connections will never reach the computer anyway.

The router firewall protects your whole network too, not just a single computer, so it creates a little protective zone where all the computers on your network can access network services (shared printers, file sharing, intranet pages etc) but nobody outside can. If your computers are also running personal firewalls, then they can't access the services on your network.

---

