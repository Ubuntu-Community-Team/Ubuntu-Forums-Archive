---
title: "&quot;Another user is controlling your desktop&quot;"
date: 2010-06-22
forum: General Help
---

### Post by zcacogp on 2010-06-22
Chaps, 

One that has me worried. 

I'm using my lappie, and have just (literally, just) had a message in the top right hand corner of the screen saying "another user is controlling your desktop" - the sort of message that shows when another user remote desktops to the machine. 

Snag is that, while the machine is set up to allow remote access without giving permission, there is no-one else on either of my other two machines at the moment. (Only one of them is on.) 

There was no change to my desktop - no movements of the mouse or anything like that, and I turned off "Allow remote access" immediately, but it has left me concerned that someone has compromised my machine. 

I checked my wireless router and there is no-one else logged in to that via the wireless system. I don't know how else to check user logs on the router, but will find out. 

Should I be worried? Can such a message appear randomly? Is it possible that I have had my system compromised? The other machine that is turned on at the moment is my desktop machine, and both the laptop I am using and the desktop are behind a firewalled Netgear DG834GT router. 

Putting it simply, what happened and how do I find out? 


Oli.

---

### Post by jnorthr on 2010-06-22
i'd look at admin>View System Logs then go to bottom and examine messages there. If it is a rogue bit of code between your machines, you may see further clues. On my setup (4xmachines behind a firewall) i do the same - allow signon without passwords, i cannot see how your system would say that unless another client from outside your router on the internet did the deed. That would imply you have port 5900 open on your router as that is the suggested default for people using VNC to remote-control a desktop. Could you check your router to see if either port 5900 or port 22 are open ?

thx

---

### Post by ram2500 on 2010-06-22
Some client has accessed your machine likely. It is hopeful you have security (WPA2). I would reboot and see if it happens again. Was there anyone else using any of the computers on your network? 

I think it would be best for your Ubuntu PC(s) have the password enabled to access the desktop remotely, unless you often need remote access and you're really remote, such as 500 miles away:). 

Now is also the time to perhaps reboot the router, change the passkey (if any--if you don't have WPA2 protection, set it up ASAP) and perhaps find an update to the router's firmware.

edit: as the user said above, if ports 5900 and 22 are open, this will supposedly enable remote access. If you don't need remote access, 
another step is to close them for optimum security. I am not experienced with configuring firewalls (as I'm just merely a home user)--however, there is a firewall graphical front-end (I think that's what it is) called Firestarter, which in there, you can close ports off at your will.

---

### Post by zcacogp on 2010-06-22
Chaps, 

Thanks for your replies. 

I have checked the logs on this machine and can't see anything (although I'm not quite sure what I am looking for.) I have also checked the logs on the router and everything there looks OK. 

I don't know anything about port forwarding but looking at the uPNP part of the router controls suggested that port 5900 could have been open, so I have closed it. 

The wireless network has MAC address security but no WEP security. I have no reason to think that anyone has attacked via this route, and when the message came up I checked the router to see if there was anyone else logged on - there wasn't. 

Ram - no, there is no-one else using any of the other machines on my network. There is only one of them turned on, and there is no-one in that room. 

I have just (40 minutes ago) given access to my network to a friend who is staying the night - I looked up the MAC address on his laptop and made it a 'permitted' device on my router. But he isn't IT literate enough to try and remote desktop into my machine (I don't think he would know what "remote desktop" is.) And I think he is asleep with his machine off. 

So, given the two routes in would be either wirelessly to the router or from the internal connection, and I can't see anything amiss with either, I am a bit stumped. I have re-set the "allow outside users to control this machine" setting on this laptop so that it can be remote desktop-ed to and the problem hasn't recurred, but this has shaken my confidence in my set-up a little. 


Oli.

---

### Post by t0p on 2010-06-22
Couple of points/suggestions:

If this happens again, open a terminal and type in the command

```
w
```

This will show what users are doing what on your machine.  For instance, if I run **w** now, I get the following output:

```

t0p@phobos:~$ w
 00:39:10 up 28 min,  3 users,  load average: 1.31, 1.59, 1.29
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
t0p      tty7     :0               00:13    0.00s 10:44m  0.84s /usr/bin/gnome-
t0p      pts/0    :0.0             00:21   17:29m  4.26s  3.98s wget -c http://
t0p      pts/1    :0.0             00:34    0.00s  0.26s  0.00s w

```

That shows that t0p (me) is doing stuff via gnome (ie using Firefox), another instance of t0p (me) is running wget in a terminal, and yet another instance of t0p (me) is running the **w** command.  I know this activity is all mine, so I'm happy.  If stuff appeared that I *didn't* know about, I'd be a tad concerned.

If you reckon someone is accessing your machine from the outside, disable all services you don't need (eg if you don't *need* a ssh server running on your box, get rid of it); and don't use the default ports for services.  Also, use protection.  WPA2 is pretty good.  It's unlikely (though theoretically possible) that someone could crack it.  There's other stuff too, but I'd have to write an indepth security tutorial to explain all the ins and outs!  Use Google to find out about security.  There's a link in my sig to a tut on how to use search engines more effectively.

---

### Post by zcacogp on 2010-06-23
t0p, 

Now that is a very helpful command - thanks. 

Question is whether, if it happens again, I will be able to remember 'w' as being the command to use! I guess I ought to. 

WPA2 - OK, thanks. I'll look into it. Is it more secure than MAC address security - which I currently use? (I quite like MAC security as it gives much faster network speeds and is easy to administer; the network owner can remove a MAC address from the list of permitted machines very easily.) 


Oli.

---

### Post by cryptotheslow on 2010-06-23
WPA2 is the encryption used for traffic on your wireless LAN. It is the only vaguely secure method available on most consumer grade routers. Using WPA2 should not slow throughput on the WLAN.

MAC address security is absolutely useless. A 12 year old with access to Google could learn to capture current MAC addresses on your WLAN and how to spoof them from their own machine - all with easily downloadable and easy to use software.

Likewise using the option to hide your SSID is absolutely useless as a security technique. Even the manufacturer's driver suite for my Dell laptop wireless card gives me an option to "show hidden networks".


As you are in the UK I'm going to make a huge assumption that you are using an ADSL connection with an ISP provided router. Make sure that you have setup / changed the password to the Admin interface of that router. Under no circumstances leave it as a blank password or "admin". There are known cross site vulnerability issues due to this - which can mean you visit an innocent looking site on the internet - which unknown to you runs code that changes settings on your router by passing the known/default password. Typically this would be to open the "remote assistance" facility which then allows the attacker to change whatever other settings they like to allow themselves full access to you LAN.

As for uPNP - turn it off on the router unless you really need it. On lower spec routers uPNP will trust any request coming from the LAN to open ports to the internet (again a cleverly crafted webpage could do this). On slightly better ones you have the option to only allow specific applications / port ranges to be uPNP'd - so if you have the option and you really must use it remove every other application or port range from the router's list.

Personally, I switch it off completely on the router and define static port forwards then configure the relevant applications to use those as required. Admittedly not quite as convenient as allowing any application to open up the ports it wants as it likes, but far safer (in my mind at least!).

---

