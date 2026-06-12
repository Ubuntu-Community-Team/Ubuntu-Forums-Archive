---
title: "Boot-repair"
date: 2012-03-26
forum: General Help
---

### Post by mohanradhakrishnan on 2012-03-26
I want to use boott-repair as described in [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) before rebooting my machine because it is broken.
 
The first command doesn't connect to the server. proxies are set to point to my local cntlm to connect to our outgoing NTLM proxy. This works normally for apt-get
 
root@fSSCHNDLINUX:~# sudo -E add-apt-repository ppa:yannubuntu/boot-repair
Traceback (most recent call last):
File "/usr/bin/add-apt-repository", line 88, in <module>
ppa_info = get_ppa_info_from_lp(user, ppa_name)
File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 80, in get_ppa_info_from_lp
curl.perform()
pycurl.error: (7, "couldn't connect to host")
 
I don't have a repair disk and this is the only way. Can I get some advice ?
 
**Update **: I added the PPA to the System software sources and now it is trying to update but the gpg key is missing. 
 
Since the apt-key command fails to go through our corporate proxy(port 11371) I am trying to download it from the key website. The sites though seem to be timing out when i search.
 
Mohan

---

### Post by mohanradhakrishnan on 2012-03-28
The update is that I am not getting the GPG key to load in my system before pulling the boot repair software from the repository.
 
Signing key:[1024R/60D8DA0B ]("http://keyserver.ubuntu.com:11371/pks/lookup?search=0x3C48D16124B50277AF10D27F32B18A1260D8DA0B&op=index")
 
**Update :**
 
GPG is updated and boot-repair is running. I have to go through a cntlm proxy to hit my outgoing NTLM proxy. .bashrc is updated and wget is working through it. I have even updated the network settings.
 
boot-repair takes too long to scan. Wonder if it requires its own internet configuration !
 
Thanks.

---

