---
title: "UFW - /lib/ufw/user.rules DELETE question"
date: 2011-12-18
forum: General Help
---

### Post by held7over on 2011-12-18
UFW Ubuntu 10.10

I forgot what commands I used originally to create these entries in /lib/ufw/user.rules and I am having trouble getting the syntax right to delete some rules in /lib/ufw/user.rules. Can I just manually edit the user.rules file instead and be done with it?

I am wanting to delete the two entries which refer to eth1 below--

# ufw status
Status: active
To                         Action      From
--                         ------      ----
Anywhere                   ALLOW       192.168.2.200
22/tcp on eth1             ALLOW       10.0.0.100
22/tcp on eth1             ALLOW       192.168.2.100
22/tcp                     ALLOW       192.168.0.200
22/tcp                     ALLOW       192.168.0.210

The applicable section of the /lib/ufw/user.rules file looks like this:

### RULES ###

### tuple ### allow any any 0.0.0.0/0 any 192.168.2.200 in
-A ufw-user-input -s 192.168.2.200 -j ACCEPT

### tuple ### allow tcp 22 0.0.0.0/0 any 10.0.0.100 in_eth1
-A ufw-user-input -i eth1 -p tcp --dport 22 -s 10.0.0.100 -j ACCEPT

### tuple ### allow tcp 22 0.0.0.0/0 any 192.168.2.100 in_eth1
-A ufw-user-input -i eth1 -p tcp --dport 22 -s 192.168.2.100 -j ACCEPT

### tuple ### allow tcp 22 0.0.0.0/0 any 192.168.0.200 in
-A ufw-user-input -p tcp --dport 22 -s 192.168.0.200 -j ACCEPT

### tuple ### allow tcp 22 0.0.0.0/0 any 192.168.0.210 in
-A ufw-user-input -p tcp --dport 22 -s 192.168.0.210 -j ACCEPT

### END RULES ###

Thanks! :)

---

### Post by bluexrider on 2011-12-18
R U unable 2

```
sudo gedit /lib/ufw/user.rules
```

---

### Post by held7over on 2011-12-18
Sure. Gedit and Nano both work....but...I thought I had read when I was first trying to research using UFW, that I am not suppose to manually edit the /lib/ufw/user.rules, but was rather suppose to use UFW's special command set on the commandline for changing this file. But haven't been able to find that original statement to confirm it....which is why I asked here on the forum if editing it manually was allowed or not. 

Is it? Or does that mess something up?

---

### Post by kpuz on 2011-12-18
Why not just use the command line.  Its way easier.

The following command should list the rules in numbered form:
```
sudo ufw status numbered
```

Then you can delete the rule that is identified now by a number by using:
```
sudo ufw delete [whatever the number for your rule is]
```

---

### Post by held7over on 2011-12-18
That was one of the things I tried before I asked my question on the forum. 

I am logged in as root....The "ufw status numbered" command works, but trying "ufw delete 2" or "ufw delete [2]" doesn't work and instead it gives me the entire list of commands.

I just noticed that I showed my OS as Ubuntu 10.10 above, and actually all my computers are, except the one I am doing this on, which is Debian 6.0, which I am trying to learn about creating web servers...but I assume it is the same...

---

### Post by kpuz on 2012-01-08
That is weird. Can you post what you get when you input the ufw delete 2 command?
Perhaps Debian requires a different command syntax.  You may be able to figure it out by looking at the manual page for ufw in Debian with
'man ufw'.

---

### Post by held7over on 2012-01-09
Kpuz I have listed my command line results below. But, maybe I should ask a different question. If I want to wipe out everything so that I have a brand new untouched ufw to work with, like how it exists before any rules are added anywhere, what do I need to do?

Here are my results:


root@ispy2:~# ufw status numbered
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] Anywhere                   ALLOW IN    192.168.2.200
[ 2] 22/tcp                     ALLOW IN    192.168.0.200
[ 3] 22/tcp                     ALLOW IN    192.168.0.210
[ 4] 22/tcp                     ALLOW IN    192.168.2.201

root@ispy2:~# ufw delete 2

Usage: ufw COMMAND

Commands:
 enable                          enables the firewall
 disable                         disables the firewall
 default ARG                     set default policy
 logging LEVEL                   set logging to LEVEL
 allow ARGS                      add allow rule
 deny ARGS                       add deny rule
 reject ARGS                     add reject rule
 limit ARGS                      add limit rule
 delete RULE                     delete RULE
 insert NUM RULE                 insert RULE at NUM
 status                          show firewall status
 status numbered                 show firewall status as numbered list of RULES
 status verbose                  show verbose firewall status
 show ARG                        show firewall report
 version                         display version information

Application profile commands:
 app list                        list application profiles
 app info PROFILE                show information on PROFILE
 app update PROFILE              update PROFILE
 app default ARG                 set default application policy

root@ispy2:~# ufw status numbered
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] Anywhere                   ALLOW IN    192.168.2.200
[ 2] 22/tcp                     ALLOW IN    192.168.0.200
[ 3] 22/tcp                     ALLOW IN    192.168.0.210
[ 4] 22/tcp                     ALLOW IN    192.168.2.201

root@ispy2:~#

root@ispy2:~# ufw delete [2]

Usage: ufw COMMAND

Commands:
 enable                          enables the firewall
 disable                         disables the firewall
 default ARG                     set default policy
 logging LEVEL                   set logging to LEVEL
 allow ARGS                      add allow rule
 deny ARGS                       add deny rule
 reject ARGS                     add reject rule
 limit ARGS                      add limit rule
 delete RULE                     delete RULE
 insert NUM RULE                 insert RULE at NUM
 status                          show firewall status
 status numbered                 show firewall status as numbered list of RULES
 status verbose                  show verbose firewall status
 show ARG                        show firewall report
 version                         display version information

Application profile commands:
 app list                        list application profiles
 app info PROFILE                show information on PROFILE
 app update PROFILE              update PROFILE
 app default ARG                 set default application policy

root@ispy2:~#

---

### Post by kpuz on 2012-01-09
You may have to try the command in the longer form.  
Assuming it is rule number 2 ([ 2] 22/tcp ALLOW IN 192.168.0.200)you are trying to delete you can try:

```
ufw delete allow proto tcp on any port 22 from 192.168.0.200
```

---

