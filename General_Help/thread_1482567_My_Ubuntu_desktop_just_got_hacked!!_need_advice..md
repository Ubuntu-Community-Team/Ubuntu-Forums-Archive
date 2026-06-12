---
title: "My Ubuntu desktop just got hacked!! need advice."
date: 2010-05-13
forum: General Help
---

### Post by GerryEgan on 2010-05-13
Hello all,

A few moments ago a system message popped up to say that my desktop was being shared  with another user and then someone took control of my mouse. I immediately removed the network cable and then unplugged the internet from my router. I had ports for ssh and ftp open, I  closed these and disabled remote access on the router. I don't think they had access to it as everything looked OK.

I have disabled the remote desktop access to my PC, I wasn't aware it was on in the first place. the program that the access came through was vino. 

I want to check the logs to see that on screen message again, it was in an identical format to the message that appears if you disconnect from the network. I have looked but cannot find the right one. Does anyone know where I can get this? I'm running Ubuntu desktop 10.04.

Any help or advice would be appreciated.

Gerry

---

### Post by sir_nasty on 2010-05-13
it should be somewhere in /var/logs/

make sure that your root account is secured with a solid password, also check that guest is disabled....

---

### Post by Detonate on 2010-05-13
Got to

System>Preferences>Startup Applications

and make sure "Remote Desktop" is not enabled.

---

### Post by GerryEgan on 2010-05-13
Hello,

Thanks for the response, I have disabled the guest account and changed my password although it was random previously. I have checked in /var/logs and nothing jumps out at me for this information. I have used the log file viewer in System>Administration and could not find the on screen message logging there. 

I've searched for vino logging but as its a remote access program all the results are about "logging on" with it rather than its logging.

Anyone know about Vinos/remote desktop logging?

Gerry

---

### Post by mtbmonkey on 2011-02-04
I had the same problem last night, I was using Boxee and someone took control of the desktop.

I had remote desktop activated in startup manager but it was set to not allow access to other computers, can people still get in when its set like that. I took the cable out.

I've since turned it off, are there any other ways of getting in.

I've not got any unusual ports open that I know about, just a few shared directories.

---

### Post by Sconey on 2011-05-31
Im in shock. I love Ubuntu but today I looked upon my desktop as it was taken control of 3 times. Is this for real on Ubuntu 10.10 ? Remote desktop was disabled ? Whats with that ? Does it work ? I wonder does the button really work because it didnt my end.I dont have much use for it so I went into the Ubuntu software Center and unistalled it completely. Good riddens remote desktop.
As poster above said no log of it as well. I was using firestarter as my firewall. Very clever. I was hacked three times when on Firefox. I have master passwords set on it and Thunderbird. No cookies no history. I played a bit with who ever it was and in end all they could do was log out, meaning back to the log in screen..  Sad world really is. I played with U11 lasted me 10 minutes before it collapsed, So stuck with 10.10 and 10.04 didnt do what I needed with my sketch pen.. Do you think Im safe now remote desktop is removed ? I do like 10.10..:confused:

---

