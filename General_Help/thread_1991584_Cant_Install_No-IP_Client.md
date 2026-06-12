---
title: "Cant Install No-IP Client?"
date: 2012-05-30
forum: General Help
---

### Post by deadlyxxsinn on 2012-05-30
So I tried sudo apt-get install noip2 and replaced it with no-ip and is still not working, here is a link to what I am trying to install. 

[http://www.no-ip.com/downloads.php?page=linux](http://www.no-ip.com/downloads.php?page=linux)

Please help, thanks...

---

### Post by Rodney9 on 2012-05-30
You are correct, neither are in the repositories, if you really need it you will have to download the targz and build it or follow this - [http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html](http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html)

You might wont to explain what you need this for and maybe the 'Networking' forum would be best place to ask for help, there maybe other ways.

Rodney

---

### Post by deadlyxxsinn on 2012-05-31
> **Rodney9 said:**
> You are correct, neither are in the repositories, if you really need it you will have to download the targz and build it or follow this - [http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html](http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html)

You might wont to explain what you need this for and maybe the 'Networking' forum would be best place to ask for help, there maybe other ways.

Rodney

I'll just use a static ip, seems to hard anyways.


thanks anyways.

---

### Post by synapsys on 2012-05-31
Not sure what you're trying to do here, but it sounds like you're trying to map a URL to your external IP. If that's the case, you may have this type of functionality built into your router. Some routers allow you to enter your credentials in and the router takes care of everything else. I have done this with Dyn DNS and it works quite well. Once you have that set up, you can forward the port(s) to the internal IP of your Ubuntu box. 

Also - You will benefit from learning how to install things from source. There are some pieces of software out there in the world that don't come with pre-compiled binaries for Ubuntu. It would be a shame to miss out on all of those just because you don't want to do a little command-line work. This installation IS overly complicated... Most are as easy as:

```
configure
make
make install
```

---

### Post by TipTricky on 2012-12-28
I know this is a really old post but synapsys can you link me to a tutorial on how to do that first part?

---

