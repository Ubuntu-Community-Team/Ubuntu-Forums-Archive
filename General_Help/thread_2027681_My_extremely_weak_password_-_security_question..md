---
title: "My extremely weak password - security question."
date: 2012-07-16
forum: General Help
---

### Post by Petro Dawg on 2012-07-16
Kind of a stupid question, but I'm curious.

I have an extremely weak user password (but easy for me to remember) for my Ubuntu laptop; its not 'abc' or '123', but its almost as bad.  I was curious, is it actually critical to have a strong password for my Ubuntu log-on?  Is there any real threat of someone (or some program) actually remotely hacking my computer?  What is the real threat, if any?

---

### Post by necromonger on 2012-07-16
not critical, but wise.

---

### Post by papibe on 2012-07-16
> **necromonger said:**
> not critical, but wise.
This is very true, but if you have any sort of remote access enabled, things are different.

Let's say your laptop gets stolen. Unfortunately, physical access to your computer means root access. In that case the password won't make a difference.

A different case would be if your home directory is encrypted. In that case, a long strong password could be the difference in making your personal date inaccessible to others.

When remote access is enable the situation is similar: a long strong password can protect you from attacks from other machines (think Internet café, or public library).

Hope that helps.
Regards.

---

### Post by oldos2er on 2012-07-17
Since you've revealed to the world you have a weak password, I'd go with critical.

---

### Post by jockyburns on 2012-07-17
Seems your not alone. The BBC reported that people have on average 26 separate online logins, but only about 5 passwords for all of these accounts. [http://www.bbc.co.uk/news/technology-18866347](http://www.bbc.co.uk/news/technology-18866347)

I myself will admit, I have the same login password for about 7 different sites (albeit a fairly strong password).

---

### Post by matt_symes on 2012-07-17
Hi

If you are having trouble remembering a password then use a sentence.

This is one example.

> IWasBornUnderAWonderingStar

If you can then add some numbers and other characters and mixing uppercase and lower case is also advisable.

> 1WasB0rnUnd3rAWonderingSt4r*

It's the length of the password that makes it difficult to crack and passwords like these cannot be cracked by a dictionary attack.

Kind regards

---

### Post by Petro Dawg on 2012-07-17
> **oldos2er said:**
> Since you've revealed to the world you have a weak password, I'd go with critical.

Even if I told you exactly what my password was, how would you be able to hack my computer without me giving you physical access to it, or downloading a program which gives you remote access?  If you are not using the same network as I am, I don't see how it can be done.

---

### Post by Hungry Man on 2012-07-17
Your password is the separation between user and root. If I get access to, say, Firefox.exe I have access to whatever Firefox.exe has access to ie: your user directories. If I have your password I can elevate Firefox.exe and gain access to everything. Without the password I need a local privilege escalation exploit.

> Even if I told you exactly what my password was, how would you be able to hack my computer without me giving you physical access to it, or downloading a program which gives you remote access? If you are not using the same network as I am, I don't see how it can be done.

We're all on the same network in the long run =p yes, it can be done. It's a lot easier if someone gets you to click a link to visit a malicious website, of course, but even without that there are multiple other ways.

I think it was recently said that explaining how to hack someone is against the rules though.

---

### Post by Primefalcon on 2012-07-17
using a specific pad to all your simple passwords: [https://www.grc.com/haystack.htm](https://www.grc.com/haystack.htm)

---

### Post by ammofreak on 2012-07-17
Hi ):P
Have to concur with all replies here. Just hate it when someone tells me "I told you so..." Cheers!:)

---

### Post by Quatrix on 2012-07-17
Some of you are exaggerating the situation.  I could post my IP address and password, and you couldn't do anything with it.  An intrusion requires more pieces of information and a mechanism of intrusion.

---

### Post by Balthazar54 on 2012-07-17
An easy way to create a strong password is to use the first letter in the words of a phrase or song lyric that you will remember.

You can make it even stronger by replacing one or more characters with numbers and symbols.

ie: hb2uhb2uhbd?

(happy birthday to you, happy birthday to you, happy birthday dear ?) (hope I don't get charged by the rights owners) [-X

Throw in a uppercase character or two and it is even stronger.

Learned that trick from a sysadm at Boeing's computer center decades ago.

---

### Post by Mr.Dee on 2012-07-17
Ya if you gave out your IP and username and password you woud be fine.  You are probably behind a router and also running ubuntu... However, if you have ssh server installed and port forwarding to that server... depending how long you have had the server running, someone has probably already compromised your system.
 
If you have ssh server running just take a peek at /var/log/auth.log to see all the brute force attacks.  I've had this happen to me.

---

### Post by Cheesemill on 2012-07-17
> **Quatrix said:**
> Some of you are exaggerating the situation.  I could post my IP address and password, and you couldn't do anything with it.  An intrusion requires more pieces of information and a mechanism of intrusion.

Go on then, that sounds like a challenge to me :)

Seriously though there are often zero day exploits found in all sorts of software, including your router firmware and any applications that you run. You can also be infected by DNS poisoning techniques or by visiting trusted websites that have been compromised (you don't even need to click any dialog boxes, just visiting the web site could infect you).

Most of these exploits will only give the hacker the same user privileges as the exploited software (in other words your user), the attacker will then try and escalate these privileges by any means that they can. The easiest method is try try and brute force your user password which will fall in seconds rather than the years it would take if you had a strong password.

If you're connected to the internet then by definition you are on the same network as everyone else.

---

### Post by oldos2er on 2012-07-17
> **Petro Dawg said:**
> Even if I told you exactly what my password was, how would you be able to hack my computer without me giving you physical access to it, or downloading a program which gives you remote access?  If you are not using the same network as I am, I don't see how it can be done.

You might want to read the stickies here: [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

