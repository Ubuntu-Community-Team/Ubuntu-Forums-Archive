---
title: "Group Identification Number - are they random, mean anythiing?"
date: 2010-09-08
forum: General Help
---

### Post by Cubby on 2010-09-08
Hi all,

I've been doing some research on users/groups after my recent experience with dial up and needing to 'sudo adduser <me> dip.  That's all and well, but what is dip?  In my search, I only found some program with this abbreviation.  And, why is dip issued the number 30?  Does this number actually mean something, or is it randomly picked by the kernel maintainers?  When one creates a group, how does one know what identification number to give it, or does it matter as long as the number isn't already being used by another group.

I've looked at the --help pages for both adduser/useradd, addgroup/groupadd and it doesn't give much information there, nor does the man page Group.

For instance, Redhat shows they use GID 40 for dip, but in Ubuntu it is GID 30:
[http://www.redhat.com/docs/manuals/linux/RHL-7-Manual/ref-guide/s1-sysadmin-usr-grps.html](http://www.redhat.com/docs/manuals/linux/RHL-7-Manual/ref-guide/s1-sysadmin-usr-grps.html)
This gives a bit more clues as to how GID's are chosen: 
[http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/admin-primer/ch-acctsgrps.html](http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/admin-primer/ch-acctsgrps.html)
And one bug tracker said that dip 40 didn't work, that they had to change it to dip 30:
[https://bugs.launchpad.net/ubuntu/+source/ppp/+bug/292203](https://bugs.launchpad.net/ubuntu/+source/ppp/+bug/292203)

I see the problem isn't so black and white after reading this:
[http://fixunix.com/ppp/62608-need-pppd-setuid-root.html](http://fixunix.com/ppp/62608-need-pppd-setuid-root.html)

I'm just a bit confused.  In my other Debian-based distro, there is no dip group, but a group called sqid with GID 30.  That confused me even more.  Is there a good tutorial that explains what these groups are?  Some are self explanatory, like disk and scanner, but certainly not sqid or dip.  I only found a caching program called squid when doing a search. 

Thanks for any and all help with this!
Cubby

---

### Post by gzarkadas on 2010-09-08
They are not random (they are between 0 and 65535 after all :) ), but when it comes to fine details each distribution may make different choices than the others in some not so widely used groups. There are some more or less universal conventions however (yes, both numbers and names are conventions): 

-- 0 is for root, 
-- low values (below 1000) for system groups (daemons, services, utility groups like 'users', 'staff', etc.), and
-- high values for actual users -IF- the private group scheme is used by the distribution (private scheme: each user is assigned a unique group).

Look at the document "[Users and Groups in the Debian System]("file:///usr/share/doc/base-passwd/users-and-groups.html")". It should be in your local documentation.

---

### Post by Cubby on 2010-09-08
Thank you, gzarkadas!  That does clarify some questions I had.

It seems the GID number is read first as an identifier, rather than the name of the group.  In the Debian Gnome distro that does not have group dip, but does have the group squid (not sqid as I wrote above), when I mounted the partition that contains Ubuntu, and with file manager looked at /usr/sbin/pppd, it showed the group being squid instead of dip, as both have the same GID 30, so it appears it was reading the group number.  The name could have been 'hubsaboola' as far as it could care. :)
Time to do some more reading.
Thanks again!  Cubby

---

