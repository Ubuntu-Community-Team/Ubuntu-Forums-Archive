---
title: "Newbie: help with Onboard (virtual keyboard)"
date: 2012-04-23
forum: General Help
---

### Post by mikegahan on 2012-04-23
Dear friends
 
This is my first post so please me gentle with me.
 
I successfully installed the "Onboard virtual keyboard" package(i got a message saying it was successfully installed). But now i cannot find the package to use it. Can someone tell me how to use/locate the programme?
 
Many :confused::pThanks

---

### Post by 11jmb on 2012-04-23
It always helps to say what Ubuntu version you are using and how you installed the application for problems like this, because the answer could be different

---

### Post by 11jmb on 2012-04-23
You can do a quick check in your /usr directory for your installed packages

```
grep -r onboard /usr
```

Binaries that can be run from the command line are usually installed in /usr/bin and /usr/local/bin

I think apt-get/synaptic usually installs in the former, while most source builds generally install in the latter

---

### Post by carys on 2012-04-23
Open up the dash (that is the top icon on the left hand side bar) and type in the words keyboard. If it is installed the icon should show up. You just need to click on it.

Thats if you have version 11.10 anyway

---

