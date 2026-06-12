---
title: "Conky issue with Ubuntu 9.10"
date: 2010-02-21
forum: General Help
---

### Post by tenzinmonlam on 2010-02-21
Hi,
I have been using conky for a quite long time and after upgrading to Ubuntu 9.10. Conky seems to acting up.
Conky stretch up and take half the screen space and it will automatically corect it self after few seconds as well. I have been googling up for this issue for quite long time and cant seems to find any solution. This issue is seen on 1 and two desktop running Ubuntu 9.10.  Any suggestions? 

Ps: Screen resolution: 1360*768

[IMG]http://img651.imageshack.us/img651/7103/myconkyissu.png[/IMG]

---

### Post by Brandon Williams on 2010-02-21
You should post your .conkyrc. It's hard to tell you what's wrong without seeing the config. Also, what are the dimensions of your screen and how much of the screen do you want conky to use?

My screen is 1024x600 and I want conky to take up only about 25% of it, so I have the following in my .conkyrc:
```
minimum_size 256
maximum_width 256
```

---

### Post by tenzinmonlam on 2010-02-22
I have posted the Screen resolution and conkyrc file. Plz check and let me know there is any issue with that. Thanks

---

### Post by Brandon Williams on 2010-02-22
I'm not sure whcih of the items in your config is causing the conky display to expand out that wide. It doesn't do that on my system.

If you decide how wide you want the maximum to be, you can easily limit it by setting an appropriate maximum_width value.

---

### Post by tenzinmonlam on 2010-02-23
Thanks for your prompt reply Brandon, i edited the file as per your suggestion and it seems to be working (some times it does not :D ).. I guess i have to live with that...
Thanks ...

---

