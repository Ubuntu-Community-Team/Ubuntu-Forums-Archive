---
title: "how to set synaptic package manager to auto detect proxy settings for a network?"
date: 2010-05-24
forum: General Help
---

### Post by peepudeepu on 2010-05-24
SPM has just two options 1. Direct connection(no proxy) to internet and 2.manual proxy 
but my firefox cannot connect to internet with no proxy, It can connect to internet only on auto-detect proxy settings option.

Right now my SPM is not working. I can ping the SPM server from my console but apt-get is not working . It fails to fetch. please help..

---

### Post by DawieS on 2010-05-24
If you are using Ubuntu 10.04, click on **System** >** Preferences** > **Network Proxy**. Adjust your proxy settings and click on '**Apply System Wide...**'
:grin:

---

### Post by peepudeepu on 2010-05-24
I have applied system wide settings
I can even ping the ubuntu servers from the console but apt-get doesn't work. It fails to fetch.

here is the situation:
I am running ubuntu 10.04(32 bit ) on a windows xp 64 bit host in vmware workstation. Internet is working fine, but the synaptic package manager doesn't work.. 
what to do??

---

### Post by pdbq on 2010-08-26
you have to set up proxy in /etc/wgetrc - there is a line with the proxy setting. synaptic uses wget commnad to download packages

---

