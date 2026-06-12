---
title: "OpenVPN Fail in Ubuntu 11.10"
date: 2012-03-24
forum: General Help
---

### Post by MustangGT on 2012-03-24
Hello All,

I use OpenVPN for work.  I really need it and I can't live with not using Ubuntu.

So I set out to make it work.  I naturally started with just OpenVPN... the CLI client.  That will connect for me, but, sometimes it randomly says "Error 7: error adding route to external program" etc.

If I sudo apt-get remove --purge and then reinstall it, it works fine SOMETIMES.

So then I moved on to network-manager-openvpn  -- this one will connect, gets an IP and works fine for random amounts of time.  Sometimes no problem for 24 hours, sometimes it has an issue after 2 minutes.  When it hits an issue, it will ping the vpn server, nothing else loads.

**Gopenvpn - This one MIGHT be my saving grace.  It connects fine + is stable but with one big issue -- it breaks DNS!  When connected I can easily navigate to anything with it's IP but the DNS just breaks, no www.<>.com.  If I resolve the IP for a website on my iPhone with ping then enter it into the browser on my Ubuntu w/ GopenVPN connected it loads fine.  So in theory, if I could fix the DNS issue ........... **

I know the OpenVPN server is not the issue, I can run it in Windows fine no issue.

Does anyone have any suggestions?  Looks like I may have to leave Ubuntu for something as stupid as OpenVPN!  It kills me!

---

### Post by SeijiSensei on 2012-03-24
Look at the contents of /etc/resolv.conf before and after the tunnel is started.  If you have a different set of nameservers with the tunnel enabled, that's likely to be the problem.  It's also possible that the remote server is pushing DNS servers for whose addresses you don't have correct routing enabled on your client.  Take a look at the results of "route -n" before and after the tunnel is established as well.

One clunky solution is to make /etc/resolv.conf read-only for all users like this:

```
sudo chmod 444 /etc/resolv.conf
```

That will keep the OpenVPN server from changing your nameservers, but you must be sure that the servers in your list will work with and without the tunnel enabled before making it read-only.

There's a lot of postings out there about OpenVPN and DNS.  I suggest googling for "openvpn dns" for more help.

---

### Post by MustangGT on 2012-03-24
Sei - thank you for the reply.  If I can get this working, it would be the thing that lets me stay on Ubuntu, where I am happy.  Haha.

So... the /etc/resolv.conf is identical with GopenVPN connected & disconnected.

The routes obviously change as such:

No VPN:
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

```

With VPN:

```
0.0.0.0         10.9.0.17       0.0.0.0         UG    0      0        0 tun1
10.9.0.1        10.9.0.17       255.255.255.255 UGH   0      0        0 tun1
10.9.0.17       0.0.0.0         255.255.255.255 UH    0      0        0 tun1
67.215.224.12   192.168.0.1     255.255.255.255 UGH   0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

```

I am still in the exact same issue.  GopenVPN connects, for about 1-2 minutes I can navigate fine, I goto [www.whatsmyip.org](www.whatsmyip.org) and I have an IP from the VPN, all is dandy.

1-2 minutes later... DNS stops working.  If I use the IP for facebook.com or any other website - loads great, I can navigate fine.  I can navigate all it's sub pages no problem.  Etc.

If I try a website name though wwww.something.com bam, page not found.

Any ideas?

---

### Post by SeijiSensei on 2012-03-25
If the nameserver addresses remain unchanged, I'd guess that they're unreachable over the tunnel.  Since your configuration makes the remote end of the tunnel your default gateway, any requests to the DNS servers go over that link.

Do your nameservers have public IP addresses, or are they on a private network?  Perhaps you're getting nameservers in 192.168.1.0/24?

Here's a test.  Manually change the first nameserver entry in /etc/resolv.conf to 8.8.8.8, the IP of Google's public DNS server.  Does that help?

---

### Post by MustangGT on 2012-03-25
Hello

Your information helped a lot.  I found a fix, it seems like an issue specific to 11.10.

So ... in this case my fix is:

1. Create a script called up in /etc/openvpn to auto set the 8.8.8.8 Google DNS.

But... that isn't enough, also, I have to do this:

Stop OpenVPN (it auto launches and poorly): sudo /etc/init.d/openvpn stop

and then 


sudo /etc/init.d/openvpn restart


--It auto connects on restart + works fine.  Only by that method.

---

