---
title: "Samba performance ESXi 5.0"
date: 2012-06-27
forum: General Help
---

### Post by cbuhler on 2012-06-27
Hello,

I'm currently testing out a new samba server running on top of an ESXi 5.0 server. The server has 8GB ram and an i5, this is the second VM so there is nothing running on it. I have another samba server running on significantly less hardware that can push 60-70MB/s. However, when I setup Samba on this machine I get speeds of 2-3MB/s. The configuration is indentical in terms of configuration options like TCP nodelay,

My other VM which is openfiler can push around 110MB/s using iSCSI.

I was just curious if anyone else had encountered a similar problem?

---

