---
title: "Internet Explorer For 11.10"
date: 2011-11-25
forum: General Help
---

### Post by ibrrfarr on 2011-11-25
So, I am wanting to finally break away from a dual boot type environment.  My problem is that I need Internet Explorer for parts of my business environment.  Specifically, most of the US Government business I conduct requires IE as their servers utilize ActiveX.  No need to preach to me about why this is BS; it simply is what it is.

My thread here:  [http://ubuntuforums.org/showthread.php?t=1886539](http://ubuntuforums.org/showthread.php?t=1886539) is going to be a chronicle of my new install on my latest laptop.  I am hoping to get it up and running over the weekend; however, I need y'alls help and most specifically the Internet Explorer issue.

Any help would be appreciated as once I do a permanent, singular install there is no turning back.  I am hoping that once I accomplish this I will be able to motivate many of my associates to make the switch as well!

---

### Post by vasa1 on 2011-11-25
So what is this thread to be about? Wine? I think it does IE6 and IE7. Not sure about higher versions.

---

### Post by searchfgold6789 on 2011-11-25
Thank you for choosing Ubuntu.
One thing you can try is to install Wine, which lets you run Windows programs on Linux. According to the AppDB for Wine, the latest version of Internet explorer does not work, but I think it comes with its own version of "Internet Explorer" you can try. Also, there's a tutorial here that you can try: [http://www.wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html](http://www.wine-reviews.net/wine-reviews/microsoft/internet-explorer-8-on-linux-with-wine.html)
 - search

---

### Post by WorMzy on 2011-11-25
[IEs 4 Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page")

---

### Post by oldtimer7777 on 2011-11-25
You will never get ActiveX to work on Ubuntu because that is windows proprietary.

Websites like Logmein.com require ActiveX to work for making a remote connection on their RDC like services, for example, do not work in Ubuntu even if you have IE installed, because it requires ActiveX scripts to run.  They tried using Java, but it isn't very smooth either. 

I just wanted to save you some time there..     about Ubuntu and ActiveX.  It was one of the first things I needed when I switched over to Ubuntu myself.

What exactly is it that you need to accomplish? Maybe we can try a work-around for you.

If you work for gov, then they can install Citrix on the server side for you to access via encrypted connection and use a native virtualized windows on Ubuntu. That would be one way to upgrade everything.   Gov services should be OS independent by now.

I moved everything over to Citrix and that solved the whole ActiveX necessity for work.  Work computers are still happily installed with Windows, and I am happily using Ubuntu.

---

### Post by ibrrfarr on 2011-11-25
> **oldtimer7777 said:**
> You will never get ActiveX to work on Ubuntu because that is windows proprietary.

Websites like Logmein.com require ActiveX to work for making a remote connection on their RDC like services, for example, do not work in Ubuntu even if you have IE installed, because it requires ActiveX scripts to run.  They tried using Java, but it isn't very smooth either. 

I just wanted to save you some time there..     about Ubuntu and ActiveX.  It was one of the first things I needed when I switched over to Ubuntu myself.

What exactly is it that you need to accomplish? Maybe we can try a work-around for you.

If you work for gov, then they can install Citrix on the server side for you to access via encrypted connection and use a native virtualized windows on Ubuntu. That would be one way to upgrade everything.   Gov services should be OS independent by now.

I moved everything over to Citrix and that solved the whole ActiveX necessity for work.  Work computers are still happily installed with Windows, and I am happily using Ubuntu.

Sorry, just got off work.  I do foreclosure work for top banks, local real estate brokers and HUD, FannieMae and FreddieMac.  I am based out of East Tennessee.  In a nutshell, it seems anything that even remotely deals with real estate serviced by the feds or banks requires ActiveX.  My guess is that it deals with how the photos are loaded from our computers and then imported into their servers, but I really don't know.  It has been a war for years as NONE of these folks want to change.  I take that back, one outfit did, but they kinda outsource the deal to a provider which utilizes Firefox.

It's easiest if I give you examples of the sites I need to access and then you will see what's going on.

Altisource:  [https://vms.altisource.com/](https://vms.altisource.com/)

AMS:  [http://ems.amsreo.com/cgi-bin/logout.cgi?sessionId=e535f1c5b554ccfb19664d40d24a2400](http://ems.amsreo.com/cgi-bin/logout.cgi?sessionId=e535f1c5b554ccfb19664d40d24a2400)

A2ZFS (They do the fed servicing):  [http://www.a2zfieldservices.com/FieldVendor/fi_login.aspx](http://www.a2zfieldservices.com/FieldVendor/fi_login.aspx)

This is my site:  [https://offgridops.org/foreclosurepedia/index.php/Main_Page](https://offgridops.org/foreclosurepedia/index.php/Main_Page)

So, whereas I began all my stuff in open source, I believe that everyone else started in W*ndows and that's where they're gonna stay.

I used Crossover awhile back, but the problem was that when it came to loading the photos it was a no go.

So, there you have it.  These are just a couple of the 11 companies I provide for.  They are multi billion dollar companies (when you include Bank of America and such) so I can't really tell them what they need to do in the IT arena.

I want to REALLY thank you for replying as the first poster was rather crass.  I have been preaching the gospel of Ubuntu for several years now and it's not like I joined yesterday.  I would be ready and willing to speak with someone whom could work on a hack (quasi-legal or otherwise) to access these sites via Ubuntu and be willing to pay what I could and donate all code to the community.  I've installed Ubuntu on upwards of 60 firm's computers out here and there is a REAL love for the OS; however, it has always been dual boot or they maintain a W*ndows based computer as they are real estate brokers and have to have the same access which I do.

Please feel free to PM me, email me at [email]president@offgridops.org[/email] or reply here as this is really the final challenge which myself and many others face.

Sidenote:  Wine is no go; Crossover is no go; dual boot is a real pain.

---

### Post by holycow131415 on 2011-11-26
install virtualbox, install windows in vb, and there ya go

---

### Post by ibrrfarr on 2011-11-26
Sorry to trouble you here, but is there a good FYI so that I can learn what virtualbox is?  I actually found a post on here [http://ubuntuforums.org/showthread.php?t=1881906](http://ubuntuforums.org/showthread.php?t=1881906) that dealt with it working for W*ndows gaming and such so it looks viable, but I'd like to kinda know the layman's breakdown.  Either way if you're quite sure it will run IE I am simply gonna roll the dice and install 11.10 and then the virtualbox.  I'll keep a running account of it here and the other thread where I was trying to get some good info on the install for the Compaq Presario CQ57 (that is my latest laptop I am gonna convert).

Thanks for giving me some input!  It really does mean a lot to me and I think folks FAR too often get fixes and then never bother to say, "Hey, I really do appreciate the community giving me input and helping me!"  

Any and all other advice would be INVALUABLE!  :KS

> **holycow131415 said:**
> install virtualbox, install windows in vb, and there ya go

---

### Post by gfd_2 on 2011-11-26
> **holycow131415 said:**
> install virtualbox, install windows in vb, and there ya go

What he said... 

I need I/E in order to use remote access for work and for NetFlix.  The latest version of VirtualBox was a snap to install. An additional benefit is that support for USB was very easy to setup so I could upgrade my Garmin devices.

---

### Post by searchfgold6789 on 2011-11-26
> **holycow131415 said:**
> install virtualbox, install windows in vb, and there ya go
+1. You can get the latest virtualbox from virtualbox.org. If you need further assistance in setting up Windows in a virtualbox feel free to post back here or send me a message.

---

### Post by oldtimer7777 on 2011-11-26
VMWARE is a snap to install, and you can have a basic WinXP install on that to do everything you need to do.   Here is a nice guide:

[https://debianhelp.wordpress.com/2011/11/22/how-to-install-vmware-player-in-ubuntu/](https://debianhelp.wordpress.com/2011/11/22/how-to-install-vmware-player-in-ubuntu/)

Virtualbox is great too. I use both from time to time. Almost identical, except for installing MAC OS X for using Xcode.

I have to say that Virtualbox is somewhat easier to install the USB Guest Pack.  So you would want to install Virtualbox 4.1 from the PPA.

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

The PPA is listed almost at the bottom of that to-do list with the PPA you need to use for Virtualbox. Try both and see which one you like better.

ActiveX will not work on Ubuntu. It is a proprietary issue and not something easily resolved on Linux systems at this time. But on the otherhand you don't have to deal with security issues associated with using ActiveX either on Linux, so it is a trade-off.  

Many things about switching over from Windows to Linux are usually resolved by using some kind of package/patch/etc in Linux, but ActiveX is not one of those kinds of circumstances.  Java will work though, and sometimes you can find a configuration setting within the Windows Web 2.0 application that will let you use Java if it is permitted. 

> **ibrrfarr said:**
> Sorry to trouble you here, but is there a good FYI so that I can learn what virtualbox is?  I actually found a Vpost on here [http://ubuntuforums.org/showthread.php?t=1881906](http://ubuntuforums.org/showthread.php?t=1881906) that dealt with it working for W*ndows gaming and such so it looks viable, but I'd like to kinda know the layman's breakdown.  Either way if you're quite sure it will run IE I am simply gonna roll the dice and install 11.10 and then the virtualbox.  I'll keep a running account of it here and the other thread where I was trying to get some good info on the install for the Compaq Presario CQ57 (that is my latest laptop I am gonna convert).

Thanks for giving me some input!  It really does mean a lot to me and I think folks FAR too often get fixes and then never bother to say, "Hey, I really do appreciate the community giving me input and helping me!"  

Any and all other advice would be INVALUABLE!  :KS

---

### Post by ibrrfarr on 2011-11-30
Sorry to everyone who responded and I appreciate the reply on the  ActiveX situation being proprietary.  I have been out of state doing  some foreclosure work and had no signal as most of the homes were cabins  almost as remote as the county I live in!  :)

I am kinda bummed; however, I understand proprietary.  I am going to shoot off some emails to some of the banks and find out precisely what is being used which requires IE.  It is completely mind boggling as in this day in age where smartphones are in play --- and they will NOT load on the sites either as Verizon told us there really isn't a true IE browser for their phones --- it would seem that these monolithic beasts would want to allow ease of access to speed up the process.

Anyway, I'll report back and hopefully I will have some good tech info to lay out as I feel this is a HUGE area in which Ubuntu could gain placement in the market as a viable commercial OS and besides I need the fix.

---

### Post by Mark Phelps on 2011-12-01
You think this is bad?  On another forum, someone asked about installing IE to their Android phone -- for much the same reason.

This is very disturbing (requiring IE) -- especially now, when IE has dropped below 50% of the browser market.

And, in case someone tells you to install the IE tab plugin in Firefox -- don't waste your time.  All that does is launch IE from FF; it does not actually implement IE.

---

### Post by KMKAR on 2011-12-01
My need for using IE is for a website that a company which I work with uses IE and java (and only those) for a webconferencing portal.

I can not get this to work properly, I get IE running OK, but I can not do it work with java.
I think I've tried all of the options, but sincerely, I'm stuck.

Regards!

---

### Post by gandaran on 2011-12-01
> **KMKAR said:**
> My need for using IE is for a website that a company which I work with uses IE and java (and only those) for a webconferencing portal.

I can not get this to work properly, I get IE running OK, but I can not do it work with java.
I think I've tried all of the options, but sincerely, I'm stuck.

Regards!
try different windows versions of java updates on wine till you find one that actually works well on wine (all old java updates packages are available for download at java website) most of the times the latest java update releases don't work very well on wine.

---

### Post by betterhands on 2011-12-01
> **Mark Phelps said:**
> ...This is very disturbing (requiring IE) -- especially now, when IE has dropped below 50% of the browser market.

for the first time since our existence, the website i work for revealed that more folks accessed our site from FF browsers over IE.  developing anything with the assumption that the user is using IE has never been more incorrect.

---

### Post by holycow131415 on 2011-12-01
> **ibrrfarr said:**
> Sorry to trouble you here, but is there a good FYI so that I can learn what virtualbox is?  I actually found a post on here [http://ubuntuforums.org/showthread.php?t=1881906](http://ubuntuforums.org/showthread.php?t=1881906) that dealt with it working for W*ndows gaming and such so it looks viable, but I'd like to kinda know the layman's breakdown.  Either way if you're quite sure it will run IE I am simply gonna roll the dice and install 11.10 and then the virtualbox.  I'll keep a running account of it here and the other thread where I was trying to get some good info on the install for the Compaq Presario CQ57 (that is my latest laptop I am gonna convert).

Thanks for giving me some input!  It really does mean a lot to me and I think folks FAR too often get fixes and then never bother to say, "Hey, I really do appreciate the community giving me input and helping me!"  

Any and all other advice would be INVALUABLE!  :KS

You should go to the virtualbox website and download it there because the one in the software center doesnt, or didnt support usb integration.

Virtualbox is just a program that lets you install other OSes within a virtual machine. So basically you have a machine running in a machine. It has a virtual hard drive that is basically a file on your host machine, and it uses your host machine's ram. It will definitely run IE, flash, java, any windows program, etc excellently within the virtual machine because it is a windows machine within ubuntu. I dont think it will run high power games well, because it is running on virtual hardware, which would make it laggy. Also, if your VM gets a virus, or gets messed up, it does not affect the host, so all you would need to do is delete it to start over ;)

---

### Post by vasa1 on 2011-12-01
> **ibrrfarr said:**
> So, I am wanting to finally break away from a dual boot type environment. ...

Is it possible to update Win 7 inside a virtual machine? If not, may as well dual boot.

---

### Post by yetiman64 on 2011-12-01
> **vasa1 said:**
> Is it possible to update Win 7 inside a virtual machine?...
Yes, if the networking tab is set up correctly in Virtualbox (select "bridged adapter" and choose the network card to connect to) the Win7 install will have direct internet access and can be updated as easily as if it were a full installation on the hard drive.

A windows installation into a virtual machine is as good as a "bare metal" install of the OS for internet access (yes, IE runs and ActiveX is installed and usable). The only real caveat is that your hardware needs to support virtualization (Intel-VT or AMD-V settings in BIOS need to be enabled). Also mentioned earlier is Gaming is not good (experimental DirectX support only) though that shouldn't be a bother for the OP in this case as Internet Explorer access to websites seems to be the OP's main concern.

IMO it is worth checking out in your case OP, it should do the job if your hardware is capable.

---

### Post by kurt18947 on 2011-12-01
> **ibrrfarr said:**
> Sorry to everyone who responded and I appreciate the reply on the  ActiveX situation being proprietary.  I have been out of state doing  some foreclosure work and had no signal as most of the homes were cabins  almost as remote as the county I live in!  :)

I am kinda bummed; however, I understand proprietary.  I am going to shoot off some emails to some of the banks and find out precisely what is being used which requires IE.  It is completely mind boggling as in this day in age where smartphones are in play --- and they will NOT load on the sites either as Verizon told us there really isn't a true IE browser for their phones --- it would seem that these monolithic beasts would want to allow ease of access to speed up the process.

Anyway, I'll report back and hopefully I will have some good tech info to lay out as I feel this is a HUGE area in which Ubuntu could gain placement in the market as a viable commercial OS and besides I need the fix.

Inertia is a powerful force.  In this climate especially any work that doesn't NEED to get done will probably not be done.  Only when there is a compelling reason to go away from I.E. based technologies will they.  I was talking to a bank office a few days ago.  On his computer is XP and at least a dozen open I.E. windows.  Huh, I wonder why cyber criminals target windows and I.E. :confused:

:rolleyes:

---

### Post by ibrrfarr on 2011-12-01
I don't think anything is bad other than the fact that the financial industry and really the vast majority of high level corporate US firms force W*ndows on us.  My only theory is that they bought into the servers back in the heyday of MS and are bound by the licensing agreements.

The stark reality, though, is that if you are going to do business in the US in figures with more than seven (07) zeros behind taly he number at hand (e.g.; billions and trillions) or your are going to do real estate property preservation (roughly a multi-trillion dollar industry) then you are going to play with W*ndows/IE and ActiveX.  That is why I am so driven to find a work around and I would think that either the community at large or Cannonical would key to the true need to get a hack in place.

I am going to experiment with the virtual box though and report back.

> **Mark Phelps said:**
> You think this is bad?  On another forum, someone asked about installing IE to their Android phone -- for much the same reason.

This is very disturbing (requiring IE) -- especially now, when IE has dropped below 50% of the browser market.

And, in case someone tells you to install the IE tab plugin in Firefox -- don't waste your time.  All that does is launch IE from FF; it does not actually implement IE.

---

### Post by DapperMe17 on 2011-12-01
If your using Firefox, can you not just install the "IE Net Renderer" extension, for those sites that require IE?

---

### Post by searchfgold6789 on 2011-12-01
> **DapperMe17 said:**
> If your using Firefox, can you not just install the "IE Net Renderer" extension, for those sites that require IE?
That wouldn't take care of Activex.

---

### Post by ibrrfarr on 2011-12-06
> **DapperMe17 said:**
> If your using Firefox, can you not just install the "IE Net Renderer" extension, for those sites that require IE?

I thought I would try anyway and when I went to download the extension it said, "Not compatible with Firefox 8."

---

### Post by oldtimer7777 on 2011-12-06
[QUOTE=ibrrfarr;11488426]So, I am wanting to finally break away from a dual boot type environment.  My problem is that I need Internet Explorer for parts of my business environment.  Specifically, most of the US Government business I conduct requires IE as their servers utilize ActiveX.  No need to preach to me about why this is BS; it simply is what it is./QUOTE]

What I have done to solve this kind of issue with IE ActiveX requirements on specific web pages I need to access is I seamlessly virtualize windows apps to run on my ubuntu desktop like this:

[https://debianhelp.wordpress.com/2011/11/22/how-to-install-vmware-player-in-ubuntu/](https://debianhelp.wordpress.com/2011/11/22/how-to-install-vmware-player-in-ubuntu/)

take a look at the bottom of that tutorial to get an idea of the results..   It works much better than Wine, and you will be able to use ActiveX and IE together in Ubuntu on any web site you normally would in windows.

But you can't use ActiveX in ubuntu by itself without proper visualization of Win OS apps and VMWare. If you find a way, please do let us know.

---

### Post by yetiman64 on 2011-12-06
> **ibrrfarr said:**
> I thought I would try anyway and when I went to download the extension it said, "Not compatible with Firefox 8."

IE net renderer, even **if** it were FF8 compatible is not what you wanted in your original OP, it accesses a service located in a datacenter in Germany that **checks** the url you input for IE compatibility. This is handy for a webpage **developer** using Mac or Linux to know if a page they are developing will work in IE NOT for accessing pages with IE.

Some info from the netrenderer site, 
> **IE NetRenderer** allows you to check how a website is rendered by **Internet Explorer 9**, **8**, **7**, **6** or **5.5**, as seen from a high speed datacenter located in Germany. Just type in a URL in the field above and try it out - it's free!and
> This online tool is ideally suited for web designers working on **Apple Mac** and **Linux**.  It allows to verify web designs natively on all popular Internet  Explorer versions without the need to have several Windows PCs.[[COLOR=Blue]--Source--[/COLOR]]("http://ipinfo.info/netrenderer/").

Other FF addons like IEtab etc require you to have IE installed natively, ie they are for Windows FF users only.

Your only really workable option appears to be Virtualization with either Virtualbox or VMware.

---

### Post by bluexrider on 2011-12-06
its funny you can get active-x for mozilla Firefox for windows but not the other way around?

---

### Post by yetiman64 on 2011-12-06
> **bluexrider said:**
> its funny you can get active-x for mozilla Firefox for **windows **but not the other way around?
Note the bolded word :) the OP is on LInux.

Mozilla Firefox is used in both Linux and Windows, when FF is on Windows it can access the IE rendering (thus use sites with ActiveX) via extensions like IE tab, not ActiveX natively though. It is a "hack" as Mozilla don't utilize ActiveX directly themselves afaik, so > you can get active-x for mozilla Firefoxmay not be technically correct.

Please remember ActiveX is MS proprietary tech specifically for IE use and the only way FF can utilize it is by running extensions that utilize the IE rendering engine in the MS environment.

---

### Post by bluexrider on 2011-12-06
> **yetiman64 said:**
> Note the bolded word :) the OP is on LInux.


sure, we knew that

---

### Post by JKyleOKC on 2011-12-06
> **ibrrfarr said:**
> Sorry to trouble you here, but is there a good FYI so that I can learn what virtualbox is?  I actually found a post on here [http://ubuntuforums.org/showthread.php?t=1881906](http://ubuntuforums.org/showthread.php?t=1881906) that dealt with it working for W*ndows gaming and such so it looks viable, but I'd like to kinda know the layman's breakdown.  Either way if you're quite sure it will run IE I am simply gonna roll the dice and install 11.10 and then the virtualbox.  I'll keep a running account of it here and the other thread where I was trying to get some good info on the install for the Compaq Presario CQ57 (that is my latest laptop I am gonna convert).

Thanks for giving me some input!  It really does mean a lot to me and I think folks FAR too often get fixes and then never bother to say, "Hey, I really do appreciate the community giving me input and helping me!"  

Any and all other advice would be INVALUABLE!Sorry I didn't find this thread sooner. I had a problem quite similar to yours, and solved it using virtualization. It's been working quite well for several years now.

The answer is to install VirtualBox (hereafter vbox), but use the version direct from Oracle rather than the (obsolete) one in the repositories. You can get it from [http://download.virtualbox.org/virtualbox/4.1.6/virtualbox-4.1_4.1.6-74727~Ubuntu~lucid_i386.deb](http://download.virtualbox.org/virtualbox/4.1.6/virtualbox-4.1_4.1.6-74727~Ubuntu~lucid_i386.deb) and simply "execute" the .deb file to install it. However success depends on having the proper hardware; just any old box won't give you best results. I've found that at least 2 GB of RAM, and at least two cores of CPU (or a hyperthreaded single core) are necessary for acceptable performance. More is better, in both cases.

To respond to your question of just what this "vbox" is, it's a program that emulates actual hardware to create a new, empty, *virtual* machine inside of your actual box running Ubuntu or whatever. This virtual hardware acts like a standard X86 CPU, normal RAM, and everyday disk and CD drives, although it's simply a running program that's manipulating stuff in actual RAM and stored on an actual disk. Normal software, such as Windows itself, cannot tell the difference between virtual and actual machines, so you can run Windows in a virtual machine (VM) without having to have it on your actual hardware.

This may sound like unnecessary smoke and mirrors, because you still have to install a real copy of Windows on the VM, but you gain a number of advantages. The VM can communicate with your real "host" machine and vice versa, so you can have all the advantages of both worlds, using Windows only for the things that cannot be done without it. You can also make totally accurate backups of the VMs, and can even transfer a VM from one actual machine to another in real time without interrupting the VM's operation (although I've never had a need to put this capability to the test). Best of all, you can put a VM into "saved" state, similar to hibernating a laptop, and bring it back almost instantly, so no resources are tied up with it when it's not needed.

Since you're planning to use this as production equipment in your business, you don't want to be on the 6-month life cycle of regular Ubuntu releases -- stick with the Long Term Support (LTS) releases rather than the newest, shiniest, and most bug-infested versions. The current LTS is 10.04.4; the next will be 12.04, due out next April. Use the current one; the next one is rumored to be very different and consequently may have all sorts of unexpected problems. The current one will be good for at least another year, giving time to get all the bugs worked out of the new one.

I'm using the Xubuntu variant, which has fewer bells and whistles than normal Ubuntu, but using VBox should be little different from one window manager to the next. After you set up the hardware, install the *buntu of your choice, and install VirtualBox, the next step is to create your first VM. Vbox has a wizard that will step you through this. First time out, accept its defaults for sizes. You can tweak most all of them later as you become familiar with using VMs. Set the network to use NAT, initially; this will make it much simpler to download things and verify that IE works properly.

Finally, stick a Windows setup disk of your choice into the CD drive, fire up vbox from the System menu, and start your VM. It should find the Windows setup disk and begin the installation. From there, it's exactly like installing Windows on a real machine, except that it goes a bit faster since virtual disks, strange as it may seem, are actually faster than real ones -- at least, they are until the job is done. Then they take a while to catch up to the real world! If the system seems to freeze at such a point, give it some time. Vbox caches "writes" to its virtual disks, and it can take several seconds to empty the cache; I've seen it take more than a minute, which seems like eternity when you're staring at a "dead" display and the keyboard and mouse do nothing either.

When Windows finishes installation, you can then run the Windows update program to collect all updates and install MSIE 8 -- which runs quite comfortably on each of my eight different VMs on this box, all of which lie dormant at the moment in "saved" state.

I hope this is of some help to you in solving your problem. Feel free to send me private messages, or simply continue the discussion in this thread, if I can be of more assistance.

---

### Post by ibrrfarr on 2011-12-07
Just a real quick note:  Go figure, one Okie helping another!  I am from Pond Creek/Enid!  Bah!  I will PM you tonight and thanx for the input!

> **JKyleOKC said:**
> Sorry I didn't find this thread sooner. I had a problem quite similar to yours, and solved it using virtualization. It's been working quite well for several years now.

The answer is to install VirtualBox (hereafter vbox), but use the version direct from Oracle rather than the (obsolete) one in the repositories. You can get it from [http://download.virtualbox.org/virtualbox/4.1.6/virtualbox-4.1_4.1.6-74727~Ubuntu~lucid_i386.deb]("http://download.virtualbox.org/virtualbox/4.1.6/virtualbox-4.1_4.1.6-74727%7EUbuntu%7Elucid_i386.deb") and simply "execute" the .deb file to install it. However success depends on having the proper hardware; just any old box won't give you best results. I've found that at least 2 GB of RAM, and at least two cores of CPU (or a hyperthreaded single core) are necessary for acceptable performance. More is better, in both cases.

To respond to your question of just what this "vbox" is, it's a program that emulates actual hardware to create a new, empty, *virtual* machine inside of your actual box running Ubuntu or whatever. This virtual hardware acts like a standard X86 CPU, normal RAM, and everyday disk and CD drives, although it's simply a running program that's manipulating stuff in actual RAM and stored on an actual disk. Normal software, such as Windows itself, cannot tell the difference between virtual and actual machines, so you can run Windows in a virtual machine (VM) without having to have it on your actual hardware.

This may sound like unnecessary smoke and mirrors, because you still have to install a real copy of Windows on the VM, but you gain a number of advantages. The VM can communicate with your real "host" machine and vice versa, so you can have all the advantages of both worlds, using Windows only for the things that cannot be done without it. You can also make totally accurate backups of the VMs, and can even transfer a VM from one actual machine to another in real time without interrupting the VM's operation (although I've never had a need to put this capability to the test). Best of all, you can put a VM into "saved" state, similar to hibernating a laptop, and bring it back almost instantly, so no resources are tied up with it when it's not needed.

Since you're planning to use this as production equipment in your business, you don't want to be on the 6-month life cycle of regular Ubuntu releases -- stick with the Long Term Support (LTS) releases rather than the newest, shiniest, and most bug-infested versions. The current LTS is 10.04.4; the next will be 12.04, due out next April. Use the current one; the next one is rumored to be very different and consequently may have all sorts of unexpected problems. The current one will be good for at least another year, giving time to get all the bugs worked out of the new one.

I'm using the Xubuntu variant, which has fewer bells and whistles than normal Ubuntu, but using VBox should be little different from one window manager to the next. After you set up the hardware, install the *buntu of your choice, and install VirtualBox, the next step is to create your first VM. Vbox has a wizard that will step you through this. First time out, accept its defaults for sizes. You can tweak most all of them later as you become familiar with using VMs. Set the network to use NAT, initially; this will make it much simpler to download things and verify that IE works properly.

Finally, stick a Windows setup disk of your choice into the CD drive, fire up vbox from the System menu, and start your VM. It should find the Windows setup disk and begin the installation. From there, it's exactly like installing Windows on a real machine, except that it goes a bit faster since virtual disks, strange as it may seem, are actually faster than real ones -- at least, they are until the job is done. Then they take a while to catch up to the real world! If the system seems to freeze at such a point, give it some time. Vbox caches "writes" to its virtual disks, and it can take several seconds to empty the cache; I've seen it take more than a minute, which seems like eternity when you're staring at a "dead" display and the keyboard and mouse do nothing either.

When Windows finishes installation, you can then run the Windows update program to collect all updates and install MSIE 8 -- which runs quite comfortably on each of my eight different VMs on this box, all of which lie dormant at the moment in "saved" state.

I hope this is of some help to you in solving your problem. Feel free to send me private messages, or simply continue the discussion in this thread, if I can be of more assistance.

---

### Post by ledzepjes on 2012-04-21
ibrrfarr did you make any progress?

Virtual Box is easiest way to go if you need to run windows apps inside of Ubuntu.

Put in the installation cd for the windows of your choice, or almost any operating system for that matter, into the cd tray and install windows inside Virtual Box. Or you can install from a cd copy stored on your hard drive called an ISO image file if you already have one, saving you from using cd's or carrying them with you everytime you want to install a new virtual machine.

Virtual Box is just an application, that acts as a fake hard drive with virtual hardware that the operating system can use and run with inside of the Virtual Box application window. Just like a previous post mentioned running VMWare with Unity, you have a similar feature to seamlessly run Virtual Box in Ubuntu, so when you start Internet Explorer in your Virtual Machine it runs opens just like Firefox and the windows background is hidden except for your application, you can minimize it and maximize it just like any other application in Ubuntu, just that if you save any downloads from it, it's going to be saved in the Virtual Machine and Not in your user folder in Ubuntu. However, this is the default feature, and there are ways to create a shared folder to save files back and forth, but that's for a later discussion if you need it.

Installing Windows in a Virtual Box virtual machine is by far the easiest and quickest and maybe the best option in my opinion.

You have to remember, the windows that is installed is just like a real version, you have to keep anti-virus installed on it and keep windows updated just like normal. The only difference with a virtual machine is that it's a big flat file, but the operating system thinks it's running on a real hard drive. When installing windows, remember to set it up with around 60-80 GB, and make it expandable, that's the key (I think it's expandable by default) what this does is it only creates a virtual machine the size of the data that is being used. So windows thinks it's 60 or 80 GB hard drive, whatever you specified, but it only takes up 15-20 GB on your hard drive, depending on how much space is taken up by installing windows and any additional programs or files, and it expands as you add more.

---

