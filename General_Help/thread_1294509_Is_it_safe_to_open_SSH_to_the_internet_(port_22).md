---
title: "Is it safe to open SSH to the internet (port 22)?"
date: 2009-10-18
forum: General Help
---

### Post by alexlaban on 2009-10-18
Is it safe to forward port 22 in UFW to a static IP address. The thing is I often need to access my server when I'm at another place, this place got a static IP Address, so at this moment the only port open for the outside on my server is 80 but if I would open port 22 in UFW to this IP Address would this be safe. Why I'm asking is because some of the user accounts on my server only got a 8-10 character password even tho my main got a 16 character password I don't want anyone but my to access my server, the risk that someone actually broke into the place where the ip I forwarded to and tried to hack it is low to none since it's just as easy if not easier to break in here and steal/hack the actual server. So basically what I'm wondering is if this is safe enough, is it totally sure that people won't be able to fool the server in some way that they are from that IP Adress.

---

### Post by CharlesA on 2009-10-18
> **alexlaban said:**
> Is it safe to forward port 22 in UFW to a static IP address. The thing is I often need to access my server when I'm at another place, this place got a static IP Address, so at this moment the only port open for the outside on my server is 80 but if I would open port 22 in UFW to this IP Address would this be safe. Why I'm asking is because some of the user accounts on my server only got a 8-10 character password even tho my main got a 16 character password I don't want anyone but my to access my server, the risk that someone actually broke into the place where the ip I forwarded to and tried to hack it is low to none since it's just as easy if not easier to break in here and steal/hack the actual server. So basically what I'm wondering is if this is safe enough, is it totally sure that people won't be able to fool the server in some way that they are from that IP Adress.

You should set up keys to secure yer ssh. As for the firewall, just tell it to accept stuff from that static IP on port 22.

IMHO change yer SSH port to a different port number, that'll help secure it a bit.

Check [here ]("http://www.dintz.com/in-depth-6-ways-to-make-your-ssh-logins-more-secure/")and [here]("http://www.debian-administration.org/article/Keeping_SSH_access_secure") for some infos on how to secure SSH.

---

### Post by raul_ on 2009-10-18
Well, there are bots that crawl the web trying the default ssh ports with the usual logins (user, root, admin, etc) and brute force them, so it's best to change your port and have a f*cked up password (filled with numbers and strange symbols).

Remember that ssh is a door to the outside world

---

### Post by alexlaban on 2009-10-18
> **raul_ said:**
> Well, there are bots that crawl the web trying the default ssh ports with the usual logins (user, root, admin, etc) and brute force them, so it's best to change your port and have a f*cked up password (filled with numbers and strange symbols).

Remember that ssh is a door to the outside world

And that is why I wounder how safe [UFW]("https://wiki.ubuntu.com/UbuntuFirewall") is, cause if I only open the port for that IP Adress in theory it should be just as safe as having the port open in my internal network for the server, Of course I'm not going to use the default port 22. What I asked is basically how well this feature in UFW really works, since I know that over SSH you can do anything with the server and that's why I want to really be sure that UFW is safe enough if you open the port to only one single external IP.

---

### Post by lovinglinux on 2009-10-18
You could also setup the router to forward connections only from your remote machine IP and/or mac address, if this feature is available. 

Anyway, as far as I know, if you setup ssh authentication with keys, disable password authentication and setup the firewall to accept connections only from your remote static IP, then you are pretty much safe. The firewall will block any connections originated from other machines. Even if the intruder is capable of bypassing your firewall, it would need your authentication key. It wouldn't be capable of accessing the ssh server by just guessing your password, since you password authentication is disabled.

See:

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

---

### Post by alexlaban on 2009-10-18
> **lovinglinux said:**
> You could also setup the router to forward connections only from your remote machine IP and/or mac address, if this feature is available. 

Anyway, as far as I know, if you setup ssh authentication with keys, disable password authentication and setup the firewall to accept connections only from your remote static IP, then you are pretty much safe. The firewall will block any connections originated from other machines. Even if the intruder is capable of bypassing your firewall, it would need your authentication key. It wouldn't be capable of accessing the ssh server by just guessing your password, since you password authentication is disabled.

See:

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

And then if I set sshd in host.allow to only allow the remote static IP and 192.168.0.0 and set sshd in host.deny to all the chance that someone would hack my personal home server would be close to 0.

---

### Post by Johnny B on 2009-10-18
i use [denyhosts]("http://denyhosts.sourceforge.net/") (its in the repos)
it automaticly blocks ip's that use the wrong username/password

also make sure you disable root login.

---

### Post by CharlesA on 2009-10-18
> **alexlaban said:**
> And then if I set sshd in host.allow to only allow the remote static IP and 192.168.0.0 and set sshd in host.deny to all the chance that someone would hack my personal home server would be close to 0.

You don't need to add 192.168.0.0, if you are only going to be accessing it from the remote machine and not from the local network.

---

### Post by alexlaban on 2009-10-18
> **CharlesA said:**
> You don't need to add 192.168.0.0, if you are only going to be accessing it from the remote machine and not from the local network.
Well I'm kinda going to access it on the local network as well, I don't have a monitor connected to the server so I only access it via ssh from my MacBook Pro or one of my desktops (running FreeBSD and Ubuntu on them).

---

### Post by CharlesA on 2009-10-18
> **alexlaban said:**
> Well I'm kinda going to access it on the local network as well, I don't have a monitor connected to the server so I only access it via ssh from my MacBook Pro or one of my desktops (running FreeBSD and Ubuntu on them).

If they have a static IP assigned via DHPC or just a regular static IP, you can add those IPs to hosts.allow so you can access it from there.

I've got mine set so that I can access it from work (over the internet) and from my main desktop machine (but not any other desktop machine)

My main desktop has a DHCP assigned static IP, so I don't have to allow the entire network access.

Hope that makes some sort of sense.

---

### Post by alexlaban on 2009-10-18
Well I kinda got 3 home network all with their own external ip adress where one network is just for my server and worksations. So allowing access to the entire home work network isn't really a problem.

---

### Post by CharlesA on 2009-10-18
> **alexlaban said:**
> Well I kinda got 3 home network all with their own external ip adress where one network is just for my server and worksations. So allowing access to the entire home work network isn't really a problem.

Gotcha. Sounds like you got it all figured out. :-)

---

### Post by alexlaban on 2009-10-18
I just relised I didn't post this in "Security Discussion" section, sorry my mistake, well it's kinda solved now I guess so it shouldn't matter anymore.

---

