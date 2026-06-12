---
title: "Automatic IP  Blocking after 3 failed attempts"
date: 2010-10-09
forum: General Help
---

### Post by dgohn on 2010-10-09
I am looking for a way to automatically block an ip address and add  it to /etc/hosts.deny when they have 3 consecutive password failures or try connecting to a name that doesn't exist more than like twice to help limit the brute force attacks I am experiencing.  Is there an easy way to do this already implemented in Ubuntu?

Thanks in advance for any and all help!

---

### Post by CharlesA on 2010-10-09
You can use fail2ban or denyhosts for that.

What service is this going to be for? SSH?

---

### Post by dgohn on 2010-10-09
Yes, for SSH.  Thanks I will look into those :)

---

### Post by CharlesA on 2010-10-09
I don't care about keeping a record of attempts that were blocked, so I just use iptables.

```
sudo iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set --name  SSH --rsource
sudo iptables -A INPUT -m recent --update --seconds 600 --hitcount 4 --rttl --name SSH  --rsource -j DROP
sudo iptables -A INPUT -p tcp -m tcp --dport 22 -j ACCEPT

```

---

### Post by dgohn on 2010-10-09
Could you explain what that is doing exactly?  Kind of lost on that one

---

### Post by CharlesA on 2010-10-09
Basically it blocks an ip address for 10 minutes after 4 "hits" or connection attempts. Slows down people who are trying to brute force your login.

---

### Post by dgohn on 2010-10-10
I tried the above 3 commands (copied and pasted  to make sure I got them right) but to no avail,  it is not blocking the ip for any amount of time aand lets you attempt a password 6 times before you get a disconnect.  Any ideas?  Thanks!

---

### Post by CharlesA on 2010-10-10
You have to try to connect to the machine 4 times within one minute for it to lock that ip out. It's mainly there to slow down bruteforce attacks.

Here's a snip from my auth.log:

```
[COLOR="Red"]Oct 10 07:08:00[/COLOR] atlantis sshd[1803]: Invalid user ts2 from 88.191.73.232
[COLOR="Blue"]Oct 10 07:08:02[/COLOR] atlantis sshd[1806]: Invalid user ts3 from 88.191.73.232
[COLOR="Indigo"]Oct 10 07:08:03[/COLOR] atlantis sshd[1808]: Invalid user ts3 from 88.191.73.232
[COLOR="Red"]Oct 10 08:32:57[/COLOR] atlantis sshd[1821]: Did not receive identification string from 121.10.140.214
[COLOR="Blue"]Oct 10 08:34:29[/COLOR] atlantis sshd[1824]: User root from 121.10.140.214 not allowed because not listed in AllowUsers
[COLOR="Indigo"]Oct 10 08:34:36[/COLOR] atlantis sshd[1827]: User root from 121.10.140.214 not allowed because not listed in AllowUsers
[COLOR="Red"]Oct 10 12:31:18[/COLOR] atlantis sshd[1849]: User root from 125.65.207.10 not allowed because not listed in AllowUsers
[COLOR="Blue"]Oct 10 12:31:20[/COLOR] atlantis sshd[1853]: User root from 125.65.207.10 not allowed because not listed in AllowUsers
[COLOR="Indigo"]Oct 10 12:31:22[/COLOR] atlantis sshd[1855]: User root from 125.65.207.10 not allowed because not listed in AllowUsers

```

Each connection attempt was made within a couple seconds, and after the tried to connect a 4th time, it blocked their IP address from connecting.

Also: I tested connecting to my machine running Lucid via SSH, and it disconnected me after 3 failed password attempts, not 6, so I'm not sure what is going on there.

Please note: I also use key-based authentication (and disable password authentication) for any machines that have SSH open to the internet. Can't bruteforce keys.

---

