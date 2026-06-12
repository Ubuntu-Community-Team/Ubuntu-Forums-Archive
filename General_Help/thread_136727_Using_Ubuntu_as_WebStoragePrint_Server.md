---
title: "Using Ubuntu as Web/Storage/Print Server"
date: 2006-02-26
forum: General Help
---

### Post by apu95 on 2006-02-26
I 've recently gotten access to an old machine that my family isn't using anymore. Here's the specs:

384mb RAM PC100
AMD K6-2 450mhz
ATI Radeon 32mb SDR
40gb WD drive (not sure of the rpm)
8gb Samsung (not sure of the rpm)
HP cd burner
Epson Stylus CX5400 All in one Printer

I wanna turn it into a small web server/storage/print server (I do realize that 40gb isn't much for storage, but I'll replace the 8 gig drive for a beefier one soon enough). But I'm not sure if the system will be able to handle Ubuntu  since its not that strong.

D'you guys think I could get it to run successfully and well? Or would it be more recommended to take another lighter distro instead? I figured I could always install Ubuntu and just strip everything except the very essential things, leaving only Apache and CUPS and whatnot. 

Something to note: The load on the system wouldn't be very high though, the webserver would be used very minimally and it'd be more for storage (mp3s in particular) and loading music from any other computer on the network.

Thanks in advance,
Apu

---

### Post by simon_is_learning on 2006-02-26
Alot slower machines has been used as webservers.

> 
D'you guys think I could get it to run successfully and well? Or would it be more recommended to take another lighter distro instead? I figured I could always install Ubuntu and just strip everything except the very essential things, leaving only Apache and CUPS and whatnot. 


instead you do a base-server install. And then add apache. 


Go for it.

---

### Post by apu95 on 2006-02-26
Base-server? Nice :D
I'll add Apache after installing and report back if I get any problems. Thx a lot :)

---

### Post by poctob on 2006-02-26
If you want a fast server you will need to learn how to do text based configuration.  Graphical desktops like Gnome of KDE will run on your hardware but you'll see some serious wait times for many applications to open.  But if will choose base system server install after initial configuration in text mode you won't need to do much more to keep your system going.  If you are new to linux I would still go with graphical interface to save you some frustration in a trade of slow performance.  A compromise would be low end GUI like IceWM.  But also remember slow graphical perfomance doesn't necessary mean that you server will be slow.

---

### Post by Gimbo on 2006-02-26
Well, as far as I know, what you need computing power (especially RAM) for is fancy graphical effects. If you're running a server, that isn't going to be a problem.

---

### Post by apu95 on 2006-02-26
Yeah, what I'm planning to do is do it via GUI first (I've been using Ubuntu for a while though) and then switch down to a very simple GUI so people can still use it for scanning (since the printer is all in one)

---

### Post by jamesr on 2006-02-26
MY intranet archival fileserver etc was 
 2x Pentium PRO 200MHz with 128Mb running NT4.0 
2GB scsi sda1 software only
10GB scsci sda2 Common Storeage seen by all the Network
40GB IDE local storeage
120GB IDE on a maxtor controller so the system sees it as SCSI
External TAPE drive 4GB 

This system gave me very good service until sda1 failed 
Note I did not use it as fileserver persay, but for common storeage for my home intranet. The 120GB drive was partitioned so that everybody had some additional storage space.

So A long story say yes it should work very well. 

Apache worked well on the system.

---

### Post by davebradford on 2006-02-26
you'll be fine as long and you don't run a user interface! but then thats what webmin if for! You'll be fine as long as your load avarages don't tally up too high.

---

### Post by soulestream on 2006-02-26
I just replaced a PII 400 with 184MB of RAM that has been running as my fileserver, printserver and webserver for a long time with no issues. 

Samba, CUPS, IPP, and apache(or lightpd).

Once Apache is setup you really dont need to touch it. 

Samba is basically the same, but you can enable SWAT, so you can access it from another Machine via your webrowser.

CUPS and IPP can be configrued the same way. Ubuntu doesnt allow cups webmin access by default, but you can find plenty of resources how to use it. Then once again just go to any machine put in [http://serverip:631](http://serverip:631). This will allow you to manage print jobs, add and remove printers, and other basic maintanence. 

As far as scanning, I think Sane allows for remote frontends. So you could even scan from another machine. (not sure on that though), but like you said install fluxbox, blackbox, or openbox and you will be fine. 

Just remember to turn off any services you dont need.

soule

---

### Post by apu95 on 2006-02-26
Thanks for all the replies guys. :D

For Apache, I've been reading some guides and it looks like I won't need to touch it after installing unless I wanna make something customized, which I do. Instead of having to type [http://hostname: port](http://hostname: port), I'd prefer to customize it so its something like [http://www.someName.lan: port](http://www.someName.lan: port) (I'm making it a homepage for everyone on the network to be able to access certain things).

I read about CUPS today in a Linux mag and the webmin looks to be really cool, so I'll be enabling that for sure. As for the services I won't need, I'm not sure which ones I have to disable, so I'll worry about finding a guide for that after I have it up and running (unless someone has a link handy, I'd appreciate it :) )

---

