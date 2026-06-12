---
title: "Brother HL-3040CN Won't Print"
date: 2010-10-21
forum: General Help
---

### Post by klausner on 2010-10-21
New 3040CN on 64-bit lucid. 

Test pages from console work fine. 

Cannot print using network or USB. Can http to printer on net, and system recognizes printer when USB attached.

Downloaded and installed Brother's cups & driver files (despite being labeled as 64bit, they were i386) No 3040CN found in driver selection listings! system-config-printer thinks the driver should be for an Epson Stylus Photo 2200!

Tried various generic and foomatic PCL printers.

Tried attachment to lpd://10.10.10.20/binary_p1 and socket://10.10.10.20:9100. No results with lpd address, jobs are just lost. With socket address, get blank pages.

Can't find an lpd file for this printer on line. 

[Had enough pain]("http://ubuntuforums.org/showthread.php?p=9411925#post9411925") getting a Brother HL-2170 to work. Should have learned.](*,)

Does one have a 3040CN working with Ubuntu? If so, what's the trick?

---

### Post by klausner on 2010-10-22
I want to express my profound disappointment in the lack of any response to this problem. I'm posting the solution to help others in the same mess, since there seem to be a lot of us.

Kudos go to Limulus on the [Linux Foundation Forums]("http://forums.linux-foundation.org/read.php?24,11074,12909#msg-12909") for the key to this fix.

Here's the process I finally got to work:
[LIST=1]
[*]Download the printer file and the cups wrapper from [Brother]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-3040CN").
[*]The web page says these are 64bit deb files, but they are not. If you run amd64, you have to install them using *dpkg --force-all*, or similar force option.
[*]Now here is the key. Once you've installed the packages, no print driver for the 3040CN will show up in the menu!!!
[*]Instead of picking a printer from the list, select *Provide a PPD File*.
[*]The printer package you installed from Brother will put a ppd file in either /usr/share/cups/model/brhl3040cn.ppd and/or /usr/share/ppd/brhl3040cn.ppd. Enter this into the install dialogue.
[/LIST]

Once you've done that, you should be good to go. I wasted three days because Brother's instructions (and tech support) were to half-assed to include this little gem of information. May you have better luck!

---

### Post by TroyDowling on 2010-11-28
Aha, this solves my problem with my MFC990CW. Thanks a tonne. I'm going to fire off an email to the local Brother rep. Hopefully she can escalate that. It's a minor fix to their documentation that makes all the difference in the world.

---

### Post by morrie on 2011-03-28
Thanks, Brother.

I had it setup, and remember it was a pain.  Did it just the way you described.
But,
I got a new router and now the network printer doesn't work.  I re-installed it and even tried re-discovering it in the driver.  It's not fair that this mistake causes so much trouble.   Brother messed up on this one.  I had previously chosen Brother for their Linux friendliness, but I have to say this printer's support in Ubuntu is ..  crappy

I know that the driver was bad enough to have to manually setup myself, and now  I have no idea where to start in troubleshooting this.  My network is the same, all the computers kept their same IP's, but the printers all had to be reinstalled. (Not sure why)  And I sure don't know why reinstallation didn't work on Ubuntu as it did with Windows.:confused:

---

### Post by klausner on 2011-03-29
> **morrie said:**
> Thanks, Brother.

I had it setup, and remember it was a pain.  Did it just the way you described.
But,
I got a new router and now the network printer doesn't work.  I re-installed it and even tried re-discovering it in the driver.  It's not fair that this mistake causes so much trouble.   Brother messed up on this one.  I had previously chosen Brother for their Linux friendliness, but I have to say this printer's support in Ubuntu is ..  crappy

I know that the driver was bad enough to have to manually setup myself, and now  I have no idea where to start in troubleshooting this.  My network is the same, all the computers kept their same IP's, but the printers all had to be reinstalled. (Not sure why)  And I sure don't know why reinstallation didn't work on Ubuntu as it did with Windows.:confused:

I suspect the IP address of the printer is wrong. Ping the address to see if it responds. Log into the router (or switch if you use one), and see if there is a list of attached devices.

---

### Post by xinel on 2011-05-27
this is what i did

To get the brother HL-3040CN to print using ubuntu 11.04 64bit

Go to this website
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-495CW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-495CW)

Download the LPR driver
Download the cupswrapper driver

follow these steps

sudo mkdir /var/spool/lpd

sudo dpkg -i --force-all hl3040cnlpr-1.1.1-4.i386.deb

sudo mkdir /usr/share/cups/model

sudo dpkg -i --force-all hl3040cncupswrapper-1.1.1-4.i386.deb

You then go to system -> admin -> printing

add new printer

network printer

put in the ip address

hit next

when it asks for the driver select ppd from file

the ppd file is located in: /usr/share/cups/model/brhl3040cn.ppd

hit enter a few times

finished

---

### Post by spoupard on 2011-08-08
Many, many thanks for posting this. I was about to pull my hair out. These instructions allowed me to get printing within a matter of minutes.

---

### Post by frogotronic on 2011-08-19
> **klausner said:**
> I want to express my profound disappointment in the lack of any response to this problem. I'm posting the solution to help others in the same mess, since there seem to be a lot of us.

Kudos go to Limulus on the [Linux Foundation Forums]("http://forums.linux-foundation.org/read.php?24,11074,12909#msg-12909") for the key to this fix.

Here's the process I finally got to work:
[LIST=1]
[*]Download the printer file and the cups wrapper from [Brother]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-3040CN").
[*]The web page says these are 64bit deb files, but they are not. If you run amd64, you have to install them using *dpkg --force-all*, or similar force option.
[*]Now here is the key. Once you've installed the packages, no print driver for the 3040CN will show up in the menu!!!
[*]Instead of picking a printer from the list, select *Provide a PPD File*.
[*]The printer package you installed from Brother will put a ppd file in either /usr/share/cups/model/brhl3040cn.ppd and/or /usr/share/ppd/brhl3040cn.ppd. Enter this into the install dialogue.
[/LIST]

Once you've done that, you should be good to go. I wasted three days because Brother's instructions (and tech support) were to half-assed to include this little gem of information. May you have better luck!

Worked perfectly on 10.10 - didn't need to manually link to the PPD file.

Thanks,
CH

P.S.  I have a Brother HL3070CW that is also working well with Ubuntu.

---

### Post by dmintz on 2011-10-24
I followed these instructions faithfully more times than I care to remember and kept getting errors when I tried to print -- printer not enabled. So I'd re-enable, attempt to print, then get the same error again.

I finally noticed some error briefly appear saying "unable to locate printer." Ah. You see, when I stepped through the installation screens the printer presented itself as "BRN001BA97D9D08" and I accepted it. I thought maybe in the Device URI field I should put in the IP address instead.

Ding!

I don't know much about printers and networking, but I kind of wonder if this has something to do with the fact that right after I did the physical setup of the printer, I went into the web-based admin interface and set the "boot method" to "static" to make its IP static. It seemed like a good idea at the time, and the docs to my other little print server thingy say that static IP will give you "more stable" performance. Now I wonder if the static IP had the ironic effect of making "BRN001BA97D9D08" unlocatable.

Anyway, all this is to say, if all else fails, try substituting the actual IP for the funny string Brother gives you in the Device URI setting. :p

---

### Post by MadMax2 on 2011-10-25
I'm using 11.10 I followed:

> **xinel said:**
> this is what i did

To get the brother HL-3040CN to print using ubuntu 11.04 64bit

Go to this website
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-495CW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-495CW)

Download the  HL3040 LPR driver (deb)
Download the HL3040 cupswrapper driver (deb)

follow these steps

The files were installed by the software center program [aptitude??] although they came with a warning that the files weren't of good quality which you had to override.

Then I went to

 system -> admin -> printing (in the top right hand corner... just discovered)

and that was it. 

So far it is printing o.k but I haven't tested all it's functions.

---

### Post by tep200377 on 2011-12-26
Thanks alot, finally got it to work :)

---

### Post by Sabonmu on 2012-01-13
> **klausner said:**
> I want to express my profound disappointment in the lack of any response to this problem. I'm posting the solution to help others in the same mess, since there seem to be a lot of us.

Kudos go to Limulus on the [Linux Foundation Forums]("http://forums.linux-foundation.org/read.php?24,11074,12909#msg-12909") for the key to this fix.

Here's the process I finally got to work:
[LIST=1]
[*]Download the printer file and the cups wrapper from [Brother]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-3040CN").
[*]The web page says these are 64bit deb files, but they are not. If you run amd64, you have to install them using *dpkg --force-all*, or similar force option.
[*]Now here is the key. Once you've installed the packages, no print driver for the 3040CN will show up in the menu!!!
[*]Instead of picking a printer from the list, select *Provide a PPD File*.
[*]The printer package you installed from Brother will put a ppd file in either /usr/share/cups/model/brhl3040cn.ppd and/or /usr/share/ppd/brhl3040cn.ppd. Enter this into the install dialogue.
[/LIST]

Once you've done that, you should be good to go. I wasted three days because Brother's instructions (and tech support) were to half-assed to include this little gem of information. May you have better luck!
This worked me using Mint 9 on a Thinkpad T400.
The location was:
/usr/share/cups/model/brhl3040cn.ppd 

Many thanks!

---

### Post by DragonDionysius on 2012-01-25
I want to add that in my case I needed to use the connection type: "LPD network printer via DNS-SD".

I had the problem not able to print anything, like its not able to send the job to the printers queue. system-config-printer recognise the network printer well automatically, but it seems, the first entry in the connections list ("IPP network printer via DNS-SD) is wrong. So I tried (after many times other tries) to add the new Printer with connection type "LPD network printer via DNS-SD". And it works now!

Hope it helps someone.

---

### Post by rcstook on 2012-01-25
> **DragonDionysius said:**
> I want to add that in my case I needed to use the connection type: "LPD network printer via DNS-SD".

I had the problem not able to print anything, like its not able to send the job to the printers queue. system-config-printer recognise the network printer well automatically, but it seems, the first entry in the connections list ("IPP network printer via DNS-SD) is wrong. So I tried (after many times other tries) to add the new Printer with connection type "LPD network printer via DNS-SD". And it works now!

Hope it helps someone.


This is what fixed my MFC-495CW printer not printing.
Though now I"m getting constant status that the printer is out of ink.
I know this is not true and the test pages print just fine.

Any thoughts on the constant 'out of ink' statuses?

---

### Post by MadMax2 on 2012-02-07
I've changed something and can only print text in book form (i.e landscape with two pages per sheet).

Am changing settings but no luck.

---

### Post by brotheruser on 2012-05-12
The Brother HL-3040CN is a GDI printer that needs a special driver from brother in order to print with linux.

The installation is very easy:

1. Prerequisites
```
sudo mkdir /var/spool/lpd/
sudo chown lp:lp lpd/
```

2. Download .deb driver packages from brother
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-3040CN](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-3040CN)
```

wget http://www.brother.com/pub/bsc/linux/dlf/hl3040cnlpr-1.1.2-1.i386.deb
wget http://www.brother.com/pub/bsc/linux/dlf/hl3040cncupswrapper-1.1.2-1.i386.deb

```

3. Install driver
```

sudo dpkg -i hl3040cnlpr-1.1.2-1.i386.deb
sudo dpkg -i hl3040cncupswrapper-1.1.2-1.i386.deb

```

The printer is automatically installed as usb printer now.

If you are using the printer attached to a LAN, you may change the port to be: ipp://192.168.xxx.yyy/ipp or ipps://192.168.xxx.yyy:631/ipp or you let the printer settings dialogue search for your printer.

Now, check all the other printer settings like page size A4 and others.


Have a nice day!

Could someone file a bug so that this wrapper will be included in a future ubuntu release?

---

### Post by pdr2esmolbra on 2012-05-24
Hi everyone,

Just wanted to thank you guys for the post, helpful links!

In my case, running 12.04 in a x86_64, the driver installation from Brother failed because of broken packages :(

But I went to this site:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

and followed their instructions with their bash scripts using the name "3040CN".

My network printer worked when I chose the option 11 below:

0: ipp
1: ipps
2: smb
3: lpd
4: beh
5: https
6: http
7: socket
8: dnssd://Brother%20HL-3070CW%20%40%20bionik-DX4840._ipp._tcp.local/cups
9: dnssd://Brother%20HL-3040CN%20series%20%40%20bionik-DX4840._ipp._tcp.local/cups
10: dnssd://Brother%20HL-3040CN%20series._ipp._tcp.local/
11: dnssd://Brother%20HL-3040CN%20series._pdl-datastream._tcp.local/
12: dnssd://Brother%20HL-3040CN%20series._printer._tcp.local/
13: hp
14: hpfax
15: lpd://BRN001BA966D055/BINARY_P1
16 (I): Specify IP address.

The others didn't? (10, 15, or even 16 putting number by hand!) I don't know why :P

Cheers, 
Pedro

---

### Post by kline on 2012-06-23
Thanks++ for your instructions above.  I installed 12.04 in April and have run into  a problem with load.  The next thing was my Brother 3040CN.  It worked fine on 03 June last.  When I tried it Friday, 22 June, nada.    [[ FWIW, I had two weeks of troubles in 2010... ]]  I tried everything I could find, including thed /sh/bash script you pointed at.  The first couple times, no joy.  Third times, the script ran to completion, and *yes*, lpr worked.  Then the word-processor file worked.  

Sometimes, persistance and patience pay off, :-)

gary

---

### Post by absorbubu on 2012-10-16
This thread has been a life saver. I was ready to uninstall linux and go back to my old os. Not mentioning where the .ppd file is located seems to be a MAJOR oversite.
Cheers :)

---

### Post by pdc on 2012-10-16
............you needed to locate the ppd file to get it running?

---

### Post by bonzini on 2012-10-24
Just to confirm that the instructions as given by Xinel above (on the first page of this thread) work just fine in 12.10.

I did not deviate from the instructions to see if the install had put the ppd in a place where the printer install could find them.

Thanks Xinel!!!!

---

### Post by baybe1111 on 2012-12-03
Hi, I found a new problem here and a solution, so share and enjoy.
On 12.10, the preceding did not work, neither did they work with 12.04, nor 11.04. At this point in desperation:

I finally got this to work doing something very unscientific. 
After doing everything on [http://ubuntuforums.org/showthread.php?t=1602075&page=3](http://ubuntuforums.org/showthread.php?t=1602075&page=3) 
I went to Synaptic and searched for anything containing Brother
Installed all the packages.
Sent a test page, and Bingo- it works.
Not sure what did it, but one of those packages did.

Hope this helps someone who is unfortunate enough to own a Brother printer.

---

### Post by pdc on 2012-12-03
If you copy and paste the command

> [COLOR="Red"]sudo dpkg -l | grep Brother[/COLOR]

...and copy and paste the results back .....

.....it will list what drivers you have installed ....that might be very helpful to folks ...........

---

### Post by dingo on 2013-01-04
Xinel's procedure didn't work for me on 12.10 64 Bit (printer hooked to USB) until I did:

```
sudo apt-get install brother-lpr-drivers-extra brother-cups-wrapper-extra
```

This brought in a number of other packages:

```
The following NEW packages will be installed:
  a2ps brother-cups-wrapper-common brother-cups-wrapper-extra
  brother-lpr-drivers-common brother-lpr-drivers-extra csh lib32gcc1
  libc6-i386 psutils wdiff
```

After that, I was able to add the printer (using the .ppd file) and if worked fine.

---

### Post by MarcoBumussi on 2013-05-06
As instruções dadas pelo [B][COLOR=#000000][xinel]("http://ubuntuforums.org/member.php?u=1161") foram perfeitas e com elas a minha impressora funcionou 100%.

O suporte da Brother simplesmente não auxiliou em nada.

Parabéns e obrigado.

[/COLOR][/B]

---

### Post by oldos2er on 2013-05-06
Please post in English.

---

### Post by hebein on 2013-10-28
Addendum:

If using 64bit Linux, do not forget to

[SIZE=6][COLOR=#ff0000]sudo apt-get install ia32-libs[/COLOR][/SIZE]

so that you can use the 32bit libraries with your 64bit Linux.

---

### Post by marcel4 on 2013-11-11
Thanks, klausner, for posting [your own answer here]("http://ubuntuforums.org/showthread.php?t=1602075&p=10012790#post10012790"). This, plus most probably the the installation of the 32bit libs helped me to use my Brother HL-3040CN printer on Ubuntu 12.04 64bit.

---

