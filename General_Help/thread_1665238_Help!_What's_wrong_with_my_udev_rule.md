---
title: "Help! What's wrong with my udev rule?"
date: 2011-01-12
forum: General Help
---

### Post by extraordinary_boy08 on 2011-01-12
I'm having a problem in implementing my udev rule. What I want is whenever I inserted a usb device, a script will be executed. 
This is the udevrule that I've made:
```
ACTION=="add", SUBSYSTEM=="usb", RUN+="home/jcjo/info.sh"
```

I've placed it in /etc/udev/rules.d just like what I see in different tutorials. 

When I tried to insert any usb device, the script wasn't working. I already tested and executed the script it in the terminal and it worked.

PS. Also, I'm not sure if the udevrule is right. Kindly check it for errors.

My version of ubuntu is 9.10.

Thank you very much.

---

