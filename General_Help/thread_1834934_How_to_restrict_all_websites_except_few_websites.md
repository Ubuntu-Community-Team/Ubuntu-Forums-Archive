---
title: "How to restrict all websites except few websites"
date: 2011-08-28
forum: General Help
---

### Post by seekay on 2011-08-28
Hi All, 

I want to restrict websites my kids can access. I want to restrict all websites except few websites. 

For example, I do not want them to access any site other than [www.pbs.org]("http://www.pbs.org")

As I am a novice user of ubuntu\linux, clear instructions are highly appreciated. 

Thanks in advance, 
See Kay

---

### Post by sanderd17 on 2011-08-28
You could try this, but I wonder if it's still maintained. So maybe it will not work.

[http://linuxpoison.blogspot.com/2011/01/parental-control-system-on-ubuntu-linux.html](http://linuxpoison.blogspot.com/2011/01/parental-control-system-on-ubuntu-linux.html)

---

### Post by ktmom on 2011-08-28
In my case, my computer is on when the kids have there's on, so my set-up has their internet connection go through my machine and I use Firestarter (a open-source firewall) to define what sites they can visit.  It can be set-up as permissive and then you define the IP addresses you don't want them to visit, or set it as restrictive and allow the sites.  This works if they are sharing you computer as well, and then you can turn off Firestarter if you want full access for yourself.

Another alternative is to use [OpenDNS]("http://www.opendns.com/home").  

[QUOTE=OpenDNS website]OpenDNS is the only service that lets you control the websites that are accessible on all Internet-connected devices in your home, from laptop and desktop computers to gaming consoles and mobile phones. Open lines of communication with your kids by telling them why sites are blocked on the customizable block page.[/QUOTE]

---

### Post by Sef on 2011-08-28
> ...I use Firestarter (a open-source firewall)....

Firestarter is not recommended anymore since it is no longer maintained. Instead use either ufw which is installed by default or download gufw which is available from the repositories.

---

### Post by galvatron408 on 2011-08-28
For a simple requirement like that, I would just configure it on the router or modem or whatever device it is that you use to connect to the internet.

No separate software to download/install/configure and best of all, your ISP may even help you set it up if you are using their equipment.

Other simple options include, remove the DNS entry out of /etc/resolve.conf, don't use DHCP and resolve pbs.org via /etc/hosts. ahhh, that way, even if your kids typed [www.unsafe.site](www.unsafe.site) your computer would just come back and say that it couldn't find it. haha

So anyway, there are a lot more ways to do what you wanted. I personally would keep it simple.

---

