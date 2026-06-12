---
title: "Canon Pixmaip1000 Printer Install"
date: 2012-10-02
forum: General Help
---

### Post by Repip on 2012-10-02
Hello,
I have been trying Linux for the past several years on and off ... and I am now trying again, this time with Ubuntu 12 (the latest),however each time I get very frustrated and give it away as I cannot get a printer to work.
This I would have thought would be a very basic and simple task (as it is in Windows, insert a disk and press the "Ok" button) however not so in Linux, thats Ok I am willing to try something different.
 The printer(s) I have are Canon Pixma ip1000, Canon Pixma ip1900, very simple basic machines take up little desk space, are able to be refilled by me, and are nothing fancy.
I have been reading forum questions/answers and have done what I think is correct ie downloaded the correct drivers/software package and installed it.
sudo apt-get install cnijfilter-pixmaip1000series
selected the Canon Pixma iP1000 Ver.2.50 driver when asked to
changed the permissions sudo chown root:root/usr/lib/cups/filter/pstocanonbj
tried to print a test page and all that happens is ..... nothing ....
I have been at it for 3 days (on and off) this time and have run out of ideas ....help ... please .... or its back to XP ......

---

### Post by pdc on 2012-10-02
the linux scene has been changing rapidly in recent years......

......as has canon, who now provide linux drivers for all new printers;

......whereas, when your printers were produced, they often only made rpm packages available........

however if you go here

[http://ubuntuportal.com/2011/12/how-to-install-canon-printer-driver-for-linux-ubuntu.html](http://ubuntuportal.com/2011/12/how-to-install-canon-printer-driver-for-linux-ubuntu.html)

and follow the instructions, many advocate installing Michael Gruz's ppa where he holds many canon drivers:

it would seem the commands are:

> sudo add-apt-repository ppa:michael-gruz/canon

> sudo apt-get update

> sudo apt-get install cnijfilter-pixmaip1000series

.....let us know how you get along.......

---

### Post by Repip on 2012-10-02
Thanks pdc I tried all this again (i think I went to this site before) and this is what i got 
sudo add-apt-repository ppa:michael-gruz/canon

You are about to add the following PPA to your system:
 
 More info: [https://launchpad.net/~michael-gruz/+archive/canon](https://launchpad.net/~michael-gruz/+archive/canon)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpoR1IqI/secring.gpg' created
gpg: keyring `/tmp/tmpoR1IqI/pubring.gpg' created
gpg: requesting key 3F7B4A1D from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpoR1IqI/trustdb.gpg: trustdb created
gpg: key 3F7B4A1D: public key "Launchpad Misakovi" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK

$ sudo apt-get update

a whole lot of stuff downloaded &#8230;......

Fetched 1,538 kB in 11s (137 kB/s)                                             
W: Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


$ sudo apt-get install cnijfilter-pixmaip1000series
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package cnijfilter-pixmaip1000series


so I guess that this means there are no packages for the Pixmaip1000 series ??
However I did get a package from another site named 'ip1000-driver for debian based systems.deb' whatever that all means ... I installed that by double-clicking on the file and the Software centre opened and loaded it, I was then able to pick the correct driver from the Printer driver list, however still no go ?? 
I am at a loss ... it all just seems too hard ... pity

---

### Post by Repip on 2012-10-02
this is the site I used 
[http://akuwinlinux.blogspot.com.au/2010/01/problem-install-printer-canon-pixma.html](http://akuwinlinux.blogspot.com.au/2010/01/problem-install-printer-canon-pixma.html)

---

### Post by Repip on 2012-10-02
do I need to uninstall all the stuff I have previously tried out of usr/lib/cups/filter , can you uninstall in Linux ??? or do I need to re-install the whole application (Ubuntu Ver 12.04) and start all over again ??

---

### Post by pdc on 2012-10-02
I would go to the Printers section of your system setup;

and delete any printer entry there:

........I can suggest sites to go to; to download ip1000 drivers; the very suspicious would say: beware: there could be bad things in them; the odds are that such is very unlikely; but I thought to mention it ..

so I googled on 

> ubuntu solved canon ip1000

and got this link

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon)

Canon; and Brother: and Epson; as you will know; are all Japanese companies...... so this thread is from there:

the maintainer suggests you copy and paste the following commands into a terminal; and do the usual.......

> deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/debian](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/debian) ./ 

and 

> sudo apt-get update 

and then 

> apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj 

he comments

> *Cupsys will be automatically restarted* and you can select printer in cupsys configuration ([http://127.0.0.1:631/printers/](http://127.0.0.1:631/printers/)).

It seems a very fair site; I can only suggest you try it to get your printer working;

Canon now provide drivers for all new printers; so for the MG2160 that cost us the equivalent of $US40 recently: I downloaded the debian package and had all running in less than a minute

let us know how you get along............

_______________________________________________________________________________________________________________________-


by the way, if you struggle with the above;

go here;

[http://www.turboprint.info/download.html](http://www.turboprint.info/download.html)

turboprint have supplied drivers for years.......they started on the Amiga back in the 1980s........ it is their business so they charge you a small sum; so they can put food on the table;

we used turboprint for our ip5000: it worked very well

---

### Post by Repip on 2012-10-03
Thankyou again pdc, I have actually reloaded the complete application  again (clean install), it didn't take long as i haven't transferred any  of my files onto this computer as yet, wanted to make sure the 'basics'  work first.
I did experiment with other printer I have a Canon ip1900 and found this site
[http://akuwinlinux.blogspot.com.au/2010/01/problem-install-printer-canon-pixma.html](http://akuwinlinux.blogspot.com.au/2010/01/problem-install-printer-canon-pixma.html)
downloaded the .deb file from 
[http://dl.dropbox.com/u/2858471/ip1000-driver%20for%20debian%20based%20systems.deb]("http://dl.dropbox.com/u/2858471/ip1000-driver%20for%20debian%20based%20systems.deb")
the other 2 recommended download sites don't appear to work (for me anyway)
and I did as per the site recommended and the Canon ip1900 worked fine.
However  no joy with the Canon ip1000, so I found the Turboprint site (I  actually used it several years ago with another Linux application I  tried , may have been Fedora ??? I have tried them all over the years)  .. anyway Turboprint installs quickly and WORKS with Canon ip1000, so  far I am using the 30 day trial version.
I actually have 2 machines on the go at the moment with Linux and am experimenting,  if I cant get the ip1000 going on the machine without Turboprint  installed I may consider forking out the 30 euros to purschase it.
The  reason i like the ip1000 is that it has ink tanks and is really easy to  refill -  no chips to monitor ink levels- and you only need the black  tank - a really basic printer - takes up so little desk space as well.
It  is a pity that Turboprint can actually get the print function to work  but it appears that no-one else can ?? I wonder if they use a different  'print method'  all very strange !
Anyway thanks again for your help,  my next 'challange' will be to get a Video Editor in Linux that will  open and edit .TS and .MTS files , the type that are produced in TV  PVRs, I have tried a few recommendations from the Linux sites however  they all have failed to open the files, the Editor I use in Win XP is  Squared 5 MPEG Streamclip, haven't found an equivalant in Linux yet so  I'll be on the Forums looking for that soon (after I get the printer  working)
regards

---

### Post by pdc on 2012-10-03
>  the Canon ip1900 worked fine.

........great.........

> anyway Turboprint installs quickly and WORKS with Canon ip1000

......excellent........

> It is a pity that Turboprint can actually get the print function to work but it appears that no-one else can ??

........I guess it is their business/livelihood: they have supported printer drivers since the 1980s: firstly with the Amiga.....so they know all the ins and outs........

> The reason i like the ip1000 is that it has ink tanks and is really easy to refill

........great.......turboprint may be just the job: 

____________________________________________________________

> my next 'challange' will be to get a Video Editor in Linux that will open and edit .TS and .MTS files

......interested to hear how you get along; I used a "bought" video editor made by a company in Aachen: linux is free, as in thought, but not necessarily as in beer: as Red Hat show so well........... it was "tuned" for Suse 9.3 and I still have that version running; I haven't done any editing for a while now: but it worked well: I used a firewire connection off a Panasonic camera; 

......I had a look at some of the new video editors being developed; that were free; as in beer; I couldn't get them going so well as what I was used to......I hope you do better

have you had a chance to evaluate OpenShot?

[http://www.openshot.org/features/](http://www.openshot.org/features/)

the authors are very hopeful of what it will achieve

---

### Post by Repip on 2012-10-03
again thanks pdc 
I tried the Japanese site
 [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon)
and no luck there either with the ip1000 so I'll probably pay my hard earned dollars to Mr Turboprint, what i spend on getting the Turbo program I will save on buying ink for newer printer types (I also have a Canon MP280 which only cost $38 however the new ink tanks cost more than the printer -and it takes up too much desk space)
So this little exercise taught me lots about command lines and finding my way around Ubuntu - so not completely wasted -
I will try the Video Editor OpenShot.
Thankyou for your indulgence with me ...
regards
Repip

---

### Post by pdc on 2012-10-04
when you said this

> So this little exercise taught me lots about command lines and finding my way around Ubuntu

.....it sent me off searching again........

Canon make linux drivers for the ip1000 I find;

they are rpm packages..........for Red Hat etc.......

however a programme called alien ......should convert and install....

.....if not installed, install with 

> sudo apt-get install alien

.........if you want, read about alien here.......

[http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html)

so .......suggestion......

......go to Canon Asia.......download........

[COLOR="Red"]Canon Bubble Jet Print Filter Ver. 2.50 for Linux (rpm Common package)[/COLOR]

[http://support-asia.canon-asia.com/contents/ASIA/EN/0900717601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0900717601.html)

and install with 

> sudo alien -i bjfilter-common-2.50-3.i386.rpm

then download and install the *specific driver for the ip1000*

[COLOR="Red"]Canon Bubble Jet Print Filter Ver. 2.50 for Linux (rpm Package for iP1000)[/COLOR]

from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0900717801.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0900717801.html)

and install with 

> sudo alien -i bjfilter-pixmaip1000-2.50-2.i386.rpm

.........you know........that should do it..........

.I would be happy to trust Canon Asia for having a clean site.......

---

### Post by Repip on 2012-10-04
Thanks again pdc you are too kind ...
I haven't come across those sites ..
I have downloaded all above, will get my head around Alien and try over the weekend, will let you know
I hope it works 
regards

---

### Post by pdc on 2012-10-04
> will get my head around Alien and try over the weekend

.....that would give you valuable knowledge..

....but if you just copy and paste the commands in my post, 

.....I would hope it would all work ....just like that..as Tommy Cooper might have said...........

---

### Post by Repip on 2012-10-07
Hi
Tried all of the above ... no luck ...cannot get a peep out of the Canon Pixmaip1000 except by using TurboPrint.

Thanks for all the help and suggestions however none work for this printer.
Might re-visit it sometime when I learn a little more about the code that drives the CUPS program.
I even tried installing SUSE and that didn't work for the ip1000 either.
So its TurboPrint .. I've wasted enough time ..
thanks

---

