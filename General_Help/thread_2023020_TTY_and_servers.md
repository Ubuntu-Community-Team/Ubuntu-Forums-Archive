---
title: "TTY and servers"
date: 2012-07-11
forum: General Help
---

### Post by 29732 on 2012-07-11
I know a person that can connect to his PC in another building via PuTTY, which shows up a little shell prompt in which he can run commands in.

Is there a way of making my PC have the same ability, like reserving one of my Xubuntu TTYs for just that purpose? What will I have to install? What will I have to do to access it?

---

### Post by steeldriver on 2012-07-11
you don't need to reserve anything - just install the openssh-client package and run ssh on the command line in any terminal (virtual terminal or xterm)

---

### Post by papibe on 2012-07-11
> **steeldriver said:**
> you don't need to reserve anything - just install the openssh-client package and run ssh on the command line in any terminal (virtual terminal or xterm)

Just to be a little more 'precise'....

The ability to connect to others machines is installed by default (openssh-client). As commented, you open a terminal and run:
```
ssh servername
```
Where 'servername' is the name of the machine you are trying to connect to.

However, to receive connections from other machines will require first the installation of an additional package: openssh-server. To install it:
```
sudo apt-get install openssh-server
```
That will allow other machines to connect to yours using the same syntax:
```
ssh user@yourmachine
```
Where 'user' has to exist to receive the remote connection.

I hope that clarify things a bit.
Regards.

---

### Post by 29732 on 2012-07-11
> **papibe said:**
> Just to be a little more 'precise'....

The ability to connect to others machines is installed by default (openssh-client). As commented, you open a terminal and run:
```
ssh servername
```
Where 'servername' is the name of the machine you are trying to connect to.

However, to receive connections from other machines will require first the installation of an additional package: openssh-server. To install it:
```
sudo apt-get install openssh-server
```
That will allow other machines to connect to yours using the same syntax:
```
ssh user@yourmachine
```
Where 'user' has to exist to receive the remote connection.

I hope that clarify things a bit.
Regards.

Thanks, but I need to clarify a few things:
I installed openssh, and it says it works, but I can't connect to it still. Is there a port I need to forward?
And when I do connect to it, like ssh [email]username@ip.ip.ip.ip[/email] , does it ask for my password later, or do I have to specify it somehow?

---

### Post by steeldriver on 2012-07-11
Provided the server side is configured to accept password authentication it will prompt for your password - you should be able to use either:

```
ssh user@ip.ip.ip.ip
```or

```
ssh -l user ip.ip.ip.ip
```or if you have the same username on both systems

```
ssh ip.ip.ip.ip
```For a complete list of options, type

```
man ssh
```The standard port is 22 - but many sysadmins change to an obscure high-numbered port as a first line of defense against port probing - you may have to ask the remote machine's sysadmin for that - and also check that they allow password authentication instead of / as well as key-based auth - if they *do* use a different port you can specify it with the '-p' option, e.g.

```
ssh -p 22222 user@ip.ip.ip.ip
```

> **papibe said:**
> Just to be a little more 'precise'....

I will endeavor to be more 'lucid' in the future :cool:

---

### Post by 29732 on 2012-07-11
> **steeldriver said:**
> Provided the server side is configured to accept password authentication it will prompt for your password - you should be able to use either:

```
ssh user@ip.ip.ip.ip
```or

```
ssh -l user ip.ip.ip.ip
```or if you have the same username on both systems

```
ssh ip.ip.ip.ip
```For a complete list of options, type

```
man ssh
```The standard port is 22 - but many sysadmins change to an obscure high-numbered port as a first line of defense against port probing - you may have to ask the remote machine's sysadmin for that - and also check that they allow password authentication instead of / as well as key-based auth - if they *do* use a different port you can specify it with the '-p' option, e.g.

```
ssh -p 22222 user@ip.ip.ip.ip
```



I will endeavor to be more 'lucid' in the future :cool:
Hm. Interesting.
I will try it a little bit later after I forward those ports and give you the results, but for now, it keeps timing out. c:

---

### Post by steeldriver on 2012-07-12
forgot to mention the '-v' option will make it spit out a bunch of stuff as it tries to connect - sometimes useful for troubleshooting connection failures

```
ssh -v user@host
```

---

