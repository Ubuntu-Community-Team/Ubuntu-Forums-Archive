---
title: "user with SSHD/Proxy access only?"
date: 2012-09-24
forum: General Help
---

### Post by reach on 2012-09-24
Hi there!
I'm a beginner, with only very basic understanding of Linux, but I managed to get my server up and running with Samba, Apache and Squid. However, looking for howtos for my problem it appears to be not THAT trivial...:
One of the main usecases for my Ubuntu server is building an SSH Tunnel from the outside and websurf through it. Guess you know what I mean.
Eventually I'd like to share that kind of access also with others.

So I'd like to have a user which has no other permission than to login via SSH and use squid3. 

Could someone pls explain me how this works?
I found some hints, but whatever I try, the user can at least navigate through the filesystem which I don't want. I'm starting to believe that this is not up to the user, but to my file permissions (chmod ...). But in this case I'd be afraid to mess around with those especially for system files. Any help appreciated.

Thx!
reach

---

### Post by btindie on 2012-09-25
So what you're looking for is remote port forwarding?

Take a look at this [http://blog.e-shell.org/288](http://blog.e-shell.org/288), especially the first comment which gets around the need for a hack.

Essentially you just need to set the user accounts shell to /usr/sbin/nologin
```
sudo chsh -s /usr/sbin/nologin <username>
```
And then use the following ssh command which then doesn't request a shell
```
ssh -L 3128:localhost:3128 -N <user>@<host_ip>
```
You can also use the -f option with ssh to get it to go into the background. If that's your only ssh session open you can then kill it with
```
pkill -HUP -x ssh
```

---

