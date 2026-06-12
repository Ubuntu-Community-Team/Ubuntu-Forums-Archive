---
title: "Problems with squid, mediatomb after 10.04 upgrade"
date: 2012-04-29
forum: General Help
---

### Post by dbyrne on 2012-04-29
I upgraded from 8.04 to 10.04 reasonably painlessly yesterday, but several packages failed. I've used the example of squid, but hopefully the problem will be the same in the others. I've run "apt-get update", "apt-get clean", "apt-get autoremove".

The install seems to abort with the error "chown: invalid user: `daemon\r:daemon\r'". Both user and group daemon exist.

Any ideas would be very welcome !

David

# apt-get install squid
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  squidclient squid-cgi logcheck-database resolvconf
The following NEW packages will be installed
  squid
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
Need to get 764kB of archives.
After this operation, 1,937kB of additional disk space will be used.
Get: 1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/main squid 2.7.STABLE7-1ubuntu12.5 [764kB]
Fetched 764kB in 7s (102kB/s)
Preconfiguring packages ...
Selecting previously deselected package squid.
(Reading database ... 187174 files and directories currently installed.)
Unpacking squid (from .../squid_2.7.STABLE7-1ubuntu12.5_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up mediatomb-daemon (0.12.0~svn2018-6ubuntu2) ...
update-rc.d: /etc/init.d/mediatomb exists during rc.d purge (use -f to force)
dpkg: error processing mediatomb-daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mediatomb:
 mediatomb depends on mediatomb-daemon (>= 0.12.0~svn2018-6ubuntu2); however:
  Package mediatomb-daemon is not configured yet.
dpkg: error processing mediatomb (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Setting up squid (2.7.STABLE7-1ubuntu12.5) ...
chown: invalid user: `daemon\r:daemon\r'
dpkg: error processing squid (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mediatomb-daemon
 mediatomb
 squid
E: Sub-process /usr/bin/dpkg returned an error code (1)
#

---

