---
title: "hostname is getting set to 'localhost' on startup"
date: 2010-02-22
forum: General Help
---

### Post by cong06 on 2010-02-22
Everytime I turn on the computer, the hostname is getting changed back to localhost.

```

**cat /etc/hosts**
127.0.0.1	najile	localhost

# The Following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


**cat /etc/hostname**
najile

**cat /etc/host.conf**
# The "order" line is only used by old versions of the C library.
order hosts,bind
multi on


```

So I turn off my computer, and turn it back on, and then:
```

**cat /etc/hosts**
127.0.0.1	localhost	localhost.localdomain	localhost

# The Following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Something is changing the file.

(side note: man hosts says that the name is based off the hostname file, but that's clearly not the case here. It's being named off the /etc/hosts file. Why did we move away from /etc/hostname? It's SOO much easier)

These computers (It's more then one) were all installed with the minimal Ubuntu disk and then installed basic software such as xorg, nautilus, gdm, and openoffice.

---

### Post by plucky on 2010-02-22
My /etc/hosts file looks like ```
127.0.0.1	localhost
127.0.1.1	Cobham

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Seems you are missing the 127.0.1.1  line which is my Hostname.

You could try adding the line and see if it makes a difference.

Good Luck

---

### Post by cong06 on 2010-02-22
Well, no... though I think that was a worthwile fix.

---

### Post by cong06 on 2010-02-22
I forgot to say, I'm testing this change by running the "hostname" command.

I honestly don't care too much what the prompt looks like (though it'd be nice) I care more how the environment variable "$HOSTNAME" is set since I use it in scripts.

---

### Post by cong06 on 2010-02-22
I'm fairly sure I figured it out (I have a tendency to close "bugs" before I've full tested)

It turns out I didn't give enough information.
The problem was in **/etc/NetworkManager/nm-system-settings.conf**:
```

[ifupdown]
managed=true

```

where it's supposed to look like:
```

[main]
plugins=ifupdown,keyfile

no-auto-default=00:08:a1:16:a8:83,

[ifupdown]
managed=true

```

(I had a hunch it was a network manager problem...)

---

