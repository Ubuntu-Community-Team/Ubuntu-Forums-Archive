---
title: "Router Problem: Multiple IP Addresses???"
date: 2010-06-17
forum: General Help
---

### Post by RoboticRickJames747 on 2010-06-17
Recently I bought a new Belkin wireless G router for my house. After buying a new laptop (since my past one became a catrosphic failure and emptied my wallet again), I was able to sacrifice this week's groceries for a router. Anyways... I set it up and my internet was going fast and strong.  After setting it up, I then took a shower came back and I began to notice my blazingly fast internet was now travelling at the speed of smell. So... I went to evaluate the issue, looked to see my connection and noticed that I had 15 different IP addresses in the list... 
 
I know that from past research, there can be multiple iexploxer.exe running in the background when the computer is running b/c of different tabs being open, as well as svchost.exe, etc... 
 
Could the multiple IP's be something similar to that? Could the IP's be different connection's I have with the Belkin company for fast and easy troubleshooting? Could the IP's be from viruses or malware? 
 
Help me Ubuntu forums, I already lost out on 2 weeks of food because of my laptop, I dont want to have to do another week because of this! :( ](*,)](*,)

---

### Post by RoboticRickJames747 on 2010-06-17
The number of IPs now is 19. 
 
Any suggestions/help would be factinating... it took me 23 minutes to load 1/2 of the Karma Chameleon ~ Boy George music video off of Youtube. :( ./cry

---

### Post by RoboticRickJames747 on 2010-06-18
/bump
 
I just came home, and it seems like my connection is a little better. I checked the number of IP addresses, and there are currently 9 on it at the moment. 8-) Anyone else have/had a Belkin router like mine and had the same issues?

---

### Post by dcstar on 2010-06-18
> **RoboticRickJames747 said:**
> The number of IPs now is 19. 
 

If you have 19 IP addresses used by your Router then you probably have 18 other people leeching off your Internet connection - no wonder it is slow.

Do a web search to learn how to secure your wireless network.

This is not an Ubuntu problem.

---

### Post by marshmallow1304 on 2010-06-18
Are these on the router's status pages?  If so, you are most likely providing a connection for your neighbors.  If you don't want to do so, you'll need to set up encryption.  On the router config page, check for a section like "Security" or "Wireless Security".  Check the router's manual if necessary.

---

### Post by Spr0k3t on 2010-06-18
Color me confused on this one.  Exactly which list are you referring to?

Unless you have physically assigned a network adaptor to have specific IP addresses locally on the computer system... if the connection is set up via DHCP you should only be able to see a single IP address on the adapter.  To verify this, post the output of what you get back:

```
ifconfig
```

In some cases like this, post a screen shot of this list so others can get and idea of how to help troubleshoot.

---

### Post by RoboticRickJames747 on 2010-06-19
>     If you have 19 IP addresses used by your Router then you probably have 18 other people leeching off your Internet connection - no wonder it is slow. 
  The closest neighbor I have lives 3 miles away.

> 
Do a web search to learn how to secure your wireless network.
This is not an Ubuntu problem.
I have searched this situation up on their forums, and they came up with the same conclusion as you posted originally. I responded with what I wrote above, and received no response afterward. So I have come to Ubuntu to ask for constructive advice and thoughts on this topic. I have seen several other people post questions on non-Ubuntu related topics, and people have given them useful tips in fixing their solution. Sadly, out of the 3 posters I have, only 2 offered insightful ideas/information to this topic...

> Are these on the router's status pages?Yes, these on the the status pages, but like I said earlier the closest neighbor I have lives 3 miles away. I failed to mention earlier that I have a old desktop, but that is running through a wired connection (DSL/Cable), not wireless... Is it possible that people can detect my router from that far of a distance? b/c I thought that would be one heck of a broadcasting range. Could my desktop actually be interfering with the connection, even though it is wired to the Internet? Is this a possible form of troubleshooting from the router company? I'm so confused. :(

> ifconfigI'm unsure of what your asking, am I suppose to run this in "Search"? :?

>  In some cases like this, post a screen shot of this list so others can get and idea of how to  help troubleshoot. I am unsure of how to post a screenshot, let alone take a screenshot (outside of taking one via Runescape). I have a old digital camera, if I took a picture via with that, would that suffice?

---

### Post by Spr0k3t on 2010-06-20
follow these steps exactly... but read the post before proceeding.

1. Close out of everything leaving the computer running at the Ubuntu desktop and logged in.
2. Press *ALT-F2*
3. In the "Run Application" dialog box that comes up, type *gnome-terminal*
4. Click Run.
5. type *ifconfig* and hit enter.

You will see something that looks similar to this:
```
eth0      Link encap:Ethernet  HWaddr 08:5f:32:1a:f5:c6  
          inet addr:10.0.0.15  Bcast:10.0.0.255  Mask:255.0.0.0
          inet6 addr: fe80::a00:27ff:febc:5fa2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35095 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23847 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27666210 (27.6 MB)  TX bytes:1350360 (1.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
```

However, this information is not irrelavent since you have stated the list you are looking at is from the router, not the computer.  Albeit, the information would be good for you to hang on to in case someone asks for information relating to data from a terminal.

To take a screenshot, you just need to go to Applications -> Accessories -> Take Screenshot.  Another option is to hit the "PrtScn" button on the keyboard.  The app will ask you how and where to save the file so you can upload your results here.  To post a screenshot, you have to first start a "New Reply" or "Go Advanced" and then below your composition will be a section titled "Additional Options".  Click on the button labeled "Manage Attachments".  From there, find where you saved the screenshot by clicking "Browse" followed by clicking "Upload".  Once the upload has completed, you can then close the popup window.

What I would do.  Remove any connection with the exception of the one computer you are trying to figure out.  Monitor the speed of your connection by utilizing a single site (speedtest.net, with flash, and testmy.net, without flash, are the ones I use) at varying times of the day.

Just an FYI, the longest recorded wireless connection over P2P is close to 240 miles using modified off-the-shelf equipment.  So with the right equipment and know-how, 3 miles is nothing by comparison.

I hope this information helps.

---

### Post by RoboticRickJames747 on 2010-06-22
This helped out very much, thank you!
 
I was able to enter in the ifconfig command and it did prompt up something similar to that, but it only showed one IP (which I assumed that it was mine, since the other desktop is off). But when I looked at the router status page there is 14 other IPs.
 
So would this still have the posibility of other people accessing my internet or would you believe that there is something going on in the background? 
 
As for the screenshot, I got it to work, but it just shows a picture of my detailed "Rick James wrestling a pack of thirteen hungry hyennas" desktop wallpaper. :/ 
 
I tried to call the company and they said that I need to call in a technician... As stated before, I have a limited income, and I was graced to buy groceries this week... but it would be devastating too be forced to survive for 2 weeks on 4 days worth of food if I now need to pay the technician his fee... :(

---

### Post by akakingess on 2010-06-22
I believe that he meant to take a screenshot of the screen when you are looking at the status list from your router. So, launch a browser and connect to the router (usually 192.168.1.1) and view the status list and then take the screenshot.

---

