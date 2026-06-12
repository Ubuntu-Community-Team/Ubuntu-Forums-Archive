---
title: "help! java will not stop running at 100% CPU"
date: 2012-08-16
forum: General Help
---

### Post by LLCoolJeff on 2012-08-16
Here what hapenned:

1. I installed ThinkorSwim Tdameritrade

2. It was running like crap, slow, was trying to optimize for performance from inside the program when it went unresponsive. Could not close from any method tried

3. went to terminal > top > java was running at or close to 100% CPU, and I could not kill it from within top, it said "operation not permitted" I also could not find the application process anywhere because I didn't know the proper place to look. 

4. I then decided it was best to logout and hopefully it would end everything when I logged back in. but when I logged back in java was still running...

How do I get it to stop? AND
how do I find the thinkorswim process? (I tried some common stuff I found on google, but none of them returned anything that had to do with thinkTDA)

---

### Post by SlugSlug on 2012-08-16
you can just 

```
sudo pkill java
```


but if you want to look a little deeper use

```
ps -ef
```

---

### Post by LLCoolJeff on 2012-08-16
> **SlugSlug said:**
> you can just 

```
sudo pkill java
```
but if you want to look a little deeper use

```
ps -ef
```

that did not work, it is still running after I did that. It did not give me any error code though..

---

### Post by SlugSlug on 2012-08-16
sudo pkill -9 java

is java in CAPS? in top??

sudo pkill -9 JAVA

---

### Post by LLCoolJeff on 2012-08-16
> **SlugSlug said:**
> sudo pkill -9 java

is java in CAPS? in top??

sudo pkill -9 JAVA

java was not in caps, although I had already just done a reboot, and it took care of everything. I hope that was an ok solution as well although not preferable. 

I think I somehow have JDK6 and JDK7 installed at the same time. Is this normal? should I remove both of them completely and then reinstall JDK7 to get everything cleaned up?

EDIT: it ended up happening again when I tried to get it to work normally and your solution did work like i thought it would. Thanks.

---

