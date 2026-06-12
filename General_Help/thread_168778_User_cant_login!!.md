---
title: "User cant login!!"
date: 2006-05-01
forum: General Help
---

### Post by Prasad007 on 2006-05-01
im now posting from windows
i messed up my linux user
i changed some path which was /home/prasad
my username was prasad
i changed that to /root
cuz the root user had that
how can i change it back?
i cant login now!
please help me asap.
thank you! :)

---

### Post by Zorro on 2006-05-01
Use the live cd and get to a shell that way... (mount the drive where /home resides)

Other than that I'm not 100% sure...

---

### Post by Prasad007 on 2006-05-01
oh!
so im gonna have to get the live cd...
id rather just format...

---

### Post by Ramses de Norre on 2006-05-01
In recovery mode: ```
usermod -d /home/prasad prasad
init 6
```
No need for live cd ;)

---

### Post by Prasad007 on 2006-05-01
how do i get in recovery mode ?

---

### Post by Ramses de Norre on 2006-05-01
In grub choose the line with your kernel and (recovery mode) at the end, it will boot up and give you a root shell in which you need to execute those commands.

---

### Post by Prasad007 on 2006-05-01
okay ill give it a shot.
thanks!

---

### Post by d_whitekiss@yahoo.com on 2006-05-01
[QUOTE=Ramses de Norre]In recovery mode: ```
usermod -d /home/prasad prasad
init 6
```
No need for live cd ;)[/QUOTE]


Hi All,

I cannot to thru the root user. In my installation, I was not asked for root user password. How can I access the root?

---

### Post by Ramses de Norre on 2006-05-01
[Sudo]("https://wiki.ubuntu.com/RootSudo") makes this possible, read the link ;)

---

### Post by Prasad007 on 2006-05-02
it worked . thank you :)

ps. i formatted anyway...
cuz some idiot told me a command which i didnt know the meaning of. and it screwed up my linux and booting :P

---

