---
title: "something is eating my download speed"
date: 2006-05-24
forum: General Help
---

### Post by medya on 2006-05-24
something is eating my internet speeed, I dont know what it is..
i restarted , I even turned the pc off , I even closed Gaim.

my internet speed is 64Kb , and it is using all of them...

I can see by netspeed which my pc is downloading by 9 KB Per second and uploads 400 Bytes per seconds

my internet browsing speed is so so slow now..I waitied like 5 minutes to load the ubuntu forum page.
&#1591;
what is eating my internet speed? 
and what the hell it is downloading ?
is it a virus ?

some info about my pc :
I have Eth ADSL Connection . 
my ubuntu is breezy.
I use bittorent to download files,, but I have closed it !
and even when I run Bittorent it cant download anything but it can just upload . (because somebody else is using my download)

please help me

---

### Post by robinl on 2006-05-24
Do you have apache or any http/ftp server installed? You might want to install ethereal and find out where the packets are coming from.

---

### Post by medya on 2006-05-24
Ii have apache php mysql.... 
i have ethereal..but I dont know how to use it , it shows IPs and stuff and i undrestand nothing.

---

### Post by dmizer on 2006-05-24
what is your physical setup?  ie, mine is:
cable modem > ubuntu firewall/router > networked machines.

what kind of hardware do you have in your setup?
have you tried powercycling everything (power off router, power off modem, power on modem ... wait for it to sync, power on router, power on pc).

---

### Post by nspidle on 2006-05-24
Could be a simple answer to this.

1. are you on your network alone or are your room mates / children downloading.

2. are you on a wireless network? are you sure your neighbors are not using your internet connection?

3. How is your download speed from a "fast" host such as google, gmail, or another reliable provider?

4. If you are not using any network related programs does ethereal show heavy network usage? are there IP addresses that are not yours or your router as the source or destination?

---

### Post by medya on 2006-05-24
i have ADSL internet , and I have one computer at home . [i dont share it]

it is like this 
PHone Line ---> Modem (Eth ADSL modem ) --- > Lan Card 

can u tell me more about ethreal ?
I know it is a sniffer.let say I chat with soembody, how I can see what the text of the chat in ethereal ?

---

### Post by medya on 2006-05-24
so nobody can teach me some ethreal ?

---

### Post by gibson on 2006-05-24
[QUOTE=medya]so nobody can teach me some ethreal ?[/QUOTE]


I have never used it myself, however the following link looks like it has some good tutorials etc on it. Should put you in the right direction none the less...

[http://wiki.ethereal.com/](http://wiki.ethereal.com/)

good luck

---

### Post by nspidle on 2006-05-24
Check out this thread. It may give you a solution.

[http://ubuntuforums.org/showthread.php?t=181171](http://ubuntuforums.org/showthread.php?t=181171)

About ethereal you really need to have a background in some intense networking to make it really make sense I suggest reading up and tinkering a little.

---

### Post by richbarna on 2006-05-24
you can also see what connections there are by doing a netstat.
Open the terminal/console and type :-
> netstat -na 10
You should be able to scroll up and see the i.p's of any foreign TCP/UDP connections.
Also, don't worry about the slow connection to ubuntuforums, that happens to me too, probably due to a lot of network traffic. (It's a very popular forum) :)

---

