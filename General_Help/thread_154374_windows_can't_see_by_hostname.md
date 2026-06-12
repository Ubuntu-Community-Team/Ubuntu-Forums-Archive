---
title: "windows can't see by hostname"
date: 2006-04-03
forum: General Help
---

### Post by jeffrey1681 on 2006-04-03
I'm sure this question is answered somewhere on the forum, but I wasn't able to find it after about 30 min of searching, so I apologize if I missed it.

My problem: I have 2 computers (1 with Windows XP, 1 with Ubuntu 5.10) on a network connected through a linksys router.  I am able to ping the ubuntu computer from the windows one by IP address, but if I try to ping via the hostname of the ubuntu computer I get an error that the host could not be found.  I thought this might be a DNS issue, so I installed bind9 on ubuntu, but the default config doesn't work and I don't really know enough to want to go messing around with the config files (at least without seeing if anyone here can help me first).  I know how to use a linux computer, but I'm fairly new at administering one.  Any help anyone can give would be great, thanks.

---

### Post by dcstar on 2006-04-03
[QUOTE=jeffrey1681]I'm sure this question is answered somewhere on the forum, but I wasn't able to find it after about 30 min of searching, so I apologize if I missed it.

My problem: I have 2 computers (1 with Windows XP, 1 with Ubuntu 5.10) on a network connected through a linksys router.  I am able to ping the ubuntu computer from the windows one by IP address, but if I try to ping via the hostname of the ubuntu computer I get an error that the host could not be found.  I thought this might be a DNS issue, so I installed bind9 on ubuntu, but the default config doesn't work and I don't really know enough to want to go messing around with the config files (at least without seeing if anyone here can help me first).  I know how to use a linux computer, but I'm fairly new at administering one.  Any help anyone can give would be great, thanks.[/QUOTE]
Manually edit the hosts files on the respective computers.

---

### Post by elamericano on 2006-04-03
That hosts file suggestion is kinda lame, since it would only work from that computer and would have to be updated manually anytime your IP address changed. The real question is how to broadcast your netbios name to windoze.

Try this:

In smb.conf under the [global] add the following:
netbios name = machine_name

I can't test it now, but I'll try on my all-windows network at work tomorrow.

---

### Post by jeffrey1681 on 2006-04-03
[QUOTE=elamericano]Try this:

In smb.conf under the [global] add the following:
netbios name = machine_name
[/QUOTE]

I didn't realize that this was related to Samba.  I'll take a look at it tonight when I get home, thanks.

---

### Post by jeffrey1681 on 2006-04-03
Just tried it and it works!  Thanks for your help, I'll remember this for next time.

---

