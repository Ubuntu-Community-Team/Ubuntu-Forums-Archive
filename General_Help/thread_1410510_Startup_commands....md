---
title: "Startup commands..."
date: 2010-02-18
forum: General Help
---

### Post by paraplegicpanda on 2010-02-18
Okay, I know I probably did a crappy job searching, but I need to find a solution... Here's the problem: I've got my internet shared to my girlfriend's laptop over a crossover cable, no problem. What is a problem is that I have to run these commands every time I start up my computer:
```

sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

```
What I would like to do is get these commands to run automatically when I start up my computer, but I'm not sure what the best route would be. Suggestions?

---

### Post by n0dix on 2010-02-18
You can create a shell script, but manually have to provide the password.
This can be useful: [http://ubuntuforums.org/showthread.php?t=181041](http://ubuntuforums.org/showthread.php?t=181041)

---

