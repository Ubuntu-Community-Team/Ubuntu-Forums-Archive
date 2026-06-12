---
title: "how to make ubuntu faster on a netbook?"
date: 2011-10-31
forum: General Help
---

### Post by jimicrackcorn on 2011-10-31
I just installed ubuntu and everything is ferry smooth but there's a lot of delay I've notice.  Like when launching an app it takes awhile before it finally opens.  Is there anyway to make it snappier?  Like in windows you can disable services and procceses, is there anything like that or should I try a deferent distribution?  IM using 11.10 btw

---

### Post by nothingspecial on 2011-10-31
> **jimicrackcorn said:**
>  or should I try a deferent distribution?


I faced the same issue on installing 11.10. I have found that installing lubuntu solves the issue.

---

### Post by JiuJitsu500 on 2011-10-31
11.10 is too new I think for all the problems to be solved... and FULL of crappy bugs. The worst on eI found was a completely disappearing panel and unity bar, though everything still showed what it was when I covered the space with my mouse (though I haven't reproduced this yet)

I have an HP mini 110 I'm trying my damndest to get working fast, and I seriously just logged in right now to add a new topic for just this. I've tried other distro's, even the famed for speed puppy (which holy GOD is that fast) but just do not like anything else once unity grew on me with 11.04... but now this new ocelot is killing everyone. Pretty big fail to me, 10.04 was still the best so far.

First, try to re-install, fixed a lot of my issues right off the bat. I can give you a whole bunch of stuff I did (deleting scripts, sysctl-conf/bum edits, modifying things, stripping it all down, using wicd instead of the network-manager due to issues) but I'm no really experienced super-user, I just know how to run a script and sudo some stuff and change directories to chmod +x or to apt-get (I only know a little bit).

So, I continue this thread basically by asking everyone more smarter-ier than me, how can I strip this bad boy down!!! The window manager sucks to kill (logging out takes 30 seconds or so), and rebooting takes over a minute now (11.04 had about than 30 seconds once I stripped it), and boot takes about 29 seconds with the tray icons showing up another 30 seconds after that (though the computer is still fully functional), shutdown takes 30 seconds or more now compared to about 4 or 5 in Natty...

I don't want the shell, just unity to act right again and for everything to generally run better like it did in Natty. What did they all change I wonder... more like a bad joke.

Without saying what I did so far, can anyone give some good advice that will help us netbook guys too?

---

### Post by raja.genupula on 2011-10-31
whats the Configuration of your Netbook.

if you have 1GB or less than to it i suggest you go for Xubuntu or Lubuntu.those are best where we need high speed performance with Less configuration.

---

### Post by WasMeHere on 2011-10-31
> **JiuJitsu500 said:**
> ... 10.04 was still the best so far...
Without saying what I did so far, can anyone give some good advice that will help us netbook guys too?

You wrote it yourself: ***Ubuntu 10.04 LTS Lucid*** will be supported until April 2013, and then there will be another LTS version. Or if you were happy with 11.04 Natty, continue or reinstall that version! Within a few weeks the worst bugs will be found and fixed in 11.10 Oneiric ...

Avoid frustration and have fun running Ubuntu :-)
Olle

---

### Post by jimicrackcorn on 2011-10-31
OK, lubuntu it is.  Is it possible to install it without completely formatting my drive?  It took ages to transfer all of my backup files back over, I really don't want to have to again if I can avoid it.

---

### Post by konnn on 2011-10-31
> **jimicrackcorn said:**
> OK, lubuntu it is.  Is it possible to install it without completely formatting my drive?  It took ages to transfer all of my backup files back over, I really don't want to have to again if I can avoid it.
Did you do a separate "/" and "/home" previous  installation ?

---

### Post by WasMeHere on 2011-10-31
I think that you save time in the end doing a clean (new) install and add your private files afterwards. The file transfer can be done while you are doing something else.

Good luck with Lubuntu :-)

---

### Post by SeijiSensei on 2011-10-31
More memory is always a good thing.  Oftentimes slow performance when switching between applications comes from the need to write to swap.  If you have more memory, you'll be able to run more applications more smoothly since most of their code will be in memory and not in swap on the hard disk.

If your machine has only 1 GB of memory, I'd suggest upgrading to 2-4 GB depending on what you machine allows.  Just doubling from 1 to 2 GB should make a noticeable difference.

---

### Post by KBD47 on 2011-10-31
Xubuntu and Lubuntu both fly on my netbook with 1 gig ram.

---

### Post by techvish81 on 2011-10-31
does ubuntu 2d mode gives any significant performance benefit?

---

### Post by philinux on 2011-10-31
> **techvish81 said:**
> does ubuntu 2d mode gives any significant performance benefit?

Only one way to find out. Test it. 

In theory it should be quicker. YMMV.

---

### Post by techvish81 on 2011-10-31
tried but not felt much difference,so to confirm that it's not only me or my netbook.

---

### Post by JiuJitsu500 on 2011-10-31
I have 2GB of RAM and swappiness is set to 10 with a shrunk swap partition (500MB from a GB... much more than enough since I have an SSD, not a rotational HD).

I love ubuntu, and really like the unity interface. Lubuntu and Xubuntu are really, really fast compared to this but they both still hang on strange things (which is odd... the old natty and maverick not-totally-endorsed-yet LXDE worked fine, as did XFCE) and both still have that classic look (which I like too... but netbook + unity = love).

Something in the Ocelot is just wrong. I'm giving it about a month (I'm in Iraq, internet sucks) before I make any changes like going back to an older version or another distro... hopefully the bugs are worked out by then.

Just curious as to stripping this down is all (and replacing a lot of the bloat). OH, but if you hear about upgrading your BIOS, don't even think about it... chances are very, very, very, very high it has NOTHING to EVER do with that. I saw someone post that as a solution once...

I like to tinker... even if I don't know what I'm doing too well. And besides, I have puppy on a thumb drive and a micro-SD, so even if I screw it up I can re-format and go again!

---

### Post by jimicrackcorn on 2011-10-31
Damn, ok, fresh install it is.  Is it at all possible to network share from ubuntu toa windows machine?  That'd make all of this so much easier.

---

### Post by WasMeHere on 2011-10-31
Yes. At least one of the computers must be a server, sharing files. In Ubuntu you can install a samba server (smbd).

---

### Post by S2UIRR3L on 2011-11-09
Don't know too much (still a newbie here). I'm working on a netbook that was given to me. It's an HP Mini-110 with an Intel Atom and 1-Gig of RAM. It has a bad hard drive, so I bought a new Fujitsu 80-Gig on eBay for $20 USD. I'm waiting for it to be shipped.

So far, I've made a Jaunty Jackalope 9.04 USB to see how everything will look and work... Guess what, 99% works out of the box. Wireless doesn't work, but I haven't had it hard wired to "fix" it yet, but I will. Everything else works and is quick to boot/shutdown.

Once I get my hard drive installed and Jaunty is running off of "it" instead of the USB, I'll come back here and let everyone know how it goes. I've read a few other threads on this Mini-110 and everyone has trouble with Natty and newer. Nothing on Maverick or Jaunty and older.

Yeah, I know Jaunty isn't supported anymore. But most, if not ALL the bugs are gone. I'm just the kinda guy that says "why fix something that works" lol. I've tried Maverick on my desktop and no problems, aside from some Compiz things not responding, but that's just eye candy.

-Squirrel

---

### Post by WasMeHere on 2011-11-09
> **S2UIRR3L said:**
> ...
Yeah, I know Jaunty isn't supported anymore. But most, if not ALL the bugs are gone. I'm just the kinda guy that says "why fix something that works" lol. I've tried Maverick on my desktop and no problems, aside from some Compiz things not responding, but that's just eye candy.

-Squirrel

I suggest that you try Ubuntu 10.04 LTS, Lucid Lynx. This long time support version is supported until April 2013 and it is also very stable and well debugged. I am very happy with it, particularly for 'old or middle-aged' computers.

---

### Post by S2UIRR3L on 2011-11-09
As far as my laptop (the Gateway that I'm using right now), I like it with Jaunty and I'm a stubborn jerk who doesn't like change very much lol. Everything works, so for me, there's no need to upgrade.

As for my desktop (the Dell that lives down stairs for now), I like it with Maverick. Like I said, only a few non-responsive compiz things. Gonna turn it back to Jaunty when I get the chance to format.

As for the netbook (the HP Mini-110 that I'm working on), I'm going to do a full install of Jaunty on that one as well. So far, the USB is working flawlessly, except for the wireless. But I'm sure there's a fix.

I've never had any major problems with Jaunty and only a few little tweaked issues with Maverick here and there. I think Jaunty is a strong and solid build and I love it. As I said, I'm stubborn lol.

Thanks for the advice, Olle!
And best wishes to all here!

-Squirrel

---

### Post by Fred Doolie on 2011-11-09
> **jimicrackcorn said:**
> OK, lubuntu it is.  Is it possible to install it without completely formatting my drive?  It took ages to transfer all of my backup files back over, I really don't want to have to again if I can avoid it.

Lubuntu (Ununtu with lxde) and kubuntu (ubuntu with KDE) and all the rest are just ubuntu with different graphic interfaces. You can have one installed or ten different ones installed and switch between them at will.  

Easier way: just use Synaptic to install "lubuntu-desktop". Then when you enter your user name and password before you press enter and log in, use the little gear thing to choose lubuntu instead of ubuntu. I have gnome, KDE and lubuntu installed and switch between them at will. lubuntu for speed. Gnome for everyday use and KDE for gee-whizz golly eyecandy and showing off Linux. Neener neener neener let's see Windows do THAT!

---

### Post by WasMeHere on 2011-11-09
> **S2UIRR3L said:**
> As far as my laptop (the Gateway that I'm using right now), I like it with Jaunty and I'm a stubborn jerk who doesn't like change very much lol. Everything works, so for me, there's no need to upgrade.

As for my desktop (the Dell that lives down stairs for now), I like it with Maverick. Like I said, only a few non-responsive compiz things. Gonna turn it back to Jaunty when I get the chance to format.

As for the netbook (the HP Mini-110 that I'm working on), I'm going to do a full install of Jaunty on that one as well. So far, the USB is working flawlessly, except for the wireless. But I'm sure there's a fix.

I've never had any major problems with Jaunty and only a few little tweaked issues with Maverick here and there. I think Jaunty is a strong and solid build and I love it. As I said, I'm stubborn lol.

Thanks for the advice, Olle!
And best wishes to all here!

-Squirrel

Yes I understand because I used to think so too. But I have been convinced that ***I need at least the security updates***, and it is almost impossible to do without upgrading to a supported version (now Ubuntu 10.04 LTS). If you think Linux is perfectly safe, please read this wiki under construction
[[COLOR="RoyalBlue"]_https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

I have found that more things work out of the box with 10.04, for example drivers for wireless LAN, and there are improved versions of several software packages (but of course these are not necessary).

Have fun finding out :-)
Olle

---

### Post by S2UIRR3L on 2011-11-10
> I have gnome, KDE and lubuntu installed and switch between them at will. lubuntu for speed. Gnome for everyday use and KDE for gee-whizz golly eyecandy and showing off Linux. Neener neener neener let's see Windows do THAT!


LMAO - I love showing off to all my MSW/MAC friends. The look on their faces is PRICELESS!!!

---

### Post by linuxuser12345 on 2011-11-10
> **S2UIRR3L said:**
> Don't know too much (still a newbie here). I'm working on a netbook that was given to me. It's an HP Mini-110 with an Intel Atom and 1-Gig of RAM. It has a bad hard drive, so I bought a new Fujitsu 80-Gig on eBay for $20 USD. I'm waiting for it to be shipped.

So far, I've made a Jaunty Jackalope 9.04 USB to see how everything will look and work... Guess what, 99% works out of the box. Wireless doesn't work, but I haven't had it hard wired to "fix" it yet, but I will. Everything else works and is quick to boot/shutdown.

Once I get my hard drive installed and Jaunty is running off of "it" instead of the USB, I'll come back here and let everyone know how it goes. I've read a few other threads on this Mini-110 and everyone has trouble with Natty and newer. Nothing on Maverick or Jaunty and older.

Yeah, I know Jaunty isn't supported anymore. But most, if not ALL the bugs are gone. I'm just the kinda guy that says "why fix something that works" lol. I've tried Maverick on my desktop and no problems, aside from some Compiz things not responding, but that's just eye candy.

-Squirrel

My sister has that exact same laptop, but she is running 11.04. 11.04 runs *seamlessly* with her system, wireless and all, and you should definitely upgrade! :)

---

### Post by S2UIRR3L on 2011-11-10
I'm convinced that I don't need all that stuff. I'm not a serious "internet" guy. And if my computer crashes or gets hacked, I really don't have much to lose. I back up everything on an external hard drive, as well as on hard disc CDR and DVD.

I do agree with you on the security issues tho. For when I'm doing my on-line banking or buying something on eBay, I'll use the big old Dell tower with Maverick. I don't visit "those" kind of sites lol, and I only open email from people I know.

I guess rather than going back to Jaunty, I'll keep the Dell tower on Maverick and possibly give him something new down the road because you are right. There needs to be "some" sort of security. Thanks for everything my friend!!!

-Squirrel

---

### Post by Lord_JABA on 2011-11-10
1 Use xubuntu. 
2 replace common apps with lighter ones
 eg. libreoffice calc with gnumeric
3 install [BUM - boot up manager]("http://www.ubuntugeek.com/boot-up-manager-bum-graphical-runlevel-editor.html") from synaptic and turn off services you don't use.

---

### Post by linuxuser12345 on 2011-11-11
> **S2UIRR3L said:**
> I'm convinced that I don't need all that stuff. I'm not a serious "internet" guy. And if my computer crashes or gets hacked, I really don't have much to lose. I back up everything on an external hard drive, as well as on hard disc CDR and DVD.

I do agree with you on the security issues tho. For when I'm doing my on-line banking or buying something on eBay, I'll use the big old Dell tower with Maverick. I don't visit "those" kind of sites lol, and I only open email from people I know.

I guess rather than going back to Jaunty, I'll keep the Dell tower on Maverick and possibly give him something new down the road because you are right. There needs to be "some" sort of security. Thanks for everything my friend!!!

-Squirrel
Well, if you don't have much to lose, why are you staying with Jaunty? Jaunty is out of date, and hardware support is inferior to what we get with the latest supported releases of Ubuntu. If 11.04 works seamlessly (which it does with your HP-Mini system), why don't you just switch over to it? Makes no sense to stay with an out-of-date operating system version when there is something that does the exact same thing, but has better hardware support, application support, OPTIONAL new features, and is considerably safer with security updates.
Just sayin'.

---

### Post by S2UIRR3L on 2011-11-12
I like Jaunty because it's never given me any grief. I don't need all the added security and I don't care for keeping up with the Jones. I've read so many complaints from people here that some major things have changed and are wrong with newer releases because "the team" failed to include vital drivers for things and we're forced to search for the proper ones to install.

I'll try it tho. That's one, if not the biggest reason why I love Linux/Ubuntu. I can "try it" before I "buy it" via "live" cd and usb. What will it cost me, a few minutes downloading and creating a cd or usb? I'm sorry if I sound like a jerk. I blame it on me being raised in New Jersey and New York lol. But I'm really happy with Jaunty and (for my self) see no reason for upgrading.

Now, getting back to the ORIGINAL topic of this thread. I'm going to look into downloading and creating a new USB for my little net book. Heck, I'll make a few USB sticks. One with Maverick, one with Natty and another with Oneiric and poke around each one and see which one runs faster. Possibly, which one will turn on the wireless and the speakers (no drivers yet).

And don't worry guys, I'm not going back to Intrepid (the one that I originally started out with in the first place). Tho, that was a solid release; Once I tasted Jaunty, I wanted nothing else lol. So far, I've tasted PCLOS, Xubuntu, Edubuntu, XFCE, and two flavors of Puppy (which would probably be the quickest on a net book) LMAO!!! I love these forums and everyone on them!!!

-Squirrel

---

### Post by S2UIRR3L on 2011-11-12
By the way - I failed to mention that I don't have hard wired access to an internet connection. I'm using my big lap top with Jaunty, which already had the proper drivers for my internal wireless. I'm giving my neighbor $10/month to leach off his wireless.

Internet in this area is nuts and I'm not about to spend $110/month for a television that I'm never going to watch (I don't like tv). They force me to subscribe to a channel package for internet. They won't do internet alone... (insert naughty words here) jerks!!!

I have to wait for him to be home and ask him if I can come in and use his hard wired connection to download anything because... well... The wireless doesn't work without downloading the proper drivers lol!!! Sorry for rambling on, I'll quit now lol.

-Squirrel

---

### Post by WasMeHere on 2011-11-12
> **S2UIRR3L said:**
> ...
Now, getting back to the ORIGINAL topic of this thread. I'm going to look into downloading and creating a new USB for my little net book. Heck, I'll make a few USB sticks. One with Maverick, one with Natty and another with Oneiric and poke around each one and see which one runs faster. Possibly, which one will turn on the wireless and the speakers (no drivers yet).
...

Try flavours:
Xubuntu (faster) or
Lubuntu (fastest) or
the corresponding Linux Mint XFCE and LXDE!
Try versions:
10.04 LTS lucid ~ Linux Mint 9 or
11.04 natty ~ Linux Mint 11

You can actually try them directly from the iso file using the following method:
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11227153&postcount=349_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11227153&postcount=349")

Have fun finding out :-)
Olle

---

### Post by linuxuser12345 on 2011-11-13
Why don't you try Ubuntu 11.10 in 2D mode? It gives you all the great features of Ubuntu 11.10 in compositing mode without all the hassle of delay.

---

### Post by S2UIRR3L on 2011-11-15
Doesn't look like I'm trying ANYTHING on this little guy... I just got the new hard drive from ebay today and I'm getting an error message when ever I try to install either of those flavors... Even my OEM copy of Windows XP won't get past that little error.

**Multi-Bit ECC Error M**

By the way, the OEM copy I'm talking about is for my Gateway full size laptop. I've used this cd in every computer I've owned and it's never failed. It's a legit, registered and licensed copy, just without the fancy green Microsoft label. It's a full install cd.

I did a little googling and the only return I'm getting is something to do with either the RAM or the actual mother board. I got it for free. If there's a cheap fix, I'll try it. If it's going to cost a hundred dollars, I'm going to sell it on ebay for parts and make a few dollars. So far, all I have invested is the $25 for a Fujitsu hard drive. And I know it's not the drive because I put it in the Gateway laptop and installed Natty without breaking a sweat.

I know this is the wrong thread, but since I've been interacting with you guys for the last 4 or 5 posts, I'll ask you first. Do any of you know about the "Multi-Bit ECC Error M" error message? If it means anything, the net book is an HP Mini 110 with 1-Gig RAM and an Intel Atom. Don't know much more about it so...

-Squirrel

---

### Post by WasMeHere on 2011-11-15
> **S2UIRR3L said:**
> ...
I know this is the wrong thread, but since I've been interacting with you guys for the last 4 or 5 posts, I'll ask you first. Do any of you know about the "Multi-Bit ECC Error M" error message? If it means anything, the net book is an HP Mini 110 with 1-Gig RAM and an Intel Atom. Don't know much more about it so...

-Squirrel
I would also say that ECC is about the RAM. ECC is one kind of RAM but then I found this link indicating it could also be complaining about a USB flash memory. 
[[COLOR="RoyalBlue"]_http://forums.creativecow.net/thread/56/855410_[/COLOR]]("http://forums.creativecow.net/thread/56/855410")

---

### Post by Topsiho on 2011-11-15
Squirrel complains his wifi doesn't work on his Jaunty netbook.
I have a netbook which had the same problem, though this could be solved using a webpage on this very problem. But in later versions it always worked out of the box, so Squirrel has one reason more to upgrade to a newer Ubuntu. I use 10.04 LTS, which however has problems with a newer USB wifi adapter for version N, on my desktop. That problem doesn't exist, however on still newer versions of Ubuntu (and the Linux kernel, which contains the drivers of almost all newest hardware).

I think it is always very unwise to remain using older and now unsupported distributions, when connecting to internet. And newer versions (read: kernels) have the drivers for the newer hardware, except for the very newest: it takes some time.

But: I have to say I hate the regressions that sometimes accompany upgrading (and even updating), which make havoc with some software.

I used to love Kooka, for example, but it's gone now, and not even replaced by a similar program (yes, I know about XSane Image Scanner, but think Kooka was far better).

Topsiho

---

