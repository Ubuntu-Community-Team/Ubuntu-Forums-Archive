---
title: "web server not working"
date: 2010-04-16
forum: General Help
---

### Post by gfunkera on 2010-04-16
i have apache and mysql running, i can access my web server by visiting localhost on port 80 but for some reason when it doesnt work when i try using my ISP provided IP address... (it used to work)..

i have my router setup with a DMZ on my LAN IP (my computers IP, this is the computer in my home network that serving with apache)..

oh i also cant seem to shut down my mysql server (theres an update ive been trying to get) even when i use sudo...

any ideas?

---

### Post by Monotoko on 2010-04-16
Does it work from your internal address? (From another computer inside the network, it'l be 192.168....)

Also shutting down mysql should just be a case of: 
```
sudo /etc/init.d/mysql stop
```

If that doesnt work, you could see what it throws at you in terms of errors, if you really need it closing, you could also kill the process:

```
sudo ps -ef | grep (process name)
```

Im not quite sure what the process name of mysql is, it will either be mysql or mysqld

---

### Post by gfunkera on 2010-04-16
it doesnt work from my lan either when i try to connect to my web servers internal IP address..

very weird considering the only thing i did since the last time it was working was not accessing it for a few months... i made no changes to any configurations anywhere...

---

### Post by jhollinger on 2010-04-16
Here are some thoughts in no particular order:

Can you ping your IP?

Is your machine's IP dynamic or static? If it's dynamic it may have changed over the last few months, and the IP in the DMZ isn't yours anymore. This would also explain why you can't access it from the LAN.

Changed any firewall settings? Try "sudo iptables -L" to list any firewall rules and make sure port 80 is making it through.

I assume you've already checked to see that apache is starting and running ("ps aux | grep apache").

Look at your apache access and error logs - somewhere around /var/log/apache/ I think. "tail -f" those files when your trying to access the site.

---

### Post by gfunkera on 2010-04-16
**i tried pinging the IP and there was no response...**

**the IP is static...**

**here is the result of "sudo iptables -L"**
-----------------------------------------------------
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
------------------------------------------------------

**apache is definitely started and running...**

**ill check into the log files and let you know if anything funny comes up...**

---

### Post by gfunkera on 2010-04-16
boy do i feel stupid........... i found the issue.....

a week ago comcast sent one of its ghetto boys (you know one of those backward cap wearing, off-the-clock gangsta wannabes who went through the two week training course on how to use his company issued ping testers) to muddle with the boxes and wires....

he did something that reassigned my IP from the ISP.........

:guitar:

---

