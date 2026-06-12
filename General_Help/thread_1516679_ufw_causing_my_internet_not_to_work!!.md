---
title: "ufw causing my internet not to work?!?!?"
date: 2010-06-24
forum: General Help
---

### Post by flashthedash on 2010-06-24
i recently switched from windows vista to ubuntu 10.04, so i am a complete noob at this stuff...

i enabled the ufw a few days ago and ever since then my Internet connection has been pretty spotty. i connect to the wireless network fine, and there is nothing wrong with the actual Internet connection (other computers in the house are using it fine) 

it is very frustrating and i was wondering if there is a way to stop this, do i need to forward some ports, or do i really even need the firewall at all... i don't really do many things that would allow me to get hacked in the first place.. 

please help.

thank you,
flashthedash

---

### Post by Rubi1200 on 2010-06-24
Does the wireless router have a firewall and is it enabled?

If yes, then you do not need ufw enabled.

To disable:

```
sudo ufw disable
```If the router does not have a firewall or it is not enabled or you do not have permission to enable it, then it might be a good idea to keep ufw enabled.

Some useful links and code to check your system:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

```
sudo lsof -i -n -P
``````
sudo netstat -tulnp
```Hope this helps.

---

