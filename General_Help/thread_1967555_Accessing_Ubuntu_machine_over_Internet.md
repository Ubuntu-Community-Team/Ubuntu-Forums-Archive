---
title: "Accessing Ubuntu machine over Internet"
date: 2012-04-28
forum: General Help
---

### Post by markyork on 2012-04-28
I'm planning on setting up a file server on an unused desktop computer for my home network.

I'm wondering what I would need to do if I want to be able to access the files on the server over the Internet (login from another computer outside my home LAN). If it would require some sort of web interface, that's no problem, as I can handle that myself.

What kind of security considerations do I need to make?

What exactly do I need to do (instructions) to set up my Ubuntu installation for remote file access?

Regarding where I'm starting from in terms of Linux knowledge, I've only worked with Ubuntu before for a couple of months when 11.04 came out, so I'm expecting a lot of learning involved with this project...

---

### Post by josephmills on 2012-04-28
Please read the ubuntu server manual it is free and there for you. 

also I would suggest paying 105 usd for support from Ubuntu for a year/ 


there are many many many dumb people that are going to tell you different and you will see. but just read the manual 

DO NOT LISTEN TOO PEOPLE that say just use ssh or something like that. YOU need to know how to use and why you should use. Read the manual

here is the guide 

[https://help.ubuntu.com/12.04/serverguide/](https://help.ubuntu.com/12.04/serverguide/)


you will find more and more links in there.

---

### Post by Monotoko on 2012-04-28
> **markyork said:**
> I'm planning on setting up a file server on an unused desktop computer for my home network.

I'm wondering what I would need to do if I want to be able to access the files on the server over the Internet (login from another computer outside my home LAN). If it would require some sort of web interface, that's no problem, as I can handle that myself.

Hi there, there are a few considerations for a home network. The best idea is to use SFTP ([http://en.wikipedia.org/wiki/SSH_File_Transfer_Protocol](http://en.wikipedia.org/wiki/SSH_File_Transfer_Protocol)) which filezilla (on the other end supports)

You then just put your username, password and IP address (and port 22) in on the other end and it'll connect you just fine.

Another consideration is port forwarding, you may need to log into your routers config and forward port 22 from your router to the file sharing machine.

---

### Post by bodhi.zazen on 2012-04-28
Opened again. IMO over the internet ssh (scp, sftp, or sshfs) is most secure, but you need to first learn to secure your ssh server. 

The basics of securing ssh are to use keys and disable password authentication.

See: [http://bodhizazen.net/Tutorials/SSH_security](http://bodhizazen.net/Tutorials/SSH_security)

If you do not secure your ssh server you are likely to get cracked, ssh is #2 to VNC in commonly cracked services on these forums.

Alternates to ssh exist and range from rsync , rsync over ssh, and http/https . http and https are great for one-way transfers.

---

### Post by josephmills on 2012-04-28
> **markyork said:**
> I'm planning on setting up a file server on an unused desktop computer for my home network.

I'm wondering what I would need to do if I want to be able to access the files on the server over the Internet (login from another computer outside my home LAN). If it would require some sort of web interface, that's no problem, as I can handle that myself.

> 
What exactly do I need to do (instructions) to set up my Ubuntu installation for remote file access?




Setting up a file server
puppet file server 
[http://docs.puppetlabs.com/guides/file_serving.html](http://docs.puppetlabs.com/guides/file_serving.html)

Chef 
[http://wiki.opscode.com/display/chef/Chef+Configuration+Settings](http://wiki.opscode.com/display/chef/Chef+Configuration+Settings)

Cf engine 
[http://cfengine.com/demos](http://cfengine.com/demos)

Salt 
[http://salt.readthedocs.org/en/latest/index.html](http://salt.readthedocs.org/en/latest/index.html)

Samba 
[https://help.ubuntu.com/11.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/samba-fileserver.html)

Rackspace 
[http://www.rackspace.com/knowledge_center/index.php/Ubuntu_-_Setup](http://www.rackspace.com/knowledge_center/index.php/Ubuntu_-_Setup)

Metal as a Service
[https://wiki.ubuntu.com/ServerTeam/MAAS](https://wiki.ubuntu.com/ServerTeam/MAAS)

Deploy Server fleets
p1 
[http://cloud.ubuntu.com/2011/09/oneiric-server-deploy-server-fleets-p1/](http://cloud.ubuntu.com/2011/09/oneiric-server-deploy-server-fleets-p1/)

p2 
[http://cloud.ubuntu.com/2011/09/oneiric-server-deploy-server-fleets-p2/](http://cloud.ubuntu.com/2011/09/oneiric-server-deploy-server-fleets-p2/)


Samba Standalone Server With tdbsam Backend
[http://www.howtoforge.com/ubuntu-11.10-samba-standalone-server-with-tdbsam-backend](http://www.howtoforge.com/ubuntu-11.10-samba-standalone-server-with-tdbsam-backend)

> 
What kind of security considerations do I need to make?

there are many many many. Here are a couple things that I think are important
SSH 

how to change your ports 
[http://www.youtube.com/watch?v=3YzCxBkx6GQ](http://www.youtube.com/watch?v=3YzCxBkx6GQ)

How too log in with-out ssh password
[http://www.youtube.com/watch?v=xRLzCHkfW8A&feature=relmfu](http://www.youtube.com/watch?v=xRLzCHkfW8A&feature=relmfu)

Security notices 
[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

Firewalls 
guide 
[https://help.ubuntu.com/12.04/serverguide/firewall.html](https://help.ubuntu.com/12.04/serverguide/firewall.html)

ipcop
[http://www.ipcop.org/docs.php](http://www.ipcop.org/docs.php)

pfsense
[http://doc.pfsense.org/index.php/Main_Page](http://doc.pfsense.org/index.php/Main_Page)

IP Tables 
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

GPG 
[https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

Great wiki by Dangertux, OpSecShellShock, haqking,
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

AppArmor 
[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)

Snort  & other IDS 
[https://help.ubuntu.com/community/SnortIDS](https://help.ubuntu.com/community/SnortIDS)

openvas 
[http://www.openvas.org/](http://www.openvas.org/)

Nessus 
[http://www.tenable.com/products/nessus](http://www.tenable.com/products/nessus)

NeXpose
[http://www.rapid7.com/products/nexpose-community-edition.jsp](http://www.rapid7.com/products/nexpose-community-edition.jsp)

w3af 
[http://w3af.sourceforge.net/](http://w3af.sourceforge.net/)

kippo 
[http://code.google.com/p/kippo/](http://code.google.com/p/kippo/)

OFF-SEC 
[http://www.offensive-security.com/information-security-certifications/](http://www.offensive-security.com/information-security-certifications/)

CEH 
[www.eccouncil.org/CEH.htm](www.eccouncil.org/CEH.htm)

CBTNuggets 
[http://www.cbtnuggets.com/it-training-videos/security](http://www.cbtnuggets.com/it-training-videos/security)
 
Zone-h 
[http://www.zone-h.org/](http://www.zone-h.org/)

exploit db 
[http://www.exploit-db.com/](http://www.exploit-db.com/)

squid 
[https://help.ubuntu.com/community/Squid](https://help.ubuntu.com/community/Squid)


> 
Regarding where I'm starting from in terms of Linux knowledge, I've only worked with Ubuntu before for a couple of months when 11.04 came out, so I'm expecting a lot of learning involved with this project...


that is great too hear! 


here are some more links 

Landscape 
[http://www.canonical.com/enterprise-services/ubuntu-advantage/landscape](http://www.canonical.com/enterprise-services/ubuntu-advantage/landscape)

Bugs in Samba 
[https://bugs.launchpad.net/ubuntu/+source/samba](https://bugs.launchpad.net/ubuntu/+source/samba)

juju 
[https://juju.ubuntu.com/](https://juju.ubuntu.com/)

openstack 
[http://openstack.org/](http://openstack.org/)

Debian New Maintainers' Guide
[http://www.debian.org/doc/manuals/maint-guide/](http://www.debian.org/doc/manuals/maint-guide/)

Securing a Samba File and Print Server
[https://help.ubuntu.com/10.04/serverguide/samba-fileprint-security.html](https://help.ubuntu.com/10.04/serverguide/samba-fileprint-security.html)

Ubuntu beginners Team 
[https://wiki.ubuntu.com/BeginnersTeam](https://wiki.ubuntu.com/BeginnersTeam)

dd-wrt
[http://www.dd-wrt.com/site/index](http://www.dd-wrt.com/site/index)

portforwarding 
[http://portforward.com/routers.htm](http://portforward.com/routers.htm)

DMZ 
[https://help.ubuntu.com/community/DMZ%20host%20with%20SecurePass](https://help.ubuntu.com/community/DMZ%20host%20with%20SecurePass)

canonical training 
[http://www.canonical.com/consumer-services/training](http://www.canonical.com/consumer-services/training)

Ubuntu VTC 
[http://www.vtc.com/products/Ubuntu-Server-Tutorials.htm](http://www.vtc.com/products/Ubuntu-Server-Tutorials.htm)

Live support chat 
[https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat)

In software center if you search for "ubuntu server book" 
there is a great book for sale there. 

I hope that these links help and I will try to keep up on this list. 


Joseph

---

### Post by markyork on 2012-04-28
Wow! Thanks for all of the link, Joseph!

Like I said in my original post, I know I've got my share of reading to do - hopefully not **all** of that! ;)

---

