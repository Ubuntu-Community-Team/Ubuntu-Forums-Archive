---
title: "Best Ubuntu / Linux Internet Content Filter Solutions"
date: 2012-05-28
forum: General Help
---

### Post by konakid on 2012-05-28
I've been searching for several years for a good internet content filtering solution for my Linux boxes. I've tried several different apps. Some OS based, browser addons, and even DNS. I'll explain each of the solutions and my experiences briefly here.


1) Mobicip Online Safety. :KS

Although this option is not free it is the best option I've found for the Linux OS so far. Recently Mobicip updated their repository with working .deb files for the newest versions of Ubuntu (12.04 as of now). I'm actually using this service right now. Its relatively cheap compared to other filtering services. They have a good working tutorial, and with a paid filtering service you get software support, which is a second plus. As far as I've tested it does an extremely good job of filtering...Even search terms. It also has a record of all sites blocked and for what reason. Once configured it does it by itself, Password protected and all!! It also has the option to email filtering summaries to yourself,(or even an accountability partner). I haven't bothered to disect how the service actually works but I'm guessing it uses some sort of DNS service. Not surface configured however, as it made several Kernal configurations on installation.

 It doesn't seem to pull up in a Google search for Ubuntu content filtering, so I'm hoping this thread will help its raise awareness to other Linux user's seeking an easy yet effective filtering solution for their Linux boxes. In my quest for a good filtering solution I've ran across many forums where Linux users seemed to have come to a point where a CS degree is almost necessary to configure a filtering solution. Maybe this thread will help point these user's in a better direction.

Here is the link to the Mobicip Website.

[http://www.mobicip.com/](http://www.mobicip.com/)



2) Browser Filtering addons. (Probably the Easiest)

The best browser addons I've found was TinyFilter for Chromium. This light addon can do word based filtering. It can be easily configured, and all one needs to do is type in a blacklist of words/urls/and or language which you want to block. It also can be password protected. (I've recently been impressed with Blocksi addon for Chromium...may be worth checking out also.)

For the Firefox browser I've found ProCon to be the best filtering addon. Filters such as FoxFilter slowed down browser startup too much and just decreased overall browser performance. Once again this can do word based filtering very similar to TinyFilter. This seems to be the most affective and fastest way to filter unwanted websites...In my opinion. It can also be password blocked. 



3) DNS Filtering Services 

I've also used the DynDNS Internet guide and the OpenDNS filtering services and found them to be fairly effective for basic content filtering. One thing I do like about them is that your router can be configured to use these servers. Hence any connected device will be using your filter. Simple Whole Home Filtering. But...there are easy workarounds to disable the DNS servers on your system if your at all computer savvy. Here are the links to the tutorials I used to set the services up on my Ubuntu box. 

---OpenDNS setup.

[http://www.liberiangeek.net/2010/04/how-to-setup-ubuntu-to-use-opendns-dns-servers-to-filter-web-contents/](http://www.liberiangeek.net/2010/04/how-to-setup-ubuntu-to-use-opendns-dns-servers-to-filter-web-contents/)

[http://www.liberiangeek.net/2011/06/setup-content-filteringparental-control-in-windows-ubuntu-with-opendnspart-iii/](http://www.liberiangeek.net/2011/06/setup-content-filteringparental-control-in-windows-ubuntu-with-opendnspart-iii/)


---DynDNS setup..I've tested and used this on Ubuntu 11.11 and 12.04. It seemed to be the easier of the two due to the ddclient IP update preconfigured settings.

[http://www.liberiangeek.net/2010/05/how-to-protect-your-computers-with-dyndns-web-content-filtering-system/](http://www.liberiangeek.net/2010/05/how-to-protect-your-computers-with-dyndns-web-content-filtering-system/)

[http://www.liberiangeek.net/2011/06/enable-content-filteringparental-control-in-windows-and-ubuntu-11-04-with-dyndns-part-iii/](http://www.liberiangeek.net/2011/06/enable-content-filteringparental-control-in-windows-and-ubuntu-11-04-with-dyndns-part-iii/)




----Dansgaurdian.

One can't ignore this classic option. It can be extremely effective, and configurable. Some programming background is helpful, and setup can be tricky. There is a gui app floating around the web for configuring Dansgaurdian. I've used it and it worked most of the time. Sometimes on a wake up from sleep it would be disabled. The name is Dansgaurdiangui. I believe it is from the Developers of Ubuntu CE. It ran slow but gave a gui support for opening the correct files to edit. 

Another gui for Dansgaurdian setup is WebContentControl. This didn't seem to work on Ubuntu 11.10. It needed some gambas2 sources which were no longer available in the newer software sources. It did however work on my older Mint box.(much like Ubuntu).

---

### Post by henjj on 2012-10-31
After using Mobicip for a while can you give us an update of what you think of it?  Effective?  Easy to bypass?  Easy to configure?  Decent Support?  Thanks!

---

### Post by konakid on 2013-02-27
> **henjj said:**
> After using Mobicip for a while can you give us an update of what you think of it?  Effective?  Easy to bypass?  Easy to configure?  Decent Support?  Thanks!


I used Mobicip for about six months...It worked what I thought to be very well. However, when Ubuntu 12.04 came out it seemed to be little less well...And now that Ubuntu 12.10 is out it doesn't really work on it at all. It installs fine but it kills my internet all except facebook and gmail. It doesn't block other pages, they just time out and never load in a browser. Yet I can still ping and get a response in terminal. So that's my current rant on Mobicip.

Back in Ubuntu 11.04 and 11.10 it worked very well. 

Effect = Yes!

Easy   = Yes! They have an installation tutorial...super noob friendly

Easy to ByPass: Can't say for certain as I'm no expert in Networking but of my little knowledge it seemed quite secure.

Easy to Configure: Basically in their user passworeded client software there is a enable and disable option. The rest you set in your account on their website, which is very easy, and consists of checking boxes and adding whitelist/blacklist entries. But honestly their preset settings are basically perfect. Not a one search term ever slipped past it!

Good support: Well it was I emailed them regarding my issues with the last release of Ubuntu and haven't gotten a reply in several months. I posted on their blog but their site went all weird like in the blog section, so no reply there in about 3 weeks. 

Try it!! I can't say it isn't just my account that got weirded out and is only broken for me because I installed and reinstalled it so many times on different Ubuntu releases.[http://ubuntuforums.org/images/smilies/smiley-faces-80.gif](http://ubuntuforums.org/images/smilies/smiley-faces-80.gif)

---

### Post by henjj on 2013-03-05
Thanks for the reply.  I actually tried to use Mobicip, but the repositories were not working.  I contacted their support team and they replied, but I didn't get it resolved.  I ended up asking for a refund.  It would be nice if there was a web filter for linux like k9 web protection.  As more and more people move from Windows to other operating systems like linux, hopfully there will be enough demand for a number of different filtering options.

---

### Post by konakid on 2013-03-05
I totally agree. As you could see from this thread there was a time when I tried all the options I could find. There are some random GUI's for Dansguardian. However, I don't find Dansguardian to be very reliable after any OS updates or changes. Currently I am using the DNS route. Which if you are always at your own home with a router...you can set your router to use filtering services such as Nortan DNS, ScrubIt, OpenDNS, and DynDNS. There is also the option to set your own filtering machine/server. Which all internet traffic has to go through that machine first, I believe that is a reliable method...although I haven't tried it. I think IPCop has software to do this.

I'm currently a junior and am studying for a BS in Computer Science. So as soon as I feel knowledgeable enough I'm planning to write a GUI'd Linux/Ubuntu filtering App. Its also possible with the release of the Tablet/Phone Ubuntu OS we may see some other filtering apps being released...I hope.

---

### Post by smandoli on 2013-03-07
If the Ubuntu Team wants to improve the world and promote Ubuntu, they should package up a content filter and promote its use.  Their failure on this point is mystifying and disappointing.

---

### Post by Buntu Bunny on 2013-03-07
> **smandoli said:**
> If the Ubuntu Team wants to improve the world and promote Ubuntu, they should package up a content filter and promote its use. 

I agree. A filter has a lot of needful uses. I appreciate this discussion.

---

### Post by henjj on 2013-03-09
> **konakid said:**
> 
I'm currently a junior and am studying for a BS in Computer Science. So as soon as I feel knowledgeable enough I'm planning to write a GUI'd Linux/Ubuntu filtering App. Its also possible with the release of the Tablet/Phone Ubuntu OS we may see some other filtering apps being released...I hope.

Good for you!  I work at a Christian camp where we have a lot of people coming and going who are connecting to our network.  For our network, I have used this filtering solution from DD-WRT ([www.dd-wrt.com/wiki/index.php/OpenDNS](www.dd-wrt.com/wiki/index.php/OpenDNS)).  For most users, it seems to work pretty good since it forces them to use OpenDNS.  But as my kids are getting older and for personal use, it would be great to have something more robust / userfriendly for linux (something like K9 webprotection).

---

### Post by jinhee200 on 2013-06-04
There is one more. NxFilter from [http://www.nxfilter.org](http://www.nxfilter.org). It is a freeware dns-filter or dns-firewall. It has built-in GUI, dashboard, report, AD integration, policy based on user and group, blocking by categories, clustering etc.. The latest version supports malware/botnet detection based on DNS packet inspection.

---

### Post by konakid on 2013-10-28
> **jinhee200 said:**
> There is one more. NxFilter from [http://www.nxfilter.org](http://www.nxfilter.org). It is a freeware dns-filter or dns-firewall. It has built-in GUI, dashboard, report, AD integration, policy based on user and group, blocking by categories, clustering etc.. The latest version supports malware/botnet detection based on DNS packet inspection.

I installed according to the directions on this site. But with Ubuntu 13.04 it didn't seem to work. Whenever I would go to the link which was to bring us to the filter login page...it would never load. Do you know what the version support is for nxfilter?

---

### Post by Scott_Howison on 2014-02-11
Hi. I am new to the forums but am checking out Ubuntu for use as my primary family computer. I have small children I am also mystified as to why there is no good solution for this in Ubuntu. I tried installing webcontentcontrol but could not get it to work (said it was not found). I have also tried to install Mobicip, but could not find it either. I seems that dansguardian is probably the best solution but you apparently need a phD in computer science to get if configured. I really think that if Ubuntu is truly supposed to be "main stream", a robust parental control and content filtering solution needs to be included as part of the OS.

---

### Post by dragonfly41 on 2014-02-11
OpenDNS provides one useful control and is easy to setup across your browsers.

[http://www.opendns.com/home-internet-security/parental-controls/opendns-home-vip/?var=1](http://www.opendns.com/home-internet-security/parental-controls/opendns-home-vip/?var=1)

DNS settings in browser(s)

    208.67.222.222
    208.67.220.220

You can add further content filters on top of this layer of parental control.

There is a Ubuntu parental control package "nanny" in Ubuntu Software Centre you can try.

---

### Post by konakid on 2014-02-12
I would agree with dragonfly41. If your computers are staying at home, using DNS filtering is really the easiest method of content control on Linux which will always be supported by every version of Linux. 

[OpenDNS familyshield]("http://www.opendns.com/home-internet-security/parental-controls/opendns-familyshield/") is very effective and can actually be set up on the router if you wish, which means all devices are filtered if they are connected to that router. I am actually using [Norton ConnectSafe]("https://dns.norton.com/dnsweb/dnsForHome.do") right now on my router, it has the option of eliminating inappropriate sites, but still lets torrenting sites through. One downside to DNS filtering like this is they only block a web page lookup if that site is rated as inappropriate. They do not do page by page filtering, which means inappropriate google, tumblr, wikipedia, youtube, and other generally safe pages or which haven't been blacklisted yet, will still load.

Unfortunately I believe Mobicip has been deprecated. Last time I contacted them they said there just wasn't enough demand for it in the Linux community. Which I guess makes sense; probably the majority pf Linux users wouldn't be children anyways. Although with the development of Ubuntu Touch, this may change, forcing apps like these to support Linux again.

dansgaurdian actually can be complicated. Hence why I don't use it anymore. It probably actually wouldn't be that hard to write a gui for it...I should look into building one.
 
One option if you wish is to put a computer "inline" on your network which does all the filtering. Basically you set up dansgaurdian once and leave it. All network traffic will go through that computer which will filter any content. I haven't personally tried it but [IPCop]("http://ipcop.org/") is supposed to be able to accomplish this.

---

### Post by henjj2 on 2014-12-11
Figure I'd chime in.  Internet content filter solutions is something I have been interested in for a while and now especially with some young sons who are starting to use the computer.  Here is what I have currently running.  I'm using the latest ubuntu release (14.04).  I have the admin (sudo) password and my kids don't.  The only browser installed on the system is Firefox along with Foxfilter as an add-on.  I have the paid version so that I can password protect the filter.  You can use another addon called CCk2 to creat a custom version of Firefox that eliminates access to about:config, safe-mode, etc in Firefox.  I used these instructions:  [http://www.amsys.co.uk/2014/blog/locking-firefox-cck-2/#.VIoUgPkZWPC](http://www.amsys.co.uk/2014/blog/locking-firefox-cck-2/#.VIoUgPkZWPC).     The only part that took me (a novice) a little figuring out was where to extract the autoconfig package in linux.  Extracting the files as sudo to /usr/lib/firefox seemed to do the trick.  Using CCK2 to make a locked down firefox configuration that comes with Foxfilter seems like it is working well in my situation.  Maybe this can help someone else along in the future.

---

