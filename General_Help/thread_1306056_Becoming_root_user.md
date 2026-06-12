---
title: "Becoming root user"
date: 2009-10-30
forum: General Help
---

### Post by stef25 on 2009-10-30
I'm unable to create a directory in /var/www/. This is my localhost where I want to run a few sites. When I try do this from Apatana I have the same problem. It seems I don't have the rights.

How can I permanently be root user with all permissions? This is my own laptop, taking it abroad where there's no internet so security should be almost a non issue by me being root user.

Thanks,
Stef

---

### Post by pawhtiobo on 2009-10-30
Hi :)

I advice you to not be a always "**root**", if you make a mistake in some kind of instalation or configuration....you know the results....

Just use the "s**udo nautilus**" command and create the folders you want, delete the files, etc.. :)

See ya...

---

### Post by snowpine on 2009-10-30
Hi Stef, use the 'sudo' (terminal) or 'gksu' (GUI apps) prefix to execute a command/application with root priviledges. For example, 'gksu nautilus' will launch a file manager with root priviledges. 

There is no "root user" in Ubuntu by default; it is one of the differences between Ubuntu and other Linux distributions.

---

### Post by P4man on 2009-10-30
No need to become root permanently, and trust me, if you dont know how to solve this, you really dont want to run as root. I strongly recommend you read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

As for your problem, you can either configure apache/php whatever to use a different folder than /var/www/ (pick one in your home folder so you will have all permissions) or you can change the permissions on /var/www/

Open a file browser with root privildges:
```
gksudo nautilus
```

Browse to that folder and change the permissions for your user(group).

---

### Post by stef25 on 2009-10-30
sudo nautilus works - thanks!

---

### Post by shaon3343 on 2009-10-30
thaks everyone!!! I was searching this kind of post!! :)

---

### Post by P4man on 2009-10-30
> **stef25 said:**
> sudo nautilus works - thanks!

please dont use it. Use ```
**gksudo** nautilus
```
sudo is for terminal applications and (ab)using it to launch graphical apps like nautilus can in the worst case render your system unbootable.

---

### Post by sisco311 on 2009-10-30
> **stef25 said:**
> I'm unable to create a directory in /var/www/. This is my localhost where I want to run a few sites. When I try do this from Apatana I have the same problem. It seems I don't have the rights.

 Thanks,
Stef

Change the DocumentRoot to a directory owned by your user:
[https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts](https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts)

---

