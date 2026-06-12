---
title: "Sending files over internet public ftp or apache?"
date: 2006-06-19
forum: General Help
---

### Post by CameronCalver on 2006-06-19
Hello at work i would like to create a share folder so if some1 goes to a conferanceor something then can just type the address in and download the files i am not sure how to do public ftp from the places  menu or apache

---

### Post by scxtt on 2006-06-19
if you have apache setup (and it's not to hard to do), all you have to do is put the file in /var/www/ (or however you set up apache's "root" directory) and supply the link to the person (via your IP address):

put this in a html file:
```
<a href="/path/to/file">text for link</a>
```
or if the file is, for example, my_file.zip:
```
http://xxx.xxx.xxx.xxx/my_file.zip
```

---

### Post by CameronCalver on 2006-06-19
umm i dont get it what do i need 
```
<a href="/path/to/file">text for link</a>
``` for and how do i find out my ip and if the file is is /var/www/share/blahblah.zip how do i put that on the  apache

---

### Post by CameronCalver on 2006-06-19
i acceses it by [http://192.168.1.130](http://192.168.1.130) 

but anyway i cant access it on any other computer exept for mine

---

### Post by scxtt on 2006-06-19
192.168.1.130 is your local IP, on your own network ... you'll need to find out the IP address of your modem (try typing 192.168.1.1 into a browser and logging in to your router) ... and you'll have to forward port 80 to your local IP ... it might sound confusing if you haven't done it before, but it makes sense once you see it ...

---

### Post by Ramses de Norre on 2006-06-19
If the file is /var/www/share/blahblah.zip then you'll need to make a file /var/www/index.html and put ```
<a href="/share/blahblah.zip">whatever you want</a>
``` in it, when you browse your site you'll see a link called "whatever you want".

Find out your IP [here]("http://www.ipchicken.com/").

And you should look at your router for port forwarding or virtual server or something and forward port 80 to your local ip.

(if there are more machines behind the router you might want to forward another port and configure apache to use that one.)

---

### Post by CameronCalver on 2006-06-20
ok my ip is  203.158.43.28
 and look at the screen shot

---

### Post by CameronCalver on 2006-06-20
umm now i cant login to my router it says could no find server

for some reason if i change that setting i change that setting i can no longer log on to 192.168.1.1

---

### Post by bforbes on 2006-06-20
Can you ping your router?

---

### Post by CameronCalver on 2006-06-20
yes it is right now i can log into it but if i change the remote management i will not be able to log into the router and i will have to reset it

---

### Post by Simian on 2006-06-20
I know what i'm going to suggest is a bit boring when you just want to get on with things but if you google for a basic apache tutorial you can learn a lot in a short space of time. A couple of months ago I didn't know a thing about apache. I soon grasped the basics in a very quickly. A lot of the questions you are asking are the same questions that I was asking not long ago.

---

### Post by CameronCalver on 2006-06-20
yeah but i dont think the problem is to do with apache when i change the web ip (look at the screen shot) after that i cant login to my router why would it do that

---

### Post by bforbes on 2006-06-20
Why are you messing around with remote management? That's only for when you want access to the router settings from the WAN side of the router. What you want is to set up a forwarding rule so that all port 80 traffic from the WAN is routed through to your machine on your LAN. Is there a section in the router settings about firewalls or service forwarding?

---

### Post by CameronCalver on 2006-06-20
look at screen shot

---

### Post by Ramses de Norre on 2006-06-20
What's in the NAT section?

---

### Post by CameronCalver on 2006-06-20
as you might of guesses i like screenshots

that is a screenshot of the nat section

---

### Post by CameronCalver on 2006-06-20
and under sua it has this (look at screenshot)

---

### Post by Simian on 2006-06-20
It's not easy to guessing how to use your routers options. But I can say that on many routers you need to set up a rule that say all trafic on port 80 is forwarded to your local IP (in your case 192.168.1.130). Then any body that enters your **external** ip address will be directed to whatever is in your   /var/www  directory.

on my router (netgear) those rules can be set under Firewall in my routers menu.

---

### Post by CameronCalver on 2006-06-20
so when i set it up what is the start port and end port then when i type in the ip how do i access it from a browser

---

### Post by Ramses de Norre on 2006-06-20
I think the easiest way is to search for the router's manual.. Most routers are different on how they call certain things and in which menus they are and so on.. I don't really know what to type in on your screenshot, mine works different..

---

### Post by bforbes on 2006-06-20
Can you screenshot the LAN and WAN sections?

---

### Post by Simian on 2006-06-20
[QUOTE=CameronCalver]so when i set it up what is the start port and end port[/QUOTE]


Sorry but setting your router really does depend on the router itself. I used to have an old Linksys router that was a nightmere to set up port forwarding. Now I'm using a modern Netgear router and it couldn't be easier. You click creat firewall rule and enter a few details.


[QUOTE=CameronCalver] then when i type in the ip how do i access it from a browser[/QUOTE]

When your router and apache are set up correctly, you simply type your ip into a browser and what ever is in /var/www will be displayed in your browser.

Normally you would have an index.html or index.php file there. Apache would serve that you the browser as a web page. If you just have any old files in /vaw/www then they will be listed by apache on the browser

(my understanding of apache is very limited, a more experienced  user might be able to give you better advice)

---

### Post by scxtt on 2006-06-20
you should be able to just set the "start port" and "end port" both to 80 and be fine ... a lot of routers allow you to forward a range, since some programs use multiple ports (torrent clients, for example) ... so fill it out as i have in the attachment, then after you've added a "index.html" file in your root apache directory, you'll be able to see it by typing 192.168.1.130 into your browser and outsiders can type 203.158.43.28 and see it ...

---

### Post by CameronCalver on 2006-06-21
ok that is the wan pg 1 and wan pg 2 and lan section and when i change the setting in the nat sectiopn now when i type in [http://203.158.43.28](http://203.158.43.28) it comes up my router config like i am typing in 192.168.1.1

---

### Post by bforbes on 2006-06-22
You probably get the router config page because you're accessing it from within the network. When I try to access your IP, it says page not found. I can't see anything in your router config that looks like port forwarding. It could be that your router is old or not so good. If you really need this functionality it may be worth buying a good Netgear or D-Link router.

---

### Post by scxtt on 2006-06-22
you shouldn't really be able to type your router's IP address into a browser from a computer on your network [ it's not impossible, it used to work for me until the router was reset and PROPERLY configured - this was before i really started messing w/ routers ] ...

you should edit the page that is located [here](http://www.ubuntuforums.org/attachment.php?attachmentid=11543&d=1150852444) and not have to mess w/ anything in those last 3 pages your supplied screenshots from ...

and don't use your router's IP address from w/in your network, have a friend somewhere else do it ...

---

### Post by CameronCalver on 2006-06-22
ok well i am actually doing it for my dad and at his work he has a netgear one of the white oneswith green lights so can you give me some screen shot on how to do it on that router

---

### Post by scxtt on 2006-06-22
that is one crazy sentence - how about some periods, somewhere :p ...

i can't get screenshots for a router i don't own ...

---

### Post by CameronCalver on 2006-06-22
can some1 get screenshot of how to set up port forwarding.
For the netgear router.The white one

---

### Post by bforbes on 2006-06-22
You'll have to be more specific. There's probably many white routers with green lights. Get a model number, then we can find a manual on the web.

---

### Post by Simian on 2006-06-22
[QUOTE=CameronCalver]ok well i am actually doing it for my dad and at his work he has a netgear one of the white oneswith green lights so can you give me some screen shot on how to do it on that router[/QUOTE]

I have white netgear router with green flashing lights on the top of it (That i turned of because it looks rediculous). There is a chance that yours and mine have similar setup screens. When I go home I will try to remember to post a screen shot of its port 80 forwarding thingy. If I forget then mail me.

---

### Post by CameronCalver on 2006-06-22
ok ill find out and give the model number to u as soon as possible

---

### Post by Simian on 2006-06-22
[QUOTE=CameronCalver]ok ill find out and give the model number to u as soon as possible[/QUOTE]

OK, the second image shows the simple setup of port forwarding on a Netgear DG384PN.

Select "Firewall Rules" from the menu on the left.

Choose the port that you want to forward    "HTTP (TCP:80)"
Set action to: "Always Allow"
Then enter the local ip address of your box, normally 192.168.somthing.something (you can find out by entering ifconfig at the command line) I think that you said 192.168.1.130 before.
Finally set Wan users to: "Any"


[IMG]http://benward.dyndns.org/images/router1.png[/IMG] [IMG]http://benward.dyndns.org/images/router2.png[/IMG]
sorry these images are a bit large, I couldn't be bothered to edit them :)
The second image shows what the firewall rule will like like once it has been applied.

---

