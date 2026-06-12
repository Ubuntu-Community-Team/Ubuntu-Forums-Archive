---
title: "April 26 Precise Pangolin"
date: 2012-04-22
forum: General Help
---

### Post by xworld on 2012-04-22
Hello. I was just curious as to how the update works. I have the Beta 2 right now and I was wondering what happens when the final release comes out. I'm hoping I don't have to reinstall. Can anyone clear this up for me?  Thanks

---

### Post by Hylas de Niall on 2012-04-22
As long as you've been getting the updates you'll be fine.

---

### Post by xworld on 2012-04-22
Actually I haven't noticed any updates. How do I know

---

### Post by 3rdalbum on 2012-04-22
This question has been asked a lot recently (as it is around the release time of any new Ubuntu) - did you try the forum's search function, or Google?

The answer to your question is Yes. The beta becomes the final release. You just need to run Update Manager, click the Check button, and then the "Install Updates" button. When you do this the day of the final release, it will install the remaining packages to bring your beta system up-to-date with the final release.

This is the same for every release of Ubuntu. If you install any snapshot of Ubuntu 12.10, 13.04 etc it can be updated to the final release in exactly the same way.

---

### Post by PaulW2U on 2012-04-22
An alpha, beta or release candidate is only a snapshot of the installation .iso on the day it is released. As soon as you update your system don't really have the alpha, beta or release candidate any longer. About a week before the release date you will see very few updates. 

The command **lsb_release -a** produces this output:

```
paul@R720:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04 LTS
Release:        12.04
Codename:       precise

```If the word **development** is not displayed in the output then you are running what is probably going to be the the final release with just a few updates to apply.

---

### Post by xworld on 2012-04-22
Thanks to all for your responses. When I ran the command lsb_release I get this ```
No LSB modules are available.
``` So I guess that means I'm good. Thanks

---

### Post by Mike_tn on 2012-04-26
thanks for the info, I installed a week ago. today is release day. woot!

---

