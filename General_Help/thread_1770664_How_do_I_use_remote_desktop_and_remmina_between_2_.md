---
title: "How do I use remote desktop and remmina between 2 computers not on the same network?"
date: 2011-05-29
forum: General Help
---

### Post by Mr_VeRiTy on 2011-05-29
Hi, I'm trying to use remote desktop to see and control my sis's desktop over the internet, I tried to do it to see my *own *desktop and that works, but when I try my sis's IP it fails. 

We made sure her remote desktop settings were right. We used a site (ipchicken.com) to get her IP and I was trying to use port 5906 (I *think* it's open) to connect. The program I'm using is remmina.

Does anybody know what we're doing wrong?

---

### Post by iclestu on 2011-05-29
> **Mr_VeRiTy said:**
> Hi, I'm trying to use remote desktop to see and control my sis's desktop over the internet, I tried to do it to see my *own *desktop and that works, but when I try my sis's IP it fails. 

We made sure her remote desktop settings were right.We used a site (ipchicken.com) to get her IP and I was trying to use port 5906 (I *think* it's open) to connect. The program I'm using is remmina.

Does anybody know what we're doing wrong?

I would guess she is behind a router? try 

```
sudo apt-get install nmap
```

then
```

nmap <your sis's ip address>
```

suspect the port is closed, but even if its open the router needs to forward that port to your sisters machine. This will be in the routers settings... probably changed through a webpage type interface

---

### Post by Mr_VeRiTy on 2011-05-29
> **iclestu said:**
> I would guess she is behind a router? try 

```
sudo apt-get install nmap
```then
```

nmap <your sis's ip address>
```suspect the port is closed, but even if its open the router needs to forward that port to your sisters machine. This will be in the routers settings... probably changed through a webpage type interface

Yes she's behind a router (I am too) and the output from nmap was ```
Starting Nmap 5.00 ( http://nmap.org ) at 2011-05-29 18:51 BST
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 3.07 seconds

```

---

### Post by iclestu on 2011-05-29
incidentlly - it may be better to do this through a ssh tunnel (more secure). Check this out:

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by iclestu on 2011-05-29
> **Mr_VeRiTy said:**
> Yes she's behind a router (I am too) and the output from nmap was ```
Starting Nmap 5.00 ( http://nmap.org ) at 2011-05-29 18:51 BST
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 3.07 seconds

```

Can your sister access her router setting? ooo or can you??? if one of you can forward port 22 from your router to your machine ill walk you through doing it through a ssh tunnel (time allowing :) )

---

### Post by sammiev on 2011-05-29
I would not use anything less than a ssh tunnel or you would likely have unwelcome visitors before long. GL :)

---

### Post by iclestu on 2011-05-29
> **sammiev said:**
> I would not use anything less than a ssh tunnel or you would likely have unwelcome visitors before long. GL :)


seconded!

---

### Post by Mr_VeRiTy on 2011-05-29
> **iclestu said:**
> Can your sister access her router setting? ooo or can you??? if one of you can forward port 22 from your router to your machine ill walk you through doing it through a ssh tunnel (time allowing :) )
I can get to my routers config page if that's what you mean (192.168.0.1) But I can't find port forwarding on the page... Here's the things I can configure on my router [IMG]http://www.pasteall.org/pic/show.php?id=12996[/IMG]

---

### Post by linuxinstalledfromhdd on 2011-05-29
I use Teamviewer 6, and it works between Windows, Linux (Debian or Ubuntu OS), Mac, and Andriod systems. It's free for non-commercial use. The equivalent on Windows or Mac would be LogMeIn and GotoMeeting. Hope that helps.:D

Here is a guide:

[http://cinderbox.net/2011/05/23/how-to-teamviewer-6-for-ubuntu-natty-and-maverick/](http://cinderbox.net/2011/05/23/how-to-teamviewer-6-for-ubuntu-natty-and-maverick/)

---

### Post by iclestu on 2011-05-29
> **Mr_VeRiTy said:**
> I can get to my routers config page if that's what you mean (192.168.0.1) But I can't find port forwarding on the page... Here's the things I can configure on my router 

best guess here would be 'firewall rules' or 'static routes'. Explore some and see if you can find port forwarding......

---

### Post by Mr_VeRiTy on 2011-05-29
> **iclestu said:**
> best guess here would be 'firewall rules' or 'static routes'. Explore some and see if you can find port forwarding......

I couldn't find it in firewall rules or static routes, but services looks promising: [IMG]http://www.pasteall.org/pic/show.php?id=12998[/IMG]

---

### Post by iclestu on 2011-05-29
> **Mr_VeRiTy said:**
> I couldn't find it in firewall rules or static routes, but services looks promising: 

Hmm - yeah, that looks feasible. You could fill that in with name: ssh, start port 22, end port 22. but then you still need to work out how to direct the 'ssh service' you just created to your own computer.

That make sense?

---

### Post by Mr_VeRiTy on 2011-05-29
> **iclestu said:**
> Hmm - yeah, that looks feasible. You could fill that in with name: ssh, start port 22, end port 22. but then you still need to work out how to direct the 'ssh service' you just created to your own computer.

That make sense?
Ifconfig says my (local?) IP is one of these?:```
inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0

```
What do I do from here?

---

### Post by iclestu on 2011-05-29
> **iclestu said:**
> Hmm - yeah, that looks feasible. You could fill that in with name: ssh, start port 22, end port 22. but then you still need to work out how to direct the 'ssh service' you just created to your own computer.

That make sense?

Might be worth a quick google with 'port forwarding' 'your isp name' and or 'your router model' someone will have done this before....

```
Ifconfig says my (local?) IP is one of these?:
```

yeah. your home network will have an external ip too that points to your router. whatismyip.com will give you that. The essense of your problem is telling your router that your computer is to deal with things on port 22 (used for ssh) and that the router itself is not to deal with it.

soon as we crack that its no prob to set up a ssh server at your end....

---

### Post by Mr_VeRiTy on 2011-05-29
> **iclestu said:**
> Might be worth a quick google with 'port forwarding' 'your isp name' and or 'your router model' someone will have done this before....

```
Ifconfig says my (local?) IP is one of these?:
```yeah. your home network will have an external ip too that points to your router. whatismyip.com will give you that. The essense of your problem is telling your router that your computer is to deal with things on port 22 (used for ssh) and that the router itself is not to deal with it.

soon as we crack that its no prob to set up a ssh server at your end....
Is this what we're looking for?:
 
[IMG]http://www.pasteall.org/pic/show.php?id=13003[/IMG]
###
[IMG]http://www.pasteall.org/pic/show.php?id=13004[/IMG]

I went to the documentation for my router and about port forwarding it says ```
[B] Instructions for DG834,        DG834G, DG824M, FR114W, FM114P, FR114P, FR328S, FVL328, FVS328, FVS338,        FVX538, 
      FWAG114, FWG114P, or FVS318v3[/B]     These routers do port forwarding by assigning port numbers to a "service"        associated with the application you want to run. "Rules" are set        for particular services. Rules block or allow access, based on various conditions        such as the time of day and the name of the service.
     [INDENT]        **To Create a New Inbound or Outbound Rule**
       
[LIST=1]
[*]Submit the router's address in an Internet browser. (The default is            **192.168.0.1**).
[*]Enter the router's username and password.
[*]From the main menu, click **Security** > **Rules**.
[*]Click **Add** for inbound or outbound traffic, as appropriate to            the application you are planning to run.
[*]Select the **Service**. The services the router knows about are            listed in the drop down. If the service you want is not listed, add            it as described in the next section.
[*]Select the **Action**, for example **ALLOW always**.
[*]For **Send to LAN Server**, enter the IP address of the local server.            Note that this is also the IP address the computers on your LAN will            access.
[*]For **WAN User** choose **Any**, or limit access to particular            IP addresses.
[*]For **Log** selection it is reasonable to turn logs on, especially            at the beginning when you are unsure of the result of the changes you            are making. Later, you may want to set logs to "Never" for            performance reasons.
[*]Click **Apply**.
[/LIST]
       As noted in user manual for some models:
       
[LIST]
[*]Consider using the Dynamic DNS feature on the Advanced menu, so that            external users can find your network when the DHCP lease is renewed            by your ISP.
[*]If your own LAN server uses DHCP, and your IPs change on rebooting,            consider using the Reserved IP Address feature in the LAN IP menu.
[/LIST]
       **To Add a Service for These Routers**
       
[LIST=1]
[*]Click **Security** >** Services **>** Add Custom Service**.
[*]Enter any name you choose for the service.
[*]Select whether the service is to use TCP or UDP. If you are unsure,            select both.
[*]Enter the lowest port number used by the service.
[*]Enter the highest port number used. If the service uses only one port            number, enter the same number.
[*]Click **Apply**.
[/LIST]
        
[/INDENT]
```

---

### Post by iclestu on 2011-05-29
yeah, that firewall rules looks good.

set ssh service (inbound on port 22) to allow and point to your own computer's (local) ip address

then install openssh server (unless u already got this) with 

```
sudo apt-get install openssh-server
```

---

### Post by Mr_VeRiTy on 2011-05-29
> **iclestu said:**
> yeah, that firewall rules looks good.

set ssh service (inbound on port 22) to allow and point to your own computer's (local) ip address

then install openssh server (unless u already got this) with 

```
sudo apt-get install openssh-server
```
  Do I put my local ip in LAN users or WAN servers? (EDIT nevrmind I was on the wrong thing)

---

### Post by Mr_VeRiTy on 2011-05-29
> **iclestu said:**
> yeah, that firewall rules looks good.

set ssh service (inbound on port 22) to allow and point to your own computer's (local) ip address

then install openssh server (unless u already got this) with 

```
sudo apt-get install openssh-server
```
Ok I've done both of those I think.

---

### Post by iclestu on 2011-05-29
ok, get your sister to run the following commands...

```
ssh-keygen -t rsa
```
```

ssh-copy-id 'your user id'@'your EXTERNAL ip address'
```

(she will need your password) - this copies her public key to your system to enable her to log in without password

then have her execute

```
sudo apt-get install x11vnc
```

(insalling a vnc server)

```
ssh -f -R 5900:localhost:5900 'your user id'@'your EXTERNAL ip address'
```

(Pointing her 5900 port to yours)

```
x11vnc -once -safer
```

(starts the vnc server)

You should then just be able to point your own 'remote viewer' at localhost:5900 and see her desktop

hope ive not missed anything ;)

---

### Post by Mr_VeRiTy on 2011-05-29
> **iclestu said:**
> ok, get your sister to run the following commands...

```
ssh-keygen -t rsa
``````

ssh-copy-id 'your user id'@'your EXTERNAL ip address'
```(she will need your password) - this copies her public key to your system to enable her to log in without password

then have her execute

```
sudo apt-get install x11vnc
```(insalling a vnc server)

```
ssh -f -R 5900:localhost:5900 'your user id'@'your EXTERNAL ip address'
```(Pointing her 5900 port to yours)

```
x11vnc -once -safer
```(starts the vnc server)

You should then just be able to point your own 'remote viewer' at localhost:5900 and see her desktop

hope ive not missed anything ;)

Do I keep the quotes in the 2nd a 4th commands?

---

### Post by iclestu on 2011-05-29
> **Mr_VeRiTy said:**
> Do I keep the quotes in the 2nd a 4th commands?

No quotes, no

---

### Post by iclestu on 2011-05-29
btw - this will only work whilst your external ip address remains unchanged (probably a while if you dont reset the router). When the ip address changes you can update the commands accordingly but if you want to set up a script for your sis to 'give you contol' you might want to look at dyndns.com or something similar so that you can just refer to josmith.dyndns.com or something rather than a changeable ip address. But questions on that should be directed to someone else :) (at least for tonight)

---

### Post by Mr_VeRiTy on 2011-05-29
> **iclestu said:**
> No quotes, no
Wait, so it's 5900 *not * 5906?

---

### Post by Mr_VeRiTy on 2011-05-29
> **iclestu said:**
> btw - this will only work whilst your external ip address remains unchanged (probably a while if you dont reset the router). When the ip address changes you can update the commands accordingly but if you want to set up a script for your sis to 'give you contol' you might want to look at dyndns.com or something similar so that you can just refer to josmith.dyndns.com or something rather than a changeable ip address. But questions on that should be directed to someone else :) (at least for tonight)

Ok, dyn-dns is free isn't it?

---

### Post by Mr_VeRiTy on 2011-05-29
My sister said when she tries the 4th command she gets 
```
$ ssh -f -R 5900:localhost:5900 luke@77.86.113.31
Cannot fork into background without a command to execute.
```

---

### Post by iclestu on 2011-05-29
> **Mr_VeRiTy said:**
> My sister said when she tries the 4th command she gets 
```
$ ssh -f -R 5900:localhost:5900 luke@77.86.113.31
Cannot fork into background without a command to execute.
```

ooops. ditch the '-f'. My mistake

---

### Post by iclestu on 2011-05-29
> **Mr_VeRiTy said:**
> Ok, dyn-dns is free isn't it?

yeah - think they have some extras u can pay for, but yes its free for what i described

---

### Post by iclestu on 2011-05-29
> **Mr_VeRiTy said:**
> Wait, so it's 5900 *not * 5906?

That x11vnc server we got your sis to download uses 5900 by default. Im sure there will be a means to change it bus seems pointless if we piping it all thru the ssh tunnel anyhoo....

---

### Post by Mr_VeRiTy on 2011-05-29
I tried connecting to localhost:5900 but it just connects to me.... all the commands worked on my sisters side..

---

### Post by iclestu on 2011-05-29
> **Mr_VeRiTy said:**
> I tried connecting to localhost:5900 but it just connects to me.... all the commands worked on my sisters side..

hmm - i have reread it all and cant see where i went wrong. anyone else spot an error??

have her exit any terminal and try afresh from the ssh -R 5900:localhost.... onwards. If it doesnt work, have her do a 
```
nmap localhost
```
on hers and make sure 5900 is open for vnc if it is then make sure your
```
nmap localhost
```
shows ssh open on port 22 for you..

---

### Post by Mr_VeRiTy on 2011-05-29
> **iclestu said:**
> hmm - i have reread it all and cant see where i went wrong. anyone else spot an error??

have her exit any terminal and try afresh from the ssh -R 5900:localhost.... onwards. If it doesnt work, have her do a 
```
nmap localhost
```on hers and make sure 5900 is open for vnc if it is then make sure your
```
nmap localhost
```shows ssh open on port 22 for you..
Yep, both open, is it something to do with my remmina settings?

---

### Post by Mr_VeRiTy on 2011-05-29
I'm gonna leave it for now and try to figure it out tomorrow, thanks for all your help!

---

### Post by iclestu on 2011-05-30
> **Mr_VeRiTy said:**
> Yep, both open, is it something to do with my remmina settings?

not sure, but no problem to try a different vnc viewer. I use krdc but maybe thats more suited to kde than gnome or unity. How about trying this one for now:

```
sudo apt-get xvnc4viewer
```

then, after your sis has done her bits, you can do
```
vncviewer localhost:5900
```

---

### Post by krunge on 2011-05-30
BTW, to force x11vnc to use port 5900 add "-rfbport 5900" to the x11vnc cmdline.  If something else is using the port, x11vnc will exit instead of autoprobing for an open port.

---

### Post by krunge on 2011-05-30
> 
then, after your sis has done her bits, you can do
```
vncviewer localhost:5900
```
Depending on the vncviewer it might be this instead:
```
vncviewer localhost:0
```

---

### Post by iclestu on 2011-06-01
did you get this up and running in the end?

---

### Post by Mr_VeRiTy on 2011-06-02
> **iclestu said:**
> did you get this up and running in the end?

Not yet, I've been having some OS issues recently :\  switched to Debian, and then to LinuxMint, gonna try this again on mint though. I'm guessing the commands are the same on Mint?

---

### Post by iclestu on 2011-06-02
> **Mr_VeRiTy said:**
> Not yet, I've been having some OS issues recently :\  switched to Debian, and then to LinuxMint, gonna try this again on mint though. I'm guessing the commands are the same on Mint?

can see no reason why not though I have only ever used this distro....

---

### Post by Mr_VeRiTy on 2011-06-28
I just tried this again with a laptop and computer both running Linux Mint 11, and it works fine.. But they are both on the same network, meaning I could use the local IPs.

---

