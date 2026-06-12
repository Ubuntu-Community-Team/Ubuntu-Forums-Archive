---
title: "Installing updates and packages problem"
date: 2010-09-28
forum: General Help
---

### Post by rgiles43 on 2010-09-28
Hello Everyone,

I have installed Ubuntu 10.04 server edition onto my desktop. However when I try to run updates or install any package I am running into errors. I have successfully pinged google.com, and see that I have a valid ip address and am able to communicate with another computer on the network. 

Command:

sudo apt-get install updates
sudo apt-get install xinetd
sudo apt-get install atftpd

I have also attached a screenshot of the errors I am receiving.

Any help is greatly appreciated.


Thanks,

---

### Post by snowpine on 2010-09-28
Try the following command to refresh your list of available packages:

```
sudo apt-get update
```

---

### Post by rgiles43 on 2010-09-28
Hello,

Thank you very much snowpine. I have now got my updates and I am now able to install atftpd. LOL such a small detail that I was missing. 

Again much thanks.

---

