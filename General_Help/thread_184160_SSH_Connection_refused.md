---
title: "SSH: Connection refused"
date: 2006-05-29
forum: General Help
---

### Post by Deus- on 2006-05-29
SSH: Connection refused
That is what is says when trying to connect from school etc...(it is not the exact message but the context is there)

I am using router, which I suppose is the heart of this problem. I am able to SSH to my computer from my computer. (weirdly said? well I think you got it ;) ) According to nmap the ssh port 22 is open. Ask for any information, I'll try to give them
Why I think it is the router because I have had this problem before and got it solved and because my apache server is working when checking it from my computer but not when trying to see it from school...
Thanks for help in advance:cool: 
Hope this gets solved again:???:

---

### Post by the_tiger on 2006-05-29
To see if you port is correctly open to the internet why not try, [http://www.canyouseeme.org/](http://www.canyouseeme.org/) .

Also make sure you are using the correct IP. It seems obvious but its surprising how many people use the IP of their desktop and not the IP of their ISP connection. Also make sure you router forwards the packets to the correct PC to allow ssh login.

---

### Post by Deus- on 2006-05-29
Hm... canyouseeme.org said:
Success, my ip can be seen and port 22 is not blocked by ISP

How can I decide what IP to use? o_O
How to separate the IPs?

And finally... I am not sure how to get to known if the router is letting them through and how to
forward them. I've just been reading about it on forums but never got 'in touch' ;)

---

### Post by the_tiger on 2006-05-29
The IP assigned to you by your ISP should be visible in the router setup or possibly any literature sent to you by your ISP. Alternatively it may be give to you by [www.canyouseemr.org](www.canyouseemr.org) . The problem you may experience is if your ISP periodically changes your IP address in which case you will have to keep checking. When accessing your computers from outside your network, this is the IP you will have to use.

Using virtual server in the router setup you can forward the port to the IP of your particular machine. This IP may be found using ifconfig.

---

### Post by Deus- on 2006-05-29
Yes, my IP is a changing one...

---

### Post by Deus- on 2006-05-29
Yes, my IP is a changing one...

[QUOTE=the_tiger]Using virtual server in the router setup[/QUOTE]
How exactly?

Also:
If I connect from my computer to school and there back to my computer,
the connection is successful...I don't know why. Is that way of connecting the same thing
as I was concretely at the school connecting to my computer?

---

### Post by harisund on 2006-05-29
Ok let's go through this step by step just to be sure. 

First, ensure that the SSH server is indeed running. And make sure it is listening on port 22. You can do this by executing ```
sudo netstat -plant | grep LISTEN
``` This would give you a list of ports your machine is listening on. 

Second, find out your computer's IP locally. This is established by executing ```
ifconfig | grep Bcast
```This will give you a line having the IP  address of your machine, the Broadcast IP and the mask. Typically your ip will look something like 192.168.<something>.<something>, with a broadcast of 192.168.0.255 and a mask of 255.255.255.0. Note down the ip address (192.168.<something>.<something>).

Now go to your router settings page. What router do you have? I am assuming you know how to access the router settings page through 192.168.0.1 perhaps? Look for these options ->
1. Static IP. If you can figure this out, set your desktop to always get a static IP of 192.168.<something>.<something>. Basically what this means is even though your computer thinks it gets a random IP from the router (called the DHCP server) the router actually gives it 192.168.<something>.<something> everytime (for convenience let's assume it is 192.168.0.5). Get it? 
2. Port Forward. Port forward 22, public port 22, private port 22, IP 192.168.0.5 (or 192.168.<something>.<something>). What this does is ensures that every time you connect to the router on port 22, it should go to your desktop machine. And this is also why it would be better to give your desktop a static IP as we did in step 1, so that port 22 can always be forwarded to this machine. 

Next, figure out what your *actual* ip address is. Go to [http://whatismyip.com](http://whatismyip.com) and find that out. 

Now, you are all set. Go to school and SSH to whatever your ip address is (the result of [http://whatismyip.com)](http://whatismyip.com)). 

The trick is in understanding external and internal IP addresses, or to be more technical lan and wan. Your router has 2 ip addresses, the 192.168.0.1 that is accessible from within the lan and the big number (the result of [http://whatismyip.com](http://whatismyip.com)) that is 'external' wan

---

### Post by Deus- on 2006-05-30
I made it like this:
Went into Windows, changed the network card IP to the one they give it in the [www.telewell.fi](www.telewell.fi) 
(my router branch's site),(I'm too bad linux user to be able to change it in linux :( ) 

Accessed the router settings page

I am not actually sure if I did it right but I set the static IP and the virtual server configurations
to forward the port. I took the IP from the DOS application ipconfig's Local Area Connections tab.

Then I happily get the hell out of Windows and wait for next school day to test the connection there. (You know any way to test this thing without going away from own computer?)

Ok..I test it at school and I can see that SSH still does not work but this time Apache server works. 
I remember that I had resetted my router to default settings before changing the settings.
What's up now?

---

### Post by Deus- on 2006-05-30
Oh my god, I must say...Suddenly I could connect to my computer outside of its network.
Now I must just thank you for all your help!
Perhaps now on I can solve this easier when the next time comes :D  :D  :D

---

