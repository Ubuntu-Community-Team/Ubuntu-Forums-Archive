---
title: "Live distros, banking &amp; security"
date: 2011-03-02
forum: General Help
---

### Post by ianc1 on 2011-03-02
Hi

I've got a query about live distros on either CD or USB.  I have no problem using them and get on fine with them.  My question is related to security.  I've seen a number of sites stating live distros are the way to go for internet banking as no matter what you do/happens the next time you start you have a clean machine.

See for example:
[http://www.itnews.com.au/News/157767,nsw-police-dont-use-windows-for-internet-banking.aspx](http://www.itnews.com.au/News/157767,nsw-police-dont-use-windows-for-internet-banking.aspx)
[http://www.associatedcontent.com/article/2689112/how_to_securely_bank_online_by_using.html?cat=15](http://www.associatedcontent.com/article/2689112/how_to_securely_bank_online_by_using.html?cat=15)

The first link is from Puppy Linux's page.

If I use say a 10.10 live USB (non-persistent) surely the fact that this is missing all the updates potentially puts me at risk still.  I am aware that Linux is safer by design etc but for financial matters I want to be absolutely sure.

Finally why can my live distro access my installed / and /home/user partitions without any password requirements?  Is this right?  If so isn't this an issue as an issue?

Cheers

---

### Post by Starfleet on 2011-03-02
I would think you are best off using a fully installed system rather than a live cd. Many machines take a long time to load the cd and although it may be very safe to do this, I don't think there is much of a security gain, not with Linux Ubuntu or derivatives that are installed properly in the first place. The chances of picking up a key logger in Ubuntu or any sort of infection that could compromise your security is near zero. I've been looking after Linux based computers for years and looking for viruses and keyloggers, rootkits etc and as yet have never found one on any of the hundreds of computers I have worked on.

The live cd as you say does not require a user password to access your system, this is normal. It was never really intended to be run all the time from a live cd, just installed or used to rescue a broken system. 

If you install it, you can activate the firewall, and, using Firefox or Chrome you are very very secure for online banking. I do it all the time and both my wife and I purchase items on the net almost everyday and have done so for many years. Never ever had a problem when using Linux Ubuntu of any Linux version. Linux is the safest operating system I have ever used. I speak as an ex-network manager who has been frustrated with Windows for years!

---

### Post by eriktheblu on 2011-03-02
A live CD/USB boot typically has root access. Encrypting your HDD can prevent this, or use a distro like [Lightweight Portable Security]("http://spi.dod.mil/lipose.htm") which has removed the HDD drivers.

---

### Post by sanderd17 on 2011-03-02
The best thing is an installation on a USB or external HDD (so you get security updates and can install a firewall), with the internal hdd's encrypted or removed (so nobody can access other info on your computer).

And after usage, completely wipe the /home/username directory.

off coarse, this is only when you are paranoia. Banking login systems (at least the one I know) are designed in a way that even having a keylogger on you computer is no real danger.

---

### Post by ianc1 on 2011-03-04
Thanks everyone.  It' not the security of Linux itself that bothers me.  I like the idea of using a non-persistent live distro as each time a start it its a clean system.  It's the lack of updates necessitated by the live distro that bothers me.  How much of a risk does that put me at?

eriktheblu is Lightweight Portable Security a live distro that has no access to the hard drives.  Is the idea behind this that its released safe is not updated until the next release ie a non-persistent distro.  I assume this is available to all as its Linux.

I'm not too keen on wiping ~ after every use of the live distro.

Cheers

---

### Post by peculiar penguin on 2011-03-04
>  It's the lack of updates necessitated by the live distro that bothers me.  How much of a risk does that put me at?It depends on your usage patterns. If you boot the thing, surf through a dozen sketchy porn or warez sites, install software from untrusted sources, click on weird e-mail links and then in the same session do your banking stuff, there is a certain risk (although I still haven't read anything about a proper Linux trojan, found in the wild, targeting online banking). But if you boot and then **only** do your banking stuff, an attacker would have to get exploit code onto the bank's website or have infected/hijacked your router (assuming there is one) in the past, which seems less likely but not impossible.

What kind of authentication methods does your bank offer? Mine now requires a small handheld device which (in conjunction with my bank card and optical data it reads from my computer screen) generates transaction-specific TANs (you have to confirm things like account numbers and amounts on the reader's screen), which is pretty cool (and safe).

---

### Post by ianc1 on 2011-03-04
Thanks peculiar penguin.  That's cleared things up a bit in my mind as I intend to keep the distro solely for financial stuff.  I haven't used banking for ages online.  But the last time I did it the security methods were similar although I don't know about optical data.

I'm intrigued by the Lightweight Portable Security Distro although it may be overkill as I have no top class info to hide.

---

### Post by Starfleet on 2011-03-04
Lack of any security related updates will potentially put you at risk. In reality, that risk is probably not very great but it's difficult to tell. However, I really don't think it's worth the effort to do banking from a live cd. I think the article does overlook some factors of some importance relating to security and really making that live cd method unnecessary and potentially making it less safe than using a properly installed version on the hard drive. If your fully installed version of Linux (any derivative) is properly setup and up to date, you are as safe as anyone could be and many times more secure than a Windows installation. Use of linux software such as 'BleachBit' (in the software centre) will take care of anything left on your hard drive if you want to wipe everything in the temp files (or anywhere else). So I really don't see a reason to 'live cd it' at all.

---

### Post by ianc1 on 2011-03-05
Thanks Starfleet.  I have had bleachbit unstalled for a while but have never got round to trying it out.  I assume it's similar to shred that comes with Linux.  Regarding removing temp files are you refering to the contents of /tmp or are there other locations maybe .macromedia which I think is where flash cookies are stored?

Thanks

---

### Post by Starfleet on 2011-03-06
Hi Ian, yes you can use 'bleachbit' to shred /temp files no problem. It can be used to target anywhere on your hard drive...even empty space, because often as you will probably know, the space isn't empty. It can still have files on it, just without extensions showing. So they are invisible to your computer and will be eventually overwritten. Bleachbit can target those files for you, and will show you what other files to target...it's all good! 

I personally don't erase my cookies every time. This can be counter productive for most people as they will only keep loading each time you are on the net or a particular site. Generally, these days cookies are not a big risk and it slows your computer up if you keep erasing them. If you want to be sure of complete privacy, then yes, delete them using your browser or bleachbit. I guess it's a personal choice thing and depends on how much security you need.

Your browser (excluding IE in Windows which is rubbish for security) especially Firefox, automatically rotates the file names of temporary files several times a second to prevent key loggers and other programs from 'locking on' and obtaining your information about where you have been and what you are doing. This is useful, but not fool proof. Running from a live cd slows that protection process down and makes it easier for someone to see where you have been. At least this seems to be the case, as far as my colleagues and I can determine from the tests we have done on our network. So in conclusion, from tests we have carried out on the live cd method on my network, it's very very debatable as to whether the live cd is more secure than using a properly installed version of Linux. If anyone has conclusive proof either way I'd like to see it. Good luck Ian.

---

### Post by dionysius on 2011-03-06
The suggestion to use a Live CD (which was hailed in various media as something new and exciting, running an OS from a CD, imagine that!) for internet banking was targeted at Windows users. Some banks have warned against using Windows (and IE) to access their systems, and if your OS is Windows, using a Linux Live CD to access online banking would be a good idea. If your main OS already is a Linux distro using a Live CD isn't going to improve security much. 

The only time I'd use a Live CD to access online banking would be when using a Windows machine - which is never.

---

### Post by coldraven on 2011-03-06
I'm not totally paranoid, yet, but there are some handy plug-ins for Firefox.
BetterPrivacy will delete selected/all Flash cookies.
HtppsEverywhere will force encrypted connections to many sites.
An interesting thread, thanks to everyone.

---

### Post by ianc1 on 2011-03-13
Thanks everyone some very interesting replies.  I'm going to look into the HTTPS Everywhere plug-in, although this confuses me.  If a site is not set up for HTTPS how is it possible to force secure transmission?

---

### Post by dionysius on 2011-03-15
> **ianc1 said:**
> Thanks everyone some very interesting replies.  I'm going to look into the HTTPS Everywhere plug-in, although this confuses me.  If a site is not set up for HTTPS how is it possible to force secure transmission?


It's not possible, a site needs to have at HTTPS enabled. Major websites usually do, but of course your browsing isn't confined to only Facebook and Google. Personally I don't see the advantage for data that isn't sensitive, and banks use TLS/SSL by default for online banking.

---

