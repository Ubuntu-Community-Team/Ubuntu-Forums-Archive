---
title: "How to set domain name in ubuntu?"
date: 2009-10-13
forum: General Help
---

### Post by kalyogi on 2009-10-13
Hi All,

I am new to ubuntu and this fourm as well. If I am asking in a wrong section please forgive me.

I need to set domain name/host name as apps.deyyam.com. Can someone help me to how to do it?

Thanks in advance.

---

### Post by SteveDee on 2009-10-13
Open a terminal window and type at the prompt:-
sudo gedit /etc/hostname

After entering your password when prompted, the text editor will open and you can edit your host name.

---

### Post by kalyogi on 2009-10-13
Is it so simple? I've found the following link for same and its bit complicate.

[http://nixcraft.com/getting-started-tutorials/525-ubuntu-linux-setup-configure-domain-name-server-bind.html](http://nixcraft.com/getting-started-tutorials/525-ubuntu-linux-setup-configure-domain-name-server-bind.html)

Please help me out.

Thanks in advance.

---

### Post by pmains on 2009-10-13
Depends on what you're trying to do. It appears to me that BIND9 is for setting up a domain name server. What SteveDee is suggesting works, but only locally. That is, your /etc/hosts file isn't shared with everyone on your LAN. OTOH, a domain name server could be.

So, modifying /etc/hosts is good, for instance, if you're developing a web application -- and especially if you're developing multiple web applications on the same server. It allows you to direct the right traffic to the right app.

Also, if you just want a convenient alias to be able to SSH, SCP, SFTP, etc. to, then /etc/hosts is also the way to go.

But, I'm guessing you're self hosting and want people to be able to access your website. Am I right? If so, then modifying /etc/hosts is not sufficient.

---

### Post by pmains on 2009-10-13
I had a couple more thoughts on this issue. First, the authoritative guide to BIND 9 appears to be here -- [http://www.bind9.net/manuals]("http://www.bind9.net/manuals"). So, I'd look there.

Secondly, if you're doing what I think you're doing, you are probably going to hit a wall in that your server is behind a router. So, you probably have a local IP address (which may be something like 192.168.1.x) for your computer, and all of the computers on your LAN are going to have the same external IP address.

Okay, so you bought your domain name from someone like godaddy.com, right? It doesn't matter who, but whomever you bought/leased deyyam.com from probably has a DNS server. Now, what you need to do probably has a web interface,  where you tell them the IP address of where you're hosting your site, and they point *their* DNS servers to wherever apps.deyyam.com is currently hosted.

I bought my domain name from one company and have my site hosted by another company, and that's how it went.

I'm sort of fumbling in the dark here, but if your server *is* behind a router, then you may in fact need to configure your router to act as a DNS server, but still have your domain name provider point all deyyam.com requests to your router, which will then grab the data from the particular device you are hostingwhatever.deyyam.com on. I'm not certain that will work, but I think it will.

---

### Post by kalyogi on 2009-10-14
Hi pmains,

Thanks for your detailed explanation. I've leaned a lot from this post.

I am going to use apps.deyyam.com for my local only. So, I will just edit /etc/hosts and give a try.

Thanks again.

---

