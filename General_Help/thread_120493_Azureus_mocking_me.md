---
title: "Azureus mocking me"
date: 2006-01-21
forum: General Help
---

### Post by panza on 2006-01-21
Hi all. 

I've just installed azureus, and set up port forwarding on 6881. 

I download a torrent, it connects ok to the tracker. I get the green happy face. I get 200 seeds and 200 peers, but not one of them actually connects.

The NAT test *sometimes* says OK, other times it fails (how can NAT only sometimes work?). For good measure, I uninstalled the bittorrent client that comes with the default installation, but still no joy.

Any ideas? It's doing my head in.

---

### Post by steve.horsley on 2006-01-22
I can't think what your problem might be. I think it unlikely that you can't connect to anything. Can you confirm that the torrent Details page lists no connections at all, and that the console command **netstat -pant** doesn't show any connections?

Not that I would have any idea what to do if you really can't connect.

---

### Post by PaganHippie on 2006-01-22
Try right-clicking on the file you're trying to acquire & changing its status to 'forced download.'  IME, that can help you to connect to at least 1 seeder & get the ball rolling, so to speak.  Once the download is going along well, you can usually uncheck 'forced' and let the download proceed normally.

---

### Post by spockrock on 2006-01-22
some trackers block port 6881 and the other std bit torrent ports because isps block or throttle the speeds from them, try a high number port like 40000

---

### Post by phantez on 2006-03-14
Hello,

I have exactly the same problem it works on windows but not on ubuntu, i m on the port 40004 and i have the last sun-1.5re, my router is ok on windows on the same port and with other software it works but not with azureus and i don t understand why. The sofware run i see the green smile the others people connect to the tracker but it doesn t download.

Thank you

---

### Post by skymt on 2006-03-14
It might be that Azureus isn't using the right Java. Try "ls -l /etc/alternatives/java". It should point to "/usr/lib/j2re1.5-sun/bin/java". If it points to something else (the default, non-sun, java is "/usr/lib/jvm/java-gcj/bin/java"), do "sudo update-alternatives --config java" and pick the right one.

---

### Post by deathbyswiftwind on 2006-03-14
skymt is right i had this very same problem until someone told me to point to the new sun java and now it works slick as shit

---

### Post by phantez on 2006-03-15
ok thant you very much it works well now ! ;-)

---

### Post by miasimpleman on 2006-03-15
me too! i just installed jre update 6 and azureus works like a charm :) 

ps: firefox seems to have speeded up quite a bit too since i installed update 6.

---

### Post by djlosch on 2006-03-17
i had the same problem....
port was open, nat tested fine, but i kept getting connection exception errors and such.

switched the java symlink and all is well.  thanks

---

### Post by deathbyswiftwind on 2006-03-17
You also may want to change your port. Azureus recommends to choose any port between 49152 - 65535. Its as stated in a reply about how some isps restrict ports between 6880 and 6889.

---

