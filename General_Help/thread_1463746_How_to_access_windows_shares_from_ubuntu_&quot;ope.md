---
title: "How to access windows shares from ubuntu &quot;open file browser&quot;?"
date: 2010-04-27
forum: General Help
---

### Post by rameshvel on 2010-04-27
Hi,
   I have successfully mounted windows shares in to ubuntu and can able to access the folders from nautilus. But  i wanted to open the mounted share folders from the "open file browser(select a file dialog)" in DeVeDe app. 

I have tried all the options, and nothing worked out. Am ubuntu newbie. can someone help me out?

Cheers
Ramesh Vel

---

### Post by steviefordi on 2010-04-27
Ok when you mount through nautilus you actually mount to a folder in your home directory called .gvfs. If you cannot get to the share any other way type:

```
/home/USERNAME/.gvfs/
```

into the 'file open' dialogue for your application and press <ENTER> - replacing USERNAME with your username. You should now see the server part of the share name. Double click that and you should see the share itself.

---

### Post by rameshvel on 2010-04-27
thanks[ steviefordi]("http://ubuntuforums.org/member.php?u=636740")
              You saved my day...

Cheers

---

