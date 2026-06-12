---
title: "Network bug or am i going crazy?"
date: 2011-04-17
forum: General Help
---

### Post by sale666 on 2011-04-17
Hello ok here is my whole story and the deal about it.. iv been trying to set this up for months but it just isn't working!

Here is my connection: Router that i connect to wireless with a linux machine that acts as another router because its in another house and i connect to the linux "router" with cable in short description

PC--->Linux "router" with outdoor wlan antena---->Far away router

thats about it... why am i doing this well i also have a switch connected to the lan of the linux machine and an ap to it so it routes all here and uses that wireless connection for interent hope that makes sense!...
ok now to the problem...

my router default adress is 192.168.1.1
on ubuntu i set this: Wlan on manual , ip i set 192.168.1.2, subnet 255.255.255.0 , default gateway 192.168.1.1.

done works! yeey ok lets go forward

on lan i set ip 192.168.1.3  , subnet 255.255.255.0 , default gateway 192.168.1.1.

done works! yeeey ok lets go forward

ok now my linux machine is set up i connect my windows machine that has my call of duty 6 installed :D haha hook up the cable and ok i want to host a match but hey nobody can connect? why? ok port forward i go on router portforward all to 192.168.1.2 all needed ports really easy and simple, do firewall config easy and simple again... ok i go to cmd write in ipconfig and MY LAN IS 10.42.43.18???? WTF I SET MY CONNECTION DIFFERENT ABOVE??
ok let me check linux in terminal! ifconfig 10.42.43.18!!!! WTF? is ubuntu ignoring what im typing? hmm well scroll down lets check wlan 192.168.1.248!!!! I SET THAT TO 192.168.1.2 REMEMBER?? UBUNTU WTF??? can some 1 tell me wtf is going on? why is this happening?

Thanks!
Regards 
Sasha

EDIT:
Added a video of the problem please check it out!

[http://www.youtube.com/watch?v=0Z5hH7RNaBE](http://www.youtube.com/watch?v=0Z5hH7RNaBE)

---

### Post by sale666 on 2011-04-18
bump? ubuntu ignoring me? :P

---

### Post by dcstar on 2011-04-18
> **sale666 said:**
> bump? ubuntu ignoring me? :P

[LIST=1]
[*]Networking issues belong in the Networking forum;
[*]Try writing your problem in something understandable, like English.
[/LIST]

---

### Post by sale666 on 2011-04-18
> **dcstar said:**
> [LIST=1]
[*]Networking issues belong in the Networking forum;
[*]Try writing your problem in something understandable, like English.
[/LIST]

it is in english.... what is so hard to understand ubuntu is ignoring my commands! why are you so hostile? :D i thought ppl help here lol

---

### Post by deathadder on 2011-04-18
> **sale666 said:**
> it is in english.... what is so hard to understand ubuntu is ignoring my commands! why are you so hostile? :D i thought ppl help here lol
It sounds like English isn't your first language, it's pretty difficult to read you post. 

It sounds like your two(??) hosts are still setup to use DHCP (they've both got 10.42.43.*) and are getting those addresses from a DHCP server somewhere. Can you confirm you've turned DHCP off on the hosts and router. Then try and describe the problem again without all of the "wtf's" etc, it doesn't help when trying to read your problem.

---

### Post by sale666 on 2011-04-18
well yea english is not my first language :P.. my bad sorry but im sooo mad about this and iv been trying this for 2 months!

Well ok here is the head the main router has DHCP on is it possible to stay on? because i want when i get there with my notebook some 1 wants to connect i want it to give him an ip but keep the static to my linux pc!

and yea two hosts one is the router transmiting to my linux server and linux giving interent to every one in this house! hope this makes more sense now :)

as for 10.42.43.* i do not know where is it coming from? and on my linux i chose manual configuration and so did i on windows so that should all be dhcp off! 

I think i should make a video about it it would be a lot easyer to explain!

---

### Post by antaios256 on 2011-04-18
also it sounds like your last connection is pc to linux pc via cable ensure that you are using a crossover cable for like-devices as not all NIC cards are MDIX capable

---

### Post by Shwick2 on 2011-04-18
It seems like this is what you have:
windows machine(dhcp client) -> (dhcp server)linux machine(dhcp client) -> (dhcp server)far away router(internet)

This is what you want
windows machine(dhcp client) -> linux machine(dhcp client) -> (dhcp server)far away router(internet)

This is what I understand: you're trying to use the "far away" router as your dhcp server via wireless and you want the linux machine to be an ethernet switch for your local lan.  You also want to connect to your linux machine with your windows machine and host call of duty.

You're linux machine and windows machine are both clients of the far away router so don't give them static ips.

Configure the linux machine's Wlan interface and windows machine to be dhcp clients so that they each can acquire an ip from the far away router automatically.  For windows it will be something like setting your network interface to "acquire ip automatically".  Ubuntu is configured to do this by default.

First allow the linux machine to acquire an ip, then the windows machine.

The far away router will remember and reserve the ips it assigns to your linux machine and windows machine so that probably no one else can have them.

Then set the port fowarding rules on the far away router for the ip acquired the by windows machine.

This assumes that your wired ethernet interface on your linux machine is set up to be a SWITCH and forward ip traffic, not a dhcp server.  Which in fact it may not be based on the ips you are getting, as 192.168.1.248 is a completely different subnet than 10.42.43.18.

Another solution could be to just create two port forwarding rules, one on the far away router to the linux machine, and one on the linux machine to the windows machine.

---

### Post by sale666 on 2011-04-20
shwich2 thank you that is the far best explanation that i had yet! well seems i got many things messed up and not sure how to configure the linux machine to allow certain ports! this networking is confusing but yes that how im setup! quite messy a? :D haha

please tell me ... you said windows machine(dhcp)->linux(dhcp) yes that is what i want! that means lan has to be static ip right? on linux? what should i set up and how? im confused i have tryed everything and allways ended up with what i did not want :(

---

### Post by sale666 on 2011-04-23
Bump added video [http://www.youtube.com/watch?v=0Z5hH7RNaBE](http://www.youtube.com/watch?v=0Z5hH7RNaBE)

---

