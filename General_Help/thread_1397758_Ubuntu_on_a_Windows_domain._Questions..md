---
title: "Ubuntu on a Windows domain. Questions."
date: 2010-02-03
forum: General Help
---

### Post by Roasted on 2010-02-03
At work, we run Windows... Windows domain, windows workstations, etc. Today my boss asked me my thoughts on running an Ubuntu lab within the mixture of our existing Windows setup.

Well, that brought several questions to mind. So I understand you can bind an Ubuntu computer to a Windows domain, seems easy enough, whether you do it through Samba or the other guide I read that I kind of forget at the moment, but anyway... 

I was just curious how Ubuntu interacts with domain users when on the windows domain. For example, if we have an Ubuntu machine on the Windows domain with a local user "administrator" and that's it, would any domain users be able to log into the Ubuntu work station, similar to how it is on Windows?

---

### Post by ant2ne on 2010-02-03
I've been toying with this too. There is a good thread someplace and it tells you how to add domain admins as sudoers and everything. It is bookmarked at work, so I'll dig it up tomorrow. (email me if I forget) Are you in a school district? I'm thinking about doing something similar.

---

### Post by Roasted on 2010-02-04
> **ant2ne said:**
> I've been toying with this too. There is a good thread someplace and it tells you how to add domain admins as sudoers and everything. It is bookmarked at work, so I'll dig it up tomorrow. (email me if I forget) Are you in a school district? I'm thinking about doing something similar.

Yes - I am in a school district. :) Thanks much!

---

### Post by ant2ne on 2010-02-04
here is that link [http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/]("http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/")

Here are some of my notes so far.
> 
#get required packages
apt-get update
apt-get install likewise-open samba samba-common sambaclient smbfs

#configure nssswitch for domain logins.
mv /etc/nsswitch.conf /etc/nsswitch.conf.original
cat passwd: compat winbind lwidentity > /etc/nsswitch.conf
cat group: compat winbind lwidentity >> /etc/nsswitch.conf
cat shadow: compat winbind >> /etc/nsswitch.conf
cat hosts: files dns winbind >> /etc/nsswitch.conf
cat networks: files >> /etc/nsswitch.conf
cat protocols: db files >> /etc/nsswitch.conf
cat services: db files >> /etc/nsswitch.conf
cat ethers: db files >> /etc/nsswitch.conf
cat rpc: db files >> /etc/nsswitch.conf
cat netgroup: nis >> /etc/nsswitch.conf

#joing domain
domainjoin-cli join domainname DomainAdministratorAccountName
sudo update-rc.d likewise-open defaults
sudo /etc/init.d/likewise-open start

#add domain admins to sudoers list
#I need to find a way to do an if line not exist then cat line into file
cat %DOMANNAME\\domain^admins >> /etc/sudoers

I'm working on making the windows shares (via samba) available to the users, but I'm having a hard time with that.

---

### Post by Roasted on 2010-02-04
> **ant2ne said:**
> here is that link [http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/]("http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/")

Here are some of my notes so far.


I'm working on making the windows shares (via samba) available to the users, but I'm having a hard time with that.

Yeah - our users have re-directed My Documents to \\server\students\seniors\john_smith, etc. If we can have that automatically come down accordingly to their home folder that'd be solid...

---

### Post by ant2ne on 2010-02-04
Sounds like we have similar projects in mind. We should work together. Our redirection locations are a bit more complicated, but something similar.

---

### Post by Roasted on 2010-02-04
Hmm... just to think out loud... isn't there some way that the samba config file can be tweaked to auto-link the home directory to \\server\students\seniors\john_smith somehow? Take Samba for example... you can rig it up so the windows boxes auto-link to your Linux server with their share being their home directory. Of course, that's Windows desktop/Linux server, exact opposite of what we're trying to do...

But if there's some sort of thing that can be applied to the smb.conf, 1 single command, to look at the Microsoft server and see the path to their re-directed My Documents.... hmm...

---

### Post by ant2ne on 2010-02-04
IDK if, from a client point of view, that can be done. I got a massive samba book. I'll dust it off and start digging.

---

