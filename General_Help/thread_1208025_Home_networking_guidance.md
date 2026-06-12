---
title: "Home networking guidance"
date: 2009-07-08
forum: General Help
---

### Post by draperdt on 2009-07-08
I need some guidance with my home networking situation.

I share my internet connection with upstairs guys and they want the network "open" and not secured. (long story).

I have the following electronics in "my" place.

- Old Desktop running Ubuntu Hardy and a USB external storage device with 1TB which holds my entertainment and stuff.
- Desktop running the new Mint 7 KDE which is my primary. 
- Laptop running Ubuntu Hardy.
- Netbook running XP home.
- Orginal XBOX with XBMC loaded on it.

I dropped a CAT5e from upstairs, and using a router as a switch, I networked all my wired electronics together. I then "shared" my media folder from Old Desktop and then I connected to it to stream my entertainment onto my TV using XBMC. 

I dont think this is a good setup. Primarily because I am on a open network and anyone can access my shared files. I dont want people to be able to view my files except me.

So, I started researching and I came across some concepts. One of which was using subnet masks to define my own LAN. Another was to password protect files. 

Either option is a little tricky for me since I am a super n00b. I am willing to spend some time and understand it. 

What I was wondering was if some one can give me an overview on how this needs to be done both at the computer level and at say router level. I just dont want to try 8 different things all leading to different results and when I am asking question here, and people are asking me what I did, I would probably cry. 

So, I am hoping some one can just nudge me in the right direction.

**********************************************
Because after this, I want to laern about file systems and how I can mount my external harddrive onto my primary desktop (without violation issues and such) at boot and then be able to use a bittorrent or a usenet client to write files. (I want to achieve this from every computer, as in, even if I am on my laptop or netbook or desktop, I should be able to click a link and initiate transfers and any downloaded files are saved in the external harddrive.) 

Ofcourse, the more I think about the above situation, the more I think its a bad setup, since instead of running Bittorrent clients and Usenet clients on each terminal, I should instead have the torrents/nzb downloaded onto the external harddrive and make my old Desktop monitor that folder and any new files should be downloaded. I had a similar setup with Sabnzbd.

Thanks.

---

### Post by hibliss on 2009-07-08
My suggestion would be to first slap your roomates and tell them network security is not optional. You don't want ust anyone connecting to your network, as you are responsible for what it is used for. Child porn, illegal downloads, etc. You can get in trouble for the actions of others. That is just a friendly warning.

If you want to stream to the Xbox, I recommend FUPPES. There is a good thread on setting it up for the Xbox **[here]("http://ubuntuforums.org/showthread.php?t=984325&highlight=FUPPES+PS3") **.

You can set the address of devices on the network that are allowed to connect to the UPnP server running (FUPPES) in the fuppes.cfg file. It is really very easy. If you need help with that, post back and I will walk you through it.

This will of course require you to set a static IP in your router for the Xbox based on it's MAC address so it always has the same local address that FUPPES can identify with. I can help with that too if you give me the router's model number.

Again though, I strongly recommend securing the network, for a lot of security and safety reasons, another friendly reminder.

---

### Post by CatKiller on 2009-07-08
> **draperdt said:**
> using a router as a switch

Now I'm no networking guru, but this already means that downstairs is a separate network from upstairs. It should be relatively trivial to treat the incoming connection from upstairs as the big, bad Internet and have your wired networked devices downstairs still happy to communicate with each other.

---

### Post by draperdt on 2009-07-08
> **hibliss said:**
> My suggestion would be to first slap your roomates and tell them network security is not optional. You don't want ust anyone connecting to your network, as you are responsible for what it is used for. Child porn, illegal downloads, etc. You can get in trouble for the actions of others. That is just a friendly warning.

If you want to stream to the Xbox, I recommend FUPPES. There is a good thread on setting it up for the Xbox **[here]("http://ubuntuforums.org/showthread.php?t=984325&highlight=FUPPES+PS3") **.

You can set the address of devices on the network that are allowed to connect to the UPnP server running (FUPPES) in the fuppes.cfg file. It is really very easy. If you need help with that, post back and I will walk you through it.

This will of course require you to set a static IP in your router for the Xbox based on it's MAC address so it always has the same local address that FUPPES can identify with. I can help with that too if you give me the router's model number.

Again though, I strongly recommend securing the network, for a lot of security and safety reasons, another friendly reminder.

Hi, I am able to share the files and stream it to xbox using samba. So, that is not an issue. Xbox is seeing the shared files and every other electronic equipment is seeing the files too if browsed to "Network Places -> Samba shares", which would mean that the roommates can see them too. (I am moving end of this month to a new place so I want to avoid unncessary drama with those guys and have them secure the connection. )

> **CatKiller said:**
> Now I'm no networking guru, but this already means that downstairs is a separate network from upstairs. It should be relatively trivial to treat the incoming connection from upstairs as the big, bad Internet and have your wired networked devices downstairs still happy to communicate with each other.

My thinking process so far is: I want to share my files to specific computers with maybe static IPs on a network. Users shouldnt be able to view my files unless they know the password. Xbox will log in to the Desktop computer since I will setup a user/passwd on the desktop and when I want to add a directory to xbox, I can just use login details I set up for sharing to get in.

Would you say I am on the right path?

---

### Post by alphacrucis2 on 2009-07-08
> **CatKiller said:**
> Now I'm no networking guru, but this already means that downstairs is a separate network from upstairs. It should be relatively trivial to treat the incoming connection from upstairs as the big, bad Internet and have your wired networked devices downstairs still happy to communicate with each other.

Not correct. A layer 2 switch doesn't provide any network isolation at all unless it was running VLANs which doesn't apply in this case. In effect he is on the same LAN as the people upstairs. However he can secure his Samba shares by not permitting guest access.

---

### Post by munky99999 on 2009-07-08
> 
I share my internet connection with upstairs guys and they want the network "open" and not secured. (long story).
I have time. Well I guess I dont but I'm interested in their reasoning :)

> So, I started researching and I came across some concepts. One of which was using subnet masks to define my own LAN. Another was to password protect files.
You could subnet-dhcp reserve all the computers into 1 subnet and then reserve the rest of your subnet for fakemacs nobody will use.

This means that the router will need to route the traffic to get access to you. Routing rules then might be able to be put in place to ensure no such thing can happen.

Realistically you are going to find a ton of setup necessary in that case. Plus no ready expandability.

> Either option is a little tricky for me since I am a super n00b. I am willing to spend some time and understand it. 
Probably a bad idea then.

WPA + strong password.

> My suggestion would be to first slap your roomates and tell them network security is not optional. You don't want ust anyone connecting to your network, as you are responsible for what it is used for. Child porn, illegal downloads, etc. You can get in trouble for the actions of others. That is just a friendly warning.
Well obviously you cant make a statement about this worldwide but generally this isnt true. If someone steals your car and then robs a bank with it. You arent liable.

The only case where you have to worry... the person who is doing the child porn is a good friend. Or the person who stole your car is a good friend. Then it's FAR FAR FAR more suspicious.

Obvious fix is have no friends. LAWL.

---

### Post by CatKiller on 2009-07-08
> **alphacrucis2 said:**
> Not correct.

As I said, I'm not a networking guru :)

My point was simply that he already has a router in place. My not-especially-sophisticated router has a connection marked "Internet" and a four-way switch for the LAN. Downstairs traffic for the OP may already be separated out from upstairs traffic, and it may be simply a case of configuring the router to block access to his downstairs shares from upstairs whilst still allowing normal Internet connections to travel unmolested. Or I could be mistaken.

---

### Post by draperdt on 2009-07-08
My upstairs "roomates" are in army. Technically only 1 person should live there but any time they have 4 random guys living upstairs and since they shuttle a lot between forts and drills and getting deployed and such, they dont want security. Everyone sports an Iphone, Ipod, laptop and they dont like getting to type in a key apparently. I tried and tried to tell them but they just dont get it and it has been more of a hassle everytime they cant get their ipod to connect to stream pandora and they are knocking on my door. So all that aside, I am moving at the end of this month so I am not terribly worried but I was thinking about it and I was wondering how to acheive this goal. I pick up small projects like these to learn more about networking, computers or OS in general.

So, dealing with subnets and IPs is a little overboard, I will try to set up samba share such that a password is required before people view the files. This is just for my own satisfaction.

---

### Post by t4thfavor on 2009-07-08
The best way:

Get an openwrt capable ([www.openwrt.org](www.openwrt.org)) atheros based router/AP like the accton mr3201A, and setup a secure and non-secure SSID. Put the Non-Secure SSID into its own vlan, and setup AP isolation, and lan bleock. Users on the AP will not be able to access other users on the AP, and wireless clients will be isolated from the wired lan. Everyone will have Internet access, and life will be good.
(all this can be done easily, and decently cheaply with the services rendered at [www.open-mesh.com](www.open-mesh.com))


An OK way:
Get a decent HW firewall/AP like a Linksys wrt54gl and load Tomato firmware on it. Plug the cat5 from upstairs into its WAN port host your own WIFI, and ignore what they do upstairs as you will be protected by NAT.

Secure method:
IPCop with 3 nics. Setup a "red" "green", and "blue" network. Allow access from the green and blue to the red (WAN) but not from green to blue or blue to green. Its all really easy to setup, and administrate.

The technical way to do it:
Setup yourself a real router, and put both apartments on seperate lans. Make one default gateway for both, and make sure they do not have a route to each other.

I personally like the first two ways best as there is no routing black magic to work through. 

Hope these suggestions help at least a bit.

---

### Post by hibliss on 2009-07-08
> **draperdt said:**
> Hi, I am able to share the files and stream it to xbox using samba. So, that is not an issue. Xbox is seeing the shared files and every other electronic equipment is seeing the files too if browsed to "Network Places -> Samba shares", which would mean that the roommates can see them too. (I am moving end of this month to a new place so I want to avoid unncessary drama with those guys and have them secure the connection. 

FUPPES would solve that problem and only allow the Xbox to access the files. That was what I was suggesting. You set the Xbox IP as the only allowed IP to view the shared content.

---

### Post by lisati on 2009-07-08
If you own or otherwise have responsibility the network, you are free to set the rules.

---

### Post by hibliss on 2009-07-08
> **t4thfavor said:**
> The best way:

Get an openwrt capable ([www.openwrt.org](www.openwrt.org)) atheros based router/AP like the accton mr3201A, and setup a secure and non-secure SSID. Put the Non-Secure SSID into its own vlan, and setup AP isolation, and lan bleock. Users on the AP will not be able to access other users on the AP, and wireless clients will be isolated from the wired lan. Everyone will have Internet access, and life will be good.
(all this can be done easily, and decently cheaply with the services rendered at [www.open-mesh.com](www.open-mesh.com))


An OK way:
Get a decent HW firewall/AP like a Linksys wrt54gl and load Tomato firmware on it. Plug the cat5 from upstairs into its WAN port host your own WIFI, and ignore what they do upstairs as you will be protected by NAT.

Secure method:
IPCop with 3 nics. Setup a "red" "green", and "blue" network. Allow access from the green and blue to the red (WAN) but not from green to blue or blue to green. Its all really easy to setup, and administrate.

The technical way to do it:
Setup yourself a real router, and put both apartments on seperate lans. Make one default gateway for both, and make sure they do not have a route to each other.

I personally like the first two ways best as there is no routing black magic to work through. 

Hope these suggestions help at least a bit.

This is the best answer so far. OpenWRT is a bit intimidating for a networking newbie, I would suggest DD-WRT or Tomato instead, much more user friendly and can do the same thing in creating a new VLAN that would be unsecured and isolated.

Based on the response that you don't want to mess with "IPs", I am going to say that you are not going to find a good solution. IPcop is way too complicated to setup for using only one month.

I am going to endorse FUPPES one more time as an awesome option for the Xbox, it can even transcode the videos on the fly that the Xbox cannot play natively.

---

