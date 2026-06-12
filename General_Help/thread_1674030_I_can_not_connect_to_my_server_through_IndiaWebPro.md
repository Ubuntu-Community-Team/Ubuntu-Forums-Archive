---
title: "I can not connect to my server through IndiaWebProxy in UBUNTU!!"
date: 2011-01-23
forum: General Help
---

### Post by m8r-66g597 on 2011-01-23
Hello friends,

I have got a website that don't let me to connect it with SSH. That is why I uploaded a php file on my server (index.php) and I use to connect to it with [IndiaWebProxy]("http://sourceforge.net/projects/indiawebproxy/") then I could visit some websites like  FaceBook or YouTube that are banned here all in my country!!!

But my problem is that as long as I just moved to UBUNTU 10.10 I couldn't make a connection to that PHP file on my website with this AWESOME Java Application, I mean [IWP]("http://sourceforge.net/projects/indiawebproxy/")!!!

I use to work with it in Windows7 and XP but here in UBUNTU after I press the start button it says that "the port is already in use" (check the screenshot!!!) I think this IWP is working with SSH port and as I turn on my computer and run UBUNTU this port is working!!!

So guys can you help me to work with this application again!?

---

### Post by m8r-66g597 on 2011-01-25
Still no answer?

---

### Post by lme_83 on 2011-02-21
Same problem here...

I´m a newcomer to Ubuntu from XP, and among other things i NEED India Web Proxy.

Something is going on with Ubuntu when IWP tries to start the proxy.
IWP uses port 80 to communicate with the script(PHP) uploaded. 

Help please! Friends take into account that a lot of people out there, due to governements restrictions must rely in stuff like India Web Proxy to surf the web.

---

### Post by Syed75 on 2011-02-21
What Java version do you run??

---

### Post by lme_83 on 2011-02-22
I´m running Java on Ubuntu 10.04 Lucid Lynx. I installed the official java 6 packages from canonical using this method:

```
$ sudo add-apt-repository "deb http://archive.canonical.com/ubuntu lucid partner"
```

```
$ sudo apt-get update
```

```
$ sudo apt-get install sun-java6-fonts sun-java6-jdk sun-java6-plugin
```

thanks in advance...

---

### Post by Syed75 on 2011-02-22
> **lme_83 said:**
> I´m running Java on Ubuntu 10.04 Lucid Lynx. I installed the official java 6 packages from canonical using this method:

```
$ sudo add-apt-repository "deb http://archive.canonical.com/ubuntu lucid partner"
```

```
$ sudo apt-get update
```

```
$ sudo apt-get install sun-java6-fonts sun-java6-jdk sun-java6-plugin
```

thanks in advance...

No what's the package name?
The Java package?

Sun Java Web Start works for me. I had tough luck with JDK
Your Java works right?

---

### Post by lme_83 on 2011-02-23
> **Syed75 said:**
> No what's the package name?
The Java package?

Sun Java Web Start works for me. I had tough luck with JDK
Your Java works right?

Actually i don´t know the packages version. 
But i downloaded them just 5 days ago from the server listed(archive.canonical.com/)
Is there a command to check it from console?

I know there are other packages like OpenJDK, but since my internet connection is very slow i haven´t tried it yet.

By the way i think the JRE  seems to be running ok, because it do execute the java application. The problem comes when it tries to run the virtual proxy.

---

