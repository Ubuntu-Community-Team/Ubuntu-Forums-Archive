---
title: "sudo ifconfig eth0 down vs sudo /etc/init.d/networking stop"
date: 2010-06-10
forum: General Help
---

### Post by COKEDUDE on 2010-06-10
Can someone please explain the difference between these two commands. I'm currently reading about changing your mac address and both of these commands show up a lot. They sound like the same thing to me. Is one better than the other, or do you need to use both to change your mac address? 
```
sudo ifconfig eth0 down 
sudo /etc/init.d/networking stop
```

---

### Post by dcstar on 2010-06-10
> **COKEDUDE said:**
> Can someone please explain the difference between these two commands. I'm currently reading about changing your mac address and both of these commands show up a lot. They sound like the same thing to me. Is one better than the other, or do you need to use both to change your mac address? 
```
sudo ifconfig eth0 down 
sudo /etc/init.d/networking stop
```

Do not assume just because **you** only have one network device that other systems are also like that.

---

### Post by efflandt on 2010-06-10
The first command only takes down eth0 (if that is the device you are working with).  The second takes down all networking (other ethernet devices, wireless, etc.).

---

### Post by COKEDUDE on 2010-06-10
> **efflandt said:**
> The first command only takes down eth0 (if that is the device you are working with).  The second takes down all networking (other ethernet devices, wireless, etc.).

Ok that makes sense. Thanks for figuring that out.

---

