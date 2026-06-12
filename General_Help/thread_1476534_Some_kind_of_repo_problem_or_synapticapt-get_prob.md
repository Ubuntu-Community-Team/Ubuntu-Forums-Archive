---
title: "Some kind of repo problem or synaptic/apt-get prob?"
date: 2010-05-07
forum: General Help
---

### Post by HHx66 on 2010-05-07
Everytime I try to use ANY 3rd party repo (even medibuntu) I get these errors: 



```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Now the odd thing is, I can ping the hosts, I can download and install from the old lists, and it seems to be at random what repo it is (like right now its actually saying the official ubuntu ones aren't working)

I also consistently get the question whether not to install saying packages are unsigned or unverified, when I KNOW the GPG keys are installed. So is this a bug or what? Any fixes?

---

### Post by newb85 on 2010-05-17
I was experiencing the same problem myself.

Unless you've already changed one of these settings, what's basically happening is that NetworkManager is setting your router up as the DNS server, and the router should use your ISP's DNS server to resolve addresses.  Somewhere in there, addresses aren't all being resolved correctly, hence "no address associated with hostname".  If you want to see what's being used to resolve addresses, open /etc/resolv.conf

NetworkManager can easily be set up to always use a manually-specified DNS server when using a given network.  Under "Edit Connections..." select the network where the issue is occurring (selecting the proper tab at the top, if necessary), and click *Edit*.  Under the "IPv4 Settings" tab, set the *Method* to "Automatic (DHCP) addresses only" and enter a third-party DNS server (e.g., Google's 8.8.8.8 ).

With any luck, this should solve your problem.

---

