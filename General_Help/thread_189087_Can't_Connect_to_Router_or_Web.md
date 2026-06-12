---
title: "Can't Connect to Router or Web"
date: 2006-06-04
forum: General Help
---

### Post by conman23456 on 2006-06-04
I recently upgraded to Dapper, and I can't connect to the internet past the first 2-3 minutes i login. It will work if I unplug the ethernet cable, and plug it back it for another 2-3 minutes, but then stops. I also had this problem in OpenSUSE. Everything is fine in Windows though. I have an older system that I run Ubuntu on (6 years) but I dont think that should affect it. Can anyone help? :confused:

---

### Post by link141 on 2006-06-04
It sounds like your router is rejecting the Ubuntu side of your computer.  Do you have a fire-wall, Wepp-key protection, a permitted list of computers allowed on your computer, or the like configured with your router.  Also, did this only happen to Open Suse when you upgraded to Dapper, or did you just install it?  Keep in mind that your router may look at the different OSes as seperate computers (though it souldn't).  I'm not that experienced with Networks, so I may not see something that will appear conspicuous to someone with more knowledge about networks.  If you provide more information about your router, computer and network, it will help to solve the problem faster.  With the help of this forum, you'll get this sorted out in no time :).

---

### Post by conman23456 on 2006-06-11
I have even tried bypassing the router. Same problem

---

### Post by djsroknrol on 2006-06-11
> I recently upgraded to Dapper, and I can't connect to the internet past the first 2-3 minutes i login. It will work if I unplug the ethernet cable, and plug it back it for another 2-3 minutes, but then stops. I also had this problem in OpenSUSE. Everything is fine in Windows though. I have an older system that I run Ubuntu on (6 years) but I dont think that should affect it. Can anyone help?  



Your settings should have stayed the same in the router from OS boots, but there is a timing seting for router uptime and release / renew time in most home units....

You might find your answer in there...

---

### Post by djsroknrol on 2006-06-11
Woah...sorry....missed the part of being separated from the router...

Check eth0 (your interface) in networking to make sure it was installed properly...

we could use a little more info on it...wired, obviously

> I have even tried bypassing the router. 

 what make, model?

what's the lspci output? In terminal, 
```
lspic -v
```

---

