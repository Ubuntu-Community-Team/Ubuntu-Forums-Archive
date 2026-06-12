---
title: "Internet and email problems"
date: 2009-12-20
forum: General Help
---

### Post by Steptoenson on 2009-12-20
Hi all,
 
I have experiencing internet and email problems for a little while now. I can access some sites using firefox, but not ebay at all; I can't send messages via madasafish webmail, and certain other sites, if they allow me onto the site, won't go to certain links or perform certain tasks. I was also unable to send any posts to this forum from my laptop, which is why I am using my wife's. Hers runs on windows vista and all the above problems are okay on hers. I am also unable to send any emails via evolution mail, but I can receive them. The computer seems to be simply waiting...ie. 'waiting for ebay.co.uk' or similar, without ever advancing.
I decided to upgrade from 8.04 LTS to 8.10 to see if that would cure the problem, to no avail. I am not technically knowledgeable, so therefore do not intefer with the running of the computer or make any changes. I did have a brief look for similar problems already posted on the forum, but the replies confused me.
Can anyone help or offer advice, ideally in idiot-proof instructions, please?
Eventually the computer times out. I did try reporting it as a problem via one of the pull down menus. It tried to gather  information, but failed, posting the following error message;
Network Problem. Couldn't upload report data to crash database. HTTP Error 500: Internal Server Error.
 
Thank you in advance of your assistance in this matter.
 
Richard  :)

---

### Post by koepked on 2009-12-20
It sounds like there's a problem with your connection. Are you using wireless or wired? Is the Ubuntu computer using the same router as the Vista computer? I know you stated that you are not technical, but do you know the IP address of your router? There's a good chance that it is 192.168.1.xxx, but it may not be. If you can figure that out, the first step is to go to the terminal and at the prompt, type: 
 $ ping 192.168.1.xxx

Replace the numbers above with your router's IP address. After a few seconds, press Ctrl-C to stop the ping program. You should see lines that look like this:

```
64 bytes from mango (192.168.1.1): icmp_seq=0 ttl=255 time=0.5 ms
64 bytes from mango (192.168.1.1): icmp_seq=1 ttl=255 time=0.3 ms
64 bytes from mango (192.168.1.1): icmp_seq=2 ttl=255 time=0.3 ms

``` 

If you don't see lines like above, you're not connected to your router.

I know you said firefox allows you to go to some sites, but my guess is that you're not actually going to them. Web browsers do something called caching, which is storing a copy of a website on your local computer so that you can still see the info if you lose your network connection.

---

### Post by Steptoenson on 2009-12-20
Hi,
 
Thanks for prompt response and advice.
My IP address seems to be 192.168.1.4
I entered the text you said at a terminal and the lines that appeared were very similar to the ones you mentioned.
My laptop is not wireless. I connect to the router via an ethernet cable. I don't think it has wireless capability/software.
The inforamtion on the web sites I can get on seems to be up-to-date as opposed to remembered info from a previous visit. So I think I am accessing some sites.
Anything else I could try or it could be?
Thanks again,
 
Richard

---

### Post by koepked on 2009-12-20
Sorry, I can't explain what you are experiencing, I've never seen anything like that! Hopefully someone else can jump in here...

---

### Post by Lukas666 on 2009-12-20
> **Steptoenson said:**
> Hi,
 
Thanks for prompt response and advice.
My IP address seems to be 192.168.1.4
I entered the text you said at a terminal and the lines that appeared were very similar to the ones you mentioned.
My laptop is not wireless. I connect to the router via an ethernet cable. I don't think it has wireless capability/software.
The inforamtion on the web sites I can get on seems to be up-to-date as opposed to remembered info from a previous visit. So I think I am accessing some sites.
Anything else I could try or it could be?
Thanks again,
 
Richard

How is pinging remote sites??

ping [www.google.com]("http://www.google.com")
ping [www.cnn.com]("http://www.cnn.com")
etc.

I would also try a Live CD version and check network from there. Maybe it's a hardware problem?

---

### Post by dcstar on 2009-12-20
> **Lukas666 said:**
> 
........
I would also try a Live CD version and check network from there. Maybe it's a hardware problem?

Yep, bad network cable/port, bad card/motherboard etc etc. A live CD test will show this because if it does not work correctly, then it is the hardware.

---

