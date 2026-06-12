---
title: "Hosts file is reseted on every reboot"
date: 2011-11-23
forum: General Help
---

### Post by der_mythos on 2011-11-23
Hi,

I have Ubuntu 11.10 installed with a Lamp-Server.

So when I change my hosts file. Everything works fine.

I reboot my System and my hosts file is reseted to a State I seted it half a year ago.


Any one a idea why this could happen?


Best regards Robin

---

### Post by der_mythos on 2011-11-25
Nobody? Actually just a hint or sth. it could be, because it's realy anoying. I would realy appreciate if somebody could help me out :)

---

### Post by Lampi on 2011-11-25
Can you post the file?
Also take care of /etc/hostname

---

### Post by der_mythos on 2011-11-25
Hi Lampi,

thanks for your reply.

My etc/hosts looks like this:
```

127.0.0.1    localhost
127.0.1.1    robin-lapp


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```This is the state it is set on every reboot.

My temporary workaround is typing on every restart:
```

sudo -i
echo 127.0.0.1 myHost >> /etc/hosts

```I tried it with a start skript in /etc/init.d/ but it seems that it gets changed after this script is executed :(


Best regards Robin

---

### Post by dcstar on 2011-11-26
> **der_mythos said:**
> Hi Lampi,

thanks for your reply.

My etc/hosts looks like this:
```

127.0.0.1    localhost
127.0.1.1    robin-lapp


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```This is the state it is set on every reboot.

My temporary workaround is typing on every restart:
```

sudo -i
echo 127.0.0.1 myHost >> /etc/hosts

```I tried it with a start skript in /etc/init.d/ but it seems that it gets changed after this script is executed :(


Best regards Robin

AFAIK the "127.0.0.1 localhost" entry is a required system object and should not be changed by users under any circumstances.

If this is changed then the system security could be compromised by hackers redirecting calls that the software assumes will be going to the system to somewhere else.

Probably all the system is doing at boot is a basic security clean-up to ensure that it is not compromised.

The bottom-line is that you should **not** touch this entry.

---

### Post by der_mythos on 2011-11-26
Hi,

I don't change the upper entries, I just add the line:
```

127.0.0.1 myHost

```Afaik a OS should not change the entries in your hosts file. So why could that be?



Probably all the system is doing at boot is a basic security clean-up to ensure that it is not compromised.

So what could I do about that? Is there anything I could check?


Best regards Robin

---

### Post by der_mythos on 2011-11-27
> **der_mythos said:**
> Hi,

I don't change the upper entries, I just add the line:
```

127.0.0.1 myHost

```Afaik a OS should not change the entries in your hosts file. So why could that be?



Probably all the system is doing at boot is a basic security clean-up to ensure that it is not compromised.

So what could I do about that? Is there anything I could check?


Best regards Robin


Nobody knows what a solution could be?

---

### Post by Habitual on 2011-11-27
> **der_mythos said:**
> ...I tried it with a start skript in /etc/init.d/ but it seems that it gets changed after this script is executed :( ...

stick the same script in /etc/rc.local?

---

### Post by der_mythos on 2011-11-28
> **Habitual said:**
> stick the same script in /etc/rc.local?

Thank you for your reply, I'm at work atm. I will test this asap.

BTW: What's the difference between /etc/rc.local and /etc/init.d?

That's still just a workaround, what could be the cause of this error?


Best regards Robin

---

### Post by Habitual on 2011-11-28
> **der_mythos said:**
> .../etc/rc.local and /etc/init.d...

Robin: I don't know the exact difference, I just recently starting using rc.local myself. It seems|ed more 'manageable' than some init.d scripts.

rc.local does process stuff ***after*** all init.d scripts have been processed, so generally, items in it are some of the last things to be processed.

rc.local has never failed me. :)

is there an /etc/hosts.template file and if there is, what are the contents?

Thanks.

---

