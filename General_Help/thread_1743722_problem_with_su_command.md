---
title: "problem with su command"
date: 2011-04-29
forum: General Help
---

### Post by digitalboy on 2011-04-29
Hi,

I've just downloaded and installed Ubuntu 11.04
Now I'm trying to install an application.
Well, I bought hidemyass VPN and I'm trying to install it.
For that they wanted me to install openvpn and curl.
I did that.
Now, the problem is with the su command - that's what I think.

Well, below is the message I'm getting in terminal :-

root@gordy-ThinkPad-R60:/home/gordy/Desktop/hma# dir
client.cfg hma-start keys README.txt
root@gordy-ThinkPad-R60:/home/gordy/Desktop/hma# sudo ./hma-start -l
sudo: ./hma-start: command not found
root@gordy-ThinkPad-R60:/home/gordy/Desktop/hma# ./hma-start -l
bash: ./hma-start: Permission denied
root@gordy-ThinkPad-R60:/home/gordy/Desktop/hma# 


Well, I thought it would be the super user problem with Ubuntu - so I have enabled root access. And tried with the root account also. When trying with root account I need not use su rite?- so tried it without that (as shown in the above terminal message) and I'm getting permission denied message.


I don't know what I'm doing wrong.

If anybody knows solution to this, please help me out.


Thanks

---

### Post by sisco311 on 2011-04-29
Hi,

You have to make ./hma-start executable:
```
chmod +x ./hma-start
sudo ./hma-start
```

If the file is not owned by your user, then you have to run the chmod command as root (**sudo chmod ...**).

---

### Post by digitalboy on 2011-04-29
> **sisco311 said:**
> Hi,

You have to make ./hma-start executable:
```
chmod +x ./hma-start
sudo ./hma-start
```

If the file is not owned by your user, then you have to run the chmod command as root (**sudo chmod ...**).

Fantabulous !!!!
That worked !!

Thanks a lot mate.

---

### Post by sisco311 on 2011-04-29
You're welcome!

---

### Post by wh1zz0 on 2011-07-13
> **sisco311 said:**
> You're welcome!

Worked for me too.. Thanks!

---

### Post by sisco311 on 2011-07-13
> **wh1zz0 said:**
> Worked for me too.. Thanks!

No problem.

---

