---
title: "Revert Firefox 8 To Firefox 7 In Maverick"
date: 2011-10-08
forum: General Help
---

### Post by Precipitous on 2011-10-08
How can I revert Firefox 8 to Firefox 7 in Maverick? I have the Mozilla Stable PPA installed, so I tried uninstalling Firefox in Synaptic, then running sudo apt-get install firefox in the terminal. This just put version 8 back on my machine...

Does anybody have any suggestions?

---

### Post by kamaji792 on 2011-10-08
Hi Dude,

I think you need to remove the repository you used to install ff8.

When you installed ff8 I guess you must have added a new repository to allow you to do this.  Unless you remove that ff8 repository it will just re-install it.

Try the following link to see how to manage repositories:
[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Repositories_in_Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Repositories_in_Ubuntu")

atb k

---

### Post by Precipitous on 2011-10-08
> **kamaji792 said:**
> Hi Dude,

I think you need to remove the repository you used to install ff8.

When you installed ff8 I guess you must have added a new repository to allow you to do this.  Unless you remove that ff8 repository it will just re-install it.

Try the following link to see how to manage repositories:
[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Repositories_in_Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Repositories_in_Ubuntu)

atb k
That was removed long before I decided to downgrade to version 7. The only Mozilla PPA I have installed is: mozillateam/firefox-stable. Anybody have any other ideas?

---

### Post by Precipitous on 2011-10-09
I was able to resolve this by running the following commands in the terminal:

```
sudo apt-get purge firefox
sudo apt-get install firefox=7.*
```

---

