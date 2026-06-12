---
title: "Trouble Installing Java in Ubuntu 9.10"
date: 2010-02-10
forum: General Help
---

### Post by Cunnilingus on 2010-02-10
I can't seem to be able to get Java working on my computer which is running Ubuntu 9.10 and firefox 3.6. I have followed instructions to download Java and when I restart firefox there is no Java plugin and it does not appear to be installed.

---

### Post by patchwork on 2010-02-10
Which java packages did you install?   I think the one you are looking for is 
```
sun-java6-plugin
```

---

### Post by Cunnilingus on 2010-02-10
"sun-java6-plugin is already the newest version."

---

### Post by Cunnilingus on 2010-02-10
I tried these and they didn't work:
```
sudo aptitude install sun-java6-jre sun-java6-plugin
```
```
sudo apt-get install sun-java6-jre sun-java6-plugin  sun-java6-fonts
```

---

### Post by patchwork on 2010-02-10
Did you check your preferences in firefox to make sure java was enabled there? 
 If so, perhaps this will help

On my system, I have installed:

sun-java6-plugin
sun-java6-bin
ubuntu-restricted-extras

I'm not exactly sure if any of these (or a combination) are what you need, but it is working on mine with no trouble.

---

### Post by Cunnilingus on 2010-02-10
I can't even find an option to enable Java in my preferences. Where would it be?

---

### Post by patchwork on 2010-02-10
I'm using FF 3.57, so it may be slightly different (but this has been pretty common to FF as long as I can remember)  

Edit > Preferences > Content > Enable Java

---

### Post by Cunnilingus on 2010-02-10
"sun-java6-plugin is already the newest version."
"sun-java6-bin is already the newest version."
"ubuntu-restricted-extras is already the newest version."

I just checked and Java is enabled.

---

### Post by patchwork on 2010-02-10
Are you using the NoScript add-on (or another javascript blocker) for Firefox?

I'm not really sure where to go from here, maybe someone else in the community can jump in and give a hand...

---

### Post by Cunnilingus on 2010-02-10
I'm not using the NoScript add-on. Oh well, thanks for your help.

---

### Post by waj1122 on 2010-02-10
The old java in the repositories will not work with FF-3.6. You'll need to install the newest. Here's a link with instructions on how to do this and it works like a charm.

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by Cunnilingus on 2010-02-10
That tutorial was excellent. Thanks!

---

