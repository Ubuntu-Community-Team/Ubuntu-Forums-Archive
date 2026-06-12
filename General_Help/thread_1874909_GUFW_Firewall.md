---
title: "GUFW Firewall"
date: 2011-11-04
forum: General Help
---

### Post by crutch145 on 2011-11-04
I would like to block all outgoing traffic, and create custom rules that allow me to use trusted programs.  For example, I would like obvious things to be allowed out, e.g. Google Chrome, Firefox, Update Manager, etc.  How can I do this?  Right now my firewall is setup to allow all outgoing traffic.  That just makes me nervous.  Is there a reason I shouldn't be nervous?  

Thanks,

Justin

---

### Post by Dangertux on 2011-11-04
Yes, you should use strong outbound firewall rules as well as inbound rules so your concern is well placed.

This : [https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

Should help you with configuring your firewall properly.

Hope that helps.

---

### Post by lovinglinux on 2011-11-04
I wouldn't be nervous. Blocking outgoing connections is something common on Windows due to a wide range of applications phoning home, including virus installers. Not much of a concern on an OS which gets is software from trusted repositories,  doesn't have virus in the wild and has a much more strict policy on who can install software on your system.

Besides, if you have a router, then most likely you don't even need a firewall to block incoming connections as well.

I recommend reading [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Dangertux on 2011-11-04
> **lovinglinux said:**
> I wouldn't be nervous. Blocking outgoing connections is something common on Windows due to a wide range of applications phoning home, including virus installers. Not much of a concern on an OS which gets is software from trusted repositories,  doesn't have virus in the wild and has a much more strict policy on who can install software on your system.

Besides, if you have a router, then most likely you don't even need a firewall to block incoming connections as well.

I recommend reading [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)


With all due respect most of what is said here is based in opinion not best practices.

"Phoning Home" otherwise known as a reverse connection is pretty much commonplace for bypassing firewalls (routers included). 

Software in trusted repositories can be exploited to achieve remote code execution (Wireshark, VLC and Xserver all come to mind as recent examples)

Not having viruses in the wild...well...that's debatable. 

Strict policies on software installation do not prevent a user from visiting a malicious website or loading a malicious media file. 

I suggest reading this thread I took the time to create.

[http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)

You will also note the firewalling information in the link you provided advocates the same strategy.

---

### Post by crutch145 on 2011-11-04
Thank you for this information.  I think where I am having a hard time is the I set my outbound to Deny, and then added rules to allow... But no matter what I allowed, my Google Chrome and Firefox could not connect to the web... So I had to change the default back to Allow.  Whst would bd the specific rule to allow Chrome snd Firefox outbound access?  Is there a reference page where I can find this type of info?

---

### Post by Dangertux on 2011-11-04
You need to make sure you allow port 53 UDP and TCP outbound as well, otherwise the browser will not be able to do DNS lookups , thus no web sites.

---

### Post by Dangertux on 2011-11-04
> **Dangertux said:**
> You need to make sure you allow port 53 UDP and TCP outbound as well, otherwise the browser will not be able to do DNS lookups , thus no web sites.

For web browsing you need the following outbound ports allowed

80 TCP
443 TCP
53 TCP & UDP

GAH!!! I didn't mean to double post that...lol

---

### Post by linmick on 2012-09-13
Thank You almost double posted and they need to add this to the tutorials. I wanted to block all both ways except allow some out both ways. Deny all caused the browser not to work even after adding the exceptions to http and https.


> **Dangertux said:**
> You need to make sure you allow port 53 UDP and TCP outbound as well, otherwise the browser will not be able to do DNS lookups , thus no web sites.

> **Dangertux said:**
> For web browsing you need the following outbound ports allowed

80 TCP
443 TCP
53 TCP & UDP

GAH!!! I didn't mean to double post that...lol

---

