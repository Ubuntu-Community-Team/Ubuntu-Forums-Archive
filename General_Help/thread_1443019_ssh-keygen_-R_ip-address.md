---
title: "ssh-keygen -R ip-address"
date: 2010-03-30
forum: General Help
---

### Post by superbob666 on 2010-03-30
hey ppl;


i have tried using "ssh-keygen -R hostname/ip-address" on 9.10 ( fresh installed) it doesn't have any effect.it works prefectly on debian lenny".
is it just me or something i m missing ?


thanks

ps i know rm .ssh/know_hosts solve the problem but why is ssh-keygen -R not working :|

---

### Post by 2hot6ft2 on 2010-03-30
> **superbob666 said:**
> hey ppl;


i have tried using "ssh-keygen -R hostname/ip-address" on 9.10 ( fresh installed) it doesn't have any effect.it works prefectly on debian lenny".
is it just me or something i m missing ?


thanks

ps i know rm .ssh/know_hosts solve the problem but why is ssh-keygen -R not working :|
The format may have changed a little.
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[https://help.ubuntu.com/9.10/serverguide/C/openssh-server.html](https://help.ubuntu.com/9.10/serverguide/C/openssh-server.html)

---

### Post by superbob666 on 2010-03-31
hey 

thanks for reply but i cannt seem to find the information regarding "ssh-keygen -R" that is removing verification fingerprint. This option is suppose to remove the verification key of given hostname. Little confused :/

---

