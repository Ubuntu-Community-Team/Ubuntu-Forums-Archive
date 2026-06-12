---
title: "Can't load ebay and a few others"
date: 2011-11-29
forum: General Help
---

### Post by dianemeeks on 2011-11-29
I can no longer load ebay or a couple local media sites.  I'm at a loss.  Everything else loads fine, but these few I can't load in Firefox or Chrome. I'm running Maverick.  Suggestions or questions would be greatly appreciated.

---

### Post by wolfen69 on 2011-11-29
Try Opera web browser to see what happens and then we can go from there. [http://www.opera.com/download/](http://www.opera.com/download/)

---

### Post by dianemeeks on 2011-11-30
I tried Opera and got the same thing, after a long wait the standard "check the spelling of the address" message. Where to from here?

---

### Post by dianemeeks on 2011-11-30
I believe I have determined that it is my router that is the problem.  I realized my phone also can't access those sites, but only when using my router.  I had read about similar problems, but every solution or troubleshooting tip was using Windows.  If anyone has any suggestions, I'm willing to give it a try. Thanks!

---

### Post by frncz on 2011-11-30
I have the same problem, as if ebay was blocked by my ISP.
I tried on 3 computers, using firefox or chromium. ebay.co.uk or ebay.com cannot be found, nor ebay.fr for that matter.
Very strange. I'm using Virgin media as my ISP.
I really don't understand what is going on.

Have you found a solution?

---

### Post by dianemeeks on 2011-11-30
Unfortunately, I haven't found a permanent solution yet.  For the time being, I had to just use my desktop and disconnect the router.  I'm just keeping my fingers crossed that someone helps us out.

---

### Post by gordintoronto on 2011-11-30
If you right-click on the network icon and select "connection information," it should tell you the primary and secondary DNS being used. This is almost certainly where the problem lies. 

Tell us what it says with and without the router? And what is the brand and model of the router.

---

### Post by dianemeeks on 2011-12-01
The router is a Linksys WRT120N.  The DNS numbers without the router are:
Primary: 209.55.24.10
Secondary: 209.55.24.11

With the router:
Primary: 213.109.66.185
Secondary: 213.109.74.118

Thanks!

---

### Post by holycow131415 on 2011-12-01
Have you completely unplugged the router from an outlet for 30 seconds, then plugged it back in?

You should have your router set to dynamically get dns and ip if you dont have a static ip address from your isp. please check those settings by visiting [http://192.168.1.1](http://192.168.1.1) (default IP, you may have changed it).

Your router gui looks like this:
[http://ui.linksys.com/files/WRT120N/1.0.01/](http://ui.linksys.com/files/WRT120N/1.0.01/)

Static dns should be all 0's, and do auto dhcp from the drop down list.

---

### Post by dianemeeks on 2011-12-01
"please check those settings by visiting [http://192.168.1.1](http://192.168.1.1) (default IP, you may have changed it)."
I have tried unplugging it, but as for the above part, it asks for a user name and password, which I don't have.

---

### Post by holycow131415 on 2011-12-01
[http://www.routeripaddress.com/routers/1277/linksys-wrt120n_default_settings.html](http://www.routeripaddress.com/routers/1277/linksys-wrt120n_default_settings.html)

default username is left blank. password is "admin" with no quotes. if this doesnt work, you did change it some how, and if you dont know what you did, you need to reset the router to factory default by holding the reset button down until it starts blinking.

---

### Post by dianemeeks on 2011-12-01
I knew I hadn't changed anything, but it did not have zeros, as it should.  Changing them to zero, fixed the problem, but just out of curiosity, what could have triggered the change?  Is it just a fluke that happens sometimes?  It was fine until about a month ago.

Anyway, thanks!!!!!!!!!!!

---

### Post by gordintoronto on 2011-12-01
If you did not set an admin password, it's possible someone hacked into your router....

---

### Post by holycow131415 on 2011-12-02
It is a wireless router, i hope you put security on your ssid and that you change the default password.

---

### Post by dianemeeks on 2011-12-02
No I didn't because I thought they would have to be within the range of the router.  Do they not have to be in range?  I live in the middle of nowhere.

---

### Post by holycow131415 on 2011-12-02
I dont know how far away you are from anyone or a road, but i would prefer security over uncertainty. It takes less than 3 mins to set up.

---

### Post by dianemeeks on 2011-12-02
about 1/2 mile from a road, farther from houses, but I might give it a shot just to be safe.  Living this far out can give a false sense of security in a lot of ways.  I'll let this be a lesson. :)

---

