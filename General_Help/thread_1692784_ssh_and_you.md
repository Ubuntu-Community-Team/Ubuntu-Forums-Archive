---
title: "ssh and you?"
date: 2011-02-21
forum: General Help
---

### Post by Mallachar on 2011-02-21
Right now I just installed open ssh because i was told its a great thing to have for remote controlling my machine if I am at work on my windows system. My question is, how on earth do I acess my machine from my windows machine now that its installed? i did sudo apt-get ssh and thats about all so far...

---

### Post by coffee412 on 2011-02-21
Putty is the choice I guess for that.

I use it now and again for a windows machine.

---

### Post by tjwoosta on 2011-02-21
Start here
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

Make sure to follow the links under the resources section, its important stuff.

That will get your server setup.

As for connecting to it from your windows machine I agree about putty

---

### Post by Mallachar on 2011-02-22
Thanks a lot for the help guys, got it set up, and I can now connect to it from my work machine. Thanks!

---

### Post by seawolf167 on 2011-02-22
I don't know if this is still an issue, but DNS lookup for SSH used to make authentication take a very long time, if you notice a delay and don't need DNS, edit the config file and add this line:

```
gedit /etc/ssh/sshd_config
```

add the line

```
UseDNS no
```

at the bottom of the file, save & exit, the restart ssh

```
sudo service sshd restart
```

---

### Post by HermanAB on 2011-02-22
Use Cygwin if you want to run Linux graphical programs remotely from Windows.

---

