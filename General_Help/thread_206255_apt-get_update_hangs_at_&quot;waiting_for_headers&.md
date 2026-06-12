---
title: "apt-get update hangs at &quot;waiting for headers&quot;"
date: 2006-06-29
forum: General Help
---

### Post by StickyStyle on 2006-06-29
I'm having a strange problem with a 6.06 server i just built, whenever i try to 'apt-get update' it hangs at "Waiting for headers".  It is connecting through an apt-proxy server on another 6.06 box, and all the other servers on the same vlan as the problem server can update just fine, just not this new one.  I have reinstalled twice now and i have the same issue each time, anyone have any ideas?  If i put the same us.archive.ubuntu.com address that is in my /etc/apt-proxy/apt-proxy-v2.conf file on the apt-proxy server into the problem servers sources.list it work fine :confused: 


When i do a debug apt-get with " apt-get update -o Debug::Acquire::http=true " i get -
0% [Working]GET [http://aptproxy:9999/ubuntu/dists/dapper/Release.gpg](http://aptproxy:9999/ubuntu/dists/dapper/Release.gpg) HTTP/1.1
Host: aptproxy:9999
Cache-Control: max-age=0
User-Agent: Debian APT-HTTP/1.3


GET [http://aptproxy:9999/ubuntu/dists/dapper-updates/Release.gpg](http://aptproxy:9999/ubuntu/dists/dapper-updates/Release.gpg) HTTP/1.1
Host: aptproxy:9999
Cache-Control: max-age=0
User-Agent: Debian APT-HTTP/1.3


GET [http://aptproxy:9999/ubuntu/dists/dapper-security/Release.gpg](http://aptproxy:9999/ubuntu/dists/dapper-security/Release.gpg) HTTP/1.1
Host: aptproxy:9999
Cache-Control: max-age=0
User-Agent: Debian APT-HTTP/1.3


0% [Waiting for headers]


From there it just hangs forever.  (when i say 'forever', i mean i waited no more than 20min :rolleyes: )

---

### Post by Seti on 2006-08-04
I'm having the same exact problem with Ubuntu 6.06.

---

### Post by StickyStyle on 2006-08-04
> **Seti said:**
> I'm having the same exact problem with Ubuntu 6.06.

[https://launchpad.net/distros/ubuntu/+source/apt-proxy/+bug/46776](https://launchpad.net/distros/ubuntu/+source/apt-proxy/+bug/46776)

There is a patch in there from Mark Howard that fixes the issue.

---

### Post by sgbirch on 2006-08-08
I ran into this problem, new dapper installations would not update from an apt-cache based server.  The following solved the problem:

Change /etc/apt.conf:

Acquire::http::Proxy "false";
to
Acquire::::Proxy "false"


I have absolutely no idea why this works though!

---

### Post by sanity on 2007-02-09
Well, this isn't working at all for me. Trying to do this on edgy, fully updated before I started. There is NO proxy config setup anywhere in /etc/apt or "apt-config dump". Explicitly turning off pipelining in apt-proxy does nothing. Explicitly turning off pipelining in apt does nothing. Restarting apt-proxy does nothing. Putting netcat between apt and apt-proxy shows that apt is not putting the hostname in its GET request.

In other words, I've tried every single fix for this issue I can find, with no results.

To be fair, the issue is slightly different. It doesn't die immediately, but at some random point while downloading. It also doesn't hang forever -- sometimes (after 5-10 minutes), it actually does get an update, but if I have to wait 5-10 minutes for the package list, apt-proxy is doing the opposite of speeding things up...

Couldn't find anything relevant in the logs for awhile, although I did find a python crash in there at one point. It also seems to simply be insanely slow while one client is downloading, whereas I actually get errors if two clients are downloading.

---

