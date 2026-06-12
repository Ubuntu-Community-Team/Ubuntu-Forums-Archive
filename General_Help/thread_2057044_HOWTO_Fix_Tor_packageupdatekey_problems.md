---
title: "HOWTO Fix Tor package/update/key problems"
date: 2012-09-12
forum: General Help
---

### Post by XxionxX on 2012-09-12
I was updating my Ubuntu 10.04 laptop, and I received this error,

```
W: GPG error: http://deb.torproject.org lucid Release: The following signatures were invalid: [problem-sigs]
```]

When I Googled it there weren't any helpful suggestions, but luckily I have had a similar problem before. So I went to[ the tor page which had the information about their gpg keys]("https://www.torproject.org/docs/debian"). And I followed these directions:

```
Then add this line to your /etc/apt/sources.list file:
deb     http://deb.torproject.org/torproject.org <DISTRIBUTION> main  where you put the codename of your distribution (i.e. lenny, sid, maverick or whatever it is) in place of <DISTRIBUTION>.   Then add the gpg key used to sign the packages by running the following commands at your command prompt: 
gpg --keyserver keys.gnupg.net --recv 886DDD89 gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -  Now refresh your sources, running the following command (as root) at your command prompt: apt-get update  If there are no errors you're good to continue. 
```

And I was good to go! I hope this helps someone, because Googling the exact error pulls up some stuff from 2010, and some totally unrelated stuff.

---

