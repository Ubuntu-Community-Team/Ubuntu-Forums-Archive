---
title: "Need remote command line administration"
date: 2012-01-26
forum: General Help
---

### Post by volvo64 on 2012-01-26
Hi,

I'd like to set up some sort of remote administration for our Ubuntu 10.04 boxes going out. We're pushing ~500 out. I'd like to be able to enable a service that would 'register' each box with a central server and allow for either command line administration or GUI administration.

Since we won't be able to do port-forwarding on each site and because the public IP may constantly change, vanilla SSH is unacceptable. I need something like Teamviewer (which I would use, except they don't allow for Unattended Access in Linux).

We have a server we can use for this, if anyone knows of any solutions.

---

### Post by Lars Noodén on 2012-01-26
More information is needed to come up with decent suggestions.  How many sites are you talking about and where is the one server in relation to them?  Can you tell a little more about the topology of your network(s)?

---

### Post by volvo64 on 2012-01-26
> **Lars Noodén said:**
> More information is needed to come up with decent suggestions.  How many sites are you talking about and where is the one server in relation to them?  Can you tell a little more about the topology of your network(s)?

This info is hard to quantify. We're rolling out kiosks in any number of different service industries. The machines could be placed in hotel lobbies, restaurants, stadiums, malls, etc... We'll have no control over the networks that they're placed on. 
The server isn't completely defined yet (we don't have it set up or bought, but it will be available if we need it), but I'm going to push for a cloud solution (i.e., we won't have any of our own hardware on-site; the hardware will be maintained through a third party). I believe we're going to have to use a Windows server in order to facilitate another software we use.

---

### Post by Lars Noodén on 2012-01-26
well if you're going for a hosted solution (aka Cloud) then you will almost certainly have one external IP address.  That will allow the machines to phone home.  In that case you could do anything from a reverse tunnel in SSH to running synchronization software like [Radmind](http://rsug.itd.umich.edu/software/radmind/).

---

### Post by volvo64 on 2012-01-26
Thanks for the quick reply. However, what I'm seeing about reverse-SSH is that it's well suited for accessing one machine behind a firewall, but I don't think it will scale well. I don't think it will be a good idea to have 500 open SSH connections to our server. Also, there seems to be a lot of room for error when the tech on-site sets up the SSH tunnel (i.e., he could easily pick a port taken by another service or accidentally duplicate ports used by different computers). It seems to be better suited to accessing one computer behind a firewall, not 500.

As far as radmind goes, unless I'm missing something, that doesn't allow for remote CLI administration, just for image deployment. While it may be nice to  upgrade kiosks this way, it won't make for good everyday troubleshooting. Also, commands would have to be run physically from the client, which is what I'm trying to work around. Was I wrong? Did I miss a feature or hack?

---

### Post by Lars Noodén on 2012-01-26
That about sums up the shortcomings of both.  The ports problem is what keeps the reverse tunnel idea from scaling that well.  However, I'm not so sure that idle connections would be such a burden on the machine.  

Not having permanent IP addresses to work with is not an insignificant constraint.  

Another option might be to configure the kiosks to use a [dynamic DNS](https://help.ubuntu.com/community/DynamicDNS) service to be accessible via a host name, but that is not 100% reliable.  There, you'd have to make sure that the on-site tech sets up each machine with a unique address.

---

### Post by CharlesA on 2012-01-26
My suggestion would be to try dynamic DNS, but that might not work if you are unable to allow ssh thru the firewall on the network it is on.

reverse ssh would be the best solution unless you can get team viewer working.

---

### Post by volvo64 on 2012-01-26
> **CharlesA said:**
> My suggestion would be to try dynamic DNS, but that might not work if you are unable to allow ssh thru the firewall on the network it is on.

reverse ssh would be the best solution unless you can get team viewer working.
I don't think Dynamic DNS would do much for punching holes in firewalls or NAT.

Another problem I see with reverse SSH is that with 500 (or more) connections to one server, how would you find which one you're looking for? How would you organize it to know which connection goes to which computer? I'd still have to have someone on-site to figure out which port it's connected through, which is what I'm trying to avoid (having someone on-site). I could have them fire up TeamViewer instead, or hell, as long as someone were there to type and/or tell me stuff, have them create the reverse SSH on demand.

---

### Post by CharlesA on 2012-01-26
> **volvo64 said:**
> I don't think Dynamic DNS would do much for punching holes in firewalls or NAT.

Another problem I see with reverse SSH is that with 500 (or more) connections to one server, how would you find which one you're looking for? How would you organize it to know which connection goes to which computer? I'd still have to have someone on-site to figure out which port it's connected through, which is what I'm trying to avoid (having someone on-site). I could have them fire up TeamViewer instead, or hell, as long as someone were there to type and/or tell me stuff, have them create the reverse SSH on demand.

You'd need a list. ;)

I'd go for having someone there that can launch teamviewer and them read you off the info and then connect that way.

---

### Post by volvo64 on 2012-02-01
I've been working on other projects, but haven't forgotten about this one. 

Other fora have suggested using Puppet. Any opinions on that? I'm just now getting to know what it is.

---

### Post by CharlesA on 2012-02-01
Never heard of it.

---

