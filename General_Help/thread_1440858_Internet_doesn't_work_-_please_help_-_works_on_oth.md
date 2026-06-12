---
title: "Internet doesn't work - please help - works on other machine with ubuntu"
date: 2010-03-28
forum: General Help
---

### Post by metroedged on 2010-03-28
The internet just stopped working recently.

I was in the IRC and someone else said the same thing happened - that the internet just mysteriously stopped working.

I was downloading something with transmission on my computer, then my dad wanted to use the modem, so he took it.

After I got the modem back and plugged it into my computer (which worked flawlessly for the week or so which I've had ubuntu installed) it no longer works.

The modem detects everything working, and the phone even works in the phone line that I use for DSL (same one that worked fine before)

I have done no changes to the computer or software at all since the problem occurred.

I am on ubuntu 9.10 karmic koala.

computer is amd athlon 64 x2 3800, 2x1gb pc 6400 2.5-7-5-7, 500 watt psu, one 200gb and one 500gb hard drives, motherboard is an MSI k9pgn6 something.

Again - everything on the computer works other than internet - also, it seems that with firefox I am unable to access the modem as usual via the 192.x.x.x that usually worked.

I am currently trying to burn a CLEAN ubuntu CD as the first one was a used and scratched CDRW that I threw out and the DVD reader seems to not want to work to install it.

Any help is appreciated.

I will have to re-install XP pro and only install ubuntu inside of windows this time, sadly.

I really wanted to completely switch over to WINux and ditch LOSEdows.

---

### Post by Citizen Bleys on 2010-03-28
Getting dial tone in the jack you use for the modem is inconclusive, unfortunately.  The only way to ensure the modem is functioning properly would be to call your ISP.  Since they'll probably hang up on you as soon as they find out you're running Linux, it's best to go by the lights.  Most DSL modems will have a DSL light--it's got to be on, preferably solid.

On your end of things:  can you post the results of the ifconfig command?  Are you connecting directly from your computer to the modem, or through a router?  If through a router, you may need to access your router's firmware to determine your actual, public IP address.  Your public IP address should not start with 10, 172.16, 192.168, or 169.254.  Any other numbers (barring 255, 1, or 2 as the last octet) should be fine and you can star out the last octet or two if you have security concerns.

For now I'm going to assume the most common configuration -- connecting via a router.  In this case we'll need to try to find the point of failure.

start with this:

```
ping -c 5 www.yahoo.com
```

if it times out or fails to respond, we want

```
ping -c 5 69.147.125.65
```
*that's Yahoo's IP address*

Next step is your ISP's gateway; If you don't know it, go to [http://www.whatismyipaddress.com/](http://www.whatismyipaddress.com/) and you'll get an IP address; replace the last octet with a 1 to get your ISP's gateway

if you're still failing, try pinging your own public IP, then your router's internal IP (in my case 192.168.1.1), and finally 127.0.0.1.

If you can't ping 127.0.0.1 you have either a faulty NIC (test with a LiveCD such as Knoppix?) or a driver problem.

If you can get to 127.0.0.1 but not your router's internal IP, you probably have a router problem.  If you can get to your router but not your public IP or gateway, your problem probably lies at your IP address.  If you can ping Yahoo by IP but not by domain name, you've got a DNS problem.  This can be router-related too, but try manually specifying 8.8.8.8 as your primary DNS and 8.8.4.4 (google's DNS) as your secondary.

I risk writing a novel here, so I'll wait to hear back from you with more info.

Fun fact:  100% of this post is something your ISP's techs should know, 0% of it is Linux-specific, but most ISPs won't spill the beans if they know you're running Linux :(

EDIT:  If you have a router/modem combo, it might be trickier.

---

### Post by metroedged on 2010-03-28
I'm not going to quote because your reply was so long, but I appreciate the help and will answer each question in the order they were given.

1. DSL lights:

They are all working fine; ethernet, dsl, activity, etc. Only the activity light was not solid (obviously).

2. IPconfig command:

Can't do that as I've already begun re-installing losedows XP PRO to get things stable again - I just want my torrents working!

I will get ubuntu installed again ASAP but this time INSIDE of windows or on another partition so I can switch back and forth if a problem like this occurs.

3. Router/modem

I am on a DSL modem, no router (hence the switching it back and forth)

My dad barely uses it so we decided it wasn't worth the money to buy a wireless router.

It's working fine on his computer (with ubuntu instead of windows now)

I will bookmark this page/not delete the email and will come back here if the problem should arise on his computer or mine again.

I hope you will still have this under email notification and thank you again for the fast response.

I will keep this thread updated.

---

