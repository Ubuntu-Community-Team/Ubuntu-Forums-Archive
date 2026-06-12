---
title: "Dual Boot - Same LAN IP for both?"
date: 2012-08-03
forum: General Help
---

### Post by danieldiazdon on 2012-08-03
Im currently dual booting 2 separate UBUNTU's 12.04. One I use for social networking, documents, etc. While I use the other one for future server management, messing around with white hat hacking on my network, and so forth. 

When I access my router homepage (192.168.1.254) I notice that the name registered to my LAN IP changes as I change between my dual boots. In other words, both dual boots have the same LAN IP. Im a little bothered by this, as I would prefer each dual boot to have its own LAN IP. Why did it join them? My guess is that since they are both ubuntu and on the same computer, that my router registered them as 1 os. In the past I have dual booted Windows with Linux and they each were separately assigned their own LOCAL IP.

[IMG]http://s15.postimage.org/plshmlrsb/Screenshot_from_2012_08_03_00_07_26.png[/IMG]

As I log in between the dual boots and check the router home page (192.168.1.254), the name for my computer LAN IP changes from AdminMan to my other. 

Besides as to why it happens. I would prefer them to have separate LAN IPS. To clarify, I want each each of my 2 dual boots to have its own LAN IP as opposed to them both being the same. Like this, when I go to check my router homepage, there should be two os's registered. 

EX:
-BOB 192.168.1.1
-John 192.168.1.2

Yet they are both dual boots on the same computer. Thanks Guys :D

---

### Post by Dylan1473 on 2012-08-03
I was going to say it might be because you're using the same MAC address but then you said you've had separate IPs before using Windows/Linux dual boots. I think the simplest way to do this would be to set a static IP address from within each Ubuntu install (I'd say do it from the router normally, but both are using the same MAC address and I'm guessing you don't feel like changing it in either). Here's hoping I remember how. I'm pretty sure this is what you need  to do (you can do this from the GUI to but it sounds like you might not have a GUI on the one, so I'm giving you the command line way):

Boot up Ubuntu. Either one. This same method will work on either but you can probably figure it out using the Gnome Network Manager for the one that has a GUI (I'm assuming at least one doesn't) if you'd prefer that. The file you need to edit is /etc/network/interfaces, so use 
```
sudo nano /etc/network/interfaces
```of course you can replace nano with the text editor of your choice if you'd prefer. There'll be a section in there that says something like
```
auto eth0
iface eth0 inet dhcp
```You want to comment that out (put # symbols in front of each line) and then add
```

auto eth0
iface eth0 inet static
            address PUT YOUR IP ADDRESS HERE
            netmask 255.255.255.0
            gateway PUT YOUR ROUTER IP ADDRESS HERE
            dns-nameservers PUT YOUR ROUTER IP ADDRESS/DNS SERVERS HERE

```I feel like there's supposed to be more than that but I just checked and I've got a server running with just that so I guess it's okay. Also, I'm not 100% certain the dns section is even necessary, I've just got it there because I use some custom ones. Anyway, put your IP address in the places indicated. EDIT: I forgot to mention, you might have to replace eth0 with the name of your network interface if it's not eth0. It's probably wlan0 if it's wireless. EDIT AGAIN: I also forgot to mention, in addition to that, if you're using wireless you'll probably need to add this:
```

wpa-ssid YOUR WIRELESS NETWORK NAME
wpa-psk YOUR WIRELESS NETWORK PASSWORD

```

Be sure to back up the configuration file first! It's been a while since I've done this and it could mess up your internet if you do it wrong. To back up the config file just type
```
sudo cp /etc/network/interfaces /etc/network/interfaces.backup
```I know some of these are probably things your pretty familiar with and I don't mean to patronize or anything, I'm just not sure how much information you need/who might read this later, so I'm trying to stick in as much as possible.

---

### Post by danieldiazdon on 2012-08-03
Okay, Im gonna give this all a try the second im able too. First things first, thanks for the response, I greatly appreciate it. And 3 things too clarify upon.

1- You said to add the comment symbols to the lines. So it will look like this?

```
 
#auto wlan0 
#iface wlan0 inet dhcp

auto wlan0
iface wlan0 inet static
            
address PUT YOUR IP ADDRESS HERE (Is this my INTERNET IP or ROUTER IP?)
netmask 255.255.255.0             
gateway PUT YOUR ROUTER IP ADDRESS HERE            
dns-nameservers PUT YOUR ROUTER IP ADDRESS/DNS SERVERS HERE (You said that I prob wont need this one, so I wont bother with it)

```2- You said to put my IP ADDRESS under address. Do you mean my internet one or my LAN one. Ex, 192.168.1.50 If I enter my internet IP then thats it, but if I have to enter my LAN IP, do I choose which ever one I want, or do I put the one that relates to my router now, which is 192.168.1.72? 

3- After I get my static IP setup, then the UBUNTU version which file I edited will have a different LAN ip, and the other UBUNTU dual boot will have the old one (192.168.1.72)?
Just wanna make sure so im not lost here!

I think those are the questions I have, before I start your instructions. Oh and like you clarified (THANK GOD), Im running wireless. All of this is happening off my laptop. Once again, thanks a ton :D

OH, and before I start the process, would it be easier to just change the mac address of the dual boots? Wouldnt they register differently on the router (as 2 separate connections)? Or would that be more complicated? Would I be able to change my MAC ADDRESS right through here? Whats your opinion, set a static IP or change the MAC ADDRESS of one of the laptops? 

[IMG]http://s18.postimage.org/6m2jlu1bd/Screenshot_from_2012_08_03_13_42_22.png[/IMG]

---

### Post by Dylan1473 on 2012-08-03
1. That's correct with the commenting. Technically you could just remove it but this has the same effect and makes it easier to restore it later.

2. Your IP address here is the IP assigned to your computer by the router. More specifically, the one you *want* to be assigned*.* Any IP that will work with your router will do. Sorry, that wasn't very clear.

3. The Ubuntu with the edited file will have the IP you put in the address section if everything works properly. If your router insists on assigning both Ubuntus the static IP you assign to one you can simply carry out the same process on both with different IPs.

Regarding the DNS servers, you *might* need it. I'm honestly not sure. You can just put your router IP there again if you don't have special DNS servers to use though, it probably redirects to your ISPs servers. I've just got the Google ones there (8.8.4.4 and 8.8.8.4 ).

Regarding the MAC thing, what this will do is make your computer lie about the MAC address of your network adapter so the router thinks it's a different device than it actually is. This might help if the router is in fact assigning the same IP because it's the same OS/MAC address. I've never actually attempted a *permanent* MAC address change, but a cursory search seems to indicate you'd add 
```
hwaddr [A MAC ADDRESS]
``` to the same file. I forget the exact formatting rules for a MAC address but I know that 00:11:22:33:44:55 will do. If you're editing the file anyway I'd recommend just using the static IP method though, it's a more direct solution to your problem.

EDIT: Not only can you change your MAC address through there, you can setup a whole static IP more easily. If you have the Gnome Network Manager on both computers you can do it on both. For that:

1. Edit your wireless network.
2. Go to the IPV4 settings (I'm guessing you're using IPV4) tab
3. Switch the method drop down box to Manual
4. Click Add
5. Fill out the Address field with your desired IP address
6. Enter 255.255.255.0 in the Netmask field
7. Enter your router's IP in the Gateway field
8. Enter your router IP (or the DNS servers of your choice) in the DNS Servers field.

This is actually an easier method, it's just that it won't work without a GUI/if you're using a different network manager.

EDIT AGAIN: Forgot to answer your actual question. Enter a MAC address in the Cloned MAC field if you want to use a fake one.

---

### Post by danieldiazdon on 2012-08-03
Alright thanks for all the clarification and effort youve given :D Something weird, when I opened up the network interface file, this is what was in it..

```

auto lo
iface lo inet loopback

```Does that matter? Do I proceed to add the comment marks infront and copy and paste the code you gave me along with any info I add?

---

### Post by Dylan1473 on 2012-08-03
No, leave that alone. That's your local loopback interface, it can just stay as it is. Just comment out and add the new bits about your wlan interface. I'd recommend using the Gnome Network Manager where that's an option, though.

---

### Post by danieldiazdon on 2012-08-03
If you could please clarify a few more things. Trying to expand my knowledge on all of this. Thanks

ALRIGHTY, ill use the GUI then on both of my UBUNTUS then. It looks  easier. And oh alright, so thats how I can change the mac address. If I  were to "clone"/change it, would anybody ever be able to discover that  it was changed and what my old one was? Thanks bro Oh, and what exactly  is a DNS server? Whats its purpose?

 Im doing the change of the static IP as I type this. For my  desired static IP, like you said I can choose whatever I want. How high  does it go? like 192.168.1.x (how high does x go?) Thanks man. In the  IPv4, theres a checkbox that says "Require IPv4 for this connection to  complete.." Should I have this checked? What does it do?

---

### Post by Dylan1473 on 2012-08-03
I don't believe there's any way to determine an original MAC address from a faked one, I don't believe they were ever intended as a security measure. It's possible to change it to obscure your MAC address from other people watching your adapter/network. It is possible to determine someone's physical location based on wireless signals though. I'm not sure how well it's working on Linux right now but a program I used to use to monitor how my network was doing called inSSIDer had a feature where you could use a GPS to learn the physical locations of access points. I'm not sure but I believe there are tools for Linux (maybe associated with aircrack) that can establish the physical locations of access points and other network adapters with GPS.

A DNS (or Dynamic Name Server) is a server that translates IP addresses to names and vice versa. They're the reason you don't have to enter random strings of numbers to access websites and services. You could set one up on your network to give each of your computers a name - for example, if you were to host a web server on your laptop others could access it by going to danieldiazdonslaptop.danieldiazdonsnetwork.net (or some less absurdly long name) so long as they were using your DNS server. It's also possible to redirect traffic there from your router. Or, if you don't mind spending some money (it's actually pretty cheap, usually less than $15 a year per name, sometimes way less) you can register a domain name so that anyone can get to the servers you attach to the name.

The IP address has a total of 256 possible entries per section (0 through 255). Your router may be able handle anything from 192.168.1.0 to 192.168.1.255, but some of those will be reserved for other purposes. 192.168.1.1 is probably the IP address of the router itself, for example. You can pick pretty much anything in that range, just be sure not to cause conflicts. I'd assume your router probably handles this automatically, but maybe choose one a bit higher up so the router doesn't automatically assign it to another device and cause conflicts. It shouldn't but I had this happen with a really crappy router before. There are also ways to configure what addresses your router will and will not automatically assign.

 I'm not sure what the require IPV4 checkbox actually means (I assume it has to do with the distinction between IPV4 and IPV6, and I've never made use of IPV6) but I know it should work fine unchecked. I doubt checking it would render your connection useless either though.

---

### Post by jerome1232 on 2012-08-03
> **danieldiazdon said:**
> 
 Im doing the change of the static IP as I type this. For my  desired static IP, like you said I can choose whatever I want. How high  does it go? like 192.168.1.x 

1 - 254, assuming you have the standard subnetmask for your address range (you do). Routers often take the lowest or the highest ip, so 1 or 254 will be taken automatically. 

What router are you using? Does it save a small pool of addresses for statics?

---

### Post by Dylan1473 on 2012-08-03
jerome1232 makes a good point - your router might only allow certain addresses to be assigned and trying to go for others might prove...interesting. Try taking the one that's already been assigned as your static IP and maybe go one higher for the other if you have problems picking other ones.

---

### Post by danieldiazdon on 2012-08-03
Alright guys so I changed their static IPs to
-192.168.1.99
-192.168.1.98

However, what I noticed is that the router shows them as both having the same MAC address. Therefore, as I switch between them, and check the router homepage, my computer entries change. 

EX. on UBUNTU 1

user23291742 - 11:11:11 (whatever mac address) - 192.168.1.99

but then when I switch to Ubuntu 2, the same entry changes too.

user 2343454 - 11:11:11 (same mac address) - 192.168.1.98

Therefore, both Ubuntus are not entirely separate. So in order to completely separate them, im going to have to change my MAC address. In order to do this, what do i do? I think I have an idea of how to, correct me if im wrong.

1. network connections
2. Open up my ssid link
3. Put whatever MAC address under "Cloned Mac"

Then thats it? Oh, and I only have to do this on one of the Ubuntus, correct? Can I put in any mac address?

---

### Post by Dylan1473 on 2012-08-03
The router shows them as both having the same MAC address because they do both have the same MAC address. The address is hard coded into your network adapter (though it can be changed using software on your computer). I don't think it'd actually be an issue in any way unless you were planning to make some MAC based configurations.

However, changing it probably won't do any harm, again unless you've changed other things based on MAC address, so you can go ahead and change it in the way you described. That's not how I've changed it in the past, but I've done temporary changes and I'm pretty sure your method should work as a permanent one (until such time as you choose to revert it, of course). Just blank that field out if something goes wrong.

EDIT: Also, yes, you only need to do it on one Ubuntu - the other will just use the hardcoded MAC address. No, you can't put in absolutely any MAC address. There are certain rules for how they're setup, and I don't remember all of them. I know that it has to be in this format though:

00:11:22:33:44:55

or sometimes

00-11-22-33-44-55

(and incidentally that address is a working one). I believe the other rules have to do with using specific sections at the start (first three sections, I think) since different codes refer to different manufacturers or something. Both letters and numbers are valid characters to use. EDIT: As pointed out by jerome1232, only letters a through f are acceptable. You could probably use, for example:

00:11:22:ef:3b:ac

or basically any characters of 0-9 and a-f for the last three sections. That's if I'm remembering the formatting rules correctly.

---

### Post by danieldiazdon on 2012-08-03
> 
I don't believe there's any way to determine an original MAC address from a faked one, I don't believe they were ever intended as a security measure. It's possible to change it to obscure your MAC address from other people watching your adapter/network. It is possible to determine someone's physical location based on wireless signals though. I'm not sure how well it's working on Linux right now but a program I used to use to monitor how my network was doing called inSSIDer had a feature where you could use a GPS to learn the physical locations of access points. I'm not sure but I believe there are tools for Linux (maybe associated with aircrack) that can establish the physical locations of access points and other network adapters with GPS.


What problems would I have with changing the mac address through the method I described? Wouldnt it just allow the router to register them as two separate mac addresses? 

Oh and earlier you mentioned something about GPS and the program you described. I looked into that a little bit and wanted to clarify. There is NO WAY to GPS locate a computer connected to a network? From what you mentioned, im understanding that the program GPS locates the router itself but not the computer connected to it. Thanks

---

### Post by jerome1232 on 2012-08-03
> **danieldiazdon said:**
> What problems would I have with changing the mac address through the method I described?

It's remotly possible you arbitrarily pick a mac in use by another device and wonder why something has ip conflicts in the future.

It's a prettttttty remote chance, I would go with changing the mac under one OS, this will allow your router to treat them as seperate computers and do that thing it does normally. Scrap the static assignments if you change the MAC imo.

---

### Post by Dylan1473 on 2012-08-03
I doubt you'd have any problems, changing MAC addresses is quite safe and you can always revert them. As far as I know there are literally no consequences to doing so. I don't think your computer will even allow you to use a non-functional one.

For sure you can use GPS to locate routers, but it might be possible with computers connected to the network as well, though more difficult. Now, I'm not sure about this - I've certainly never done it. Wouldn't mind trying but I don't have a GPS to plug into my computer. But network adapters broadcast signals while they're turned on, even if they're not in master mode, and it might be possible to track their physical location. If it is possible though I'd assume it would be much more difficult and you'd need to be closer since the signals aren't as strong. I'd further assume that a network adapter operating in master mode (like if you set your computer up to be a router) would certainly be trackable just like a conventional router (though again maybe from a shorter distance).

EDIT: A small addendum: if it's possible to track computers with GPS they wouldn't necessarily need to be connected to a network I don't think, just have an active network adapter. If I recall correctly you can see computers not connected to networks using aircrack.

---

### Post by danieldiazdon on 2012-08-03
Oh alright, thanks Dylan for the clarification. But now I have a problem. When I try to change the MAC address following the steps I showed, my Ubuntu wont connect to the router, hence I dont have access to the internet...

I tried: 
00:11:22:33:44:55
00:11:22:3b:4e:55

and a few others to see if it would allow me to connect. Am I doing something wrong? Thanks guys for the patience and effort

---

### Post by Dylan1473 on 2012-08-03
That's interesting. Do you have any MAC filtering in place on your router? Did you set up your connections with one of those things where you push the button and it automatically makes a secure connection for your computer? I don't know if those would do MAC filtering (never used it) but it's conceivably possible. Also, try temporarily setting a MAC address:

```

sudo ifconfig wlan0 down
sudo wlan0 hw ether [YOUR MAC ADDRESS]
sudo ifconfig wlan0 up

```

rebooting will revert this.

---

### Post by jerome1232 on 2012-08-03
> **Dylan1473 said:**
> 

00:11:22:ar:3b:r3

or basically any random characters for the last three sections. That's if I'm remembering the formatting rules correctly.

MAC addresses are Hexadecimal numbers, you can only use the numbers 0-9 and the letters A - F in each place (ie 01:25:AB:E9:99:11 is a valid MAC while [COLOR="Red"]R[/COLOR]5:11:11:11:11:11 is not)

It's also possible your driver doesn't support chaning the MAC of your network device, can you verify the MAC address has actually changed, and have you tried it throught the GUI interface? right click the icon in top right, click edit connections, select the connection, hit edit, change the mac

---

### Post by Dylan1473 on 2012-08-03
Ahh, I knew I was forgetting *something*. Edited to correct that.

---

### Post by danieldiazdon on 2012-08-03
When I attempted to change it, I had done it through the GUI, and after that it didnt allow me to connect. And Im not sure what Dylan was saying, but to connect to my router, I enter the SSID Password and then I am connected

---

### Post by Dylan1473 on 2012-08-03
Yeah, I wasn't very clear there. I forget the name for it, but with some routers there's an option to push a button on the router and then have the computer connect in the period where it's allowing connections. Then I guess it gives you a random password or something, I don't know how it works. I think my router has it but I just set it up manually anyway.

I'm assuming you already blanked out the changed MAC field to revert it to normal. Did you try the method I suggested of setting the MAC temporarily? I've never done the permanent one so I can't be 100% sure I'm giving you the right instructions. This is to make sure your computer is otherwise able to change the address.

---

### Post by danieldiazdon on 2012-08-03
```

sudo ifconfig wlan0 down
sudo wlan0 hw ether [YOUR MAC ADDRESS]
sudo ifconfig wlan0 up

```rebooting will revert this.[/QUOTE]

Yea I tried doing this method. I did it a little differently though based on some code I found online. I did..

```

[B]sudo service network-manager stop
[/B][B]sudo ifconfig [COLOR=magenta]wlan0 [/COLOR]hw ether [COLOR=#cc0000]xx:xx:xx:xx:xx:xx
[/COLOR][/B][B]sudo service network-manager restart
[/B]
```

It did actually change it, but like you said, it was only temporarily. I ran IFCONFIG and under "wlan0" it appeared to what I had set it too. Then I check my router homepage and it registered as a separate computer. However, the second I restarted my computer, It returned to its old one...

---

### Post by Dylan1473 on 2012-08-03
And you had internet after you changed it? Then you are at least able to change your MAC address. And yes, that's fine to - ifconfig wlan0 down turns off your interface, that I believe turns off networking, so you'll have much the same result. Maybe that's not the proper way to do it through Gnome Network Manager; like I said, I've never actually tried.

There's an alternative: you could just run the temporary script on every bootup. It's probably possible to set it to do so manually. Lemme just double check how to do so on Ubuntu and I'll edit with the answer.

EDIT: Okay, you need to edit rc.local. I'm not 100% sure but I think it'll allow commands that require administrative privileges. Just be prepared to revert it to it's defaults if something goes wrong. So, do 

```
sudo nano /etc/rc.local
```and add those three lines.  You might have to use ifconfig though, network-manager might not even be running at that point. Actually, it's possible only the middle line would even be necessary. You can also use a utility called macchanger which has some interesting features (like picking a random address from a specific manufacturer). This is what I've used in the past. You'll have to install it though.

All that's just me being "pretty sure" though, I remember if I've run commands at start using text files in Ubuntu.

---

### Post by danieldiazdon on 2012-08-03
TO answer your question, once I did the manual mac address change, I was able to access the internet and everything. Im sorry for being difficult, but im not understanding what your telling me to do. 

What is the file your telling me to edit? Is this the only way to permanently change the mac address? How come when I restart my computer using the method you showed me, the mac address goes back to what it was? Theres no other way to make it permanently stay to what I set it as?

Thanks Dylan and everybody else that has contributed :D

EDIT: So I can change the mac address permanently with the program mac changer and save myself all this hassle??

---

### Post by Dylan1473 on 2012-08-03
The file I'm talking about is located in the /etc/ directory, it's a configuration file. You type commands in there much like you would in a terminal and they run at the start. I'm hoping it has root privileges, but I can't remember for sure. If not things are a lot more complicated.

The method that does work for you is only intended to be a temporary change - when the system starts up it reverts to your hard coded MAC address. You can't get rid of a hard-coded MAC address, but you *can* instruct your system to make a fake one every time it starts up. I figured that'd be what changing it in the Gnome Network Manager would do, but it doesn't seem to be working. By placing the commands that do work in the /etc/rc.local file they'll be run every time at start, creating the fake MAC address each time your computer boots up. 

You can edit the file in a graphical text editor by typing gksudo gedit /etc/rc.local if you prefer. Then, just type these commands before the exit line but after the comments and save the file:

```

sudo ifconfig wlan0 down
sudo wlan0 hw ether [MAC ADDRESS]
sudo ifconfig wlan0 up

```*Hopefully* rc.local has root privileges - if so, that should work perfectly assuming it doesn't get messed up by something that starts after it runs somehow. Try that and tell us what happens.

EDIT: Actually it might not need the sudo, try without that first.

---

### Post by danieldiazdon on 2012-08-03
Alright, so I gave it a try. Followed your instructions..put the code in..restarted the ubuntu..and when I logged back in, I couldnt connect to the router. The wifi signal icon just kept going and going. And then it asked me for the ssid password thinking that it was incorrect.

So that method didnt work.. :/ Its amazing what a pain this can be.. damn!

Any other ideas?

---

### Post by Dylan1473 on 2012-08-03
Okay, I just attempted the very same thing with the same result. It seems that only the first command got executed. I'm going to try something and edit this, maybe there's something I can do....

---

### Post by danieldiazdon on 2012-08-03
Like  I said, thank you so much for all the effort youve put. Im sure there is a way to permanently spoof a mac address. Let me know if you think of anything else. Ill do some research myself.

---

### Post by Dylan1473 on 2012-08-03
Okay, I got it. For some reason that command isn't working, so you'll have to download macchanger. Type: 

```
sudo apt-get install macchanger
```then you need to make a script (just a text file) anywhere that looks like this:

```

#!/bin/bash
ifconfig wlan0 down && macchanger --mac 00:11:22:33:44:55 wlan0
ifconfig wlan0 up

```replacing 00:11:22:33:44:55 with the MAC of your choice, and save it as an sh file (save as yourfilename.sh). Make it executable either by right clicking, selecting properties, opening the permissions tab and selecting "Make this file executable" or typing
```
sudo chmod +x [YOUR FILE PATH]
```Then add
```

sh [YOUR FILE PATH]

```to rc.local. I recommend placing it in a path without any spaces, such as your home directory. If there are spaces it might be okay to put quotes around the directory path. Then reboot your computer and check your MAC.

---

### Post by danieldiazdon on 2012-08-05
Perfect! Works great, it changed is sticking after reboot. Thanks so much for all your help! :D

---

