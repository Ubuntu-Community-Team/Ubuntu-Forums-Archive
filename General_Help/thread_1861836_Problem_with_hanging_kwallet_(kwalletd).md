---
title: "Problem with hanging kwallet (kwalletd)"
date: 2011-10-16
forum: General Help
---

### Post by piteer1 on 2011-10-16
Hi,

After clean install of Kubuntu 11.10 I have problems with kwallet. It does not serve passwords to all programs requesting it. This gives lots of other problems (hanging Akonadi, network manager, etc.). I saw that the only solution to make it running back for current session is killing kwalletd and restarting it. It is really frustrating because network manager does not want to connect immidiately to any wifi and additionally I'm getting requests for password for all my email accounts from Akonadi. For now I've only found this error in ~/.xsession-errors
```

[2145:2273:66244067:ERROR:native_backend_kwallet_x.cc(594)] Failed to complete KWallet call: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```
Any ideas how to repair this issue?

Best regards

---

### Post by Sebastien Beausoleil on 2012-04-14
Hi,

I just installed Kubuntu 11.10 64bits on a Lenovo B575 laptop and I'm pretty sure that I have the same problem as piteer1.

I really don't know where to start to solve that problem so any help is welcome.

I don't know which infos I could send here, so ask me what I should post.

Symptoms:

After I log in my session, Kwalletmanager ask for the password to unlock the Kwallet. Despite the fact I enter the right password, the NetworkManager, like all other application, didn't seems to receive the passphras and the key icon stay on the wifi icon. 

Thank you for your help.

---

