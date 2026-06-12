---
title: "Cannot access DMZ host"
date: 2011-09-12
forum: General Help
---

### Post by gnomeout on 2011-09-12
Hi peeps,

So I recently upgraded the hardware in my computer, new motherboard, new Solid State Drive, new processer, new memory (graphics card coming later). 

My issue is that now, all of a sudden, I cannot access my computer from outside my network. Although there are a few exceptions for this rule.

Here are the symptoms, and I have NO idea what could be causing this, but I am looking for YOUR input...

I connect to my home computer remotely fairly often. Usually through SSH, sometimes I put some files on an Apache web server on my machine and just use a browser. 

Anyway, I have been able to connect remotely from work for the last year with no issues at all. Now I have a new machine and I cant seem to access any of my ports. Connecting via SSH or just using my browser to connect to the Apache server results in a timeout. Strangely though subsonic (subsonic.org) is still running and accessible from port 4040 (although it could be doing some special configuration to make port 4040 work; the installation process was ridiculously easy for what it accomplishes). 

Anyway, thats my main problem. Cant seem to SSH into my machine, even though other services are working remotely. If I use Hamachi, then I can of course SSH into my computer, but this is not something that should be necessary.

My local machine is in the DMZ of my router. It is configured to always be assigned the same local IP which is the local IP assigned to the DMZ. It is my understanding that using the DMZ should eliminate the need for port forwarding. I do not immediately suspect my router configuration though since it was working completely fine before I changed my computer.

But I have no idea where to look for firewall settings in Ubuntu... is there even such a thing???


Help?

Thanks,
B.

PS: I ran a port check from windows for some unrelated ports (which should behave the same as my ssh and http ports since they are all configured the same in DMZ) for a video game, and they came back as "stealth" ports. Will try running checks on ports 443 and 80 in Ubuntu when I get a chance.

---

### Post by Dangertux on 2011-09-12
Yes there is a firewall in Ubuntu , however it is not enabled by default. If you want to check the status of said firewall you can do the following.

```

sudo ufw status

```

if it returns something like this

```

Status: active

```

Then the firewall is enabled and likely blocking the ports you want to connect to. You could do something like this to allow connection from the outside world.

```

sudo ufw allow from any to 192.168.0.2 port 80 proto tcp
sudo ufw allow from any to 192.168.0.2 port 22 proto tcp

```

where 192.168.0.2 is the ip address of your machine and 22 is the port you wish to allow with tcp being the protocol

at that point you can restart UFW by doing the following

```

sudo ufw disable && sudo ufw enable

```

Test to see if your external connections work.

---

### Post by gnomeout on 2011-09-27
That is useful information. I dont think it was my problem as things just magically started working a couple days later after making no changes.


I was going to suggest this post get removed, but since this is somewhat useful info i guess it should stay up.

Thanks anyway.

---

