---
title: "Proxy support for various applications"
date: 2010-09-24
forum: General Help
---

### Post by harsh1kumar on 2010-09-24
There are some of applications that ship with ubuntu that do not have proxy support. I am a university student and I need to access internet behind a proxy server. But as some of the applications have no proxy support, I have to install alternate applications to do the same job.

Some of these applications are : Ubuntu Software Center, Gwibber, Empathy.

Is there any program which can create direct connection to internet so that there is no need to specify proxy settings explicitly for each application? Is this kind of thing possible? Any kind of help will be greatly appriciated.

---

### Post by andrewthomas on 2010-09-24
Check this out:

[http://ubuntuforums.org/showpost.php?p=9884641&postcount=4](http://ubuntuforums.org/showpost.php?p=9884641&postcount=4)

---

### Post by efflandt on 2010-09-25
Have you configured System > Preferences > Network Proxy?  That is a general proxy setting instead of setting it for specific applications.

---

### Post by harsh1kumar on 2010-09-25
> **efflandt said:**
> Have you configured System > Preferences > Network Proxy?  That is a general proxy setting instead of setting it for specific applications.

Yes, I have configured proxy for gnome global settings. And it is working for some applications like weather updates near the clock, but the apps that I mentioned before still do not read gnome proxy settings.

---

### Post by andrewthomas on 2010-09-27
Have you tried editing  **[FONT=monospace][/FONT]/etc/bash.bashrc [B]?** 
[/B]

---

### Post by harsh1kumar on 2010-09-27
> **andrewthomas said:**
> Have you tried editing  **[FONT=monospace][/FONT]/etc/bash.bashrc [B]?** 
[/B]

Yup, I have tried that. 

After searching for sometime, I found out that the problem is not with specifying the proxy server. All these applications know my proxy server and port number. The problem is with authentication. Some how these applications are not able to get the proxy authentication information (username and password). I have specified username and password in configuration files like /etc/bash.bashrc & ~/.bashrc

---

