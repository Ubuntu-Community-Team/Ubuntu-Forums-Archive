---
title: "init script returns eth0 HW Address 00:00:00:00:00:00 on boot?"
date: 2009-10-03
forum: General Help
---

### Post by scottburton11 on 2009-10-03
I wrote a simple init.d script that assigns a machine's hostname and eth0 MAC address to some global variables and then prints them to the appropriate places in an application's config file. It works correctly when I manually execute the init script. However, when the machine starts up and hits runlevel 2, the hardware address evaluates to all zeroes, the broadcast MAC address.

Here are the relevant pieces:

/etc/default/my-init-script
```

HOSTNAME=`hostname`
MACADDRESS=`ifconfig -a | grep eth0 | awk '{print $5}' | tr '[:lower:]' '[:upper:]' | sed s/://g`

```

The template-config.sh is a here-doc that evaluates $HOSTNAME and $MACADDRESS in context:

/etc/init.d/my-init-script
```

#!/bin/bash

case "${1:-''}" in
  'start')
	mount -t tmpfs tmpfs /this-node
	/templates/template-config.sh > /this-node/config-file.xml
        ;;
esac

```

```

root@host:/# update-rc.d my-init-script start 98 2 3 4 5 . stop 98 0 1 6 .

```

At boot, $HOSTNAME evaluates properly but $MACADDRESS is all zeroes. When I manually run /etc/init.d/my-init-script, both evaluate properly.

Can anyone help me understand what I'm doing wrong here? Thanks!

---

### Post by blueridgedog on 2009-10-03
What happens if you call your script via an entry in /etc/init.d/rc.local?

---

### Post by dcstar on 2009-10-03
> **scottburton11 said:**
> I wrote a simple init.d script that assigns a machine's hostname and eth0 MAC address to some global variables and then prints them to the appropriate places in an application's config file. It works correctly when I manually execute the init script. However, when the machine starts up and hits runlevel 2, the hardware address evaluates to all zeroes, the broadcast MAC address.
.........
At boot, $HOSTNAME evaluates properly but $MACADDRESS is all zeroes. When I manually run /etc/init.d/my-init-script, both evaluate properly.

Can anyone help me understand what I'm doing wrong here? Thanks!

The Network Manager package **only configures your networking after you log in**, not before then (is is a piece of crap, IMH0).

Uninstall it and **install the gnome-network-admin package**, when you use that the network is actually available and working at start up.

---

### Post by lswb on 2009-10-04
First, HOSTNAME is already set by the system during boot and exported to all processes, that is why the HOSTNAME variable works OK.

Did you post the complete initscript? I don't see it reading /etc/default/my-init-script anywhere. Also variables must be "exported" if they are to be available to child processes. Try adding these lines after #!/bin/bash:

```

[ -r /etc/default/my-init-script ] && . /etc/default/my-init-script
export MACADDRESS

```
somewhere before the case statement.

---

### Post by scottburton11 on 2009-10-04
Thanks for the helpful input, everyone.

> **lswb said:**
> 
Did you post the complete initscript? I don't see it reading /etc/default/my-init-script anywhere. Also variables must be "exported" if they are to be available to child processes. Try adding these lines after #!/bin/bash:

```

[ -r /etc/default/my-init-script ] && . /etc/default/my-init-script
export MACADDRESS

```
somewhere before the case statement.

I left out most of it so as not to bore anyone. It's your basic "case start stop restart esac"-type affair. 

But you're right, I wasn't sourcing the /etc/default/my-init-script file. I added one of these at the top:

```

DEFAULTFILE=/etc/default/my-init-script

if [ -f $DEFAULTFILE ]; then
    . $DEFAULTFILE
fi

export MACADDRESS

```

And it works! Thanks!

Still, it leaves the mystery of the zeroes. If the file in /etc/defaults wasn't sourced on startup, shouldn't $MACADDRESS be an empty string? Why was it a perfectly formatted broadcast MAC?

I should have mentioned btw, this app likes the MAC as an upcased string without delimiters, that's why I'm stripping the colons. So ifconfig -a | grep eth0 | awk '{print $5}' would have to return 00:00:00:00:00:00 to get a string like 000000000000, right?

[quote=dcstar]
The Network Manager package only configures your networking after you log in, not before then (is is a piece of crap, IMH0).[/quote]

I wholeheartedly agree. Luckily, I'm not stuck with Network Mangler on this build - it's a super minimal debootstrapped system and the network is controlled by net-tools and iproute2.

Anyway, thanks again for the input!

---

### Post by blueridgedog on 2009-10-04
> **dcstar said:**
> The Network Manager package **only configures your networking after you log in**, not before then (is is a piece of crap, IMH0).

Uninstall it and **install the gnome-network-admin package**, when you use that the network is actually available and working at start up.

For a decade and a half, I configured RedHad Linux systems via entries in /etc/systemconfig/networking where there were config files for each interface.  It was really basic and very easy to manager/learn/teach.

Upon moving to Ubuntu as a desktop (being out of the IT field now) I was and am a bit stumped as to how one would go about configuring the the interfaces by hand other than raw ifcfg commands.  I can't find any config files that are close to my experiences.  There are files in /etc/network, but as your post suggests and my experiences allude to, I think gnome is actually managing the interfaces.  

Can you shed any light as to how interfaces are configured in a Debian system by default and in Ubuntu in particular?

---

### Post by lswb on 2009-10-04
> **scottburton11 said:**
> 
...
Still, it leaves the mystery of the zeroes. If the file in /etc/defaults wasn't sourced on startup, shouldn't $MACADDRESS be an empty string? Why was it a perfectly formatted broadcast MAC?

I should have mentioned btw, this app likes the MAC as an upcased string without delimiters, that's why I'm stripping the colons. So ifconfig -a | grep eth0 | awk '{print $5}' would have to return 00:00:00:00:00:00 to get a string like 000000000000, right?
...


It is a mystery to me too. Is it possible you have used MACADDRESS in an earlier part of the script and given it a default format of some kind?

---

### Post by scottburton11 on 2009-10-04
> **lswb said:**
> It is a mystery to me too. Is it possible you have used MACADDRESS in an earlier part of the script and given it a default format of some kind?

No, that's the strange thing. The only place MACADDRESS appeared was in the config file in /etc/default. While troubleshooting, I moved the file, and it predictably returned an empty string. When the config file is there, but not sourced in the init script, it returns all zeroes on startup. Weird.

> **blueridgedog said:**
>   
Can you shed any light as to how interfaces are configured in a Debian system by default and in Ubuntu in particular?

The /etc/networking/interfaces file is used by the ifupdown package, which is part of the standard Debian distribution. Here's a good rundown of how it's used:

[http://www.debian.org/doc/manuals/reference/ch05.en.html#_the_basic_network_configuration_with_ifupdown](http://www.debian.org/doc/manuals/reference/ch05.en.html#_the_basic_network_configuration_with_ifupdown)

When Gnome/Network Mangler is installed, their GUI tools manage the contents of this file and the ifupdown tools, and fail in unpredictable and frustrating ways. I don't understand why the Gnome tools suck so bad, but whenever I'm managing anything other than a standard desktop Ubuntu system, it's the first thing I remove. The net-tools, ifupdown and iproute packages are more widely supported and generally easier to use once you get used to them.

---

