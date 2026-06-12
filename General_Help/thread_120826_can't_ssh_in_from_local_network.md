---
title: "can't ssh in from local network"
date: 2006-01-23
forum: General Help
---

### Post by darth_vector on 2006-01-23
do you have a firewall that could be blocking port 22 from the internal network?

you may also want to check /etc/ssh/sshd_config and look at the ListenAddress entry.

---

### Post by AndrewStout on 2006-01-23
[QUOTE=darth_vector]do you have a firewall that could be blocking port 22 from the internal network?[/QUOTE]

Not to my knowledge--not one that I set up.

[QUOTE=darth_vector]you may also want to check /etc/ssh/sshd_config and look at the ListenAddress entry.[/QUOTE]

I've done this, and R-ed TFM, but still don't quite know what it all means.  my sshd_config (unchanged from the installed version) starts with:
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
[...]

other entries in the man page that I thought sounded relevant were:

     GatewayPorts
             Specifies whether remote hosts are allowed to connect to ports
             forwarded for the client.  By default, sshd binds remote port
             forwardings to the loopback address.  This prevents other remote
             hosts from connecting to forwarded ports.  GatewayPorts can be
             used to specify that sshd should allow remote port forwardings to
             bind to non-loopback addresses, thus allowing other hosts to con&#8208;
             nect.  The argument may be “no” to force remote port forwardings
             to be available to the local host only, “yes” to force remote
             port forwardings to bind to the wildcard address, or
             “clientspecified” to allow the client to select the address to
             which the forwarding is bound.  The default is “no”.

     ListenAddress
             Specifies the local addresses sshd should listen on.  The follow&#8208;
             ing forms may be used:

                   ListenAddress host|IPv4_addr|IPv6_addr
                   ListenAddress host|IPv4_addr:port
                   ListenAddress [host|IPv6_addr]:port

             If port is not specified, sshd will listen on the address and all
             prior Port options specified.  The default is to listen on all
             local addresses.  Multiple ListenAddress options are permitted.
             Additionally, any Port options must precede this option for non
             port qualified addresses.

     UseDNS  Specifies whether sshd should look up the remote host name and
             check that the resolved host name for the remote IP address maps
             back to the very same IP address.  The default is “yes”.

...but I don't understand any of them well enough to make heads or tails.  Any further advice, anyone?

--A.

---

### Post by AndrewStout on 2006-01-23
Hi folks--

I've tried asking this question on a couple local mailing lists, and haven't gotten the answer I'm really looking for--I'm hoping the Ubuntu formus can help.

I recently set up my Ubuntu box so I can ssh in to it (by installing open-ssh).  Everything works fine from outside my local network--i.e., from almost anywhere, I can ssh to my IP (71.192.X.X) or to the dyndns.org subdomain I set up, and reach my box.  However, it doesn't work from my local network--i.e. from my laptop, right next to the Ubuntu box.  The setup is that the 71.192.X.X IP is actually the IP of my (Apple Airport Base Station) router, which I've set up to port-forward port 22 to my ubuntu box.  When the laptop is at home, it appears (to the external world) to have the same 71.192.X.X IP, of course.  If I ssh from the laptop-on-local-network to the Ubuntu box's LOCAL IP (10.0.1.X), it works, but if I ssh to the external IP (71.192.X.X) I get a "connection refused" message.  Someone has suggested to me that this is a "feature" to block connections coming from the same IP address (something about a "LAND attack"...), but I'd really like to be able to have access to my ubuntu box at a consistent name.

If anyone could tell me how to configure my setup so I can access my Ubuntu box by it's (or more accurately my router's) external IP from behind that same router, I'd really appreciate it.  I'm not even sure if the problem lies at the Ubuntu box or at the router, but I haven't seen any promising configuration options on the router's config interface, and I don't know what I'm doing on the linux box.  =)

(Others have suggested running my own DNS server, or setting up something in a hosts file.  I'm not crazy about either of these options--for one thing, 10.0.1.X may resolve to something else when I'm elsewhere...)

Thanks in advance,
Andrew Stout

---

