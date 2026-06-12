---
title: "DNS \ Gateway Problems"
date: 2006-05-30
forum: General Help
---

### Post by deejross on 2006-05-30
I have a very strange problem with my linux box. Whenever the server sends an email via a php script, or when you try to go to a webpage, there is about a 20-30 second delay where the machine sits idle before sending the email or opening the webpage. Connecting with IP addresses works fine, so I would have to assume there is a DNS problem.

Here is my configuration (I use Webmin to set this up):
Machine is behind a modem/router that has an internal IP of 192.168.1.254.
Linux box has a static IP of 192.168.1.100 and I set the gateway to be the IP of the router.
I tried manually setting the DNS server to IP addresses of my ISP's DNS servers, which fixes the problem, but 10 minutes later, the DNS changes itself back to the router's IP address.

Anyone have any thoughts?

---

### Post by stenka on 2006-05-30
It must deal with the DHCP settings of your router.
What model is it ?
Check, if you can, that it gets correctly the DNS of your ISP and that no static DNS is set to your LAN. Just leave it empty.

---

### Post by deejross on 2006-05-30
I read the documentation on the router. It says to leave the DNS set to 0.0.0.0, and that is what it is set to now. The Windows servers were manually setup for the ISP's DNS, so why can't linux do it?

---

### Post by AirRaven on 2006-05-30
[This thread](http://www.ubuntuforums.org/showthread.php?t=181171) might help you.

I had the same problem. The solution suggested at the end of the thread seems to have fixed it- at least most of the time.

I'm still having major pageloading problems in Firefox occasionally, but all in all it's far better than it was before.

---

### Post by stenka on 2006-05-30
0.0.0.0 means default route, so I find the behaviour of Linux rather logical : it uses the gateway as DNS.
I don't know why it works on Windows, but I wouldn't be surprised they don't follow the standard and that your documentation consider you are a windows user by default.
You should set it with your ISP DNS, it is a clean network configuration which will work in all situations.

---

### Post by deejross on 2006-05-30
I think that might work. But we'll find out in a few hours if it resets itself again. Oh, and I figured that was the case with Windows. Not only is it a monolithic monstor of unoptimized code, but it does things it's own way and I don't think Bill himself knows why it does the things it does. This is the main reason for trying to swtch to linux :)

---

### Post by stenka on 2006-05-30
Yes, and specially their networking protocols are a big mess.

---

