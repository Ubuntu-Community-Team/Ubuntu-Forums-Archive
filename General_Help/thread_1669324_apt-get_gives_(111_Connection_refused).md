---
title: "apt-get gives (111 Connection refused)"
date: 2011-01-17
forum: General Help
---

### Post by davidah on 2011-01-17
I am getting a connection refused when I run sudo apt-get update

I am able to ping Internet hosts example:
ping [www.google.com]("http://www.google.com")

PING [www.l.google.com]("http://www.l.google.com") (74.125.227.19) 56(84) bytes of data.
64 bytes from 74.125.227.19: icmp_seq=1 ttl=58 time=29.8 ms
64 bytes from 74.125.227.19: icmp_seq=2 ttl=58 time=27.8 ms

--- [www.l.google.com]("http://www.l.google.com") ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 27.825/28.827/29.830/1.016 ms

I can even use wget to get the index page for a given repository where the updates are failing , but the updates still fail for example: 
wget [http://security.ubuntu.com/](http://security.ubuntu.com/) 
this will successfully download the index page. Yet when I run apt-get update I get this:
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:999 (91.189.88.30). - connect (111 Connection refused) [IP: 91.189.88.30 999]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:999 (91.189.88.30). - connect (111 Connection refused) [IP: 91.189.88.30 999]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:999 (91.189.88.30). - connect (111 Connection refused) [IP: 91.189.88.30 999]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:999 (91.189.88.30). - connect (111 Connection refused) [IP: 91.189.88.30 999]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to archive.ubuntu.com:999 (91.189.88.30). - connect (111 Connection refused) [IP: 91.189.88.30 999]

ext...

Any help would be greatly appreciated.

---

### Post by Smart Viking on 2011-01-17
Can you print the contents on your /etc/apt/sources.list file? Looks like some line is wrong, pointing it to port 999 or whatever

---

### Post by tredegar on 2011-01-17
I think "hardy" is out of date now, and no longer supported.
10.04 is Long Term Support (good for a few years yet)
10.10 is current
11.04 is soon ready for release.

---

### Post by davidah on 2011-01-17
As requested, here on the contents. This Server Edition of Hardy Heron which, if I read correctly is still supported.

# 
# deb cdrom:[Ubuntu-Server 8.04.4 _Hardy Heron_ - Release amd64 (20100121.3)]/ hardy main restricted

#deb cdrom:[Ubuntu-Server 8.04.4 _Hardy Heron_ - Release amd64 (20100121.3)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by Smart Viking on 2011-01-17
Maybe there is something wrong with apt-get, try to run```
sudo aptitude update
```instead

---

### Post by davidah on 2011-01-17
Same message using aptitude...

---

### Post by JC Cheloven on 2011-01-17
> **tredegar said:**
> I think "hardy" is out of date now, and no longer supported.
10.04 is Long Term Support (good for a few years yet)
10.10 is current
11.04 is soon ready for release.
 ^ this is good advice. 10.04LTS or 10.10

But as a matter of fact, Ubuntu 8.04 Hardy Heron it's alive until april 2011, [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) so it should still work. 

So to the OP: please try
```
sudo dpkg-reconfigure -a
```

---

### Post by davidah on 2011-01-17
Tried the below...Restarted the server, still no luck. 
sudo dpkg-reconfigure -a

---

### Post by JC Cheloven on 2011-01-17
Mmmm... perhaps the server you're trying to update from, is down temporarily. You could try updating for another mirror, or simply waiting a day or so. 
Can't thing of anything smarter right now...

---

### Post by davidah on 2011-01-17
I don't think the issue is on the update server's end. I have another server running the same version of Ubuntu. As a test, I copied the sources.list file from that server (which updates fine) to this one. Same result still gives an error connecting on port 999.

---

### Post by tgm4883 on 2011-01-17
Out of curiosity, can you ping archive.ubuntu.com? And what is the IP addresses.

---

### Post by tgm4883 on 2011-01-17
Also, what is the output of

```
ls /etc/apt/apt.conf.d/
```

---

### Post by davidah on 2011-01-19
Pinging the archive poses no issues..gives what appears to be a valid IP:

PING archive.ubuntu.com (91.189.88.46) 56(84) bytes of data.
64 bytes from lithium.canonical.com (91.189.88.46): icmp_seq=1 ttl=52 time=127 ms
64 bytes from lithium.canonical.com (91.189.88.46): icmp_seq=2 ttl=52 time=128 ms
64 bytes from lithium.canonical.com (91.189.88.46): icmp_seq=3 ttl=52 time=128 ms

--- archive.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 127.284/128.118/128.831/0.637 ms

The results of the directory listing are:

00trustcdrom  01autoremove  01ubuntu  05aptitude  70debconf

I'm baffled, and would really applicate any help solving this...This is a production mail server.

---

### Post by cjejuni on 2011-03-12
check the apt 

$ cat /etc/apt/apt.conf

did you get something like:
Acquire::http::Proxy "http://localhost:80/";

this is what i did...
$ sudo mv /etc/apt/apt.conf /etc/apt/apt.conf.bak

try again. if it does not work, put the apt.conf.bak > apt.conf

---

