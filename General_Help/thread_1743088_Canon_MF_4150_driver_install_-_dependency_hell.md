---
title: "Canon MF 4150 driver install - dependency hell"
date: 2011-04-29
forum: General Help
---

### Post by Gene Pool on 2011-04-29
Hello this is my very first post. I have spent a couple hours tracking leads on other posts relating to installing .deb drivers for my Canon MF4150 printer/scanner. From what I read, I should rule out using the scanner.

My immediate need is to get the printer driver installed.

I downloaded the driver and opened the folder for 32 bit systems, in it there were two .deb files

cndrvcups-common_2.10-1_i386.deb 
and cndrvcups-ufr2-uk_2.10-1_i386.deb

When I try to extract these each one seems dependent on the other "Dependency is not satisfiable: gs-esp" and "Dependency is not satisfiable: cndrvcups-common (>= 2.10)"

I extracted these files to my home directory - Is there a better place to start the .deb install process?

I followed the instructions in the following thread: [http://ubuntuforums.org/showthread.php?t=1592487](http://ubuntuforums.org/showthread.php?t=1592487)

and installed this transitional package [http://security.ubuntu.com/ubuntu/po...ntu1.2_all.deb]("http://security.ubuntu.com/ubuntu/pool/universe/c/cups/cupsys_1.4.3-1ubuntu1.2_all.deb")

I would really like to understand the process of unzipping the file, saving it to the correct place, and installing it using the command line if possible, but just getting my printer running would be great.

---

### Post by dino99 on 2011-04-29
try this:

[https://numberformatdata.wordpress.com/2010/05/09/ubuntu-printer-installation-of-canon-mf4150/](https://numberformatdata.wordpress.com/2010/05/09/ubuntu-printer-installation-of-canon-mf4150/)

---

### Post by Gene Pool on 2011-04-29
Thanks, I'll try that approach. In the command below what is the "--scripts"? Do I need to omit or put in an appropriate script or erase it?

sudo alien --scripts pkg-name.rpm

---

### Post by Gene Pool on 2011-04-29
Also, one more noobie question. where should i save the .rpm file when I extract it? is there a best place to always save these files? In other words, where will the following commands look for the pkg? Thanks!

sudo alien --scripts pkg-name.rpm
sudo dpkg -i pkg-name.deb

---

### Post by Gene Pool on 2011-04-30
I figured out how to install the driver, but it took over six hours over a couple days. I am so new to Linux though that at least some of my problems were not specific to the issue. At one point I was almost ready to go buy a new printer that was compatible with Ubuntu.

In order to hopefully help anyone trying to do this in the future and to try to remember the lessons I learned, I wrote a full procedure below. A good software install primer is available at: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

I have a four-year-old Dell Latitude D610 laptop and was running Natty Narwal. 

The linux driver for the MF 4100 Series printers and many others is available from Canon at:

[http://software.canon-europe.com/software/0038852.asp](http://software.canon-europe.com/software/0038852.asp)

The most useful information that I found through the help of this forum was at the following post:

[https://numberformatdata.wordpress.com/2010/05/09/ubuntu-printer-installation-of-canon-mf4150/#comment-39](https://numberformatdata.wordpress.com/2010/05/09/ubuntu-printer-installation-of-canon-mf4150/#comment-39)

In the post, the user tells us that the .deb file that is included in the linux driver from canon doesn't work, but that using the program Alien, one can convert the .rpm file to a separate .deb file that for some reason DOES work. I spent my first few hours just trying the canon .deb file.

For someone like me (brand new to linux), there were a some details that I didn't understand which caused my confusion. The first of which was simply where to extract the .rpm

After installing Alien, I extracted the .rpm file to my desktop, then opened the Konsole and moved to the desktop directory using the "cd desktop" command. From that directory, I ran the following commands:

user-laptop:~/Desktop$ sudo alien --scripts cndrvcups-common-2.10-1.i386.rpm
user-laptop:~/Desktop$ sudo alien --scripts cndrvcups-ufr2-uk-2.10-1.i386.rpm

Then:

user-laptop:~/Desktop$ sudo dpkg -i cndrvcups-common_2.10-2_i386.deb ; sudo dpkg -i cndrvcups-ufr2-uk_2.10-2_i386.deb

Next I restarted the Cups Daemon by issuing the following command

sudo service cups restart

and mapped by putting the following URL in my browser: [http://localhost:631/admin/](http://localhost:631/admin/) 

The two above steps were found on the following thread: [http://technostripe.com/?p=246](http://technostripe.com/?p=246)

That did it.

Lastly, I erased the .deb files from the desktop - which I am not sure is correct. I would appreciate if someone replys with the best location to install software from. Perhaps it doesn't matter? Is erasing the .deb or .rpm file ok? 

Good luck and hope it goes faster for you.

---

### Post by thaegen on 2011-06-14
Thanks for the post, Gene Pool.  That worked for me with a MF4350d.  8)

---

### Post by sytoby on 2011-07-24
Thank you very much for your post.  Because of it, I was able to fairly easily get my MF4150 working.  Again thanks a lot.

---

### Post by dancingLoki on 2011-09-26
I have the same printer...ya think someone would make installing printer drivers easier - it's really a newbie thing to want to do.

For some reason it installed easily when I was running wubi.  never tried the scanner - but why shouldn't the scanner & fax work in Linux too?  Does this depend on Canon to write drivers or is there a generic driver that works?  How about running the virtual windows I've heard about - will drivers work there?

damn, I get the following error: 
>  
alien : Depends: rpm (>= 2.4.4-2) but it is not going to be installed
         Depends: rpm2cpio but it is not going to be installed
 cndrvcups-common : Depends: gs-esp but it is not installable
 debhelper : Depends: html2text but it is not going to be installed
             Depends: po-debconf but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


Now I went to "synaptic package manager" to look for aptitude & it says I have a broken package.  I try running the filter & nothing obvious results - unless its all those packages with green in the box...but says I have 1 broken package, not hundreds...

Ok - seems the broken package was from my previous attempts to install the printer drivers.  I followed all the instructions above, but still can't print!!!  Do I need to restart the computer?

I did get this message: > Use of uninitialized value $postinst in length at /usr/share/perl5/Alien/Package/Deb.pm line 750, <GETPERMS> line 44.
 - could this be the problem?  And I have Ubuntu's latest (11.04) - why does there appear to be no automatic installer for drivers?

---

### Post by dancingLoki on 2011-09-26
Restarted AND IT STILL DOESN'T WORK!!!  I can't afford to buy a new printer, idea of using Linux was to avoid hassles of windows...but at least windows could install printer drivers!

Please help.  I have no desire to become a Linux techie, I just want a very basic setup to work!:frown::frown:

---

### Post by Chuy42 on 2013-01-29
I've tried to install my Canon MF4100 for several months and nothing has worked, even the suggestion by Gene Pool. It's been frustrating!!!!

---

### Post by pdc on 2013-01-29
Hi Chuy42; you seem very frustrated and disappointed;

the forum administrators will close this thread as it is OLD:

please start a new thread; please tell us if you use 32bit or 64bit: please let it be 32bit.....and the release of Ubuntu? you are using

.....and maybe a little of what you did to install the printer driver

I am guessing you downloaded something like the [COLOR="SeaGreen"]Linux_UFRII_PrinterDriver_V250_uk_EN.tar.gz[/COLOR]

---

### Post by Chuy42 on 2013-02-18
I have a 64 bits system and I used the file [COLOR=SeaGreen]Linux_UFRII_PrinterDriver_V250_uk_EN.tar.gz.
[/COLOR]

---

