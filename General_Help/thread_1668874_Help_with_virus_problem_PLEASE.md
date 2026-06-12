---
title: "Help with virus problem PLEASE"
date: 2011-01-16
forum: General Help
---

### Post by Zacknafain on 2011-01-16
Ok - so this issue is REALLY kicking my *** 9 ways of sunday

My ISP has been telling me they are getting trojan activity in the form of automated spam from our end and sending me that irritating form e-mail
After a number of calls too support - they finally admit that this can happen without an email client - so the windows machine on our network was suddenly re-admitted as a suspect, a trojan was found and removed, several different av scanners used - definately clean.  all was good

then we get the form e-mail again.  Only at this point the windows computer has been entirely out of commission for over a week.

I'm stumped - firstly this is linux I am using not windows, secondly I have been running clamav - or thought I had ...  but here's the rub

It appears that clam AV was never actually COMPLETING a scan - it was still in progress, some 4 days later.
running it command line only had it scan currently running processes - for some reason no matter what I did it would not scan more than the currently running processes that way
I tried running it in 'safe mode' - set it up and let her rip - 2 days later I had to cancel it because I needed my computer back
I tried again through the root user with basically the same results.

So I went looking for an alternative av program.  a bit of hunting on the forums someone posted a list of companies that supposedly provided linux anti virus
CRAP
out of the list of about 15 companies they gave - about 12 only provided a remote scanner too scan linux servers for windows viruses
The few that did advertise a debian package - most of them didn't actually PROVIDE the advertised deb package.
leaving me with avast!

Which I was able too get the deb package for (currently sitting on my desktop) and able too get a registry key for through their website
and able to INSTALL the debian package for
all great right?
until I actually want to RUN it
the avast! engine returns an invalid argument
I've tried reinstalling, redownloading and so forth

I just want a virus scanner that will work this century that will stop this madness!!

---

### Post by sammiev on 2011-01-16
[BitDefender]("http://download.bitdefender.com/repos/#") can be setup in just mins. GL :)

---

### Post by jcolyn on 2011-01-16
Sounds like your email account has been hacked and is being used as a zombie server. Not uncommon. Change the password..or kill the email account and create a new one with a good password..

You're wasting your time scanning Linux for virus infection..ain't none there.............

---

### Post by 3rdalbum on 2011-01-16
If you are using a wifi network, someone might be connecting to your router and using your connection. Check the settings on your router; use only WPA (or even better, WPA2) for the encryption and set a nice long, non-obvious password.

---

### Post by moffa on 2011-01-16
> **3rdalbum said:**
> If you are using a wifi network, someone might be connecting to your router and using your connection. Check the settings on your router; use only WPA (or even better, WPA2) for the encryption and set a nice long, non-obvious password.

+1
Login to your router and check which wireless clients are connected.

---

### Post by HermanAB on 2011-01-17
OK, calm down and think about it for a bit first.

It is ***very*** unlikely that your Linux machine is sending out spam.  However, if you have been playing with VNC then it could be compromized.  

It is easy to check.  Stop everything that you are doing, then look at the network light - if it is blinking furiously, then your machine may very well be a spambot.

To make assurance doubly sure, install Wireshark or tcpdump and look at the activity on port 25 SMTP in ASCII form:
$ sudo tcpdump -i eth0 -A tcp port 25

If there is SPAM being sent, then you will immediately see it.

---

### Post by Zacknafain on 2011-01-17
> **sammiev said:**
> [BitDefender]("http://download.bitdefender.com/repos/#") can be setup in just mins. GL :)

I scoured bit defender - but couldn't find either a deb package or rpm package I could convert (not that I really know how too but I have alien and could work it out I am sure)

---

### Post by HermanAB on 2011-01-17
Hmm, antivirus on Linux is useless.  Run tcpdump and see whether you have problem.  If so fix it. If not, find a clueful ISP.

---

### Post by HermanAB on 2011-01-17
Hmm, antivirus on Linux is useless.  Run tcpdump and see whether you have problem.  If so fix it. If not, find a clueful ISP.

---

### Post by Zacknafain on 2011-01-17
> **jcolyn said:**
> Sounds like your email account has been hacked and is being used as a zombie server. Not uncommon. Change the password..or kill the email account and create a new one with a good password..

You're wasting your time scanning Linux for virus infection..ain't none there.............

Already done that - and if that was the case it would not be running through the ISP it would be yahell that would be bitching

Which is what stumped me entirely in the first place - my isp email is not accessable from my machine - they've blocked my e-mail client entirely, and are now denying it is them that did it, so the only email I can get is webmail - and zombie-computer spam would not be comming from HERE. - so I am left with a vague impression it has to be some kind of virus or trojan with it's own built in email client that bypasses their port blocking.

It sounds ludicrious I know, but for my own certainty and sanity - I need a virus scanner that will actually complete a scan of my machine.

And sure as hell no guarantee of there not being a virus there - not these days.

---

### Post by HermanAB on 2011-01-17
So, why are you too scared to run tcpdump and see what is going on?

---

### Post by Zacknafain on 2011-01-17
> **3rdalbum said:**
> If you are using a wifi network, someone might be connecting to your router and using your connection. Check the settings on your router; use only WPA (or even better, WPA2) for the encryption and set a nice long, non-obvious password.

:D  thought of that possibility and double checked it first up
if anyone has got onto our wi-fi they are ****ing houdini's ghost, it's encrypted, password protected, and firewalled twice by mac address (yes I found the mac address of every peice of equipment we have and entered it into our wi-fi router firewall as exceptions)  

And on top of that, they managed to do it without leaving log entries  :D

The other thing that the isp didn't like was I forced them too check their records to make sure someone hadn't found a way to tap our cable and break in - but according too the ISP tech I spoke too only our modem's mac addy turns up on their records too.

---

### Post by Zacknafain on 2011-01-17
> **HermanAB said:**
> OK, calm down and think about it for a bit first.

It is ***very*** unlikely that your Linux machine is sending out spam.  However, if you have been playing with VNC then it could be compromized.  

It is easy to check.  Stop everything that you are doing, then look at the network light - if it is blinking furiously, then your machine may very well be a spambot.

To make assurance doubly sure, install Wireshark or tcpdump and look at the activity on port 25 SMTP in ASCII form:
$ sudo tcpdump -i eth0 -A tcp port 25

If there is SPAM being sent, then you will immediately see it.

Herman - you sound like the guy I need to be talking to right now.  Thanks

Not exactly a ubuntu/linux expert yet so please be patient with me.

The modem traffic light does not go nuts when nothing is happening - I get a bit of occasional traffic when the computer is idle - but I have an IP phone so that is to be expected - but I tried unplugging that and letting it sit for a bit - pretty much dead.

I figured it was pretty unlikely that a linux machine had been virused and spambotted too - but research showed me that it was POSSIBLE however unlikely.  And every time I try to slap my isp into shape they keep waving the possibility around as a reason to legally deny my service or parts of it.  so I need to be able to entirely rule out even the possibility.

I'll go teach myself how to do that tcpdump or wireshark and that will give me something I can take too them and shove up their noses (or show me where to find my problem)

Thanks - I'll probably be back scratching my head at some simple step I am missing running one of those but this is a start  :D

---

### Post by Zacknafain on 2011-01-17
> **HermanAB said:**
> So, why are you too scared to run tcpdump and see what is going on?

I'm not - but I didn't know about it
just tried, is there any reason it would need to be done from the root user?  It's telling me that I don't have permission to capture on that device - which is really odd too me.  My user account is the prime user account and an administrator setup.
going to try from the root user

Hmmm - the disadvantage of still learning this stuff is not knowing what is going on when something doesn't work as expected.
from the root user, tcp dump responded with an 'unable to resolve host <my compy>' followed by a supressing verbose output - suggesting a -v or -vv switch
then sat there listening but doing nothing (is that good news?  it sounds a little like it to me - was sitting there not seeing any trafic means nothing is going backward and forward right?

Gonna try wireshark - I find the graphical interfaces make a little more sense too me - I might have grown up on DOS but linux command line is alien too me still.

Ok - I really don't know what's going on with wireshark either.  Just been battering my head against it and it's wiki - I can't seem to get my wireshark to access my ethernet adaptors - the only things it seems to see are my usb buses which, in this case, is utterly useless too me - everything I see on the wiki shows the wireshark listing the ethernet connections and whatnot - but mine doesn't seem to see them at all, and there is no information on how to force it to look ....  going to try again later after I restart to see if I am missing something - but need to take a break before I break something out of sheer agrovation

---

### Post by james_mcl on 2011-01-17
> **Zacknafain said:**
> it's encrypted

What with? WEP is utterly insecure, and WPA the first may have fallen ([http://www.theregister.co.uk/2011/01/11/amazon_cloud_wifi_cracking/](http://www.theregister.co.uk/2011/01/11/amazon_cloud_wifi_cracking/) - though maybe weak passwords were partly to blame?)

If you don't have WPA2, you really should step up to it.

---

### Post by yetiman64 on 2011-01-17
> **Zacknafain said:**
> ... tcp dump responded with an 'unable to resolve host <my compy>' followed by a supressing verbose output - suggesting a -v or -vv switch
then sat there listening but doing nothing [B](is that good news?  it sounds a little like it to me - was sitting there not seeing any trafic means nothing is going backward and forward right?
[/B] 
Gonna try wireshark - I find the graphical interfaces make a little more sense too me - I might have grown up on DOS but linux command line is alien too me still.
[B]
Sounds very good to me[/B]. As a contrast try the command with port 80 instead of 25  and while watching it refresh the webpage here in your browser.;)

Edit: to break the tcpdump output in terminal use Ctrl + c, on the keyboard OP.

@HermanAB, thanks for the new toy to play with. :lol:

---

### Post by HermanAB on 2011-01-17
Howdy, if tcpdump shows nothing, then there is nothing.

You can prove it by looking at port 80 and then refreshing your browser:

# tcpdump -i eth0 -A tcp port 80

or for fun and profit:
# tcpdump -i eth0 -A tcp port 110 | grep -e password

then refresh your POP mail client.

---

### Post by Zacknafain on 2011-01-17
> **HermanAB said:**
> Howdy, if tcpdump shows nothing, then there is nothing.

You can prove it by looking at port 80 and then refreshing your browser:

# tcpdump -i eth0 -A tcp port 80

or for fun and profit:
# tcpdump -i eth0 -A tcp port 110 | grep -e password

then refresh your POP mail client.

That's what I needed - thanks Herman - stuff wireshark - can work that out another time when I really need it

I'll be off beating my head against a bloody minded ISP - wish they didn't have a protected local monoply and I had some alternatives in my area.

---

### Post by Zacknafain on 2011-01-17
> **james_mcl said:**
> What with? WEP is utterly insecure, and WPA the first may have fallen ([http://www.theregister.co.uk/2011/01/11/amazon_cloud_wifi_cracking/](http://www.theregister.co.uk/2011/01/11/amazon_cloud_wifi_cracking/) - though maybe weak passwords were partly to blame?)

If you don't have WPA2, you really should step up to it.

It's been WPA2 since I first got the router - that and two mac firewalls, one for connectivity and one for data transmission - I like my routers like I like my ducks asses

---

