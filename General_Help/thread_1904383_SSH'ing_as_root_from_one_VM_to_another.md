---
title: "SSH'ing as root from one VM to another"
date: 2012-01-04
forum: General Help
---

### Post by tg1390 on 2012-01-04
Hey everyone,

I'm running two identical Ubuntu 10.4 vms with VMWare and I need to be able to ssh from one to the other as root.

I've got openSSH 5.3 on both systems and the sshd_config is wired to permit root login for both.

When I try to ssh as root into either system. I'm prompted for the password.  When I try to put in the password, I get the following:

"Permission denied, Please try again"

I've grabbed the output from /var/log/auth.log and this is what is says:

"Jan  4 15:18:41 ubuntu sshd[6465]: Failed password for root from 192.168.136.150 port 51162 ssh2"

I know I must be missing something, just not sure what it is.

And yes, I'm sure I'm putting in the right password :)

---

### Post by mobrien118 on 2012-01-05
Are you *sure* you have the right root passwd?

What I mean is, when you use "sudo" that uses *your* password.

On the target system, you have run "sudo passwd" to set the root password, right?

I have 6 Ubuntu machines, and 3 additional Ubuntu VMs, and all I had to do to use ssh on all of them was "sudo apt-get install ssh" and I can ssh as root into any of them (using "ssh root@mysystem" and supplying the root password).

Sorry if this response is too basic, but since you're connecting far enough to get prompted for password, I rule out network configuration, and OpenSSH should detect the encryption, which should be the default on both ends, anyway, so that really only leaves account or configuration issues.

--mobrien118

---

### Post by tg1390 on 2012-01-06
Yeah, I am 100% sure I have the right password.  I think it's defiantly a configuration issue.  I know that the sshd_config has a switch to enable/disable root login over ssh but I checked there first and it is enabled.  Do you know of any other places where root access over ssh could be disabled?

Thanks for the quick reply btw :)

---

### Post by killermist on 2012-01-06
May not be the case in your case, but in dealing with multiple machines and/or multiple VMs, I've made incorrect assumptions about IP addresses and ended up trying to log into the wrong machine/VM. Misconfigured /etc/hosts files have also screwed me up before.

Again, not sure that it is related, but might be worth investigation.

---

### Post by mobrien118 on 2012-01-06
> **tg1390 said:**
> Yeah, I am 100% sure I have the right password.  I think it's defiantly a configuration issue.  I know that the sshd_config has a switch to enable/disable root login over ssh but I checked there first and it is enabled.  Do you know of any other places where root access over ssh could be disabled?

Thanks for the quick reply btw :)

OK. It *sounded* like you knew what you were doing as far as passwords, but I just wanted to make *sure*.

That should be the only place that it is configured (in the sshd.conf file) and Ubuntu has this turned on by default (which is arguably a bad idea), so there shouldn't be any reason that it shouldn't work.

I really can't think of anything else that would cause this issue, other than what killermist suggested, that you're somehow connecting to the wrong machine.

This is an odd one, indeed.

---

### Post by killermist on 2012-01-06
Is the root account maybe configured to use a shell that is either not valid, or refuses login?

If you've reconfigured anything, have you restarted the services (like SSH)?

So many little places that things can (and do in my experience) go wrong.

---

### Post by Wayne_V on 2012-01-06
if you can't log in as root, you can't ssh as root.   try:

$ sudo passwd root
$ sudo passwd -u root
$ ssh root@localhost

if that works you should be set.

---

### Post by tg1390 on 2012-01-10
Thanks guys, as it turned out it was the password.  I was confusing the password for sudo'ing with the password for root.

---

