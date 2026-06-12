---
title: "Remote Desktop all of a sudden stopped working"
date: 2010-05-31
forum: General Help
---

### Post by Axilus on 2010-05-31
Hey guys,

I recently setup an ssh tunnel and wrote a script to connect to my Home PC from my laptop no matter where I am.

I have previously tested this on my own network and multiple other networks while I was over at my friends houses, and it worked completely fine.

So just now I decided to use it after about a day or two after not using it and now nothing happens. Normally it prompts me for a password and takes about 5 seconds then I am in.

I'm using openssh, vinagre, and dyndns for the hostname. Here is the script:
```
#!/bin/sh

ssh -f -L 5900:localhost:5900 axilus.ath.cx \
	x11vnc -safer -localhost -nopw -once -display :0 \
	&& sleep 5 \
	&& vinagre localhost:5900
```

Any suggestions?

---

### Post by krunge on 2010-05-31
Can you ssh in?

---

### Post by Axilus on 2010-05-31
No I get this message:
ssh: connect to host 199.172.197.22 port 22: Connection timed out

I have however already forwarded both port 5900 and 22 with the IP 192.168.1.101 when I set it up the first time.

---

### Post by krunge on 2010-06-01
> **Axilus said:**
> No I get this message:
ssh: connect to host 199.172.197.22 port 22: Connection timed out

That is your problem then, you can't ssh to the machine.  The problem has nothing to do with remote desktop.
> 
I have however already forwarded both port 5900 and 22 with the IP 192.168.1.101 when I set it up the first time.
Why would you forward port 22 through ssh?

Or are you talking about router port forwarding?  From what you say it sounds like you might have some problem with that.

---

### Post by Axilus on 2010-06-01
> **krunge said:**
> Why would you forward port 22 through ssh?

Or are you talking about router port forwarding?  From what you say it sounds like you might have some problem with that.

Yes I was instructed in [the tutorial]("https://help.ubuntu.com/community/VNC") to do it, and after following that and making the script it worked fine. Now I get the previous mentioned message.

I went back into my router and the ports 5900 and 22 are still forwarded to 192.168.1.101 and are enabled.

---

### Post by krunge on 2010-06-01
> **Axilus said:**
> 
I went back into my router and the ports 5900 and 22 are still forwarded to 192.168.1.101 and are enabled.
You haven't said, but I assume 192.168.1.101 is the private IP of your workstation, correct?  Does it still have that IP?

You should **not** have your router forward port 5900. You have port 5900 going **through** the ssh tunnel. Redirecting 5900 is not needed and is insecure. The guide you reference says this too.  

I think you should remove the port 5900 from your router ASAP.  You are probably being port scanned on it 10-20 times per day.  If you had a VNC server running their w/o passwd (e.g. x11vnc without "-localhost") then they would control your desktop.

I don't know what do to about your not being able to ssh in. You have something else misconfigured.  Perhaps DNS, or a host-level firewall on 192.168.1.101, etc.

When troubleshooting, run ssh with "-v" for verbose logging. Also examine the access logs on your router (if available) and on your workstation. AFAICS you are not able to even reach the ssh server on the workstation.

---

### Post by Axilus on 2010-06-01
My private IP has in fact changed from *.*.*.101 to *.*.*.100; Changing that in my router has fixed the problem. Is there anyway to stop it from doing that, or to allow my router to automatically detect the change?

I also removed the fowarding with 5900 in my router, and is it safe to still have the port 22 forwarded in there? I'm not really a networking guy, but can you please explain why it is insecure?

Thanks for your help :D

---

### Post by BoneKracker on 2010-06-01
You can do one of two things:

a) use a fixed IP address on the sshd machine

b) if your router supports it, configure dhcp to always issue the same IP address to that machine

There are other things you can do (e.g., dynamic firewall rules, ipsets, etc.), but they are absurdly complicated compared to those.

---

### Post by Axilus on 2010-06-01
How would I go about doing one of those?

---

### Post by MrDiaz on 2010-06-01
> **Axilus said:**
> How would I go about doing one of those?

Preferences -> Network Connections -> Ethernet -> Edit -> IPv4 settings -> Manual configuration.

Set the new IP Address you want to use. Use as gateway your router's IP.

---

### Post by Axilus on 2010-06-01
I got it to work for about 5 seconds then it suddenly stopped loading webpages while I was browsing.

---

### Post by krunge on 2010-06-01
> **Axilus said:**
> My private IP has in fact changed from *.*.*.101 to *.*.*.100; Changing that in my router has fixed the problem. Is there anyway to stop it from doing that, or to allow my router to automatically detect the change?

I don't know, I always use static IP's for internal machines.
> 
I also removed the fowarding with 5900 in my router, and is it safe to still have the port 22 forwarded in there? I'm not really a networking guy, but can you please explain why it is insecure?

You can leave 22 for SSH access.  That is fine because it is encrypted and you have a good unix password.  OTOH, most people I know play it safe and redirect a high random port on their router, say 25752 to 22 (SSH service) on the internal workstation.  Then they access via:
```
ssh -p 25752 myuser@myip.net
``` (or set the port in ~/.ssh/config) This way you are much less likely to get a portscan revealing your SSH login service.

If you redirect port 5900 on your router to VNC port 5900 on the workstation first realize that if you connect via that channel the VNC session is (in nearly all cases, see below) unencrypted.  So anyone on the internet could sniff the VNC password and then later obtain access to your workstation.

The nice thing about your ssh tunnel is first they would have to break in via ssh before they could even access your vnc server.  Of course if they  are in via ssh that is bad enough and they probably don't care about vnc at that point. 

If you use something like "x11vnc -ssl" for SSL encryption to port 5900 then the encryption protects you (and presumably your VNC password is very good.)  When doing this I also suggest a "random" port, e.g. 5937, then you  specify VNC display "37" to the viewer to avoid portscanners from detecting the service.

---

### Post by krunge on 2010-06-01
> **Axilus said:**
> I got it to work for about 5 seconds then it suddenly stopped loading webpages while I was browsing.
When you ssh in to a shell, does the connection hang like this after a few seconds?

Just a guess, maybe you need the "-noxdamage" option to x11vnc.  The Xorg server has an XDAMAGE bug that stops sending update messages to x11vnc.  Search these forums for "x11vnc noxdamage" for more info.

---

### Post by Axilus on 2010-06-14
The script is working fine now. I just need instruction on keeping my PC on the same IP.

I'm using a WRT54G linksys, and I got it working with a defined IP address 198.162.1.7 for about 5 seconds of browsing then it simply stopped working.

---

### Post by NCLI on 2010-06-14
> **Axilus said:**
> The script is working fine now. I just need instruction on keeping my PC on the same IP.

I'm using a WRT54G linksys, and I got it working with a defined IP address 198.162.1.7 for about 5 seconds of browsing then it simply stopped working.

I'd install DD-WRT on that router, then it's easy :D

---

### Post by Axilus on 2010-06-14
Truesay, thank you.

---

