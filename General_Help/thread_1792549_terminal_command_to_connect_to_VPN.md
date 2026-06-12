---
title: "terminal command to connect to VPN?"
date: 2011-06-28
forum: General Help
---

### Post by loolooyyyy on 2011-06-28
i hate nm-applet, it keep fails, and doesnt recognize network well
it fails and turns down the eth0
i have to manually do this: sudo ifconfig eth0 up
and also manually connect: sudo pon dsl-provider
but still i cant connect to vpn (after failing of nm, since manually connecting to internet doesnt enable me to connect via nm)

i dont know how to use command "pptp" and it's manual is totally confusing (man pptp)

how does nm do it? what command does it run? i want to do it myself

ps: i know there is many fixes for nm-applet issues but if i solve it another problem pops out, so...

---

### Post by Azdour on 2011-06-28
Hi,

Sometimes I have to work on machines that have no nm-applet (for various reasons). I too am interested in how it creates the VPN connection. 
I know it stores the properties for each VPN connection in:

/home/<username>/.gconf/networking/connections

In here you will find connections numbering 1 upwards. In most of these directories is a further vpn directory that contains the %gconf.xml. This xml seems to contain the properties for that VPN connection.
 
How it uses these properties files I do not know. I have a feeling its using PON. I have used PON myself but have not found a way to use the existing VPN properties files. The following is a guide to using PON that maybe helpful to you:

[http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)

See the section titled: "Configuration, by hand"

Once set up I can then use the terminal to create a VPN connection.

---

### Post by Azdour on 2011-06-28
Hi,

I've done some more looking it seems when I use nm-applet to create a VPN connection on my process list I see a huge command it has run:

```

/usr/sbin/pppd pty /usr/sbin/pptp <gateway ip> --nolaunchpppd --logstring nm-pptp-service-9795 ipparam nm-pptp-service-9795 nodetach lock usepeerdns noipdefault nodefaultroute noauth user <username> refuse-eap refuse-pap refuse-chap require-mppe lcp-echo-failure 0 lcp-echo-interval 0 plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so

```

But I have been unsuccessful in copying and pasting this command to see if I can create the same connection with the same command via the Terminal...

---

### Post by loolooyyyy on 2011-06-28
> **Azdour said:**
> Hi,

I've done some more looking it seems when I use nm-applet to create a VPN connection on my process list I see a huge command it has run:

```

/usr/sbin/pppd pty /usr/sbin/pptp <gateway ip> --nolaunchpppd --logstring nm-pptp-service-9795 ipparam nm-pptp-service-9795 nodetach lock usepeerdns noipdefault nodefaultroute noauth user <username> refuse-eap refuse-pap refuse-chap require-mppe lcp-echo-failure 0 lcp-echo-interval 0 plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so

```

But I have been unsuccessful in copying and pasting this command to see if I can create the same connection with the same command via the Terminal...

i guess you're right manual suggests that you should use pptp through pppd (instead of allowing pptp to launch a new connection)
i'm already connected to vpn and i'm working, but as soon as i get disconnected, i'll try it,
however i'm not so positive about the last part> plugin :D

---

