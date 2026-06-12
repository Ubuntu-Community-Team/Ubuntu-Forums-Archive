---
title: "Kubuntu 10.04: System Wide Proxy Settings?"
date: 2010-06-10
forum: General Help
---

### Post by o_swas on 2010-06-10
Hello,

I've installed both Ubuntu 10.04 and Kubuntu 10.04 in VM's on my Mac, so I could try them both.

One thing I noticed is that Ubuntu has a central system property for setting network proxy information, including the proxy host, port, and authentication credentials.  When I enter those, Ubuntu apps like Synaptic are able to get out to the internet.

However, in Kubuntu, the system property for network property information appears incomplete.  I can enter the proxy host and port, but it won't let me enter authentication credentials.  Because I am behind an authenticating corporate proxy, Kubuntu is nearly useless because so many of the apps that depend on internet access (like KPackageit) simply dont' work.

Is there a way to set the system property for authenticating network proxies in Kubuntu?  Will the UI ever be finished so I can enter it in via a GUI like on Ubuntu?  I think I've seen this problem on previous Kubuntu releases so I think it's been around a while.

Thank you!!!

-Ryan

---

### Post by ba_saish on 2010-06-11
I am not sure about the Kubuntu GUI but until then you can use the terminal (knosole)  to install your packages.
export http_proxy=http://"username:password@proxy:port"
export ftp_proxy=ft://"username:password@proxy:port"

---

