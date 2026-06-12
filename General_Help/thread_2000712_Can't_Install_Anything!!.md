---
title: "Can't Install Anything!?!"
date: 2012-06-10
forum: General Help
---

### Post by sattmullivan on 2012-06-10
I just got Ubuntu today, and I haven't been off to a good start. My wireless wan't working, but i came on the forums and someone fixed my problem pretty quick, so i am hoping to have the same luck with my new problem...Which is I can't install anything

I tried installing an app I found on the ubuntu software center but it didn't work, so i thought i had to get some updates since i had 261 updates available!! So when i tried installing those updates, same problem... everyone i try to install gives this message:

Package Operation Failed

installArchives() failed: (Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%%dpkg: unrecoverable fatal error, aborting: 
 reading files list for package 'humanity-icon-theme': Input/output error 
Error in function:  


So if anyone knows what i can do pleeeeaase help. I just started ubuntu and keep hitting roadblocks  :-?

---

### Post by codemaniac on 2012-06-10
Open up a terminal by alt+ctrl+T and fire the below command .

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by drpjkurian on 2012-06-10
It seems your package is beyond recovery. So I suggest you to reinstall using a CD

---

### Post by codemaniac on 2012-06-10
you can try regenerating your sources.list from the belo0w link .

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by sattmullivan on 2012-06-10
I tried typing in that code, it didn't do anything after I entered it in the terminal, and when I tried to install something I got the same error as before

---

### Post by sattmullivan on 2012-06-10
and i clicked that link, but i dont know what i am supposed to do there...guess i will try reinstalling the os....

---

### Post by codemaniac on 2012-06-10
> **sattmullivan said:**
> I tried typing in that code, it didn't do anything after I entered it in the terminal, and when I tried to install something I got the same error as before

You supposed to get some verbose output from the above commandline ,
that would fetch metadata information of available packages in the repository .

Have you tried regenerating your sources.list file by using the above link .

Sources.list file contains all the repository informations , and repositories host the package you want to install in your ubuntu system .

---

### Post by sattmullivan on 2012-06-10
I re installed from the same disk i originally installed from and it seems to work. who knows what happened...

---

