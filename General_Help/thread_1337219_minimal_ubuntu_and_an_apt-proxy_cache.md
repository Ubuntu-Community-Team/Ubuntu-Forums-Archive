---
title: "minimal ubuntu and an apt-proxy cache"
date: 2009-11-25
forum: General Help
---

### Post by cong06 on 2009-11-25
I'm working on installing several computers. I've found that the most efficient way to go about doing this is to install with the minimal ubuntu CD and then use an full apt-proxy cache to copy the rest of the files over (via local network)

The minimal ubuntu CD has a way to set the proxy, which is good, but it only does this for the ubuntu software updates. Is there a way to set this up for the security updates too?
I know after the CD runs, I can edit the /etc/apt/source.list file to point to my proxy, but while the CD itself is installing it's pulling files off of the security.ubuntu.com backend instead of my own.

---

### Post by cong06 on 2009-12-14
Since I'm also running squid and squidguard on this server, I added this line to my squidGuard.conf file

```

rew aptproxy {
    s@^http://security.ubuntu.com/ubuntu/@http://10.42.43.1:9999/ubuntu-security/@
    s@^http://ke.archive.ubuntu.com/ubuntu/@http://10.42.43.1:9999/ubuntu/@
    s@^http://archive.ubuntu.com/ubuntu/@http://10.42.43.1:9999/ubuntu/@
    s@^http://archive.cannonical.com/ubuntu/@http://10.42.43.1:9999/partner/@
}

```


found at: [http://www.linuxquestions.org/questions/linux-networking-3/squid-squidguard-rewrite-247544/#post3790690](http://www.linuxquestions.org/questions/linux-networking-3/squid-squidguard-rewrite-247544/#post3790690)

Note: add localnet ips to "manage"? maybe that made it work...

---

### Post by SecretCode on 2009-12-14
I've been using a simpler :) solution - disconnect the network for the CD install, then edit /etc/sources.list, then update - upgrade!

---

### Post by cong06 on 2009-12-16
And you're using the Minimal Ubuntu? Cause mine says:
> The specific Ubuntu archive mirror is either not available, or does not have a valid Release file on it. Please try a different Mirror.
If I try and install without an Internet connection for my apt-proxy computer.

---

