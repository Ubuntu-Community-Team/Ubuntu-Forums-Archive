---
title: "what is practical when setting passwords?"
date: 2006-06-24
forum: General Help
---

### Post by tefflox on 2006-06-24
Since changing from windows to linux, the built in security features are surprising, an OS built from the internet up, rather than the.. shelf down.  I had so much trouble with malware on windows that since using ubuntu I have gone a lot further in setting passwords.  I'm using reasonably strong passwords for everything I use, but with the built in security, hearing many say there's really no need to install a firewall even, and since I'm the only person with physical access to my computer, can I relax on the passwords?

I'm behind a router, and their tech support says that there is no way my router control panel can be accessed from the internet, only from the lan.  

I want to use passwords and change them periodically, but can I make them short and easy?

---

### Post by IYY on 2006-06-24
> and since I'm the only person with physical access to my computer, can I relax on the passwords?


If you use telnet, SSH or FTP, people *will* try cracking your system by guessing the password. If you do this and have a password like "guest" or "password", you *will* get hacked. 

Otherwise, you shouldn't really worry, but it's always a good idea to have at least 5 characters in the password, maybe throw a number or two as well.

---

### Post by tefflox on 2006-06-24
I forgot to mention that yes, I do use an ftp to connet to my hosting service, but the problem I had in windows was it was "owned" externally, so I guess it didn't even matter what passwords I set, because it seems they could get the hash codes (?) off my drive and brute force them (?)...  But this isn't something to worry about with linux?  thx for helping.

also, about the services you mention, if the sessions themselves aren't secure, what can happen, and what can happen further?

---

### Post by bscbrit on 2006-06-24
There is always a compromise between ease of use and security.  In your case, if you are certain that unauthorised physical access is unlikely, you can err towards ease of use.  You have already presented several barriers to an attacker from the internet but, not matter what you do, if someone is prepared to put in sufficient hard work they could probably get into your system.  But it is more likely that they will simply look for an easier target elsewhere.
A good password need not be that difficult to remember.  For example, if your address is 123 Nowhere Crescent, Somewhere, you could use something like "123ncS%".  It is sufficiently difficult to guess for someone else but relatively easy for you to remember.  Try to avoid words that can be found in a dictionary.  However, even the password above could be broken given sufficient time.  Your decision is whether the person trying to obtain access will give up before he gets into your computer.  My guess, given your combination of linux / router / good password, is that you will probably remain safe.

---

### Post by tefflox on 2006-06-24
thanks, but now I want to add that my system has been/will be targeted specifically by people who know a lot about me.  Where am I vulnerable ---grub boot, linux login, ftp session, web page content, IP address?  I mean for the case that I am being personally targeted.  Thanks

---

### Post by Sye d'Burns on 2006-06-24
I'm a big fan of taking the first letter in each word of a phrase. For instance: It was the best of times, it was the worst of times = IwTBoT1Wt0t 

It can be any phrase really, just stay away from actual words.

---

### Post by bscbrit on 2006-06-24
Well it rather depends on what you want to use your computer for.  If it is used for email and web browsing then you can prevent many attacks by using a firewall that blocks any outside access from the internet.  If you want it to be a server (web, email or whatever) then you will have to let connections from the outside get in, but you can still do quite a lot to block those that you do not wish to accept.   To put it simply, set the firewall to stop any connection that you do not explicitly want it to pass.
If your 'attacker' knows a lot about you 'personally', then avoid passwords that are based on information that an attacker might already know.  Use something like "$tYU52#" - it will only take you a day or two at most to learn it and it will not be easy for someone else to guess.  Afterall, if they cannot get physical access to your computer then you can probably even safely write the password down!
If your attacker knows so much about you, do you also know who your potential attacker is?  There might be something you can do to have his illegal actions stopped - it rather depends on where you live, what the local law is, and how much damage they are likely to cause or have already caused.
Your IP address will be available fairly easily - especially if you want to offer some kind of server!  Otherwise, you will have a very under-used web site.  But the fact that someone knows your IP address doesn't make it simple to crack into your system.  There are still loads of obstacles that you can put in their way.
There are many internet sites that can give you tips and ideas about securing your system.  I would also get into the habit of frequently checking your logs to see if any attacks are being made.  Use some of the many programs available in linux to ensure that you know what a good system looks like, check that nothing is being changed, make regular backups so that you do not lose data even if someone does get it etc, etc.
My own favourite protection is however, DO NOT USE WINDOWS! But you have already made that decision :-)

---

### Post by tefflox on 2006-06-24
I'm installing JAP services with the package "anon-proxy" and the JAP site says:

Without Anonymization, every computer in the internet communicates using a traceable Address. That means:

    * the website visited,
    * the internet service provider (ISP),
    * and any eavesdropper on the internet connection

How easy is it for someone to "eavesdrop on my connection"?  What must be compromised on my part (if anything) to let that happen?

---

### Post by bscbrit on 2006-06-24
I would recommend that you install 'tor' and 'privoxy' - although nothing guarantees you **total** privacy.  Google for them for more information, but to install them they are readily available for Ubuntu in the repositories.  

I am **not** suggesting that you use these programs to hide anything that you might wish to do that is illegal.  Simply that they give you an enhanced degree of privacy on the 'net.

---

