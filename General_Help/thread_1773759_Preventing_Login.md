---
title: "Preventing Login"
date: 2011-06-02
forum: General Help
---

### Post by katykat on 2011-06-02
I have here a small peer-peer network with total sharing, and being the only user besides the better half, no interest whatever in local security. We do NOT use wireless so that is not an issue. 

Thje Win XP machines have most of their services disabled, and the few buggers that get in have a devil of a time reaching out. 

There is one main Linux machine, and that is the basis of this inquiry. It boots normally to Meerkat, but can also boot to Win and Fedora. 

The Linux machine, through Samba on gnome-commander has full access to the other Win machines. 
They DO NOT have access to it, and I plan on keeping it that way.  

I have yanked ssh, nfs, and anything resembling remote desktop functions from init.d (though I can enable them if needed). Telnet and some ports are blocked at the router.  Hosts.deny is set to all:all. 
I am behind a hardware firewall. 

The object of my inquiry here is how to ensure that nothing ever gets a login prompt from this machine, after bootup. Aside rrom, my local TTY's . In other words, I dont want anything, local or internet to be able to access this machine. But total access from the keyboard. 

Is there a FAQ for this type of security? 
I dont want to waste time or CPU cycles trying to verify users at the keyboard. If they are at the keyboard I want total access with minimum fuss. 

As far as the internet goes I do want to ensure that nothing ever downloads with executable permissions, or executes without explicit permissions - no automatic updates permitted here.

Is there a utility that will allow processes internet access, but only on a case-by-case basis like Comodo in Win? And allow - NO, TEMPORARY, FULL ACCESS priviledges?

Are there any good local port scanners, that can also hopefully make recommendations?

---

### Post by pricetech on 2011-06-02
> **katykat said:**
> 
I am behind a hardware firewall. 


Unless it's poorly configured, you're good.

---

### Post by katykat on 2011-06-07
Any good FAQs for configuring the router?

This is a Netgear FVS318. 

It has VPN on it, and I havent a clue as to what VPN is, or how I can protect any 'tunnelling' into it.

I am on a cable network, if that is of any herlp. Comcast!

---

