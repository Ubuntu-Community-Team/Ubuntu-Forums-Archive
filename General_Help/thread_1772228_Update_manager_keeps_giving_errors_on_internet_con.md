---
title: "Update manager keeps giving errors on internet connection"
date: 2011-05-31
forum: General Help
---

### Post by samMD on 2011-05-31
I got an update notification from update manager just now and tried to update (internet working perfectly) but before it finishes downloading it gives an error of "check internet connection" constantly

---

### Post by searchfgold6789 on 2011-05-31
You may have to update the package information first. You can do this by entering this into a terminal window: (Applications > Accessories > Terminal):```
sudo apt-get update
```

---

### Post by Jesse813 on 2011-05-31
was just having the same problem myself and tried your your advice. worked great. didn't see any updates in the update manager when i checked it afterwards. Thanks :)

anyone know of any good reading material for getting familiar w/ the **Terminal**.  I'm a bit of a Noob to Linux and don't know much about it but I'd like to learn.

---

### Post by NewsMan2010 on 2011-05-31
I have the same problem, so let me try this out and I'll check back in if it works or not. ;)

---

### Post by searchfgold6789 on 2011-05-31
Here's a good one: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by Jesse813 on 2011-05-31
Thanks searchfgold6789 :) bookmarked it & will read it some more when I get time to.

---

### Post by NewsMan2010 on 2011-05-31
It worked. Thanks. :)

---

### Post by samMD on 2011-05-31
@searchfgold6789 worked like a charm thanks! Updates were downloaded and installed just fine!

---

### Post by tacantara on 2011-05-31
> **searchfgold6789 said:**
> You may have to update the package information first. You can do this by entering this into a terminal window: (Applications > Accessories > Terminal):```
sudo apt-get update
```


After running that command, you can install the updated packages while still in the terminal by entering the following command:

```
 sudo apt-get upgrade 
```

I had the same issue as the OP when Update Manager informed me of the 23 new packages it had waiting.  Using the Terminal resolved the problem.

Has anyone found any information on why Update Manager is having this issue today?

---

### Post by monkeybanana on 2011-09-21
thank you all. this helped me out!

---

