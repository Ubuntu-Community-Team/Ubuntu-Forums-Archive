---
title: "Linux/Ubuntu in a corporate environment – Help"
date: 2011-07-25
forum: General Help
---

### Post by Williamea on 2011-07-25
We are currently rolling out Citrix and the powers that be decided as a good ROI point we would drop MS and go with Ubuntu. So We have made a locked down image and have gotten it to connect to our Citrix environment. We have a lot of remote users and now need to figure out how to patch these.
 
 
Is there a way to setup a patch server and regulate which patches get presented to our clients?
 
 
The clients will not be on the domain and will not be VPN'n back into our network.
 
 
 
Thanks in advance for any help and let me know if I need to move this to another Forum Topic.

---

### Post by 1clue on 2011-07-25
How many people do you have in IT?

It might make sense to make a regular mirror [https://wiki.ubuntu.com/Mirrors](https://wiki.ubuntu.com/Mirrors) of whatever image you choose, but to do anything more amounts to branching to your own distribution IMO, and you'd better have a whole lot of budget money for testing and building.

**Edit:**
Oh yeah.  Maybe you should pick an LTS image instead, that's generally aimed directly at the sort of setup you're after.

Another possibility is to go with a business-oriented distro like RedHat Enterprise Linux or Suse.  Then you not only have something that is already set up, you also have paid support whenever you need it.

---

### Post by drdos2006 on 2011-07-25
Have a look at Untangle [http://www.untangle.com/](http://www.untangle.com/) It may offer what you need......

regards

---

