---
title: "How to install netspeed ?"
date: 2012-01-05
forum: General Help
---

### Post by meetdilip on 2012-01-05
On latest Ubuntu. How to install this ?

[https://launchpad.net/ubuntu/+source/netspeed/0.16-2](https://launchpad.net/ubuntu/+source/netspeed/0.16-2)

Any better options available ? I am using a limited data plan.

---

### Post by sj1410 on 2012-01-05
sudo apt-get install netspeed

---

### Post by meetdilip on 2012-01-05
I am updating Ubuntu and it shows this window now. Shall I proceed with above command ?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210282&stc=1&d=1325763075[/IMG]

---

### Post by crazy bird on 2012-01-05
You don't need to add any PPA for netpeed. It is standard available in the repositories. Open Synaptic and do a search on netspeed. Mark the package for installation and press on Apply. 
 
Netspeed is a tool which needs to be placed on the task bar.

---

### Post by meetdilip on 2012-01-05
I executed the command. It shows like this now. How to find the data consumed, current upload and download speed ? 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210283&stc=1&d=1325764492[/IMG]

Thanks

---

### Post by meetdilip on 2012-01-05
> **crazy bird said:**
> You don't need to add any PPA for netpeed. It is standard available in the repositories. Open Synaptic and do a search on netspeed. Mark the package for installation and press on Apply. 

Where to find Synaptic ? 
 
> **crazy bird said:**
> Netspeed is a tool which needs to be placed on the task bar.

Can you tell me how to do it ?

---

### Post by sj1410 on 2012-01-05
[http://www.ubuntugeek.com/netspeed-traffic-monitor-applet-for-gnome.html](http://www.ubuntugeek.com/netspeed-traffic-monitor-applet-for-gnome.html)

---

### Post by meetdilip on 2012-01-05
When I right click (or even left click) on the free area above the screen (the white bar), nothing happens. :(

---

### Post by crazy bird on 2012-01-05
> **sj1410 said:**
> [[FONT=Arial][SIZE=2]http://www.ubuntugeek.com/netspeed-traffic-monitor-applet-for-gnome.html[/SIZE][/FONT]]("http://www.ubuntugeek.com/netspeed-traffic-monitor-applet-for-gnome.html")
 [FONT=Arial][SIZE=2]This is for Ubuntu version up to 10.10. Not very usefull for Ubuntu 11.10 (OP mentioned that he uses the latest version).[/SIZE][/FONT]

**[FONT=Arial][SIZE=2][/SIZE][/FONT]** 
**[FONT=Arial][SIZE=2][/SIZE][/FONT]** 
**[FONT=Arial][SIZE=2]@meetdilip:[/SIZE][/FONT]**
[FONT=Arial][SIZE=2]With the withe bar, do you mean the task bar next to the system tray??[/SIZE][/FONT]

[FONT=Arial][SIZE=2]It looks like synaptic is not installed by default which is a shame since synaptic is a better tool then software center to install programs. You can install it using the terminal:[/SIZE][/FONT]
[FONT=Arial][SIZE=2]> sudo apt-get install synaptic[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Then go to Dash and search for synaptic.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]See also: [Synaptic - How to]("https://help.ubuntu.com/community/SynapticHowto").[/SIZE][/FONT]

---

### Post by meetdilip on 2012-01-05
It seems the terminal mode install worked. This is how it shows now. Can you please tell me how to add to task bar (yes, similar to the one in Windows but on top left to clock and empathy).

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210284&stc=1&d=1325769339[/IMG]

PS : I install Synaptic through steps mentioned by Crazy Bird. Thanks.

---

### Post by crazy bird on 2012-01-05
[SIZE=3][FONT=Calibri]Normally it&#8217;s right click on the task bar elect add to panel and then you get a pop-up windows with all the applications you can add on the taskbar. Scroll down until you see netspeed and click on **Add**.[/FONT][/SIZE]

---

### Post by meetdilip on 2012-01-05
Yes, I had 10.10 for a small bit of time where you helped me. But it was 32 bit so I had to put 64 bit. Both right click and left click is giving no option in this case. I even tried a different workspace. Do update if you find a way to fix this. 

PS : The link in your signature is very useful. Bookmarked, will read and try to learn things. Your site ? Good work :)

---

### Post by crazy bird on 2012-01-05
> **meetdilip said:**
> Both right click and left click is giving no option in this case. I even tried a different workspace. Do update if you find a way to fix this. 
Strange, normally it should work... But since i'm still using 10.04 LTS version i don't know how to fix this honestly.
 
> PS : The link in your signature is very useful. Bookmarked, will read and try to learn things. Your site ? Good work :)
Yes, it's my site and thank you!

---

### Post by ajgreeny on 2012-01-06
I don't think you can add applets and shortcuts to the panel of 11.10 as you could with previous versions of Ubuntu, though you could try **Alt+Rt Click**, but I believe that is only for the **gnome-session-fallback** desktop.  I may be wrong as I don't use ubuntu 11.10;  all that lack of configuration was one reason why I gave up on both unity and gnome-shell.

---

### Post by meetdilip on 2012-01-07
Thanks ajgreeny. tired " **Alt+Rt Click ", **not working. :(

If I use 

> sudo apt-get install gnome-session-fallbackand go back to classic desktop, is it permanent ? Can I get back to Unity if I do not want classic look ?

---

### Post by pretty_whistle on 2012-01-07
> **meetdilip said:**
> Thanks ajgreeny. tired " **Alt+Rt Click ", **not working. :(

If I use 

and go back to classic desktop, is it permanent ? Can I get back to Unity if I do not want classic look ?
Yeah you can go back to unity.

---

### Post by wildmanne39 on 2012-01-07
Hi, this link should allow you to do it in 11.04 and 11.10 unity.
[http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html](http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html)
Thanks

---

