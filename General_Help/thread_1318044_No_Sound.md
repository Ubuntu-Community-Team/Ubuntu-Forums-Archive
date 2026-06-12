---
title: "No Sound"
date: 2009-11-07
forum: General Help
---

### Post by claudiuh on 2009-11-07
Hello! 

I installed ubuntu on my computer and everything works fine. In the sound settings I selected the 5.1 sound. So far so good. The problem is when I go to the seven ... The sound does not work ... Any suggestions?

---

### Post by Defrector on 2009-11-07
To get the ball rolling...

What is your sound device? If you don't know specifically, bring up a terminal and enter the following command:
```
lspci
```

...and paste the result of that command in your reply. What will print out is a list of (almost) all of your devices as detected by ubuntu. This will help people figure out if your issue is a config issue, a driver issue, etc.

Note if you are using speaker outputs, line outputs, an optical output, or whatever I haven't mentioned.

Is it safe to assume you are using the plain old vanilla ubuntu and not any of the special versions like Kubuntu, Xubuntu, Ubuntu studio, etc?

---

### Post by claudiuh on 2009-11-07
My sound device is Audigy SE from creative. 
Yes i am using ubuntu.

---

