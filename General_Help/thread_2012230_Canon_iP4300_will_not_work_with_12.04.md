---
title: "Canon iP4300 will not work with 12.04"
date: 2012-06-28
forum: General Help
---

### Post by VanCardboardbox on 2012-06-28
I have a Canon iP4300 printer that has worked flawlessly with the last six releases of Ubuntu, but will simply not get along with Precise. I am dual booting 12.04 alongside 11.10 and Windows 7, both of which continue to work fine with this printer. I am having to boot back into 11.10 any time I need to print.

After much reading I find that there are a few experiencing this issue with Canon printers on 12.04 but there seems to be some disagreement on what is causing the problem (is it CUPS? Is it the gutenprint driver?) or how it can be corrected. 

I am attempting to install the michael-gruz Canon driver for the iP4300 to see if this provides a remedy but do not know how to proceed. I succesfully added the PPA and installed the driver package **cnijfilter-ip4300series**. Now what? When I use the printer management utility to add the printer it does not find this driver and I do not see how one can direct the utility to it. Can anyone shed some light on this process, or offer an alternative fix to this frustrating problem? No printing is a show-stopper.

Cheers

---

### Post by hlynur on 2012-09-24
I'm having the similar problems. Have been using ubuntu 6.06 8.04 10.04 flawlessly as a print server for my home lan with the canon4300.  12.04 is giving me a lot of problems. Often the job freezes after printing half a page. Sometimes it prints 3 lines then spits out the page and prints the remaining stuff from the 1st page on the following page. 

Really strange. The colors are often messed up as well, fx when printing a picture it prints the black colour in the right place in right porportions but the remaining colors in another much bigger porportions. The printer test page is ok though. 

I'll post if i find any solution, I'm though starting to look at setting up cups on my pfsense firewall as an alternative. 


cheers - Thor

---

### Post by daslinkard on 2012-09-24
I had a friend who had a similar issue with a canon and his work around was to add a printer and use the suggested drivers per Ubuntu.  What happens when you try this?

---

### Post by landstander on 2012-10-09
daslinkard

I'm having the same issue with the iP4300 printer. 

If I understand your instructions correctly, I believe that is the first thing most people try when installing a printer under Ubuntu. (Using the suggested default settings).

I haven't found any fixes for this yet, but if you were looking for a confirmation that this problem occurs with the default suggested settings during the installation process of a Canon iP4300 printer, I can can confirm that the problems that both the other two posters have mentioned are definitely happening after using the default settings.

I tried finding fixes for this for almost a month. No joy. I'm not optimistic about this anymore. I hope someone figures it out.

---

### Post by daslinkard on 2012-10-10
> **landstander said:**
> daslinkard

I'm having the same issue with the iP4300 printer. 

If I understand your instructions correctly, I believe that is the first thing most people try when installing a printer under Ubuntu. (Using the suggested default settings).

I haven't found any fixes for this yet, but if you were looking for a confirmation that this problem occurs with the default suggested settings during the installation process of a Canon iP4300 printer, I can can confirm that the problems that both the other two posters have mentioned are definitely happening after using the default settings.

I tried finding fixes for this for almost a month. No joy. I'm not optimistic about this anymore. I hope someone figures it out.
I found this in a related thread
Well - a minor miracle seems to have happened!```


Digging around in Ask Ubuntu, I found the references below.

I would like to know more of the background, but it looks as though one  Michael Gruz has set up a PPA which allows you to install a huge range  of Canon drivers via Synapt, which WORK - just like that!

I followed these steps:
1. Add the PPA to Synapt & accept that it is untrusted or whatever.
2. Reload Synapt.
3. Search 'cnijfilter'
4. Remove what I had, in my case cnijfilter-common & cnijfilter-ip4300 (if I remember right).
5. Install latest cnijfilter-common & cnijfilter-ip4300series
6. System Tools > Printing > Add > Follow all the defaults.

And it just works!

The guy deserves a medal !

Links:
[http://askubuntu.com/questions/97869...rinter-working]("http://askubuntu.com/questions/97869/how-do-i-get-my-canon-mx420-printer-working")
[http://www.ubuntubuzz.com/2011/06/do...er-driver.html]("http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html")
[https://launchpad.net/~michael-gruz/+archive/canon]("https://launchpad.net/%7Emichael-gruz/+archive/canon")
```

The post can be found [here]("http://ubuntuforums.org/showthread.php?t=1912988").  Check out the links and let me know if it works for you....if not let me know and I will do some more digging around for you!

---

### Post by landstander on 2012-10-28
daslinkard,

Thanks for the links. I did the following steps:
Step 1, Action:
sudo add-apt-repository ppa:michael-gruz/canon
Step 1, Results:
The repositories keyring and public gpa installed correctly and everything was ok so far.

Step 2, Action:
sudo apt-get update
Step 2, Results:
The repositories updated with the usual long list of hits and ignores, then the following lines towards the end:
W: Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

So it looks as if Michael's PPA is currently off-line.


A few things to note about the post you found these links in on ubuntuforums:
1.) The thread's subject line reads: "Canon iP4300 Printer in 11.10?"
This printing problem to my knowledge isn't happening in 11.10 but is present in 12.04 which is why the first poster "VanCardboardbox" mentioned he is booting into 11.10 whenever he needs to do his print jobs instead of 12.04 which can't print. I've so far decided to use a similar method (running 11.10 on a netbook and sending my printjobs to my netbook over the wireless network) until someone finds a fix that works in 12.04 so I can finally start printing from my desktop again.

2.) At post #6 on the ubuntuforums thread you found these links at, the same person who posted these links ("2CV67") states that he is unable to print duplex any more using Michael's cannon print drivers which almost makes it not worth it to install the fix.

In any case the engineering physics courses I'm taking are keeping me very busy and I haven't had much of a chance to trouble shoot this problem, so if any one else can jump in and help find a solution for Ubuntu 12.04 that would be really helpful.

Thanks.

---

### Post by drdos2006 on 2012-10-28
From your browser, can you connect via "http://<IP-address>:631" to access the CUPS administration screen ?

I have the same printer working on my equipment without issues.
Ubuntu 12.04, ASUS motherboard connecting to Gigabyte motherboard LAN connected computer with printer attached.

regards

---

### Post by pdc on 2012-10-28
this printer is 5 years old, and at that stage in the evolution of supporting linux, Canon made rpm packages available;

you can use alien to convert rpm packages to deb packages and install them

[http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html)

...... you need alien installed:

check with 

> [COLOR="Red"]sudo dpkg -l | grep alien[/COLOR]

.......and if not installed

> [COLOR="Red"]sudo apt-get install alien[/COLOR]

you don't say if you are using 32bit or 64bit ubuntu

you need to install 1) the common package and then 2) the ip4300 package

if you go here 

[http://support-asia.canon-asia.com/P/search?model=PIXMA+iP4300&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+iP4300&menu=download&filter=0&tagname=g_os&g_os=Linux)

and download the IJ Printer Driver Ver. 2.70 for Linux (rpm Common package)

and I suggest downloading and saving into your Downloads directory

if you issue the commands 

> [COLOR="Red"]cd Downloads[/COLOR]

and then 

> [COLOR="Red"]sudo alien -i cnijfilter-common-2.70-1.i386.rpm[/COLOR]

and then go to 

[http://support-asia.canon-asia.com/contents/ASIA/EN/0900719301.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0900719301.html)

to download the IJ Printer Driver Ver. 2.70 for Linux (rpm Package for iP4300)

and if still in your Downloads directory ........

> [COLOR="Red"]sudo alien -i cnijfilter-ip4300-2.70-2.i386.rpm[/COLOR]

that should install the ip4300 driver for you.............

---

### Post by landstander on 2012-11-29
_drdos2006_: I can't speak for the original poster but I'm using 64 bit, and yes I can access my printer via a web browser pointed at "http://<IP-address>:631".  Which motherboard do you have your ip4300 printer directly connected to, the ASUS or the Gygabyte?

_pdc_: As I've told drdos2006, I'm using 64bit Ubuntu 12.04. I've also tried using the force architecture option with alien using the drivers you've suggested but the printer still doesn't print.

_Note:_
One thing I have noticed is that if the ink levels are too low that it will start behaving the same in Ubuntu 11.10, (only prints half a sheet and then becomes unresponsive, randomly prints garbage etc). I have since installed a CISS (continuous inking system) which has solved that problem in Ubuntu 11.10. I will try once again to force the architecture of the suggested drivers from the last post, and if that doesn't work I'll check again to see if those other links posted earlier are still dead.

_A small rant_:
To argue that the printer is 5 years old and that i386 packages are available in rpm format is helpful and I'm thankful for at least that much but all versions of Windows support this printer out of the box and I hate Windows and Microsoft in general but just in terms of printer support its difficult to argue against there ability to get printers both old and new from all major manufactures to work with their machines, when Ubuntu can't. That is a small complaint for now though since printing from Windows still works, but I sure wish there was a way to stop supporting windows without having to buy a new printer every time the open source community decides a printer is to old to support any more.

_Final Question_: 
Does any one know where to find the main bug report for CUPS and or Gutenprint associated with the ip4300 printer running on 64bit Ubuntu 12.04?

I've found a few bug reports but nothing on that specific setup.

Thanks.

---

