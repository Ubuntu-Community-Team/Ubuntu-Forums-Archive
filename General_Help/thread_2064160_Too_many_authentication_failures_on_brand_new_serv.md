---
title: "Too many authentication failures on brand new server"
date: 2012-09-28
forum: General Help
---

### Post by Xplorer4x4 on 2012-09-28
I have a brand new ubuntu server. When I try to log in for the first time ever I get "Too many authentication failures for root." My friend tried to ssh in and got in fine I logged in to my old server, and sshed in from there. That also works, so something has to be wrong with my ssh, but I have no idea what.

---

### Post by josephmills on 2012-09-28
You can set your server up so that you do Not need a password and so that only people with the correct ssh keys can get in. 

Here is a video that I made 

Changing ssh Ports 
[http://www.youtube.com/watch?v=3YzCxBkx6GQ](http://www.youtube.com/watch?v=3YzCxBkx6GQ)

Adding ssh keys and loging in with out a password 

[http://www.youtube.com/watch?v=xRLzCHkfW8A](http://www.youtube.com/watch?v=xRLzCHkfW8A)



Hope that this helps.

but as far as to many auth tries that is also in the files /etc/ssh/sshd_config or is it /etc/shh/ssh_config

there is a line that lets you set the number of auth tries

---

### Post by Xplorer4x4 on 2012-09-28
Hey josephmills, thanks but first off I don;t even get a password prompt. Just ask to verify the fingerprint, and I do. As soon as it is added to known_hosts, I get the error. I am aware of using keys, but that doesnt explain why this error occurs on my machine(kubuntu) but not when I ssh in from another server or if another person tries to ssh in.

---

### Post by josephmills on 2012-09-28
> **Xplorer4x4 said:**
> Hey josephmills, thanks but first off I don;t even get a password prompt. Just ask to verify the fingerprint, and I do. As soon as it is added to known_hosts, I get the error. I am aware of using keys, but that doesnt explain why this error occurs on my machine(kubuntu) but not when I ssh in from another server or if another person tries to ssh in.

Can you ssh into anything on the affected box (kubuntu)?


**EDIT**

Could you also paste the output of 
```
 cat /etc/ssh/ssh_config 
```

---

### Post by Xplorer4x4 on 2012-09-28
Yes as I said in the OP, I can ssh in but I have to ssh in to my old box from the same hosting provider and then ssh in from that box. Also my friend can log in no problems as well. So I am wondering if ssh on my Kubuntu machine is broken. I don;t see how since I can log in to other servers(using keys) just fine.

---

### Post by josephmills on 2012-09-28
> **Xplorer4x4 said:**
> Yes as I said in the OP, I can ssh in but I have to ssh in to my old box from the same hosting provider and then ssh in from that box. Also my friend can log in no problems as well. So I am wondering if ssh on my Kubuntu machine is broken. I don;t see how since I can log in to other servers(using keys) just fine.

Yeah this all sounds kinda funny I would re-install ssh on both machines

---

### Post by Xplorer4x4 on 2012-09-28
For what it is worth, I had the problem with the new server, so I formatted it and reinstalled Ubuntu and it still persisted after a format. I will hold out for other input since I gotta leave now but thanks for the responses.

---

### Post by Xplorer4x4 on 2012-09-28
> **josephmills said:**
> Yeah this all sounds kinda funny I would re-install ssh on both machines

I purged ssh on my desktop and then reinstalled. Still get this same problem, even logging in as a different user.

Got it, I had not told the config file to use keyfiles for specific domains so it was trying to use the keys instead of password.

---

