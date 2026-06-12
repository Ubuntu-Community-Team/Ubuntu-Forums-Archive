---
title: "Set up DNS Name for Local Network Machine"
date: 2010-05-31
forum: General Help
---

### Post by mparker1113 on 2010-05-31
Hi, Ubunu 9.1 and I would like to set up my machine so that when i type a domain name into another browser on my local network, I will get the apache server. I currently access the pages i have on the ubuntu server by typing the ip address into another machine on the network, I would like to type in a DNS type of name instead. 
 
Ultimately, I would like to access this machine from outside of my network over the internet, and would appreciate insight on how to do this, too.
 
Thanks much for any input.

---

### Post by Dejavou42 on 2010-05-31
DYNDNS offers free services for what you are wanting to do. They also have guides for configuring the linux DNS Update software. Take a look here: [http://www.dyndns.com/support/clients/](http://www.dyndns.com/support/clients/).

---

### Post by Lucky. on 2010-05-31
Two ideas for your local network:

1.  Edit your /etc/hosts file on each of your linux client machines.  Add entries like the following:

```

<Your Server's IP Address>     <Your hostname>

```

Below is an example for my hosts file.  My file server "boss" also hosts two test web sites.

```

192.168.1.10     boss
192.168.1.10     webtestsite
192.168.1.10     anotherwebtestsite

```

If you're using Windows clients, you can edit:

C:\Windows\System32\Drivers\etc\hosts

And do the same type of thing for that file.

Once you have these files updated correctly, it's as simple as typing in the hostnames in a browser to get them to work.  This works pretty good, but it gets annoying every time you have to reformat a machine.

2.  The other way is to set up a DNS server on your network (or add DNS to your existing server).  Once you have hostname entries in your permanent DNS server that point to your website, all of your local clients (windows or linux) will automatically "work" when you type in the hostname on their browsers.

Problem is, if you're going go make a DNS server, you need to make sure that DHCP points to your DNS server (so either you configure your home router to use your DNS server, or you disable DHCP on your home router and make a DHCP server as well).

The whole thing is a bit tricky, but here's some how-to's on it:

[DHCP Server](https://help.ubuntu.com/10.04/serverguide/C/dhcp.html)

[DNS Server](https://help.ubuntu.com/10.04/serverguide/C/dns.html)

For a home implementation, don't worry about the secondary DNS server and replication in the how-to.  If you skip that part, that shortens the how-to by half.  One server should be enough for experimentation in your household.

Everything I wrote here will *only work for your local network*.  For external access on the web, Dejavou42 has it nailed on the head.  Sign up for a dynamic DNS service on the web, and make sure that your router supports it.  Combine that with port forwarding on your router.  Unfortunately since every router is different, there aren't many good "how to's" on the subject.

---

### Post by sdennie on 2010-05-31
The above suggestions are very good and I'd like to add another.  If all of your machines are Ubuntu (or probably any modern Linux) or OS X, you will automatically have a .local domain created for you that refers to the local network.  Try typing hostname.local in the browser and see if it resolves.

---

