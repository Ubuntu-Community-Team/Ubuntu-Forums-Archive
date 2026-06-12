---
title: "SSH from OSX to Ubuntu?"
date: 2012-05-08
forum: General Help
---

### Post by bulldoze on 2012-05-08
Ok, so I can do it from Ubuntu to OSX the mac sharing program helpfully gave me the command to do it.

eg ssh [email]fred@unknown-e0-f7-57-0a-df-6b.home[/email]

but I cant seem to go the other way, one of the reasons is I don't know how to find out my ip address of my Ubuntu box.

 I have tried ifconfig but it gives me about 6! which ones do i use eth0? lo? wlan0? HW addr inet address? I have tried all to no success. I also opened a browser and did a google whats my ip and it came up with one in the more usual 155.45.67.65 (made up!) format but that does not work either.

Any ideas anybody? many thanks.

---

### Post by papibe on 2012-05-08
Hi bulldoze.

By default the server side of ssh is not installed on Ubuntu. Did you install it?

If not, it's pretty simple:
```
sudo apt-get install openssh-server
```
I hope it helps, and tell us how it goes.
Regards.

---

### Post by bulldoze on 2012-05-09
Thanks! I will give that a go later - got to go to work!

---

### Post by Bucky Ball on 2012-05-09
If you are getting the IP address via DHCP (eg assigned by your router) then it will change everytime you reboot the machine which makes networking with other machines on the LAN kinda difficult. I think you can use names instead of IPs but I've never done it that way. 

If you intend using IPs then perhaps give the Ubuntu box a static IP if it hasn't got one already. That will stay the same regardless. Right click the network icon and 'Edit Connections' to do this. Let us know if you need any help with that if you do it.

---

### Post by bulldoze on 2012-05-09
> **papibe said:**
> Hi bulldoze.

By default the server side of ssh is not installed on Ubuntu. Did you install it?

If not, it's pretty simple:
```
sudo apt-get install openssh-server
```
I hope it helps, and tell us how it goes.
Regards.

Ok I have done this now and restarted the pc.

does not seem to have helped though - to be honest my problem I think is to know what ip address to use. I cant even ping the ubuntu box from the macbook. as i just dont know what ip address to use and what format.

I did similar stuff at work today on a redhat box and the ifconfig command came up with an ip4 ip address underneath the eth0 HW address. Not sure why this is so complicated on Ubuntu although that was over a local lan and not over the internet.

---

### Post by papibe on 2012-05-09
I would try to make it work on your LAN home, and then try to access it from the Internet.

Could you post the ifconfig from the Ubuntu machine?
```
ifconfig
```
Regards.

---

### Post by bulldoze on 2012-05-09
To be honest I think I need to give up on this installation. I tried to do as you said and copy the ifconfig and firefox (and the whole machine) keeps randomly freezing for 30secs at a time. I noticed this yesterday but a reboot gave a brief respite.

Looks as though I have bigger fish to fry! I think I might reinstall with a more stable release and then try again in a few days.

This was the last straw after being unable to install tor as well, so I think I will cut my losses and start again.

Thanks for the help, I'll probably be back!

---

### Post by Bucky Ball on 2012-05-09
Have you read my post? #4? It shouldn't be this hard. ;)

---

