---
title: "Software update failure - Linux headers"
date: 2006-05-06
forum: General Help
---

### Post by wouterommeslag on 2006-05-06
I have a very weird problem:

In the software updates windows, I see three updates: 

linux-headers-2.6.12-10
linux-headers-2.6.12-10-386
linux-image-2.6.12-10-386

But I can't install them: I see the download window for a sec, and then I get the update window back, he doesn't download / install the updates.. Any ideas?
thx

---

### Post by Ramses de Norre on 2006-05-06
```
sudo apt-get update && sudo apt-get upgrade
``` that will give a more detailed error message.

---

### Post by Computeruser on 2006-05-06
Had you installed these items before?

I had installed the prior version of source and headers as of the most recent kernel version upgrade in order to install the VMware tools on this Ubuntu machine. I had also done a  "sudo apt-get install build-essential" as part of this process. 

The upgrade today went through without issue.

---

### Post by wouterommeslag on 2006-05-06
I just used Ramses'  apt-get upgrade and it finished without a problem... Thanks for your help!

---

