---
title: "Initial Message after upgrade &quot;No required driver detected for Unity&quot;"
date: 2010-10-12
forum: General Help
---

### Post by kraus3742 on 2010-10-12
Hello all,

I have a Dell Mini 10 and after upgrading from version 10.04 to 10.10 I received a message on boot: "No required driver detected for Unity".  From what I have been able to find this is a 3D graphic support issue.  

The temporary workaround that I found was to switch to either the Ubuntu Desktop interface or the Ubuntu Netbook 2D interface.  Oddly to me it appeared that in 10.04 I had 3D support.  

Any help would be appreciated!  Thanks!

---

### Post by pedalwrench on 2010-10-12
You may want to look at this bug:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/614088]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/614088")

basically if your machine can't do 3D the netbook interface will fail and go into 2D mode.  You may have to manually install the 3D drivers for your video card (nvidia, or ATI)

---

### Post by persapiens on 2010-10-12
Hi kraus,

    I have dell mini 10 and i had the same problem too after upgrade to 10.10.

    So, I've installed intel gma 500 following the instructions at [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

    My netbook is faster with graphics now, the option "Ubuntu Netbook inteface" log in, but does not work property :(

---

### Post by kraus3742 on 2010-10-12
Hi persapiens, 

Thanks for the reply and I too experienced the same results with the link you provided.  One step closer to the solution!

---

