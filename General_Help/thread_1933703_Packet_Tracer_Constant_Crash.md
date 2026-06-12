---
title: "Packet Tracer Constant Crash"
date: 2012-02-29
forum: General Help
---

### Post by timburkard on 2012-02-29
Hello for the first time!

I have installed Cisco Packet Tracer 5.3.1 on my 11.10 laptop.  The font thing drove me a little crazy, but that has been solved with the updated libQt4-gui, -dev, -Qt3support, and -webkit and remarking the old lib line in the packettracer file. 

Packet tracer opens like a champ!  Add a router, cool.  Modify the router, cool.  Add a switch, cool.  connect them, cool.  delete an object -- segmentation fault!  Open it again, do it over, save the file -- segmentation fault!  Help Please.  I don't know enough to even be dangerous on this one.

Thanks in advance.

T

---

### Post by imachavel on 2012-02-29
You know what I hate about packet tracer?? That I can't delete a router or switch or hub or serve or pc or laptop once configured. It really doesn't work well with wine in Ubuntu, it's just prone to crash. The only thing I think is good about it that you can practing using ip addresses and subnets and default gateways. Otherwise I think it's garbage. Lol. It's great if you want to pass that CCNA exam and need to practice finding cidrs or whatever.

To answer our question it'll crash in Linux one way or the other. Wine just doesnt like it. I'm trying to remove mine. Dude, you want a real thrill? get a few thousand dollars, build a server with quad sockets, buy one of those 20 port Cisco routers or whatever, install Linux host on server, install a 6 drive raid array with maybe raid 1+0, now bench mark it, try installing 15 vms, each with vdi virtual hard drive or vmdk, see how many vm situations you can connect with the router, which I believe needs a config t privilege log in and then from there I'm not sure how the command line works with that router, I don't know the shell commands, or what the shell is. Now you can set the clock rate, get all those special cables that are slightly more advanced then standard straight through Ethernet (o, wo, b, wg, g, wg, b, wb) or something? Well, that only matters if both ends are different and in that case what I listed would be A category side for cross over. For straight through I think as long as both ends match it doesn't matter.

Now this won't teach you what packet tracer will, how to manage thousands of ip addresses, learning different cidrs and subnet masks needed for all the hosts. What That won't teach you, is anything other then how to address a network, which is almost always done automatically anyway, is it useful? Yes, but it won't teach you how to capture an image of an OS and transfer it through a large network. It won't teach you how to deploy install OS from a server to thousands of computers. How to remove a virus found in a dns server farm and look on thousands of different servers file systems for it. It won't teach you how to manage a name server. It won't explain how to install a back end apache server, how to create an index.html page, create a domain URL address, put it in /var/www/local host, keep other needed files in the folder such as images, videos, other HTML files, manage the .net framework directories.

I suppose opening ports goes along with that Cisco stuff, and ssh and rdp and what not. And now the most important part, the social people skills. Wouldn't it be nice if every person was able to manage thousands of dns servers in a server Internet farm? Reality check, very rare. Building pcs and installing OS and fixing windows for people, that it where it's at, web design. Because the customer is never wrong, and they will change their mind a million times. Good luck with packet tracer

---

### Post by yataketumbe on 2012-03-14
@timburkard
I have similar situation as yours.  But instead of segmentation faults, the application(packet tracer) just exists whenever I delete some objects.  I still couldn't find solution to making packet tracer work.

@imachavel
Thanks for the reply and suggestion.  But I just wanted packet tracer to work.  It's saves me money and easy to learn.

I'm using it to teach basic ccna level networking to friends and colleagues on Windows, But I'm loving Ubuntu right now. It's now my main OS.

BTW, I'm running packet tracer as a native app(installed from a deb file) and not within wine.

I hope someone will share a solution on this.

Thanks.

---

### Post by supergroove1979 on 2012-03-16
my problem with packet tracer is that when i build a topology, and it's not even that big, it strat to slow down my computer, and it's impossible to work on it, but when i tried it on windows, same pt version, same topology it runs smooth.do any of you guys have this problem? i don't know what to do with it.

---

