---
title: "All kinds of problems"
date: 2011-09-10
forum: General Help
---

### Post by W-Unit on 2011-09-10
Hey guys,

So I'm still learning Linux... I wouldn't say that I'm still a noob at this point, but I'm still very much in the frustration phase of the learning process - coming from being a PC Techician and Computer Engineering major, it's always aggravating and embarrassing to have so many problems working with a PC...

Anyways, I'll just list the problems I've been having. I am running an Asus Eee PC, my original install was Ubuntu Netbook Remix 10.10. I recently upgraded to Natty, and this was the start of a couple of these problems.

1. Ever since installing the Xubuntu package (which was prior to my upgrade to Natty), I've had problems with keeping my wireless connection alive when I'm using it. It just goes out every so often, and asks me for my username/password (I am on a university network that requires both; it is not a WPA key or anything like that), then (usually) reconnects. Most often I will be disconnected for about 1 minute at a time, and this happens on average every 15-20 minutes or so. Occasionally, I will have problems reconnecting, and will be prompted to enter my username/password multiple times before successfully reconnecting. Sometimes momentary disconnects happen - although these are rare - where a little popup window will notify me that I'm now disconnected, then within a second or two, it'll pop back up and say that I'm connected again. Once again, this problem only occurs when I am in a Xubuntu session. 
2. Since upgrading to Natty, I have been unable to run a Ubuntu Netbook Remix session. If I select this session from the login screen, the logon sound plays, and the background and a blank toolbar are displayed. There is no mouse cursor, and nothing else loads. The computer is not "frozen" per se though, because I can still switch to a console session by pressing CTRL+ALT+F1. But I have to reboot the computer if I want to get to a different type of desktop session.
3. Also since upgrading to Natty, the regular Ubuntu Desktop session has been prone to freezing up. This is not like what happens with the Ubuntu Netbook Remix sessions; in these freeze-ups, I will be able to run Ubuntu normally for a few minutes (I would estimate usually around 5-10 mins), then the mouse and keyboard will become unresponsive, and I cannot even switch to a console session. I have to hold the power button and reboot the computer that way.

You know, I'm really starting to love a lot of things about Linux. But this stuff drives me crazy!!!! Why all the instability and problems after performing an upgrade!? Is this the way it'll always be? Should I just avoid upgrading in the future unless I have some explicit reason to do so? I am not trying to be cynical, but this is an awful lot of problems to fix in exchange for benefits I am unclear on.

Thank you for your time and any help you can provide.

---

### Post by al1x on 2011-09-10
> 2. Since upgrading to Natty, I have been unable to run a Ubuntu Netbook Remix session. If I select this session from the login screen, the logon sound plays, and the background and a blank toolbar are displayed. There is no mouse cursor, and nothing else loads. The computer is not "frozen" per se though, because I can still switch to a console session by pressing CTRL+ALT+F1. But I have to reboot the computer if I want to get to a different type of desktop session.

There is no UNR session for 11.04 Natty.It's the same for desktops and netbooks.If you want the UNR stick to 10.04.
As for the bugs with 11.04 there is a lot of them for me too so I still run 10.04 lucid, besides it's the LTS version...

---

### Post by holycow131415 on 2011-09-10
sounds like upgrading screwed up your system... try to fresh install. download the iso and reinstall clean slate.

---

### Post by Wim Sturkenboom on 2011-09-10
I doubt the EEE has the specs for Unity; it would definitely explain it. I did not want to try it on an Acer Aspire One and dropped Ubuntu in favour of lubuntu 11.04 which had the wireless dropping at occasion.

Is it possible that your problem on the university network is related to wireless dropping and automatically reconnecting (without prompting for WPA passphrase).

Now running Crunchbang on it and the problem seems to be solved.

---

