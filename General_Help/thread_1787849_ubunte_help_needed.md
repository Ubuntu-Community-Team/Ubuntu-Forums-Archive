---
title: "ubunte help needed"
date: 2011-06-21
forum: General Help
---

### Post by canadabear07 on 2011-06-21
i instaled the one to see if u like it than u can install the real thing. but the menue dosent show any wireless networks??

---

### Post by dFlyer on 2011-06-21
can you please post a clear question with a little information on you system. From what I understand from your post there is no wifi? Can you connect hardwired with ubuntu? Can you check if there are driver under restricted hardware to install.

---

### Post by akand074 on 2011-06-21
Probably because you require proprietary drivers to connect to a wireless network. Check additional drivers to see if they exist. You may not be able to install them from the Live CD. But if they exist, you should be good. Do you know what wireless card you have? If not you can post the output of:

```
lspci
```

from a terminal in Ubuntu

---

### Post by haqking on 2011-06-21
> **canadabear07 said:**
> i instaled the one to see if u like it than u can install the real thing. but the menue dosent show any wireless networks??

I am trying to translate what you wrote ? you mean you are running a Live CD and you are getting no wireless ?

---

### Post by canadabear07 on 2011-06-21
ok how do u get the drivers?

---

### Post by canadabear07 on 2011-06-21
yes haqking

---

### Post by akand074 on 2011-06-21
> **canadabear07 said:**
> ok how do u get the drivers?

Which version of Ubuntu are you using? If you are using 11.04 just open the dash (assuming you are using Unity) and search "additional drivers", if you are using 10.10 go to the menu, then System > Administration > Additional Drivers. Again, you might not be able to install them within a Live CD and you **have to be connected to the internet**. So you'll have to plug in a wired connection to find/install the drivers.

---

### Post by haqking on 2011-06-21
> **canadabear07 said:**
> yes haqking

what type of machine ? Wireless  card and chipset ?

it is a good idea when you post driver related or hardware related issues  to post as much information as possible about your machine and software so people can better assess the issue ;-)

---

### Post by dFlyer on 2011-06-21
If your running 11.04 click the icon on the top bar all the way to your right and select System settings than under hardware click additional drivers. You need to be hardwired to the internet for the additional drivers to be install if they are not on the cd.

---

### Post by canadabear07 on 2011-06-21
dell mini 10v and i have a modem/wirless

---

### Post by haqking on 2011-06-21
> **canadabear07 said:**
> dell mini 10v and i have a modem/wirless

not much information there LOL;-)

however on the wiki it seems to be supported.

what version of Ubuntu ?

---

### Post by haqking on 2011-06-21
depending on version of Ubuntu you are using and the chipset this may help for manual install but you will need to hardwire

[http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html](http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html)

---

