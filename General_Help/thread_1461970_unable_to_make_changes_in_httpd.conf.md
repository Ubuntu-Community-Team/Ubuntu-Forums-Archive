---
title: "unable to make changes in httpd.conf"
date: 2010-04-24
forum: General Help
---

### Post by cancer10 on 2010-04-24
Hi

I have installed XAMPP on my ubuntu machine, I typed nautilus in the command line and from there I tried to change the httpd.conf file from  "/opt/lampp/etc" but it does not allow me to change the contents of the file. Error attached with this post.


Please tell me a solution.

---

### Post by Aearenda on 2010-04-25
Your username doesn't have the necessary permission to change that file. You should try typing this to gain admin rights:
```
gksudo gedit /opt/lampp/etc/httpd.conf
```
It should prompt you for your password.

---

### Post by cancer10 on 2010-04-25
Hi

That worked!


Q1. What does gksudo do?

Q2. When I typed "nautilus", should not it give me root permissions to change the file contents?







Thanks

---

### Post by Aearenda on 2010-04-25
Good!

gksudo is used to start graphical apps with full admin rights. The app is run using the 'root' username. Only admin users can do this. 

Just starting nautilus from the command line doesn't change the user context. You could type 'gksudo nautilus' to achieve what you want, but don't - it's too dangerous. One slip of the mouse could hose your system!

---

### Post by cancer10 on 2010-04-25
Thank you for your reply.

<offtopic>

How do you update the kernel of ubuntu?

---

### Post by Aearenda on 2010-04-25
> **cancer10 said:**
> 
<offtopic>
How do you update the kernel of ubuntu?

It depends - what are you wanting to do?

You could start [with this...]("http://ubuntuforums.org/showthread.php?t=311158")

But in general, I'd say, just don't go there...

---

