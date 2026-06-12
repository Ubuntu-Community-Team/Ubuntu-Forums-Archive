---
title: "Internet Content Filter"
date: 2006-05-16
forum: General Help
---

### Post by PacShady on 2006-05-16
Hey all

I'm making the transition from Windows to Linux, and I'm awaiting the arrival of my Ubuntu CD. There's only one thing holding me back...

I'm currently using a program called Safe Eyes for internet content filtering. After a long Google search, I can't find a Linux equivalent to this program.

What I need is a customisable internet filter, similar to this program. It needs to be server-side filtering, with a web interface for administration. It needs to be installed and integrated into the system, and unable to be removed without the admin password, or it breaks the internet connection. If possible, it should also have the option to block or allow specific programs installed on the system. I don't want a program that simply changes proxy settings in the browser, that system is FAR too easy to remove. I need something that acts as a hard proxy/firewall, virtually nothing gets onto the Internet unless it goes through this program. I don't want to put a proxy machine between the system and the router, it's quite easy to unplug one cable and plug in another.

From what I can make out, the SurfSafe program from Linspire is kind of what I need, except that this program appears to only be available for Linspire, and Linspire isn't the kind of Linux I want installed (Too similar to the Microsoft system of things I'm trying to get away from, all those extra charges and fees, and difficult to customise etc). I need something that'll work on any Linux, including Ubuntu.

Anyone heard of such a thing? Or has anyone either found a way to get Safe Eyes to work on Linux, or how to get SurfSafe to work on anything but Linspire?

'Shady

---

### Post by az on 2006-05-16
[QUOTE=PacShady]
Anyone heard of such a thing? Or has anyone either found a way to get Safe Eyes to work on Linux, or how to get SurfSafe to work on anything but Linspire?

'Shady[/QUOTE]
[http://dansguardian.org/](http://dansguardian.org/)
and
[https://wiki.ubuntu.com/ContentInternetFiltering](https://wiki.ubuntu.com/ContentInternetFiltering)

---

### Post by PacShady on 2006-05-16
Thanks for the links, but I don't think these are quite what I need.

I'm not setting up content filtering for my kids. I'm setting it up for myself. I need a filter that I, even with root access, can't remove or bypass in any way without either getting someone else (who isn't in the same house as me, thus the web interface) to give me the administration password for the program itself, or removing Linux altogether and reinstalling (ie. a HUGE difficult job) otherwise any other removal attempt blocks all internet access until the program is either reinstalled or the system is reinstalled.

**- **It needs to have a Web interface that can be accessed over the Internet via an administrator password.

**- **It needs to have accountability features (ie. a list of attempted accesses to blocked sites is emailed to a specific address daily). 

**- **It needs to be virtually impossible to remove without a password, reinstalling the entire system, or about 4 months of work tediously removing files one by one and patching other core files.

**- **It needs to be self contained, and force redirection through itself (ie. no simply changing proxy settings in browser, it's incredibly easy to simply tell the browser to connect directly to the net). It needs to integrate itself into the operating system.
[B]
- [/B]It needs to be customisable. It needs to be able to be set to block sites with nudity, or personals, or violence, or chat, or politics, or FLOWERS if need be.

**- **I don't much care what kind of system it uses to block sites, just as long as it works at least 95% of the time (no system is flawless of course, but it should be at least reasonably close). I'm already paying for Safe Eyes now, so paying a subscription fee isn't so much a worry.

So there's the criteria, LOL. A bit extreme, but if there's several programs for Windows that do it (Safe Eyes, Net Mop, S4F, etc. are a few names), then there HAS to be at least ONE that works on Linux similar to this, that even one with root access can't remove without authority or many hours of hard work or lost data.

'Shady

---

### Post by PacShady on 2006-05-22
*bump*

---

### Post by jkplayschess on 2006-05-25
I'm interested in any answers anybody might have as well.  I read something about Edubuntu getting some content filtering... anyone know if that's going to be included in dapper?  Is that just a server based filtering thing?
Has anyone created an easy set of steps to setup Dans Guardian for dapper?

What about monitoring software?  How easy is it to setup a keylogger or screenshot monitor with password protection?  Do any of them offer the option of emailing anything questionable to an email address?  I'm also open to commercial options.

Thanks for any help in advance!

---

### Post by tjomara37 on 2006-07-24
For step by step Instructions, Walkthrough (walk through), Guide to disable, remove, uninstall, eliminate, eradicate, delete Safe Eyes, Safeeyes, Internet Content Filter; Email me [email]tjomara37@yahoo.com[/email] I will be more than glad to assist you. 

I know its frustrating for all of those who have this program and now your stuck. I was there myself. Some of you have: 

1. Lost Safe Eyes password. 
2. Virus or other Program has screwed up Safe Eyes so it will not function properly anymore. 
3. Someone gave you a computer that had Safe Eyes already installed without giving you the password. 
4. Someone may have downloaded this filter to your computer without your permission. 

I have had several people contact me explaining many different situations like these... I am glad to help. Send me a email, as I check my email several times a day, for how to receive step by step instructions to remove, disable, uninstall, delete Safe Eyes. You do not have to know much about computers to follow these directions. They are very simple. 

All in all great program unless you have problems

[email]tjomara37@yahoo.com[/email] (Jerry)

---

### Post by PacShady on 2006-07-25
Thanks, but I think you're a bit confused. We're looking to find a way to INSTALL Safe Eyes, or some other kind of similar content filtering, onto Ubuntu, NOT removal.

Any progress from anyone so far?

'Shady

---

### Post by tonhou on 2006-07-26
You may be interested in this howto that I wrote on setting up dansguardian on a single system:

[http://www.ubuntuforums.org/showthread.php?t=207008](http://www.ubuntuforums.org/showthread.php?t=207008)

--Tony

---

### Post by PacShady on 2006-07-27
Thanks, I'll have a look through it.

However, I need a filter that is untouchable after install, even by root, unless accessed with a separate admin password. Safe Eyes for instance installs into Windows, and unless the user has the administrator password for Safe Eyes (NOT an administrator account in Windows), they can't change settings, OR uninstall the program. Also, Safe Eyes not only filters web browsers, but can ALSO filter other programs, for instance a file sharing program can be set up in Safe Eyes to be denied access to the internet.

As far as I know, dansguardian is easily accessible and editable/uninstallable by root, and only filters web broswers. Unless there's a way to prevent dansguardian being edited, deleted or otherwise bypassed even by root access, unless some kind of separate admin password is supplied, it's not what I'm looking for. Thanks anyway.

'Shady

---

### Post by JSchwage on 2006-08-01
I'm trying to find out a way to do the exact same thing. I need a content filter, but I don't want to have the permissions to be able to change settings or uninstall it myself. But I also want to have root access to my computer.

I was thinking, there may be a way to only allow the root user to access the configuration and whatnot, but disallow sudo from configuring it. If this is possible, I can deal with using sudo all the time since I hardly ever use su.

---

### Post by T700 on 2006-08-01
Because of the nature of Linux/UNIX, I'm not sure it is possible to shield something from root.  You could of course set a password that root couldn't crack or you could encrypt something, but root can *always* delete/disable something--otherwise it wouldn't be root.

Paul

---

### Post by JSchwage on 2006-08-01
What about what I suggested? You could have someone set the root password so you wouldn't know it. Then, if possible, edit the sudoers file to disallow sudo users access to the content filter configuration.

---

### Post by T700 on 2006-08-01
> **JSchwage said:**
> What about what I suggested? You could have someone set the root password so you wouldn't know it. Then, if possible, edit the sudoers file to disallow sudo users access to the content filter configuration.

I suppose that would work, because you would basically be demoting yourself to where you could no longer assume root.  By doing so you would also no longer be able to do the multitude of common tasks required of the owner of a Linux box.  This is obviously a very important issue to at least a couple of poster, but for the life of me, I can't figure out why.  Not a slam, just confusion and lack of understanding on my part!  

Good luck and I'll be very interested to see if you find a good solution.

Paul

---

### Post by John.Michael.Kane on 2006-08-01
This may be of some use [**[COLOR="Blue"]censornet[/COLOR]**]("http://www.censornet.com/") .

---

### Post by JSchwage on 2006-08-07
> **SD-Plissken said:**
> This may be of some use [**[COLOR="Blue"]censornet[/COLOR]**]("http://www.censornet.com/") .Does it do what we need though? Will it allow me to know the root password in Ubuntu and not allow me to mess with the filter configuration?

---

### Post by bieber on 2006-08-07
The only truly effective solution I could think of for this would be to set up a seperate machine with CensorNet, and then physically secure that machine, and make sure you don't know the root password to it.

---

### Post by urukrama on 2006-08-08
Is it actually possible to use Censornet just on one computer (ie, without it connecting to the internet through another computer) like dansguardian?

Initially I got that impression. I donwloaded the software, burned it on a cd, and realise now that I need a separate machine for it to run. Am I correct?

(It would be a pity, as Censornet looks pretty good!)

EDIT: just figured out it is what I feared. It's a separate linux distro specifically designed to filter internet access. Great, I guess, but not for my purposes. :sad:

---

### Post by PacShady on 2006-08-16
Any idea how simple it would be to unplug a network cable from a proxy box such as CensorNet and plug it back in directly to the network? It's easier to bypass than root access on the same machine! CensorNet sounds good, but as long as it's impossible to bypass the proxy box, both through the software AND physically.

The theoretical idea of disabling sudo access to any config files sounds the most promising idea yet, if it's feasible. It wouldn't be disabling sudo altogether - Ubuntu is designed such that to do that would cripple the entire system. But somehow blocking sudo access to just those specific files would allow sudo to work for everything else that it's needed for, but prevent it from altering filter configurations, thus effectively disabling "root" access within Ubuntu (other distros besides Ubuntu, that allow actual logging in as root wouldn't work with this idea, but still we're not so much talking about that here are we?). So tell me, is this idea possible?

And in that case, do dansguardian or any of the other filtering solutions have a web interface? This is another important component I'm looking for, as my "administrator" doesn't have physical access to my computer, and having a passworded web interface to edit the configuration files would allow ease of administrating.

'Shady

---

### Post by timwoolsey on 2006-09-28
I'm in need of the same thing as PacShady.  Anyone have anything?

---

### Post by PacShady on 2006-09-28
I think everyone forgot about us :(

I actually got into contact with someone in the last month or so, from a different forum, who's got experience with PHP scripting and such, and has agreed to making a Dansguardian web interface that will be more user friendly than the Webmin plugin currently, and be password protected. This will be a major step in the right direction methinks!

Only thing now though, is we still need a way to prevent sudo from accessing dansguardian files to write to them, or otherwise prevent the user from being able to access those files. Does anyone know if this is even possible in Linux?

'Shady

---

### Post by A-star on 2006-09-29
What about just removing sudo access for that user?

---

### Post by PacShady on 2006-09-29
In this scenario, the main user is the one who needs filtering, and the "administrator" of the filtering software doesn't have physical access to the computer. Removing sudo access entirely from this user would prevent them from doing other functions that the main user would probably require sudo access for. In this case, we need a way of disabling sudo access ONLY to the dansguardian files, IF it's possible.

'Shady

---

### Post by Hey_I'm_new_at_this on 2007-04-20
Hey have you all seen Ubuntu CE? It has dansguardian integrated right into the OS. I haven't installed it yet because I'm not sure how, but it looks interesting. 

As far as your accountability question: If you used the filter to send your partner a log of your Internet activity then there would be a noticeable gap in the log if you disabled it. Your partner could then question you about that gap. Just a thought.

---

### Post by kyle.quamme on 2007-05-23
I know this is old, but how about this? You create another user that has powers like root, but doesn't include power over dansguardian files? Then have someone reset the root password. That was you can still administer certain things and be denied access to others. Just a thought.

---

### Post by conebox on 2007-09-07
The perfect solution for this problem is a Linux distribution called "ClarkConnect".  They have a free community edition that provides all the features described in the original post on this thread.

ClarkConnect functions as a gateway/router that replaces your broadband router (or replaces your IPCop, Smoothwall, etc. firewall).  You need an old PC, then you simply load ClarkConnect and use the web interface to configure the server, which includes content filtering.  (The content filter relies on dansguardian and squid, and works great.)  It's also transparent to all the client computers in your house, so you won't need to go tweak all your other computers.

I think ClarkConnect is a great option for people who want to create an extremely safe home network (i.e. protect both yourselves and your family from content that you don't want in your home).  You can give someone else the root password, but you can still configure yourself as an administrator for all the other capabilities of the server ... that way you'll only be blocked from changing the content filter settings.

I have this set up in my home as a gateway/router, and I use Ubuntu on my home desktop.  This creates a very safe home networking environment for me and my family.

(Also, ClarkConnect is based on RHEL, so it includes other server software, such as samba file sharing, LAMP, ftp server, VPN, and lots of other cool stuff for Linux geeks -- but you can be a very unsophisticated user and still use it effectively.)

---

### Post by Jon Bn on 2007-10-28
Buy a highend modem/router that has content filtering with a password. I believe Netgear has one and there are several others. These modem routers also have a web based interface and will email if a user tries to access a blocked site.

---

### Post by scorpia1275 on 2007-10-28
Hi 

I have some experience with internet filtering that I thought I would share.  I will admit straight away that it is not what you are looking for, but I thought I would share it anyway.  

Also I would just like to say up front that it is not my intention to slam people or other wise "evangelise".

I can completely understand having internet filtering on a home pc to protect children from adult content and other questionable content, but content filtering for adults is doomed to failure!

I used to a born again Christian for fifteen years and fought a battle with adult content for much of that time.  I tried various filtering solutions, including using SafeEyes,  Every single one of these software solutions can be bypassed and rendered ineffective given the correct knowledge, skill and patience, and of course the desire to do so.

For me personally the answer was simple.  My attitudes to sex, and nudity had to change rather than trying to prevent access to such material.  I do not want to moralise here as this is something for each individual to figure out for themselves, and is certainly off topic but it is human nature to desire sex and  and to see members of the opposite sex unclothed, it is only when a person recognises this, and realises that it is not wrong to indulge in this occasionally that issues with this kind of material (and attitude) will cease being an issue. 

Finally just to point out the futility of content filtering, even if you had the best most secure filter in the world it can easily be bypassed simply by popping in a live CD of any one of the Ubuntu or other Linux distros which would immediately give you free and unhindered access to the internet.

I hope this helps someone.

scorpia1275

---

### Post by conebox on 2007-10-28
scorpia1275,

I won't comment on the "moral" content of your post, since this is a technical forum rather than a philosophical/religious forum.  We should assume that other people in this thread have good reasons for their technical questions, and leave it at that.

However, from a technical perspective, my personal experience is that it's *definitely* possible to set up a secure content filtering system for your home network, to protect both your family and yourself from web content that you would rather not have in your home.

It won't be indestructible, of course, but with a little thought you can make it pretty darn close.

It's relatively easy to set up a content-filtering strategy that shields your kids from inappropriate content.  But, if your goal is to protect *yourself* from a harmful addiction to certain kinds of web content, the task is a little more complicated, but still in the realm of possibility.  

There have been many options suggested so far in this thread, and I think most of them would work pretty well.  *The key is to make sure the content-filtering software is running on a separate system that serves as the internet gateway for your home.*  Also, make sure it's password-protected.  If necessary, restrict yourself from being able to physically access the gateway.  (For example, you might put your gateway and your broadband modem in a locked closet, and put the key in a safety deposit box.)  I really like the idea of the off-the-shelf Netgear solution that was mentioned by "Jon Bn".

One helpful exercise: make a list of ways you might be able to by-pass the content filter, and then make a list of counter-measures.

For example:
(1) Pull the ethernet switch on the fancy content-filter gateway, and "replace it" with a cheap linksys router.  **Counter-measure:** Put the system in a locked closet, OR get rid of your old linksys router so that's not an option.  If your WAP is also a router, get rid of it and choose instead a pure WAP (no router).

(2) Log in and disable the content-filter.  **Counter-measure:** Have somebody else be responsible for the password, so you can't log in and disable it.

(3) Dial-up to the internet to by-pass the content-filter.  **Counter-measure:** Disable your old dial-up accounts, or think about this ... do you really want to surf the internet over dial-up?  I certainly wouldn't have the patience for that.

(4) Connect to your neighbor's wireless access point.  **Counter-measure:** Call your neighbor and ask him to activate the WPA or WEP encryption on his wireless router.  (In my neighborhood, everybody has already done this.)

I could make a long list of things like this, but the bottom line is this: If you are really committed to it, you can definitely come up with a system that works for you.  You won't be able to *perfectly* protect yourself, but you *can* make it very inconvenient and difficult.

Plus, there' s a hidden psychological advantage to doing all this:
By investing all this time in trying to lock down your home network, you *won't even try* to hack it, for fear that you might succeed.  Once you've hacked it, you've then got to come up with more counter-measures.  You don't want to work on this anymore after you've already spent all this time and/or money securing your network from yourself, so why even try to hack it?

---

### Post by Xeltul on 2007-12-28
I know this thread is kind of old but,  couldn't you contact your ISP  and see if they offer some kind of server side filtering?  I don't know how many ISPs do it, but the technology exists that would give them the power to do it.  This solution would not work for me because my ISP does not do this but it may work for some of you.

---

### Post by djdarrin91 on 2008-01-19
Try Glubble it works real good for me!:)

---

### Post by mnrbig on 2008-02-07
Why not content filter at DNS level. OpenDNS has content filters built in to there DNS servers. One could setup the filtering, change your router to use OpenDNS' DNS servers and away you go. You could replace the router to bypass it though so you would need to secure it. If you don't have the openDNS  or router passwords, then you would be able to edit the settings.

---

### Post by sloggerkhan on 2008-02-07
I'm just curious about this, as it does not make sense to me,
WHY do you not want root to have access?

---

### Post by wordchisler on 2008-02-07
If there is an Internet Lock equivalent for Linux, then a spouse (if you have one) could be given the password, and log you in only when they're home. (I haven't tried Internet Lock, I am looking for a Linux internet lock, and found that.)

I tried setting up two separate users per person, one with net access, one without, but file sharing (particularly widget information) is a problem.

I would like most of the features you listed under filter options, except I am okay with having the password myself. I don't trust filtering, and want to password the internet browsers as an additional measure of security. I also would like to be able to restrict browsing to a whitelist of permitted websites, with the user allowed to request adding the site to the white list via email or Pidgin.

I use Opera & Firefox.

---

### Post by hobel73 on 2008-04-05
> **sloggerkhan said:**
> I'm just curious about this, as it does not make sense to me,
WHY do you not want root to have access?

Sloggerkhan, all I can say is that if you had reason to know, you wouldn't have to ask.

---

