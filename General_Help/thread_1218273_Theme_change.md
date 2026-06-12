---
title: "Theme change"
date: 2009-07-20
forum: General Help
---

### Post by satya61229 on 2009-07-20
Hi

Sometimes when I login into ubuntu, I saw some difference in theme. 
My system is a desktop system with net connection. You can see the difference near network connection icon. Firefox titlebar color also changed. When I restart the system then problem get solved.

Is there a virus problem or something else?






Thanks
Satya Prakash

---

### Post by cariboo on 2009-07-20
It is definitely not a virus, in one image you a power manager icon and no network manager icon, and in the other you have a network manager icon and no power manager icon. I would suggest you probably have a misconfigured theme.

---

### Post by grayn0de on 2009-07-21
Adding to what cariboo907 said, have you tried to reconfigure your packages?

```
sudo dpkg --configure -a && sudo apt-get update && sudo apt-get upgrade
```

---

### Post by satya61229 on 2009-07-21
> **cariboo907 said:**
> It is definitely not a virus, in one image you a power manager icon and no network manager icon, and in the other you have a network manager icon and no power manager icon. I would suggest you probably have a misconfigured theme.

Hi cariboo907

For my mis-configured theme, what to do?

---

### Post by satya61229 on 2009-07-21
> **grayn0de said:**
> Adding to what cariboo907 said, have you tried to reconfigure your packages?

```
sudo dpkg --configure -a && sudo apt-get update && sudo apt-get upgrade
```

Hi

I just run your command thinking here at ubuntu everything is secure. :D
but it seems only a simple update. I update my system regularly whenever a update message comes.

---

### Post by grayn0de on 2009-07-21
> **satya61229 said:**
> Hi

I just run your command thinking here at ubuntu everything is secure. :D
but it seems only a simple update. I update my system regularly whenever a update message comes.

Right. That just made sure your packages were configured properly and you were all updated. Sometimes the simple things fix odd problems. :)

Have you tried simply changing the theme to something else and changing it back, again?

---

### Post by cariboo on 2009-07-21
Moved to General Help, where you will probably get more help.

---

### Post by satya61229 on 2009-07-21
> **grayn0de said:**
> Right. That just made sure your packages were configured properly and you were all updated. Sometimes the simple things fix odd problems. :)

Have you tried simply changing the theme to something else and changing it back, again?

Ok. i will try. Next time when the same problem come then I will try with theme. 
Currently I am happy to know that this is not related to security. Thanks

---

