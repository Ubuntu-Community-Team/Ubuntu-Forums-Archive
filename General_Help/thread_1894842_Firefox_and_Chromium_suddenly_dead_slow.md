---
title: "Firefox and Chromium suddenly dead slow"
date: 2011-12-13
forum: General Help
---

### Post by AVH on 2011-12-13
About four days ago Firefox started taking up to 30 seconds to load pages. Sometimes it seems to freeze up and occasionally greys out before finally loading. 

Chromium is running as slow as FF.
 
The Internet itself is running fine.  Internet  speed tests in FF come out fine (2 -4 Mbs), even though it takes forever to load the site. 

I checked the DNS servers, they are the right ones for my ISP. I even changed to the OpenDNS servers as a check, with no improvement.

 Any Ideas anyone?

10.04 LTS,  64 bit

---

### Post by oldtimer7777 on 2011-12-13
I had the same problem, and then I ran bleachbit to clean out the browsers, and now they are as fast as when I first installed them:

sudo apt-get install bleachbit
gksu bleachbit

> **AVH said:**
> About four days ago Firefox started taking up to 30 seconds to load pages. Sometimes it seems to freeze up and occasionally greys out before finally loading. 

Chromium is running as slow as FF.
 
The Internet itself is running fine.  Internet  speed tests in FF come out fine (2 -4 Mbs), even though it takes forever to load the site. 

I checked the DNS servers, they are the right ones for my ISP. I even changed to the OpenDNS servers as a check, with no improvement.

 Any Ideas anyone?

10.04 LTS,  64 bit

---

### Post by TeoBigusGeekus on 2011-12-13
> gksu bleachbit
This will only clean things accessed by the root account (or using sudo).
Run 
```
bleachbit
```
to get rid of stuff from your normal user account.

---

### Post by AVH on 2011-12-13
Meanwhile back at the ranch....

 I have run Bleachbit  as root , as user,  from the GUI and from the Terminal. It didn't seem to remove very much and in any case has had zero effect on either FF or Chromium. Both are still unusably slow.

And my help thread seems to have been hijacked by an argument.

But, Thanks

---

### Post by DeMus on 2011-12-13
> **AVH said:**
> About four days ago Firefox started taking up to 30 seconds to load pages. Sometimes it seems to freeze up and occasionally greys out before finally loading. 

Chromium is running as slow as FF.
 
The Internet itself is running fine.  Internet  speed tests in FF come out fine (2 -4 Mbs), even though it takes forever to load the site. 

I checked the DNS servers, they are the right ones for my ISP. I even changed to the OpenDNS servers as a check, with no improvement.

 Any Ideas anyone?

10.04 LTS,  64 bit

When you want to load a page what do you see in Chromium? What I mean is what do you see on the tab you are currently in? When you start loading a page a line is rotating in a dark color CCW until it has found the page, then it rotates CW in bright color.
What is the line doing most of the time, rotating CCW or CW?

If it is the first then the page can't be found. Chromium, and also Firefox, is looking for the IP address to locate the webpage.
Did you do something with Samba just before this happened? Did you start using it, or did you change something in the /etc/samba/smb.conf file?
If you did open it again and look for the line that looks like this:
**name resolve order = lmhosts bcast wins host**
It's almost on top in the Global stanza.
I don't say the order in which I have the items listed is the right one, I am still trying to figure out what is the right order, but anyway this works for me. Have a look and if the order is different in your file, try my line. After saving you need to either restart Samba or re-boot to make it work.
Success.

---

### Post by howefield on 2011-12-13
Thread cleaned a bit, and please keep the petty insults out of the thread.

---

### Post by TeoBigusGeekus on 2011-12-13
Try this from command line as well
```
time wget "ubuntuforums.org"
```
In my system, it gives
```
real    0m0.721s
user    0m0.003s
sys     0m0.007s
```
Post us your times.

---

### Post by AVH on 2011-12-13
The little rotating progress indicator in the tab always rotates clockwise. At the bottom of the page a little window indicates that Chromium is sending requests and waiting for replies. It doesn't have any trouble locating the pages, it is just terribly slow in loading them. Same for FF.

My samba.conf hasn't really changed in years. My line reads "name resolve order = hosts wins bcast" and has been the same since Jaunty I think.

---

### Post by AVH on 2011-12-13
> **TeoBigusGeekus said:**
> Try this from command line as well
```
time wget "ubuntuforums.org"
```In my system, it gives
```
real    0m0.721s
user    0m0.003s
sys     0m0.007s
```Post us your times.

My results are:
```
alan@NewBlueU:~$ time wget "ubuntuforums.org"
--2011-12-13 16:26:50--  http://ubuntuforums.org/
Resolving ubuntuforums.org... 91.189.94.12
Connecting to ubuntuforums.org|91.189.94.12|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.6'

    [   <=>                                 ] 34,937      62.8K/s   in 0.5s    

2011-12-13 16:26:51 (62.8 KB/s) - `index.html.6' saved [34937]


real    0m1.790s
user    0m0.000s
sys    0m0.010s
alan@NewBlueU:~$ 

```

---

### Post by TeoBigusGeekus on 2011-12-13
> **AVH said:**
> The little rotating progress indicator in the tab always rotates clockwise. At the bottom of the page a little window indicates that Chromium is sending requests and waiting for replies. It doesn't have any trouble locating the pages, it is just terribly slow in loading them. Same for FF.

My samba.conf hasn't really changed in years. My line reads "name resolve order = hosts wins bcast" and has been the same since Jaunty I think.

Just an idea: do you use a router with wireless capability that you have recently reset and forgot to add security (wpa) to it? Someone could be stealing your connection...

---

### Post by TeoBigusGeekus on 2011-12-13
> **AVH said:**
> My results are:
```
alan@NewBlueU:~$ time wget "ubuntuforums.org"
--2011-12-13 16:26:50--  http://ubuntuforums.org/
Resolving ubuntuforums.org... 91.189.94.12
Connecting to ubuntuforums.org|91.189.94.12|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.6'

    [   <=>                                 ] 34,937      62.8K/s   in 0.5s    

2011-12-13 16:26:51 (62.8 KB/s) - `index.html.6' saved [34937]


real    0m1.790s
user    0m0.000s
sys    0m0.010s
alan@NewBlueU:~$ 

```

It's not that bad...
Try running bleachbit and checking the cache, cookies, etc. boxes under firefox and chromium.

---

### Post by AVH on 2011-12-13
Wireless is locked down tight. Encryption, password and mac#.

---

### Post by TeoBigusGeekus on 2011-12-13
...and bleachbit?

---

### Post by AVH on 2011-12-13
> **TeoBigusGeekus said:**
> It's not that bad...
Try running bleachbit and checking the cache, cookies, etc. boxes under firefox and chromium.

I ran Bleachbit with everything checked except the ones which would wipe out my bookmarks and passwords. It said it removed a bunch of stuff. But when I checked, my history, cookies, etc were all still there. There was a message about several "file is encrypted or is not a database" that it didn't remove.

---

### Post by tartalo on 2011-12-13
> **AVH said:**
> I ran Bleachbit with everything checked except the ones which would wipe out my bookmarks and passwords. It said it removed a bunch of stuff. But when I checked, my history, cookies, etc were all still there. There was a message about several "file is encrypted or is not a database" that it didn't remove.

In Firefox: History -> Clear recent history (Or simmilar, I'm translating from a non-English version)

---

### Post by TeoBigusGeekus on 2011-12-13
Is your home folder encrypted?
Anyway, try this:
Go to ~/.config and cut the chromium folder. Paste it somewhere.
Next, go to ~/.cache and again cut the chromium folder and put it in some place (not the same as the one in the .config folder as they have the same name).
These 2 folders hold all of chromium's settings and cache.
Now try to run chromium with these folders removed; is there a change in speed?

---

### Post by AVH on 2011-12-13
No change. It took 13 seconds to load the getting started tab, over 15 to get to another web site.

---

### Post by TeoBigusGeekus on 2011-12-13
> **AVH said:**
> No change. It took 13 seconds to load the getting started tab, over 15 to get to another web site.

Then put the folders back to where they belong; the problem is not Firefox/Chromium related.
Boot up with a live cd/usb and check the internet speed: if the problem persists you should contact your ISP; if not, I don't know what to say...

---

### Post by AVH on 2011-12-13
Thanks for the effort It may be time for a clean install.

---

### Post by TeoBigusGeekus on 2011-12-13
Not necessarily.
If you get normal speeds with a live cd, it means that a setting somewhere in your home folder is the culprit.
You could then add another user in your system, migrate important settings from your old home folder (settings that have nothing to do with internet of course) and then delete your old home folder.
We could do it together if you want.

---

### Post by deserthowler on 2011-12-13
I had a similar problem on my system.  Things were just timing out but at the same time I could do downloads at respectable rate.  Tried FF and Chromium.  I was running 4 computers on 10.04.  They were all bad.  First I though it was a bad update.

I then tested with friends Macs and Windows boxes.  They had the same problem.  I took one of my laptops to the public library and had no problems.  Had the cable company come out and check the lines which are old.  They replaced the lines but no luck.  Sometimes it worked but most of the time it didn't.

Went back to the library and checked again.  Worked fine.

Checked between a couple of computers and found they connected OK so I decided the router was OK.  Tried plugging into the modem and problems.  I replaced the modem. That fixed the problem.  Apparently the uplink part of the circuitry was bad although the downlink was good.

Earl

---

### Post by AVH on 2011-12-14
My network passes all the tests I throw at it. Other Ubutnu and Windows installations on the network all work fine. It is just the Ubuntu on this machine that troublesome. The Win7 partition works fine.

---

### Post by TeoBigusGeekus on 2011-12-14
Create a new user, add him to sudoers, migrate any settings from your old home folder to the new one, delete the old home folder and you're done.

---

### Post by AVH on 2011-12-14
Ahh, the joy of having /home on a separate partition! Why isn't that default?

 Since the source of the problem was so hard to identify, I decided to go after it with a shotgun.  I re-installed 10.04 LTS 

Everything is back to normal, even after installing all the updates, add-ons, plug-ins, etc. Rhythmbox even works again, although, as usual, it totally screwed up importing from my windows partition. I guess I'll never trace that seg fault now.

Thanks to Teobigusgeekus for all your time.

---

