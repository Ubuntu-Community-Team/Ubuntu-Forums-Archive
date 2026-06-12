---
title: "Printing coupons"
date: 2011-05-26
forum: General Help
---

### Post by alienmindtrick on 2011-05-26
I saw that a thread had been closed on this subject, but I would like to reopen it and ask for help. 

Prior to switching completely over to Ubuntu at my geeky friend's suggestion, I used to print grocery and other coupons which would easily save me $30-70 per grocery trip. Not knowing that these sites prevent Ubuntu and other Linux distributions from printing their coupons, and at my friend's recommendation, I overwrote Vista rather than installing Ubuntu beside it.

Disappointingly, Coupons.com has become the industry standard for coupons. There are a couple other sites, but most manufacturers now use Coupons.com even for their own site's coupons. Hence, as you guessed, you can't print even the coupons you find on most manufacturers' sites. 

I don't know where the problem lies, whether it's with these coupon hosting sites, or whether it's an issue that could be remedied by the gentle folk who generously contribute their time to build this wonderful OS, Ubuntu (no sarcasm, I LOVE Ubuntu). 

My question, and fervent hope, is that someone here can help those of us who would desperately love to take advantage of the $$$ that manufacturers throw at consumers in the form of coupons. I go through the Sunday papers for coupons, but to really make couponing work, you have to combine coupon deals. Newspaper coupons are the lesser of the two savings vehicles and usually represent items that manufacturers dearly wish to  move rather than items we dearly wish to buy. 

So...what to do?

I thank you all for the hard work and effort you've put into Ubuntu to make it the best OS anywhere. I hope that someday these other folk recognize that too, and let us play Coupons with them!

---

### Post by hwttdz on 2011-05-26
Unfortunately the required coupon printer (which is just an excuse for them to install an advertising toolbar) doesn't play nice with wine.  So the best you can do is have a virtual machine to run this software in windows.  Though I don't know how well a virtual machine will play with a printer, you could print to pdf and then move the pdf back to ubuntu to print.  I suggest contacting them and saying it'd really be great if they could provide the coupons in a format such as pdf, They're doing something kind of evil which is user agent detection to determine which browsers to serve the whole page to, if you install a firefox addon (or an addon for any other browser really) and set your user agent to 
"Mozilla/5.0 (Windows NT 6.1; WOW64; rv:2.0.1) Gecko/20100101 Firefox/4.0.1" you should be able to browse without issue. Sorry I couldn't be of more help.

There is also contacting each manufacturer directly with a message along the lines of:
"I signed up for the listerine website to print a coupon, however I get redirected to a third party website that does not support my operating system.  I encourage you to make your coupons available in a way that supports all operating systems.  Unfortunately I now will not be purchasing your product, and will recommend that my friends do the same."

You can pretty much just go down the list of manufacturers that provide coupons on that website and send the same cookie cutter message to all of them. And of course tell your friends to not buy that brand, and if there is an alternative brand that does provide coupons in a reasonable fashion make sure to tell everyone you know how awesome that brand is.

---

### Post by alienmindtrick on 2011-05-26
I've written a much lengthier letter than that short paragraph to all of the manufacturers, both major and minor, whose coupons I've sought to print, and have followed up in many cases with phone calls. In every case, they send a pre-printed coupon via snailmail, occasionally a brief (and not very sincere) apology, and usually contact information for Coupons.com, which information you can find on their website.
The upshot of course is that they have no plans on their end of changing the status quo.
If anyone wishes to cooperate in a campaign to convince them (both manufacturers and Coupons.com) to let us print their coupons, I have a full-page professionally phrased letter which I'd be happy to share for whole copy or partial copy as seen fit. Contact me via this thread or reply to [email]alienmindtrick@aim.com[/email].
Maybe if we hold their feet to the fire they'll see the wisdom of letting us in on the savings. For those who don't use coupons, I'd share this with you: In an average week's shopping, I usually save 50-70% off my grocery bill using a combination of store sales, newspaper-sourced coupons and internet-sourced coupons. Do the math. When I could print coupons, I usually spent about 10 minutes a week selecting and printing, another 5-10 selecting newspaper-sourced coupons, and then a brief scan of the grocery sales papers. So for less than 30 minutes time I would save $30-70 a week. THAT'S why I want to be able to print coupons.

---

### Post by jeremyjjbrown on 2011-05-27
I would also recommend creating a virtual machine to do this work.

Virtualbox is free and easy to set up.

[http://ubuntuguide.net/installi-windows-xp-inside-ubuntu-using-virtualbox](http://ubuntuguide.net/installi-windows-xp-inside-ubuntu-using-virtualbox)

If you don't have any kind of windows install disk you can look at Tinyxp here.

[http://techome.wordpress.com/2008/07/07/xp-is-dead-long-live-tinyxp/](http://techome.wordpress.com/2008/07/07/xp-is-dead-long-live-tinyxp/)

I believe you can even boot live from the cd.

---

### Post by eltonw on 2011-05-27
It's not the OS (ubuntu linux) but the browser. The sites you mention apparently are designed to work ONLY with MSIE. The solution is to use another browser (Chrome, Opera, KDE, etc). I've just some across the same problem using Firefos, when I tried to print a coupon.

The fastest workaround is in your browser options. IIRC, you can change some browser configuration so that the browser "identifies itself as' microsoft Internet Explorer to those sites that are designed to support ONLY MSIE.

I remember learning this trick about 1994 when I switched to linux. This should still work today.

---

### Post by alienmindtrick on 2011-05-27
No, the problem isn't just the browser. I've used Chrome, Firefox, Safari, and IE. The error message says that the certain browsers aren't supported, but it always indicates that the operating system isn't supported.

---

### Post by eltonw on 2011-05-27
> **alienmindtrick said:**
> No, the problem isn't just the browser. I've used Chrome, Firefox, Safari, and IE. The error message says that the certain browsers aren't supported, but it always indicates that the operating system isn't supported.

Have you tried installing WINE, and using the browser within it?

---

### Post by SoFl W on 2011-05-27
I went to print out some coupons from Walgreens, after I selected everything it said it needed to install some software, I just canceled out.
I use virtual machines for things like this, and that virtual machine is the only thing I use it for.  If they are tracking or spying the only thing they will see is their own site.

---

### Post by alienmindtrick on 2011-05-27
Yes

---

### Post by linuxinstalledfromhdd on 2011-05-27
I had the same problem with Ubuntu 11.04, and then I rolled it back to 10.10
and followed this guide. I'm able to print all the coupons like I did with Windows. 

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by walt.smith1960 on 2011-05-27
The deal with coupons.com is that they make a registry entry/change to limit the number of times a coupon was printed. No registry, no work.  I don't know if that has changed recently or not.  Even doing a Windows restore point prior to printing their coupons then rolling back after didn't work, supposedly.  If I recall correctly I couldn't print to a .pdf printer, only a physical printer.  Coupons.com did work with Firefox in Windows so it wasn't I.E. only.  I don't think it worked is OSX at the time either, just Windows.

Edit: I just checked and Mac is supported now.  Linux is not.  It'd be interesting to hear how the Wine based emulators or VMs running Windows fare.

---

### Post by linuxinstalledfromhdd on 2011-05-27
I use Wine and IE in Wine.  No problem.

Here is PlayOnLinux that you can install to get that configured too.

[http://cinderbox.net/2011/05/23/2856/](http://cinderbox.net/2011/05/23/2856/)

You won't be able to print from within wine, at least not that I was able to configure myself.  However you can do screen capture with native screen capture software in Linux, and print those out for yourself.

---

### Post by alienmindtrick on 2011-05-27
OK, I've reinstalled Wine and installed VirtualBox. I'm looking to download TinyXP ( [http://techome.wordpress.com/2008/07/07/xp-is-dead-long-live-tinyxp/](http://techome.wordpress.com/2008/07/07/xp-is-dead-long-live-tinyxp/)  > [http://thepiratebay.org/torrent/4206516/TinyXP_Rev09_-_eXPerience](http://thepiratebay.org/torrent/4206516/TinyXP_Rev09_-_eXPerience) ) but I'm not sure which package I should get. I'm thinking no drivers, since Ubuntu will still be running...right? And I definitely don't want MSIE, OE, WMP or anything else I don't need. Bare bones is best, it seems. Right now, I don't foresee using it for anything beyond printing coupons. 

So...a couple of my questions are:

1. I download this via torrent...right?

2. I have VirtualBox installed, but I don't see it in the applications list. How do I run it?

Update:  I have downloaded MicroXP as an .iso file. How do I now set it up to run in VirtualBox?

---

### Post by alienmindtrick on 2011-05-27
> **linuxinstalledfromhdd said:**
> I use Wine and IE in Wine.  No problem.

Here is PlayOnLinux that you can install to get that configured too.

[http://cinderbox.net/2011/05/23/2856/](http://cinderbox.net/2011/05/23/2856/)

You won't be able to print from within wine, at least not that I was able to configure myself.  However you can do screen capture with native screen capture software in Linux, and print those out for yourself.

That probably won't work since you never actually see the coupon itself. You get a preview, but the preview doesn't have the barcode and without the barcode stores won't accept the coupon.

---

### Post by eltonw on 2011-05-27
> **alienmindtrick said:**
> No, the problem isn't just the browser. I've used Chrome, Firefox, Safari, and IE. The error message says that the certain browsers aren't supported, but it always indicates that the operating system isn't supported.

... another suggestion: flush out your browser's cache, then ***[COLOR="Sienna"]disable*** cookies[/COLOR], *before* going to the coupon site. That way they can't 'spy' on you and determine that your OS is not Windows. **LOL**:razz:

---

### Post by alienmindtrick on 2011-05-27
Yeah, that didn't work either. 

OK, I have Wine, Winetricks, and PlayOnLinux installed. What now? Remember that you're talking to a novice. I read the "tutorials", a laughable term, for all 3. They're clearly not written for the average user. Nor are they entirely in English, although they purport to be...especially PlayOnLinux. 

The core issue seems to be how to get the Coupons.com website to think I'm using Windows such that it will install the coupon printer. Using Firefox, I'm able to get to the screen where I request to download the printer, then nothing happens. 

Sooooo...what now?


Here's an update:

I downloaded and setup Oracle VM VirtualBox, created a virtual machine with MicroXP, downloaded the Windoze version of Firefox (since it's compatible with the Coupons.com website), managed to select coupons on Coupons.com, downloaded the coupon printer, clicked 'Print', it told me my coupons were waiting for me on my printer (which I knew was wrong), yet nothing printed. So I got out of the virtual machine, opened the HPLIP application for my HP Deskjet and retried selecting coupons and printing. Nothing. So I think I might need to get the Windoze version of the printer drivers which I will try to find online and do today. I tried running the setup CD that came with my printer, but the virtual machine wouldn't run it. In fact, it couldn't find the CD drive. 
I'll keep trying. I feel like I'm THISCLOSE to getting this to work. 

Thanks for the help and let me know if you have any other suggestions or ideas.

Second update:

MicroXP doesn't have a whole list of files that are needed to print and finding them seems impossible. So I deleted that virtual machine and will try to find another version of something that may (but probably won't) work.

Third update:

I downloaded TinyXP_Rev09, created a virtual machine for it in VirtualBox, but it wouldn't run.

---

### Post by jeremyjjbrown on 2011-05-31
> Update:  I have downloaded MicroXP as an .iso file. How do I now set it up to run in VirtualBox?

You can mount the iso in vitualbox either by selecting it a mounted media in the first boot setup wizard, or by closing the virtual machine and mounting the image, then restarting the machine.

---

### Post by alienmindtrick on 2011-05-31
> **jeremyjjbrown said:**
> You can mount the iso in vitualbox either by selecting it a mounted media in the first boot setup wizard, or by closing the virtual machine and mounting the image, then restarting the machine.

Yes. If you read further into the post, you'll find updates which indicate that I did that.

---

### Post by alienmindtrick on 2011-05-31
Update 31 May:  I found a complete copy of XP Pro, downloaded it, created a virtual machine with it. I downloaded IE for Windows, visited the Coupons.com site, selected coupons, downloaded the coupon printer, clicked 'Print Coupons', it seemed to send the coupons to the printer, but nothing printed. 

So my question here is this: How might I go about saving that file, transferring it beyond the virtual machine to my actual Ubuntu file system, and then print it. Remember that the actual coupon is NEVER seen until it actually prints so printing from a simple screen shot is out.

Also, I thought to try to burn it to CD, but the virtual machine doesn't recognize the CD/DVD drive. Nor can I find the right Windows drivers for the printer I intend to use, which might be the core issue. 

At any rate....H-E-E-E-E-L-P!

---

### Post by walt.smith1960 on 2011-05-31
You may be correct about not finding a hardware printer being the problem.  It wouldn't print to Cute PDF in Windows so it may only work when a "real" printer is installed.  I wonder if there's something in the "coupon printer" that recognizes that it's running in a virtual machine and so refuses to work.  DRM is not limited to music and movies it seems.

---

### Post by alienmindtrick on 2011-05-31
> **walt.smith1960 said:**
> You may be correct about not finding a hardware printer being the problem.  It wouldn't print to Cute PDF in Windows so it may only work when a "real" printer is installed.  I wonder if there's something in the "coupon printer" that recognizes that it's running in a virtual machine and so refuses to work.  DRM is not limited to music and movies it seems.

Hey, thanks, Walt. That makes me wonder if I could print something else, which I didn't try. I'll fire up the VM and see if I can print anything at all from it. 

Update:  OK, I went to the HP website, got the drivers for my printer, installed it, but NOOOOWWW it doesn't recognize the USB port. It's a Toshiba laptop. Any ideas?  Anyone?  Anyone?  Buuuuueehler? (I'm sorry, it was just there...)

---

### Post by pricetech on 2011-05-31
I hate coupon printer for windows and have fought tooth and nail to keep it off the computers here at work.

Having said that;

I'm pretty sure you're talking about the same thing.  Just for laughs I set it up on an XP VM (licensed, by the way) and was able to print to my local printer.  It would not print to my laser which was networked.  It would not "print to file" so I could print it later.  It would not print to any virtual printers.  It would only print to a physical printer set up in windows.

Dump your pirated xp and install Vista in a VM since you presumably have a license since it was on your computer.

Update it and install the driver for your printer.

You didn't say how your printer connects to your computer, but it's probably USB since that's the most common these days.  You'll have one more step to make your printer visible to windows and that's to pass it through to the guest OS.  Look in Settings under USB as I recall.

Make sure you follow the instructions for installing in windows also.  If it says to install the driver before connecting the printer, do that.

Good luck with it.  I hope you save enough to be worth all the trouble.  I didn't.  I find I can save more by choosing a different brand in the first place that cost less and avoiding the hassle of installing spyware on my computer.

---

### Post by walt.smith1960 on 2011-05-31
Yup, if your time is worth anything they can wind up being expensive coupons.  I think telling the manufacturers offering the coupon that their distribution mechanism sucks might be more productive in the long run.  Mailing out a few hundred by hand with attendant labor and postage because customers couldn't print their coupons might send that message.

---

### Post by alienmindtrick on 2011-05-31
> **walt.smith1960 said:**
> Yup, if your time is worth anything they can wind up being expensive coupons.  I think telling the manufacturers offering the coupon that their distribution mechanism sucks might be more productive in the long run.  Mailing out a few hundred by hand with attendant labor and postage because customers couldn't print their coupons might send that message.

Unfortunately that approach hasn't yielded results beyond getting a single coupon mailed. And as far as it being worth the time, I indicated earlier in this thread that in an average week using a combination of internet coupons and newspaper coupons, a total time of <30 minutes/week, I would save $30-70 on a grocery bill of $50-100. However you slice it, that makes it worth the effort to get this to work.

@pricetech:  The reason for attempting to use XP was that it is a faster and lighter OS than Vista, but having run into issues with it, I tried downloading Vista and using my original license, I updated all the drivers, tried installing the printer drivers from the HP CD (it can't find the CD/DVD drive). I ran into the same problem - it doesn't recognize anything plugged in via USB. For the heck of it, I tried every USB port on my machine. Nothing.  Also, I don't know where the USB settings are located. I searched in the Control Center and got Startup Disk Creator...

---

### Post by pricetech on 2011-06-02
Let me back up a little first;  You need to be using the PUEL version of VirtualBox, downloaded from the VirtualBox site as the OSE version from the repositories doesn't support USB.

Once you are, if you're not already;
With VirtualBox open and the virtual machine shut down, click on Settings.  Select USB.  On the right you'll see a couple of buttons that are clickable along with some that are not.  Hover your mouse over the second one and the tooltip should read "Add Filter From Device..."  Click that button and choose your printer.  Close out of the settings screens and start the VM.

Shrug and Pray should now find and install your printer.

Let us know if you need more help.

---

### Post by polardude1983 on 2011-06-02
> **walt.smith1960 said:**
> The deal with coupons.com is that they make a registry entry/change to limit the number of times a coupon was printed. No registry, no work.  I don't know if that has changed recently or not.  Even doing a Windows restore point prior to printing their coupons then rolling back after didn't work, supposedly.  If I recall correctly I couldn't print to a .pdf printer, only a physical printer.  Coupons.com did work with Firefox in Windows so it wasn't I.E. only.  I don't think it worked is OSX at the time either, just Windows.

Edit: I just checked and Mac is supported now.  Linux is not.  It'd be interesting to hear how the Wine based emulators or VMs running Windows fare.

What I did always was just print to a disconnected printer, It would create the print job, but not actually print since it couldn't. Then I copy the print job to my desktop. Open a print job viewer and then print to a pdf printer from the print job viewer program. That way I would have a pdf of the coupon.

---

### Post by linuxinstalledfromhdd on 2011-06-02
> **pricetech said:**
> Let me back up a little first;  You need to be using the PUEL version of VirtualBox, downloaded from the VirtualBox site as the OSE version from the repositories doesn't support USB.

I just installed Virtualbox 4, and have USB support with it. I can access anything from inside Virtualbox 4 regarding USB devices. 

If you want to install Virtualbox 4, it is near the bottom of the this list:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by pqwoerituytrueiwoq on 2011-06-02
> **alienmindtrick said:**
> Unfortunately that approach hasn't yielded results beyond getting a single coupon mailed. And as far as it being worth the time, I indicated earlier in this thread that in an average week using a combination of internet coupons and newspaper coupons, a total time of <30 minutes/week, I would save $30-70 on a grocery bill of $50-100. However you slice it, that makes it worth the effort to get this to work.

@pricetech:  The reason for attempting to use XP was that it is a faster and lighter OS than Vista, but having run into issues with it, I tried downloading Vista and using my original license, I updated all the drivers, tried installing the printer drivers from the HP CD (it can't find the CD/DVD drive). I ran into the same problem - it doesn't recognize anything plugged in via USB. For the heck of it, I tried every USB port on my machine. Nothing.  Also, I don't know where the USB settings are located. I searched in the Control Center and got Startup Disk Creator...
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=194002&stc=1&d=1307036007[/IMG]
the option is disabled for me since i have no cd/dvd drive installed

---

### Post by pricetech on 2011-06-02
> **linuxinstalledfromhdd said:**
> 
If you want to install Virtualbox 4, it is near the bottom of the this list:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

Even better, get it straight from the source at:

[http://virtualbox.org](http://virtualbox.org)

---

### Post by tgm4883 on 2011-06-02
> **pricetech said:**
> 
I'm pretty sure you're talking about the same thing.  Just for laughs I set it up on an XP VM (licensed, by the way) and was able to print to my local printer.  It would not print to my laser which was networked.  It would not "print to file" so I could print it later.  It would not print to any virtual printers.  It would only print to a physical printer set up in windows.


Yea these coupon websites practices are a pain. I was able to print to my networked HP laser printer, so it's not looking for just local (via VirtualBox and an XP install)

---

### Post by pricetech on 2011-06-03
Printing to an IP port I'm guessing.

Seems to fool it into thinking it's local.

---

### Post by pricetech on 2011-06-04
Come to think of it, my inkjet was networked at the time I used coupon pinter.  Installed using the full installer from HP.  Probably what made it happy.

Laser was on a Netgear print server.  Didn't make it happy.

---

