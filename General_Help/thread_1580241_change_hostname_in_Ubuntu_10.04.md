---
title: "change hostname in Ubuntu 10.04"
date: 2010-09-23
forum: General Help
---

### Post by dengbao2001 on 2010-09-23
I want to change my ubuntu hostname

So, i type below command

sudo gedit /etc/hostname

change new hosname

and next,run below command

sudo gedit /etc/hosts

change it also,

After that. I wan to stop and start hostnameservice with below comand

sudo /etc/init.d/hostname.sh stop

but get message with "sudo: /etc/init.d/hostname.sh: command not found"

So, What i can do to change hostname without restart the pc?

Thanks

---

### Post by plucky on 2010-09-23
> **dengbao2001 said:**
> I want to change my ubuntu hostname

So, i type below command

sudo gedit /etc/hostname

change new hosname

and next,run below command

sudo gedit /etc/hosts

change it also,

After that. I wan to stop and start hostnameservice with below comand

sudo /etc/init.d/hostname.sh stop

but get message with "sudo: /etc/init.d/hostname.sh: command not found"

So, What i can do to change hostname without restart the pc?

Thanks

Try ```
sudo service hostname start
```

Good Luck

---

### Post by dengbao2001 on 2010-09-23
> **plucky said:**
> Try ```
sudo service hostname start
```

Good Luck

Thanks for you quickly update. But still get error 

When i run the command  "sudo service hostname start"

get message "Job failed to start"

and when i run the command "sudo service hostname stop"

get message "Unknown instance:"

what shall i next to? thanks

---

### Post by plucky on 2010-09-23
> **dengbao2001 said:**
> Thanks for you quickly update. But still get error 

When i run the command  "sudo service hostname start"

get message "Job failed to start"

and when i run the command "sudo service hostname stop"

get message "Unknown instance:"

what shall i next to? thanks

Just tried it on my test system,the hostname would not change permanently until I rebooted.
There must be other services that you need to restart before the name will change.
Perhaps someone more knowledgeable can help.


Good Luck

---

### Post by dengbao2001 on 2010-09-23
> **plucky said:**
> Just tried it on my test system,the hostname would not change permanently until I rebooted.
There must be other services that you need to restart before the name will change.
Perhaps someone more knowledgeable can help.


Good Luck

Anyway, Thanks you so much!

---

### Post by QLee on 2010-09-23
It isn't a service.
You just want to use the "hostname" command with the new hostname as argument to the command to change to the new hostname for the current session. Use it with sudo.

Enter, man hostname, in a terminal to read the whole manual page for hostname.

---

### Post by dengbao2001 on 2010-09-23
> **QLee said:**
> It isn't a service.
You just want to use the "hostname" command with the new hostname as argument to the command to change to the new hostname for the current session. Use it with sudo.

Enter, man hostname, in a terminal to read the whole manual page for hostname.

thanks for you reply

but when i run the command ' hostname newname',  then i run the command 'hostname', it is still old hostname.

after that, i restart my pc, it is still old hostname

---

### Post by CharlesA on 2010-09-23
You need to edit these two files:

```
sudo nano /etc/hostname
```

```
sudo nano /etc/hosts
```

Replace the old hostname with the new one and reboot the whole machine.

---

### Post by dengbao2001 on 2010-09-24
> **CharlesA said:**
> You need to edit these two files:

```
sudo nano /etc/hostname
```

```
sudo nano /etc/hosts
```

Replace the old hostname with the new one and reboot the whole machine.

it is worked for suggestion. but any solution to change hostname without PC restart it?

---

### Post by dcstar on 2010-09-24
> **dengbao2001 said:**
> it is worked for suggestion. but any solution to change hostname without PC restart it?

No, just accept that changing the hostname is a serious change for a system and requires a restart.

---

### Post by sisco311 on 2010-09-24
> **dengbao2001 said:**
> it is worked for suggestion. but any solution to change hostname without PC restart it?

```
sudo hostname new-host-name
```

But you still have to edit the /etc/hosts file if you want to make the change permanent.

---

