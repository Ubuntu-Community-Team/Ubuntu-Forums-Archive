---
title: "Server Setup Tutorials?"
date: 2011-12-16
forum: General Help
---

### Post by adamantasaurus on 2011-12-16
Hello Everyone,

I am very new to ubuntu (my 4th day using it I know I'm a noob) and the reason why I am using it is solely to setup a server to host my website on. 

I was wondering if anyone on here could point me to some tutorials that can help me. 

Thanks All

Joey

---

### Post by lisati on 2011-12-16
Apache is one of the tools you can use to host a web site.

Similar thread: [http://ubuntuforums.org/showthread.php?t=1892706](http://ubuntuforums.org/showthread.php?t=1892706)
Wiki: [https://help.ubuntu.com/11.10/serverguide/C/httpd.html](https://help.ubuntu.com/11.10/serverguide/C/httpd.html)

---

### Post by adamantasaurus on 2011-12-16
Which version would you suggest I use 11.10 or 10.04?

---

### Post by worksofcraft on 2011-12-16
I recommend you get the whole apache, mysql and php package bundle.

For Linux distros it is called "lamp". I'm afraid I set mine up on windows, so I used the bundle named "wamp" but I suspect you will get good info here: [http://www.lamphowto.com/](http://www.lamphowto.com/)

In my case I was very happy I decided to use a very stable windows XP rather than the latest windows 7 and I suspect you will not regret it if you choose the dependable LTS 10.04 of Ubuntu ;)

---

### Post by garyed on 2011-12-16
If you haven't already installed Apache Server then you can do it all in one simple command:

```
sudo apt-get install lamp-server^
```
The carat on the end of the command needs to be there too.
After the server is up & running a good site to check out is 
portforward.com

---

### Post by adamantasaurus on 2011-12-16
> **worksofcraft said:**
> I recommend you get the whole apache, mysql and php package bundle.

For Linux distros it is called "lamp". I'm afraid I set mine up on windows, so I used the bundle named "wamp" but I suspect you will get good info here: [http://www.lamphowto.com/](http://www.lamphowto.com/)

In my case I was very happy I decided to use a very stable windows XP rather than the latest windows 7 and I suspect you will not regret it if you choose the dependable LTS 10.04 of Ubuntu ;)

Thank You

I was wondering about the LAMP Server in the Ubuntu Installation it gives me the option to install 
OpenSSH Server
DNS Server
LAMP Server
Mail Server

Should I choose just the LAMP server or the open SSH


,....

And if I want to be able to setup my own mail server do I need to check off the mail server installation?

---

### Post by adamantasaurus on 2011-12-16
Thanks, But can you look at my above post about the mail server lamp server open ssh server etc. and let me know also? thanks

---

### Post by worksofcraft on 2011-12-17
TBH I just set up the basic wamp (so you probably want lamp). I very much believe you can add other things when you find you really need them. AFIK mail servers are a security nightmare :(

---

### Post by Dangertux on 2011-12-17
> **worksofcraft said:**
> TBH I just set up the basic wamp (so you probably want lamp). I very much believe you can add other things when you find you really need them. AFIK mail servers are a security nightmare :(

They can be, but are a necessary evil for many applications.

---

