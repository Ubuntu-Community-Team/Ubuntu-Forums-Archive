---
title: "Block ssh tunnel"
date: 2011-04-10
forum: General Help
---

### Post by JCM_Pico on 2011-04-10
Hi there,
I'm running Ubuntu 10.04, and I noticed that by knowing my user, password and IP its easy to get access to my machine throw ssh if connected to the same network.

Is there any way to block this access or to turn it more difficult?

---

### Post by lithopsian on 2011-04-10
That's kind of the whole point :)

There are many ways to improve security!  Most obvious is to turn off ssh.  No daemon, no access.  Turn off the boot service to do this.

Do you need ssh access to your machine?  Turn off password authentication and exchange keys with only those machines that need ssh access.  Or (or and) restrict access to those IP addresses that need access, if a fixed list is available.  Also you would commonly want to prevent root access completely for obvious reasons.  Edit the config file to do these.

---

### Post by SeanTater on 2011-04-10
> **JCM_Pico said:**
> Hi there,
I'm running Ubuntu 10.04, and I noticed that by knowing my user, password and IP its easy to get access to my machine throw ssh if connected to the same network.

Is there any way to block this access or to turn it more difficult?

Like he said, that's completely the point of having SSH.

But if you're worried about it, you can use SSH keys instead. They're pretty easy to make and somewhat tough to use if you're not used to them. I'm sure you can Google a howto on that.
Meanwhile - if you didn't know what SSH does, then chances are that openssh-server is not installed, and hence you don't have it on your computer anyway, so it's not an issue.

---

### Post by JCM_Pico on 2011-04-10
> **SeanTater said:**
> Like he said, that's completely the point of having SSH.

But if you're worried about it, you can use SSH keys instead. They're pretty easy to make and somewhat tough to use if you're not used to them. I'm sure you can Google a howto on that.
Meanwhile - if you didn't know what SSH does, then chances are that openssh-server is not installed, and hence you don't have it on your computer anyway, so it's not an issue.

I have ssh installed and I use it often, to access my machine from some where else...
Bu know I'm a bit worried  about security when I connect my pc to a public network...
Been trying to configure some parameter in the ssh_config file placed in /etc/ssh/ but without success

---

### Post by marshmallow1304 on 2011-04-10
> **JCM_Pico said:**
> 
Been trying to configure some parameter in the ssh_config file placed in /etc/ssh/ but without success

/etc/ssh/ssh_config
is for the ssh client.

/etc/ssh/sshd_config
is for the ssh server.

---

### Post by conradin on 2011-04-10
better yet is enable ufw (the firewall) disabled by default in ubuntu
```


sudo ufw default deny
sudo ufw enable
ufw logging on

```

I love the firewall!! Shields up at [www.grc.com](www.grc.com) is also helpful.
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
also, disable echo (ping) requests, url tells how

---

### Post by JCM_Pico on 2011-04-10
```
jcmteixeira@jcmt-laptop:~$ cd /etc/ssh/
jcmteixeira@jcmt-laptop:/etc/ssh$ ls
moduli  ssh_config  ssh_config.factory-defaults  sshd_not_to_be_run

```

there's no sshd_config, the more obvious scenario is to not have ssh server... but I can connect from other machin to my own machine if within the same network.......

---

### Post by JCM_Pico on 2011-04-10
> **conradin said:**
> better yet is enable ufw (the firewall) disabled by default in ubuntu
```


sudo ufw default deny
sudo ufw enable
ufw logging on

```I love the firewall!! Shields up at [www.grc.com]("http://www.grc.com") is also helpful.
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
also, disable echo (ping) requests, url tells how

Thanks this worked like a charm to block it...

But since this discussion lead to my missing sshd_config I would like to understand I its not in /etc/ssh/

---

