---
title: "no proxy for apt"
date: 2010-06-12
forum: General Help
---

### Post by laronfin on 2010-06-12
hi,

I have ubuntu 10.04 installed on my laptop. While in company i need to setup proxy to use apt. At home, of course, proxy is not needed. I  have used System->preferences->network proxy to change proxy to direct internet access. however, it seems apt still tries to use the proxy i set before in company. I checked /etc/apt/apt.conf, /etc/environment, there is no proxy settings at all ... so i dont know how to remove proxy settings for apt. 

One thing i notice is that http_proxy, ftp_proxy, https_proxy is always pointing to the proxy i set before. If i unset e.g. http_proxy, and then try to use apt, e.g.
sudo apt-get install sshfs
I will get following errors:
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
If i  open another command window, http_proxy is still there and pointing to original proxy ....

Really appreciate any help

---

### Post by dcstar on 2010-06-12
> **laronfin said:**
> hi,

I have ubuntu 10.04 installed on my laptop. While in company i need to setup proxy to use apt. At home, of course, proxy is not needed. I  have used System->preferences->network proxy to change proxy to direct internet access. however, it seems apt still tries to use the proxy i set before in company. I checked /etc/apt/apt.conf, /etc/environment, there is no proxy settings at all ... so i dont know how to remove proxy settings for apt. 
........

There is no need to play with system files, use Synaptic to remove the proxy settings.

---

