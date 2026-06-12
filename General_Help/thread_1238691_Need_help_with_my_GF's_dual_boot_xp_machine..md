---
title: "Need help with my GF's dual boot xp machine."
date: 2009-08-12
forum: General Help
---

### Post by philinux on 2009-08-12
Ubuntu works just fine.

But on XP it will connect to Internet with explorer or FF but all other stuff like windows, avg or spybot wont update. Internet connection problem of sorts.

I bloody hate windows but GF's kids need this pc working properly.

Any help appreciated.

---

### Post by Crafty Kisses on 2009-08-12
Hey there Phil!, 

Now I've done a little research for you. I think I may have a solution for the AVG problem, and this solution might even fix the Spybot problem. Now this is just upon research, someone suggested you go to **windows/system32/drivers/etc/host** and in the file add the followng entry:
```
64.74.243.12 guru.avg.com # 64.74.243.12
```
Someone also suggested their ISP was blocking the updates so they changed DNS servers. The person said these are the servers they used:
```
Primary DNS 208.67.222.222
Secondary DNS 208.67.220.220
```
So I'm not sure this will help you out at all, but here is the link to the actual thread, a lot of stuff you have to dig through to get the actual answer, but I dug those up for you, but if you want the whole thread here is the **[thread]("http://www.computing.net/answers/security/avg-free-80-wont-update/22998.html")**. I just thought these links might help you.

---

### Post by philinux on 2009-08-13
Cheers I'd seen that for AVG but there's no app to open that host file I think. Double clicking it brings up the full app list.

I would appear that only a browser works either IE or FF. These two can connect to internet ok but it seems that nothing else can.

For instance spybot fails to install because it cant get updated.
Windows update fails.
etc etc

---

### Post by martinbaselier on 2009-08-13
Maybe there are some services turned off? 

This site is helpful for that:
[http://www.blackviper.com](http://www.blackviper.com)

XP troubleshooting is pretty much hell. You might find more help though on a windows forum?

---

### Post by philinux on 2009-08-13
Cheers for that link. I'll try enabling all with msconfig and if that dont work then I'll try uninstalling SP3 if it's installed.

---

### Post by P4man on 2009-08-13
you can edit the host file just with notepad. Its just a text file.

But it sounds more like some restrictive firewall is blocking everything except port 80 or every app except the browsers. Is there a software firewall installed other than the built-in one from XP ? (the XP one doesnt block outgoing requests, so it cant be the cause).

---

### Post by philinux on 2009-08-13
Cheers I'll try that.

The router is doing the firewall at the minute I've turned the windows firewall off. Nothing in the systray to show another firewall, but thats what it feels like. 

I was getting some weired google misdirects too. I'd search for avg not updating and then clicking a link opened a new tab but with an odd search engine with more links. That has now gone after using stinger to delete some trojan or worm. 

This pc has three teenage kids using it. :rolleyes:
They all got their own user but i had to give one of em admin rights as I'm not always there to install stuff for em.

---

### Post by P4man on 2009-08-13
maybe should install kubuntu on the machine and tell them its the new version of windows :)

---

### Post by philinux on 2009-08-13
> **P4man said:**
> maybe should install kubuntu on the machine and tell them its the new version of windows :)

I nearly did yesterday when i was pulling my hair out.

---

### Post by philinux on 2009-08-13
I reckon it's a virus.
[http://www.google.co.uk/search?q=windows+and+avg+wont+update&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.co.uk/search?q=windows+and+avg+wont+update&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)
[http://en.kioskea.net/forum/affich-43800-avg-windows-update-failure#p51370](http://en.kioskea.net/forum/affich-43800-avg-windows-update-failure#p51370)

---

### Post by philinux on 2009-08-15
Still no joy. Even uninstalled sp3. Nothing can update.

---

