---
title: "how to install   ksh???"
date: 2010-04-06
forum: General Help
---

### Post by pczafer on 2010-04-06
i used apt-get install ksh command but it didnt work.
I edited the sourcefile as well. i have lots of sources but says
W: couldn`t stat source package list [http://.](http://.)........

I am behind a proxy but i can access to internet.

is there any other files need to be edited????

---

### Post by gmargo on 2010-04-06
Make sure you have the universe repository enabled.
And don't forget to do an "apt-get update".

[http://packages.ubuntu.com/karmic/ksh](http://packages.ubuntu.com/karmic/ksh)
[http://packages.ubuntu.com/karmic/mksh](http://packages.ubuntu.com/karmic/mksh)
[http://packages.ubuntu.com/karmic/pdksh](http://packages.ubuntu.com/karmic/pdksh)

---

### Post by pczafer on 2010-04-07
its not working for me???

How can install without internet connection?????

I have cds but 'apt-get install' not finding anything from cds???

---

### Post by wojox on 2010-04-07
What does your sources.list look like:

```
cat /etc/apt/sources.list
```

---

### Post by gmargo on 2010-04-08
> **pczafer said:**
> i used apt-get install ksh command but it didnt work.
I edited the sourcefile as well. i have lots of sources but says
W: couldn`t stat source package list [http://.](http://.)........

I am behind a proxy but i can access to internet.

> How can install without internet connection?????If you need a proxy to access the internet, you need special settings to get **apt-get** and **synaptic** to work.  See this post: [http://ubuntuforums.org/showpost.php?p=9010252&postcount=10](http://ubuntuforums.org/showpost.php?p=9010252&postcount=10)

---

### Post by pczafer on 2010-04-09
> **gmargo said:**
> If you need a proxy to access the internet, you need special settings to get **apt-get** and **synaptic** to work.  See this post: [http://ubuntuforums.org/showpost.php?p=9010252&postcount=10](http://ubuntuforums.org/showpost.php?p=9010252&postcount=10)

This is only Manual proxy configuration.

Is there any way to set this up to Automatic Proxy Configuration URL??????????

---

