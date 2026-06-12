---
title: "SSH Login / Zentyal Problems"
date: 2012-07-01
forum: General Help
---

### Post by dwebb21 on 2012-07-01
Please exercise some patients, I am a noob.

I am running: Ubuntu 10.04.3 LTS

My home server is running Zentyal.  I wanted to change my password so I did it through SSH.  I forgot that I should have done it through Zentyal.  

After changing the password in SSH, I tried to login to Zentyal and wasn't able to get it.  After trying many things I was reading in forums, I was finally able to get in, however, I received error messages that would not let me passed it to the admin.  

I would post those errors but I have since tried to remove Zentyal without any luck.  I get this when I try to purge:

 Errors were encountered while processing:
 zentyal-dhcp
 zentyal-ntp
 zentyal-infrastructure
 zentyal-usercorner
E: Sub-process /usr/bin/dpkg returned an error code (1)

After trying to purge, I cannot re-install or completely remove.

I would be perfectly fine with removing Zentyal entirely at this point but cannot find any articles explaining how to do this.

Other issues I am having:

1. When I SSH in, it asks for my password right away.  Once I type in my password, it takes minutes before it finally connects me.  
2. When I try to FTP from outside connection and locally, it times out.  


I really would rather not start over.  Can anyone help?

Thanks in advance,
dwebb21

---

### Post by dwebb21 on 2012-07-01
Anyone willing to give me some suggestions on things to try or things to look at?

---

