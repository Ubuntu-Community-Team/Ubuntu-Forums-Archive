---
title: "Canon all-in-one laser printers"
date: 2011-04-06
forum: General Help
---

### Post by 1clue on 2011-04-06
Hi,

I have found several people who have had problems with Canon all-in-one laser printers.  I had huge problems when I first set mine up because it wasn't in Synaptic yet.

There are threads on the forum addressing specific printers, but since the driver wasn't officially supported for very long I think lots of folks have given up the fight.

My thought is that anyone who successfully installed a Canon laser should be able to post to this thread, and/or a link to threads on this or other forums which they found helpful in getting it to work.

The driver as it is shown in Ubuntu 10.10 is **cndrvcups-ufr2-uk**, and **cndrvcups-common**.

I have a Canon ImageClass MF8050CN color networked laser which works perfectly with this driver.  It supports the networking, although it takes a couple minutes to populate the list of printers when you're setting up.  I have not tried the USB port since I have no use for that type of configuration.  I have not tried scanning to the computer, only to the USB stick, which works fine.

Thanks.

---

### Post by Fraoch on 2011-04-07
Thanks for starting this thread, I'm following you over from another thread and I'll post here rather than hijack that one.:)

First of all, you said in the other thread and implied here that cndrvcups-ufr2-uk and cndrvcups-common are in the repos.  Which repo?  I wasn't able to find it so I downloaded it from the Canon Australia website as directed in another thread.  It was version 2.20.

Unfortunately it looks like my old (2005 era) imageCLASS MF5770 isn't supported.  There's no PPD file in the driver for it and similar-looking PPDs (i.e. "MF5800") don't work.

The printer is not detected over the network and I had to guess at several steps - entering the IP address then selecting the default "PASSTHRU" which I didn't understand.

I tried doing it via USB as well, two printers are detected - MF5770 and MF5770 FAX but neither work because none of the PPD files seem to operate it.

Since I'm running 64-bit, I made 64-bit .deb files from the 64-bit .rpm files using alien.  I'll try the 32-bit .deb files.  They might not work, but I just want to see if there is an MF5770 PPD there.

I had high hopes this would finally get the printer to work in Linux.  It's too bad, I guess other than the fact that it isn't supported in Linux or my fiance's Mac, it's not bad.  There's no off switch and most errors have to be cleared by unplugging it and waiting 3 minutes :rolleyes: but I can't say there's been problems with paper jams or the auto document feeder.  It prints quite fast, the fax is full-featured, the networking is solid, it runs a web configuration page at its IP address, the envelope bypass slot works well and the toner lasts a long time.  I only just got my first toner low message a few months ago and the counter indicates I've printed over 3000 pages.

If only Canon would cooperate with the Linux community more!  Among printer manufacturers they seem to be the last holdout.

---

### Post by Fraoch on 2011-04-07
Ack, checking the readme I see that the MF5770 is not supported.:(

End of the line for me then.

---

### Post by 1clue on 2011-04-07
Sorry to hear about this, but it's not necessarily the end of the line.  You might want to try to find out what other printers were in the same "family" and then google Linux and any of those printers.  Printer manufacturers always build a bunch of models that all behave the same way, and if somebody else built from modified source you might either be able to make the same changes or, possibly, convince some developer to do it so it benefits everyone with those models.

This is, after all, the basic premise behind Open Source.  If you can find a bunch of other guys who would all donate a few bucks to pay a developer, if none are willing to volunteer it, then that might get the job done too.

---

### Post by Bagh33ra on 2011-04-09
Good start of a thread, I guess my experience fits in nicely here. Just bought a Canon i-Sensys MF8030Cn and spent most of the afternoon getting it installed, especially on 64bit Ubuntu (10.10, Maverick Meerkat).

In the end it was really easy, but finding the information i needed was not: 

The driver can be obtained directly from Canon. This printer is supported by the  "UFRII/UFRII LT Printer Driver for Linux v2.20", which supports a lot of other Canon printers too (see list at the end of this posting). The driver file I downloaded was o1113enx_l_ufr220.zip, there seems to be many variants (languages?).

Canon provides .deb packaged drivers for 32 bit systems, but only (RedHat) rpm for 64 bit. The 32bit .deb packages worked nicely "as is" on my 32bit laptop, but my 64 bit desktop needed some more. Luckily the rpm converted nicely to debian/ubuntu using alien. So once I got the rpm packages unpacked on my system all I needed to do was,

sudo apt-get install alien
sudo alien -i /path/to/file.rpm (for both drivers in the package) 

and once that was done CUPS recognized the printer in the normal "add printer" process.

Have not done anything more than a few test prints, and only over network (not USB), but this far it looks good. Asfaik no driver exists that would enable the scanner, but this model has the nice option to scan directly to a usb-stick.

According to the readme file, this driver should work with the following printers: 

LBP3360
LBP3370
LBP3460
LBP5360
LBP5960
LBP5970
LBP5975
LBP6650dn
LBP6750/3560
LBP7750C
imageRUNNER ADVANCE C2020/2030
imageRUNNER ADVANCE C2020/2030i
imageRUNNER ADVANCE C2020/2030L
imageRUNNER ADVANCE C2025
imageRUNNER ADVANCE C5030/C5030i/C5035/C5035i
imageRUNNER ADVANCE C5051/C5051i/C5045/C5045i
imageRUNNER ADVANCE C7055/C7065
imageRUNNER ADVANCE C9060/C9070 PRO
imageRUNNER ADVANCE C9065/C9075 PRO
imageRUNNER ADVANCE 6055/6055i/6065/6065i
imageRUNNER ADVANCE 6075/6075i
imageRUNNER ADVANCE 8085/8095
imageRUNNER ADVANCE 8105
imageRUNNER2520/2520i
imageRUNNER2525/2525i/2530/2530i
imageRUNNER2535/2535i/2545/2545i
iR105+
iR1018
iR1020
iR1022
iR1024/1024A/1024F/1024i/1024iF
iR2016/2016i
iR2018/2018i
iR2020/2020i
iR2022
iR2025
iR2030
iR2230
iR2270
iR2318L
iR2320L/2320N
iR2420D/2420L
iR2830
iR2870
iR3025
iR3030
iR3035
iR3045
iR3225/3225N
iR3230/3230A/3230N
iR3235/3235A/3235N
iR3245/3245A/3245N
iR3530
iR3570
iR4530
iR4570
iR5055
iR5065
iR5075
iR5570
iR6570
iR7086
iR7095/7095P
iR7105
iR8070
iR85+
iR9070
iR C1021/C1021i
iR C1028/C1030
iR C2380i
iR C2550/C2550i
iR C2580i
iR C2880/C2880i
iR C3080/C3080i
iR C3180/C3180i
iR 3180C/3180Ci
iR C3380/C3380i
iR C3580/C3580i
iR C4080
iR C4580
iR C5180
iR C5185
iR C5870
iR C5880/C5880i
iR 5880C/5880Ci
iR C6870
iR C6880/C6880i
iR 6880C/6880Ci
imagePRESS C1
imagePRESS C1+
D400-450
D460-490
D500 Series
D1100 Series
MF4010 Series
MF4100 Series
MF4200 Series
MF4320-4350
MF4360-4390
MF4400 Series
MF4500 Series
MF4600 Series
MF5800 Series
MF6500 Series
MF6600 Series
MF7100 Series
MF8000 Series
MF8300 Series
MF8400 Series
MF9100 Series
MF9200 Series
MF9300 Series
L160
L3000 Series

---

### Post by 1clue on 2011-04-10
I should have thought to put that list here.  Thanks!

---

### Post by Fraoch on 2011-04-12
A good HOWTO involving the UFRII drivers:

[http://ubuntuforums.org/showthread.php?t=1140724](http://ubuntuforums.org/showthread.php?t=1140724)

It's a bit old though, using a previous version of Ubuntu and the drivers, but the procedure should still be the same.

---

### Post by 1clue on 2011-04-12
Yes, there are already threads covering this material but most of them didn't show up when I was searching.  All I did here is make a thread for people who searched on the terms I used.  Please add any threads for UFRII drivers that you find here.  And thank you.

---

### Post by lkub on 2011-05-04
New problem with new Ubuntu release:(

I've just upgraded to Natty (11.04), and my Canon MF 6590 stopped working even though it worked flawlessly with the UFRI driver (mentioned above) with several previous versions of Ubuntu including Maverick 10.10.  Any help would be greatly appreciated.  Here are details of what happened and what I tried to do (all my attempts failed, unfortunately):

-During the upgrade to 11.04, the ugrader/installer removed the driver;
-After the upgrade, CUPS does find the printer but has no driver, obviously;
-When I'm trying to reinstall the driver, I'm getting the following message from the Ubuntu Software Center:"Dependency is not satisfiable: gs-esp".  Note that it doesn't just complain that a program is missing; it states that the dependency is NOT SATISFIABLE (?).
-So, I tried a different approach using the PPD file for MF6590.  I copied that file (Canon-MF6500.ppd) from another machine running Ubuntu 10.10 and asked CUPS to install the printer using that PPD.  Much to my surprise, CUPS wouldn't do that either (!).  To be more precise, "print test page" leads to a complain that there is a missing program, pstoufr2cpca.  
-So, I copied that program from another machine as well, converted it into an exe and copied into its proper directory.
-Now the outcome is different: CUPS does install the driver, "print test page" doesn't complain about anything but it doesn't print anything either.:confused:

I'm out of ideas here and would appreciate any help.  Google tells me that people have had a similar problem with previous upgrades but is there a solution?

Many thanks, guys!

---

### Post by ykkhern on 2011-05-05
Hi lkub,

I'm in the same situation as you, just download and install gs-esp from the following link and reinstall the drivers, everything should work fine (at lease in my case for sure, I'm using Canon iR3245).  Hope this help.

[https://launchpad.net/ubuntu/natty/i386/gs-esp/9.01~dfsg~svn12047-0ubuntu1]("https://launchpad.net/ubuntu/natty/i386/gs-esp/9.01%7Edfsg%7Esvn12047-0ubuntu1")

> **lkub said:**
> New problem with new Ubuntu release:(

I've just upgraded to Natty (11.04), and my Canon MF 6590 stopped working even though it worked flawlessly with the UFRI driver (mentioned above) with several previous versions of Ubuntu including Maverick 10.10.  Any help would be greatly appreciated.  Here are details of what happened and what I tried to do (all my attempts failed, unfortunately):

-During the upgrade to 11.04, the ugrader/installer removed the driver;
-After the upgrade, CUPS does find the printer but has no driver, obviously;
-When I'm trying to reinstall the driver, I'm getting the following message from the Ubuntu Software Center:"Dependency is not satisfiable: gs-esp".  Note that it doesn't just complain that a program is missing; it states that the dependency is NOT SATISFIABLE (?).
-So, I tried a different approach using the PPD file for MF6590.  I copied that file (Canon-MF6500.ppd) from another machine running Ubuntu 10.10 and asked CUPS to install the printer using that PPD.  Much to my surprise, CUPS wouldn't do that either (!).  To be more precise, "print test page" leads to a complain that there is a missing program, pstoufr2cpca.  
-So, I copied that program from another machine as well, converted it into an exe and copied into its proper directory.
-Now the outcome is different: CUPS does install the driver, "print test page" doesn't complain about anything but it doesn't print anything either.:confused:

I'm out of ideas here and would appreciate any help.  Google tells me that people have had a similar problem with previous upgrades but is there a solution?

Many thanks, guys!

---

### Post by rabosajr on 2011-05-05
thanks a lot bagh33ra. i'm running ubuntu 10.10 on my canon IR2318L.

i am now able to use my printing on a very limited basis. we are using 8.5in by 13in (long bond) as our standard paper in the office but the printer configuration does not allow me to set up 8.5in by 13in as paper size.

My present set up is that the printer is set at custom paper size of 8.5 by 13 while in the computer's printer configuration the paper is set as 8.5 by 14 (this is the only set up where canon IR2318L allows me to print). But I can only print one page at a time since the printer error light blinks and I have to cancel printing to proceed to print the next apge.

Can anyone help me to configure my printer in ubuntu to set 8.5in by 13 as paper size. There is no 8.5in by 13in (or long bond) in the printer configuration.


thanks.


PS I'm holding off upgrading to ubuntu 11.04 because of this problem.

---

### Post by R. M. Frank on 2011-05-16
Same problem here:

upgraded to 11.04 and printing on the canon iR2380i stopped. I was using cque and now tried the URF-II driver, which worked like a charm under 10.10.

First, installation failed du to the no longer existing gs-esp package. I then converted the rpm (i386) to deb and installed. All seemed well, as jobs were sent to the printer, BUT: the pstoufr2cpca 'driver' was missing - as found in the error log. As I need print jobs with an id, I set up accounting using cnjatool - all seened fine, the accounting files were properly created and populated.
NO printing! Because the accounting id was not sent. And not only that, all jobs arrive at the printer without a name and user. (The printer is set up not to print anything without an id - so that is the correct behaviour of the printer.) I tried compiling from the sources and managed to get the missing 'driver' - still no luck.
Then I found this thread, removed all I did, installed the missing gs-esp and installed the deb packages URF-II-v2.20. Now the jobs aren't even sent to the printer! I tried debuging, but am quite lost at the output. The error log show nothing when not debugging.
Making the cndrvcups-lb-2.20  binaries failes with the message:
libtool: link: can not build a shared library (yes, I did ./allgen.sh -deb) 

I'm stumped. 
-Robert

---

### Post by 1clue on 2011-05-17
I just knew there was a reason I hadn't upgraded yet.

That's pretty much the same sort of junk I put up with in the early days.  I hope somebody fixes it soon.

---

### Post by 1clue on 2011-05-28
Any news about getting the UFRII driver going with 11.04?

---

### Post by 1clue on 2011-07-03
Finally upgraded to 11.04.  My package system was broken on the old system and the easiest way was to upgrade.

This printer driver works just fine, didn't have to change a thing.

---

### Post by pvandoren on 2011-11-14
Ok  Trying to get UFR II Drivers working in Ubuntu 11.10.

I have successfully installed the 2.10 and 2.20 drivers on Ubuntu 10.04 LTS, with no problems,  On a new machine with 11.10, the drivers install fine, but we were getting an error with the test print with the filter file pstoufr2cpca.

I found that apparmor will blocking pstoufr2cpca from running.

Following the instructions on: [http://islandlinux.org/howto/upgrading-ubuntu-breaks-printer-cupsys](http://islandlinux.org/howto/upgrading-ubuntu-breaks-printer-cupsys)

I was able to get around the apparmor error, but now Ubuntu seems to send the test print, and regular prints to the printer, but nothing ever comes out.  (IE they disappear from the printq and say they have printed, but nothing comes out of our printer..)

Any ideas?

Pete

---

### Post by scheusso on 2011-12-26
Had the same problem:

I have a network printer that requires the ufr2 driver. I installed the 64bit deb file generate by alien from the rpm. Successfully added the printer both in ubuntu dialog and also cups frontend and printing seemd to be fine except that nothing ever happened at the printer.  

After some hours of work I found the following solution:
The deb file generated by alien copies some libraries to /usr/lib64 instead of /usr/lib. When i copied/moved these file over to /usr/lib everything worked fine again.

Hope this helps other people to save some time ;)

Edit: I'm using ubuntu 11.10 right now

---

### Post by cbanakis on 2011-12-29
AHA!

Worked for me.

Thank you for posting your findings.

> **Bagh33ra said:**
> Good start of a thread, I guess my experience fits in nicely here. Just bought a Canon i-Sensys MF8030Cn and spent most of the afternoon getting it installed, especially on 64bit Ubuntu (10.10, Maverick Meerkat).

In the end it was really easy, but finding the information i needed was not: 

The driver can be obtained directly from Canon. This printer is supported by the  "UFRII/UFRII LT Printer Driver for Linux v2.20", which supports a lot of other Canon printers too (see list at the end of this posting). The driver file I downloaded was o1113enx_l_ufr220.zip, there seems to be many variants (languages?).

Canon provides .deb packaged drivers for 32 bit systems, but only (RedHat) rpm for 64 bit. The 32bit .deb packages worked nicely "as is" on my 32bit laptop, but my 64 bit desktop needed some more. Luckily the rpm converted nicely to debian/ubuntu using alien. So once I got the rpm packages unpacked on my system all I needed to do was,

sudo apt-get install alien
sudo alien -i /path/to/file.rpm (for both drivers in the package) 

and once that was done CUPS recognized the printer in the normal "add printer" process.

Have not done anything more than a few test prints, and only over network (not USB), but this far it looks good. Asfaik no driver exists that would enable the scanner, but this model has the nice option to scan directly to a usb-stick.

According to the readme file, this driver should work with the following printers: 

LBP3360
LBP3370
LBP3460
LBP5360
LBP5960
LBP5970
LBP5975
LBP6650dn
LBP6750/3560
LBP7750C
imageRUNNER ADVANCE C2020/2030
imageRUNNER ADVANCE C2020/2030i
imageRUNNER ADVANCE C2020/2030L
imageRUNNER ADVANCE C2025
imageRUNNER ADVANCE C5030/C5030i/C5035/C5035i
imageRUNNER ADVANCE C5051/C5051i/C5045/C5045i
imageRUNNER ADVANCE C7055/C7065
imageRUNNER ADVANCE C9060/C9070 PRO
imageRUNNER ADVANCE C9065/C9075 PRO
imageRUNNER ADVANCE 6055/6055i/6065/6065i
imageRUNNER ADVANCE 6075/6075i
imageRUNNER ADVANCE 8085/8095
imageRUNNER ADVANCE 8105
imageRUNNER2520/2520i
imageRUNNER2525/2525i/2530/2530i
imageRUNNER2535/2535i/2545/2545i
iR105+
iR1018
iR1020
iR1022
iR1024/1024A/1024F/1024i/1024iF
iR2016/2016i
iR2018/2018i
iR2020/2020i
iR2022
iR2025
iR2030
iR2230
iR2270
iR2318L
iR2320L/2320N
iR2420D/2420L
iR2830
iR2870
iR3025
iR3030
iR3035
iR3045
iR3225/3225N
iR3230/3230A/3230N
iR3235/3235A/3235N
iR3245/3245A/3245N
iR3530
iR3570
iR4530
iR4570
iR5055
iR5065
iR5075
iR5570
iR6570
iR7086
iR7095/7095P
iR7105
iR8070
iR85+
iR9070
iR C1021/C1021i
iR C1028/C1030
iR C2380i
iR C2550/C2550i
iR C2580i
iR C2880/C2880i
iR C3080/C3080i
iR C3180/C3180i
iR 3180C/3180Ci
iR C3380/C3380i
iR C3580/C3580i
iR C4080
iR C4580
iR C5180
iR C5185
iR C5870
iR C5880/C5880i
iR 5880C/5880Ci
iR C6870
iR C6880/C6880i
iR 6880C/6880Ci
imagePRESS C1
imagePRESS C1+
D400-450
D460-490
D500 Series
D1100 Series
MF4010 Series
MF4100 Series
MF4200 Series
MF4320-4350
MF4360-4390
MF4400 Series
MF4500 Series
MF4600 Series
MF5800 Series
MF6500 Series
MF6600 Series
MF7100 Series
MF8000 Series
MF8300 Series
MF8400 Series
MF9100 Series
MF9200 Series
MF9300 Series
L160
L3000 Series

---

### Post by venik212 on 2012-01-04
Which files did you move/copy to /usr/lib?  This problem with my Canon MF6530 is driving me back to XP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by scheusso on 2012-01-05
I hope the following is correct. The files in /usr/lib64 were:

libcnpkufr2.a
libcnpkufr2.la
cups/backend/cnusb
cups/filter/pstoufr2cpca

Just copy them over to /usr/lib keeping the directory structure (for cnusb and pstoufr2cpca).

please let me know if it works for you

btw: I just saw, that there is a ppa for canon drivers ([https://launchpad.net/~michael-gruz/+archive/canon](https://launchpad.net/~michael-gruz/+archive/canon)), But it seems that the required files are not available for oneiric ...

---

### Post by vincegata on 2012-01-08
Same story here: MF4150 worked in 11.04 but not in 11.10. I am running 64-bit version.

I installed these two drivers (converted them from rpm that are provided on Canon website) without problem as I did in 11.04

sudo dpkg -i cndrvcups-common_2.20-2_amd64.deb
sudo dpkg -i cndrvcups-ufr2-us_2.20-2_amd64.deb

however when I print I get an error:

printer-state-message="/usr/lib/cups/filter/pstoufr2cpca failed"

I do not have the files mentioned in the previous post (I did locate), I do not even have /user/lib64 folder, only /user/lib and /user/lib32.

Could someone help me with this please?

---

### Post by kurt18947 on 2012-01-08
> **scheusso said:**
> Had the same problem:

I have a network printer that requires the ufr2 driver. I installed the 64bit deb file generate by alien from the rpm. Successfully added the printer both in ubuntu dialog and also cups frontend and printing seemd to be fine except that nothing ever happened at the printer.  

After some hours of work I found the following solution:
[B]The deb file generated by alien copies some libraries to /usr/lib64 instead of /usr/lib. When i copied/moved these file over to /usr/lib everything worked fine again.
[/B] 
Hope this helps other people to save some time ;)

Edit: I'm using ubuntu 11.10 right now

The  drivers from Brother did the same thing in 11.10, it was in Brother's FAQ.  It looks like an 11.10 problem, not a printer driver problem.

---

### Post by 1clue on 2012-01-08
You know, this is one of the main reasons I haven't moved to 11.10 yet.  When somebody comes on this thread and says, "I got mine working in 11.10 64-bit with these easy steps:..." I'm staying on 11.04.

Or maybe I just need to set up a VM on virtualbox to test it.

---

### Post by scheusso on 2012-01-09
> **vincegata said:**
> Same story here: MF4150 worked in 11.04 but not in 11.10. I am running 64-bit version.

I installed these two drivers (converted them from rpm that are provided on Canon website) without problem as I did in 11.04

sudo dpkg -i cndrvcups-common_2.20-2_amd64.deb
sudo dpkg -i cndrvcups-ufr2-us_2.20-2_amd64.deb

however when I print I get an error:

printer-state-message="/usr/lib/cups/filter/pstoufr2cpca failed"

I do not have the files mentioned in the previous post (I did locate), I do not even have /user/lib64 folder, only /user/lib and /user/lib32.

Could someone help me with this please?

can you post the contents of the cndrvcups-ufr2-us_2.20-2_amd64.deb file (dpkg -L cndrvcups-ufr2-us_2.20-2_amd64.deb) ? Then you can see where the files are located...

---

### Post by vincegata on 2012-01-09
When I run: 
sudo dpkg -L cndrvcups-ufr2-us_2.20-2_amd64.deb

I get:
Package `cndrvcups-ufr2-us_2.20-2_amd64.deb' is not installed.

I re-installed the drivers but still get same result.

When I install specific driver I get:
sudo dpkg -i cndrvcups-ufr2-us_2.20-2_amd64.deb
Selecting previously deselected package cndrvcups-ufr2-us.
(Reading database ... 186425 files and directories currently installed.)
Unpacking cndrvcups-ufr2-us (from cndrvcups-ufr2-us_2.20-2_amd64.deb) ...
Setting up cndrvcups-ufr2-us (2.20-2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

- looks alright to me.

(I run afterwords: sudo service cups restart)

Are the drivers not getting installed?

I followed this instructions
[http://ubuntuforums.org/showpost.php?p=10745713&postcount=5](http://ubuntuforums.org/showpost.php?p=10745713&postcount=5)
which worked in 11.04.

Anything else I should do, any help will be appreciated!

TIA

---

### Post by scheusso on 2012-01-09
Sorry, it should be: dpkg -L cndrvcups-ufr2-us

---

### Post by vincegata on 2012-01-09
Apparently I do have /usr/lib64 folder now.

I copied two files into to /usr/lib. Two other files in cups subfolders were already there 

But I still get the same error:
Idle - "/usr/lib/cups/filter/pstoufr2cpca failed"

---

### Post by vincegata on 2012-01-09
I also tried to print from Win 7 set up in VirtualBox but I get an error 'out of paper'. 

No luck all around.

---

### Post by scheusso on 2012-01-10
does the file
/usr/lib/cups/filter/pstoufr2cpca exist?
if yes, does it have the right permissions? (same as in /usr/lib64, check with ls -l)

---

### Post by vincegata on 2012-01-10
I copied those files over to make sure they have the right permissions.

Now, when I send something to print I get notification "Printing completed", I get no error, but it does not print anything. Print jobs used to stay in queue and show that error. 

Anything else I can try please?

---

### Post by scrooge_74 on 2012-01-10
Is not the same case, but my server is 64 bits and my HP only has drivers for 32 bits so I ended making a VM 32 bit server just for printing and I have it running in the server

---

### Post by 1clue on 2012-01-10
I'm using the 64-bit Canon driver, so it works.  But I'm on 11.04 rather than 11.10.

---

### Post by vincegata on 2012-01-15
I am rolling back to 11.04 because my Canon ImageClass MF4150 does not work on 11.10.

---

### Post by OnSite511 on 2012-01-15
After reading the readme in the Linux_UFRII_PrinterDriver package, it looks my specific printer isn't supported. I've got an MF5550 from my old windows days (which worked great). Any idea how to begin to get it working?

---

### Post by rrinjapan on 2012-01-18
Don't know if this will help a lot of you ... and frankly I don't know if it's truly advisable but I was having the same kind of problems that you all are having with my Canon All-in-one ink jet ... I was about to move back to 11.04 ... as a last chance step I uninstalled CUPS from the software center then reinstalled it ... now everything is fine ... I'm afraid to shut it off for the night ... I don't know why it worked but it seems to have ...

I'm running 11.10 64bit ...

---

### Post by adenilso on 2012-02-11
Hi,

  What worked for me (Canon IR1023iF, but I guess the problems is with ubuntu 11.10 as a whole) was the following:
* Create a sym link lib64 to lib (sudo ln -s /usr/lib /usr/lib64)
* Install drivers from canon (o1113enx_l_ufr220.zip)
* unzip it and alien'ed the 64bit RPMs
  - sudo alien cndrvcups-ufr2-uk-2.20-1.x86_64.rpm --scripts
  - sudo alien cndrvcups-common-2.20-1.x86_64.rpm --scripts
* install the drivers
  - sudo dpkg -i cndrvcups-common_2.20-2_amd64.deb cndrvcups-ufr2-uk_2.20-2_amd64.deb 
* install the printer
* (this may be specific to my case, since the printer I use requires a login to print) set the account
  - sudo cnjatool -e <printer-name>
  - cnjatool - <printer-name>

I hope it helps.

Abracos,
Ades

---

### Post by RobotJox on 2012-03-07
Anybody managed to get this working on 12.04?
I' ve had no luck - I can install my MF8030Cn printer, but I get this error when I try to print a test page:

> PDF file is damaged - attempting to reconstruct xref table...

Tried everything posted on this thread. :confused:

---

### Post by vincegata on 2012-03-07
> **RobotJox said:**
> Anybody managed to get this working on 12.04? 
I' ve had no luck

I haven't tried on 12.04, waiting for the release. That would suck big time if our printers will not work on LTS.

---

### Post by Mopar1973Man on 2012-03-08
I'm another one stuck with a MF4150 printer that doesn't work... I've also tried a bunch of thing and now I got a driver that sees a printer but does absolutely nothing. 

So do I need to roll back to 11.04 to get things working right? :confused:

---

### Post by vincegata on 2012-03-08
Unfortunately it looks this way. I had to go back to 11.04 to be able to use my MF4150. The driver installs just fine but the printer doesn't work on 11.10. It is very lame on Ubuntu part. If you find the solution please post.

---

### Post by hqadah on 2012-03-14
I had the same problem with my Canon Mf4150 on 11.10 64 bit.  Where the printer driver was recognized and would say test page printed but nothing comes out. It turns out that some dependencies are missing.

sudo apt-get install libc6-i386 ia32-libs lib32z1


Should fix the problem.

---

### Post by vincegata on 2012-03-14
> **hqadah said:**
> I had the same problem with my Canon Mf4150 on 11.10 64 bit.  Where the printer driver was recognized and would say test page printed but nothing comes out. It turns out that some dependencies are missing.

sudo apt-get install libc6-i386 ia32-libs lib32z1


Should fix the problem.

Thank you for letting us know! I am not going to re-install 11.10 right now (I am on 11.04 for the very reason) to see if it works for me with your suggestion but I'll just wait till 12.04 comes out - it's around the corner.

---

### Post by Mopar1973Man on 2012-03-20
Ok gang...

I managed to do the Canon MF4100 drivers on Ubuntu 10.4 x64.

You need to install the dependencies...

sudo apt-get install libc6-i386 ia32-libs lib32z1

Then reboot...

The install the drivers from Canon I'm using 2.40 Version now with zero issues.

[http://usa.canon.com/cusa/support/consumer/printers_multifunction/imageclass_series/imageclass_mf4150](http://usa.canon.com/cusa/support/consumer/printers_multifunction/imageclass_series/imageclass_mf4150)

If it done correctly the printer will already be in the printer control panel. Just right click hit properties and then check with a test page...

---

### Post by vincegata on 2012-03-20
> **Mopar1973Man said:**
> Ok gang...

I managed to do the Canon MF4100 drivers on Ubuntu 10.4 x64.



10.04 LTS? It was working on the old versions out of the box, it did not work on the later 11.10.

---

### Post by Mopar1973Man on 2012-03-20
Right On!

I'm now on Ubuntu 11.10 and got Canon MF4100 drivers 2.40 loaded and working... Once again the magic is loading the dependency files above, reboot, and then install in your alien produced .DEB packages. All working just fine so far... Now to tie in the other network computer. (Grin!)

---

### Post by vincegata on 2012-03-20
ah, just a typo, thanks for confirming. Let's hope now it'll work on 12.04.

---

### Post by Mopar1973Man on 2012-03-20
Not a typo... I ran it on 10.4 first and got it figured out... Then network the second computer in with 11.10 and it worked fine. So then ran the upgrade on the 10.4 computer and updated to 11.10 so both are running the same version of Ubuntu Linux (11.10). The like I said above I ran the dependency files, reboot, install drivers...

Both computers are now 11.10 Ubuntu with Canon MF4100 drivers 2.40 and the second computer is network sharing off the first... :biggrin:

---

### Post by yaq on 2012-03-22
> **Bagh33ra said:**
> Good start of a thread, I guess my experience fits in nicely here. Just bought a Canon i-Sensys MF8030Cn and spent most of the afternoon getting it installed, especially on 64bit Ubuntu (10.10, Maverick Meerkat).
(...)
Hi! Got an i-SENSYS MF4410 & did all of the above (installed driver using alien, using Canon MF4400 UFRII LT as driver for the printer with localhost:631). However, trying to print a test page gives me funny error messages:
"src = libcanon_pdlwrapper.c, line = 512, err = 0¥nError Response:ReqNo=2, SeqNo=3,opvpErrorNo=-2"
"src = libcanon_pdlwrapper.c, line = 512, err = 0¥nDEBUG: usb_find_devices=6"

Any suggestions will be greatly appreciated!

Oh, btw, LMDE 64bit, Kernel 3.0.0-1-amd64, Gnome 3.0.2

---

### Post by moffa on 2012-03-24
Thanks, I just moved everything from /usr/lib64/ to /usr/lib.

---

### Post by hellion_fi on 2012-04-20
Hi all, and thanks for the info - got my new Canon MF8040Cn to print with your help. Now I'm wondering, if anyone has any ideas how to get the scanner to work? I tried sane, but that doesn't recognize the device. It is connected via LAN, I have not tried USB as of yet. 
Running 10.04 LTS  (not a typo, I know, there are newer ones to try as well - running parallel with 11.10, waiting to transit to 12.04 LTS later).

(Annoyed because the older Lexmark scanned fine, but didin't print. Older Canon did print fine, but wanted to get rid of the two-device approach.)

---

### Post by bjtuna on 2012-04-25
> **adenilso said:**
> Hi,

  What worked for me (Canon IR1023iF, but I guess the problems is with ubuntu 11.10 as a whole) was the following:
* Create a sym link lib64 to lib (sudo ln -s /usr/lib /usr/lib64)
* Install drivers from canon (o1113enx_l_ufr220.zip)
* unzip it and alien'ed the 64bit RPMs
  - sudo alien cndrvcups-ufr2-uk-2.20-1.x86_64.rpm --scripts
  - sudo alien cndrvcups-common-2.20-1.x86_64.rpm --scripts
* install the drivers
  - sudo dpkg -i cndrvcups-common_2.20-2_amd64.deb cndrvcups-ufr2-uk_2.20-2_amd64.deb 
* install the printer
* (this may be specific to my case, since the printer I use requires a login to print) set the account
  - sudo cnjatool -e <printer-name>
  - cnjatool - <printer-name>

I hope it helps.

Abracos,
Ades

Brilliant! Thanks!

---

### Post by vincegata on 2012-04-25
> **hellion_fi said:**
> Hi all, and thanks for the info - got my new Canon MF8040Cn to print with your help. Now I'm wondering, if anyone has any ideas how to get the scanner to work? I tried sane, but that doesn't recognize the device. It is connected via LAN, I have not tried USB as of yet. 
Running 10.04 LTS  (not a typo, I know, there are newer ones to try as well - running parallel with 11.10, waiting to transit to 12.04 LTS later).

(Annoyed because the older Lexmark scanned fine, but didin't print. Older Canon did print fine, but wanted to get rid of the two-device approach.)

Scanner works for me no problem on any Ubuntu via USB.

---

### Post by hellion_fi on 2012-04-27
> **vincegata said:**
> Scanner works for me no problem on any Ubuntu via USB.

Which drivers / what model of MF-device do you use? I tried via USB-connection, and also with 11.10. :-k

---

### Post by vincegata on 2012-04-27
> **hellion_fi said:**
> Which drivers / what model of MF-device do you use? I tried via USB-connection, and also with 11.10. :-k

I am on 11.04 right now, scanners worked for me on 11.10 as well. I have multifunction MF-4150, I also had a dedicated scanner which I sold - I cannot remember the model. I did not have to do anything for scanners to work, plug&play really.

---

### Post by vincegata on 2012-04-27
12.04 is out! I am wondering if anyone has tried if multi-functional work?

---

### Post by hellion_fi on 2012-04-28
> **vincegata said:**
> I am on 11.04 right now, scanners worked for me on 11.10 as well. I have multifunction MF-4150, I also had a dedicated scanner which I sold - I cannot remember the model. I did not have to do anything for scanners to work, plug&play really.

Ok, it's because of the model then - from the  [sane backend documentation]("http://www.sane-project.org/sane-mfgs.html#Z-CANON"), the MF-4150 was supported, but not much with 8000-series that were. :( Thanks anyway.

---

### Post by mdhooge on 2012-05-09
We have an MF8340 (which BTW is never listed as compatible, when 8330 & 8350 are…) and the print part works. But one needs **first** to create the **symlink**! And then the alien-ed packages install correctly. It works both on ubuntu & debian.

Cheers

> **adenilso said:**
> 

  What worked for me (Canon IR1023iF, but I guess the problems is with ubuntu 11.10 as a whole) was the following:
* **Create a sym link lib64** to lib (sudo ln -s /usr/lib /usr/lib64)
* Install drivers from canon (o1113enx_l_ufr220.zip)


---

### Post by bjtuna on 2012-05-09
> **mdhooge said:**
> We have an MF8340 (which BTW is never listed as compatible, when 8330 & 8350 are…) and the print part works. But one needs **first** to create the **symlink**! And then the alien-ed packages install correctly. It works both on ubuntu & debian.

Cheers

That is correct. I will update my original instructions. You need to create the symlink first because when you install the alien'd packages, those packages are looking to copy files to /lib64.  I suppose we could also mangle the package definition files to write to /lib instead but I have zero experience packaging debs and when I wrote those instructions I was so completely tired, elated it was working, and admittedly enjoying a very nice northwest microbrew.

---

### Post by mdhooge on 2012-05-09
@bjtuna: don't worry :)

I insisted on that point because I missed it at first when scanning through this thread…

And I also wanted to make it clear (to google and others ;)) that the MF8340 is compatible, even though on Canon support there was no driver to download for linux.

Michel

---

### Post by danpav2881 on 2012-05-17
Same trouble on Ubuntu Server 12.04 LTS 64bit.

I installed the rpm drivers using alien and installed the net-printer (MF8350cdn).
Trying to print the test page the process is stopped and I get this printer state:

"Idle - /usr/lib/cups/filter/pstoufr2cpca failed"

I tried to find any solution but no-one method can help me......](*,)[-o<

```
I also tried to compile sources but I still have some problems....
```Launching "sudo make gen" on common driver I get:

```
/usr/bin/ld: load.o: undefined reference to symbol 'g_module_close'
/usr/bin/ld: note: 'g_module_close' is defined in DSO /usr/local/lib/libgmodule-2.0.so.0 so try adding it to the linker command line
/usr/local/lib/libgmodule-2.0.so.0: could not read symbols: Invalid operation
```Launching "sudo ./allgen.sh" I get:
```
libtool: link: can not build a shared library
libtool: link: See the libtool documentation for more information.
libtool: link: Fatal configuration error.
make[3]: *** [libcnpkufr2.la] Errore 1
```

---

### Post by danpav2881 on 2012-05-18
Executing sources installation step-by-step and modifying some things, I was able to install drivers from sources.

Now I haven't any trouble showed in printer status but printer doesn't do anything....... That's incredible, it looks like a never-ending story........:confused::confused::-&:-k:-|[-(

---

### Post by che_bizarro on 2012-07-10
Hi all,

I've had a fairly epic time getting Canon drivers to work on my 64-bit  12.04 LTS install but this morning I finally cracked it and hope that by  sharing others will get the same joy...

Getting Canon drivers to work on 64-bit Ubuntu 12.04

Step 1. Download UFR drivers from Canon - [http://support-au.canon.com.au/contents/AU/EN/0100270808.html](http://support-au.canon.com.au/contents/AU/EN/0100270808.html)

Step 2. Convert the 64-bit RPM files to .deb using alien
      ```
sudo alien -s cndrvcups-common-2.40-1.x86_64.rpm
sudo alien -s cndrvcups-ufr2-uk-2.40-1.x86_64.rpm
```Step 3. Make Sym links in usr for lib64 -
        ```
sudo ln -s /usr/lib /usr/lib64
sudo ln -s /usr/local/lib /usr/local/lib64
```Step 4. Install .deb files
       ```
sudo dpkg -i cndrvcups-common_2.40-2_amd64.deb
sudo dpkg -i cndrvcups-ufr2-uk_2.40-2_amd64.deb
```Step 5. AppArmor  denies the CUPS executables which the driver needs. Add to  /etc/apparmor.d/local/usr.sbin.cupsd:
       ```
 /usr/lib64/cups/backend/cnusb Uxr,
 /usr/lib64/cups/filter/pstoufr2cpca Uxr,
```Don't forget the commas at the end of each line!

Step 6. Add the 32-bit libs that the driver seems to depend on:
        ```
sudo apt-get install ia32-libs
sudo apt-get install libjpeg62:i386
```Step 7. Restart CUPS
        ```
sudo service cups restart
```Step 8. Add your printer and everything should work just fine!

I hope this helps someone else!

---

### Post by SB21487 on 2012-07-23
> **che_bizarro said:**
> Hi all,

I've had a fairly epic time getting Canon drivers to work on my 64-bit  12.04 LTS install but this morning I finally cracked it and hope that by  sharing others will get the same joy...

Getting Canon drivers to work on 64-bit Ubuntu 12.04

Step 1. Download UFR drivers from Canon - [http://support-au.canon.com.au/contents/AU/EN/0100270808.html](http://support-au.canon.com.au/contents/AU/EN/0100270808.html)

Step 2. Convert the 64-bit RPM files to .deb using alien
      ```
sudo alien -s cndrvcups-common-2.40-1.x86_64.rpm
sudo alien -s cndrvcups-ufr2-uk-2.40-1.x86_64.rpm
```Step 3. Make Sym links in usr for lib64 -
        ```
sudo ln -s /usr/lib /usr/lib64
sudo ln -s /usr/local/lib /usr/local/lib64
```Step 4. Install .deb files
       ```
sudo dpkg -i cndrvcups-common_2.40-2_amd64.deb
sudo dpkg -i cndrvcups-ufr2-uk_2.40-2_amd64.deb
```Step 5. AppArmor  denies the CUPS executables which the driver needs. Add to  /etc/apparmor.d/local/usr.sbin.cupsd:
       ```
 /usr/lib64/cups/backend/cnusb Uxr,
 /usr/lib64/cups/filter/pstoufr2cpca Uxr,
```Don't forget the commas at the end of each line!

Step 6. Add the 32-bit libs that the driver seems to depend on:
        ```
sudo apt-get install ia32-libs
sudo apt-get install libjpeg62:i386
```Step 7. Restart CUPS
        ```
sudo service cups restart
```Step 8. Add your printer and everything should work just fine!

I hope this helps someone else!


Hi Bizzaro,

I followed your instructions step-by-step ( I think alien -s should be alien -d). the installation went without any hiccups but when I print the printer state says "data file sent successfully" but nothing comes out of the printer.

I'm doing this via Ethernet, does this only work for USB?

Thanks,
SB

---

### Post by retsofbob on 2012-08-15
Bizzaro,

I followed your instructions also but with V250 version of Canon's driver and 12.04 64-bit.  I dropped the "-s" option on alien in order to create the DEB files.

Install looks good and printer properties shows toner levels but printing results in connection error to printer.

Still looking for a solution to this.

Thanks,

Bob

---

### Post by retsofbob on 2012-08-16
Found this worked for our iR C7055 on Canon Europe website:
[http://software.canon-europe.com/products/0010989.asp]("http://software.canon-europe.com/products/0010989.asp")

I'm using Ubuntu 12.04 64-bit and chose the 64-bit DEB download.

Installed fine and then ran ```
sudo cque
```

Use File/Create to make your new printer ("queue" in their lingo).  

When naming the printer make it a valid filename (no spaces) or it will fail to create.

I chose postscript and LP (the defaults).

When I got to the options page during the setup process there is an Extra tab that shows up and at that point I clicked on Accounting to set my user, id, and password as we require this for printing.

When printing it said something like "error connecting" as it had before with the difference being that something actually printed correctly!

Good luck.

Bob

---

### Post by gapsaph on 2012-09-01
Thank you so much for this tutorial! I've been playing with this for 4 hours to no avail until I read your post. I (thanks to you) got the Canon Super G3 (MF4100 series, or model F149200) to work successfully with Ubuntu 12.04.

Again, I can't thank you enough!!


> **che_bizarro said:**
> Hi all,

I've had a fairly epic time getting Canon drivers to work on my 64-bit  12.04 LTS install but this morning I finally cracked it and hope that by  sharing others will get the same joy...

Getting Canon drivers to work on 64-bit Ubuntu 12.04

Step 1. Download UFR drivers from Canon - [http://support-au.canon.com.au/contents/AU/EN/0100270808.html](http://support-au.canon.com.au/contents/AU/EN/0100270808.html)

Step 2. Convert the 64-bit RPM files to .deb using alien
      ```
sudo alien -s cndrvcups-common-2.40-1.x86_64.rpm
sudo alien -s cndrvcups-ufr2-uk-2.40-1.x86_64.rpm
```Step 3. Make Sym links in usr for lib64 -
        ```
sudo ln -s /usr/lib /usr/lib64
sudo ln -s /usr/local/lib /usr/local/lib64
```Step 4. Install .deb files
       ```
sudo dpkg -i cndrvcups-common_2.40-2_amd64.deb
sudo dpkg -i cndrvcups-ufr2-uk_2.40-2_amd64.deb
```Step 5. AppArmor  denies the CUPS executables which the driver needs. Add to  /etc/apparmor.d/local/usr.sbin.cupsd:
       ```
 /usr/lib64/cups/backend/cnusb Uxr,
 /usr/lib64/cups/filter/pstoufr2cpca Uxr,
```Don't forget the commas at the end of each line!

Step 6. Add the 32-bit libs that the driver seems to depend on:
        ```
sudo apt-get install ia32-libs
sudo apt-get install libjpeg62:i386
```Step 7. Restart CUPS
        ```
sudo service cups restart
```Step 8. Add your printer and everything should work just fine!

I hope this helps someone else!

---

### Post by 1clue on 2012-09-03
I'm also trying to get it working with 12.04 64-bit.  No go, no matter what.  I can get it to see the networked printer but nothing comes out when I print.

My fiancee's 32-bit xubuntu laptop was configured in a few minutes.  My amd64 is not so lucky.

---

### Post by thatisme on 2012-09-18
> **che_bizarro said:**
> Hi all,

I've had a fairly epic time getting Canon drivers to work on my 64-bit  12.04 LTS install but this morning I finally cracked it and hope that by  sharing others will get the same joy...

Getting Canon drivers to work on 64-bit Ubuntu 12.04

Step 1. Download UFR drivers from Canon - [http://support-au.canon.com.au/contents/AU/EN/0100270808.html](http://support-au.canon.com.au/contents/AU/EN/0100270808.html)

Step 2. Convert the 64-bit RPM files to .deb using alien
      ```
sudo alien -s cndrvcups-common-2.40-1.x86_64.rpm
sudo alien -s cndrvcups-ufr2-uk-2.40-1.x86_64.rpm
```Step 3. Make Sym links in usr for lib64 -
        ```
sudo ln -s /usr/lib /usr/lib64
sudo ln -s /usr/local/lib /usr/local/lib64
```Step 4. Install .deb files
       ```
sudo dpkg -i cndrvcups-common_2.40-2_amd64.deb
sudo dpkg -i cndrvcups-ufr2-uk_2.40-2_amd64.deb
```Step 5. AppArmor  denies the CUPS executables which the driver needs. Add to  /etc/apparmor.d/local/usr.sbin.cupsd:
       ```
 /usr/lib64/cups/backend/cnusb Uxr,
 /usr/lib64/cups/filter/pstoufr2cpca Uxr,
```Don't forget the commas at the end of each line!

Step 6. Add the 32-bit libs that the driver seems to depend on:
        ```
sudo apt-get install ia32-libs
sudo apt-get install libjpeg62:i386
```Step 7. Restart CUPS
        ```
sudo service cups restart
```Step 8. Add your printer and everything should work just fine!

I hope this helps someone else!

I tried really hard to get my canon mf 4120 working. Also tried the solution of che_bizarro using alien -d instead of alien -s but still nothing happens. I just got the message: sending data to printer. Thats really annoying.
I hope someone will find a solution

---

### Post by pdc on 2012-09-18
> I tried really hard to get my canon mf 4120 working

If  you google on 


you get 

[http://software.canon-europe.com/products/0010408.asp](http://software.canon-europe.com/products/0010408.asp)

and if you click on the 2,20 version you get this

[http://software.canon-europe.com/software/0040355.asp?model=](http://software.canon-europe.com/software/0040355.asp?model=)

if you scroll to the bottom of the page, there is a .zip file to download

download

..it should download into your Downloads directory?

If you open that; you should see it is 0113....zip

If you right click, and open with archive manager; it gives the picture I have called choose

.......assuming you have a 32bit system involved; open that folder; and choose Debian; open that;

and you see the picture URFdriver

1) right-click on the **_common driver_** *first*; install with gdebi installer; (it will ask you for your password);

2) now right-click on the **_cups ufr2 driver_**.. install with gdebi installer;

3) check in system-admin-printing .......it should all be there now ready to go

if you subscribe to a thread, you can follow more easily

.......right-hand side; near top ............thread tools......subscribe via email................

---

### Post by bernd nagez on 2012-09-23
Hi,


 I've got a 64-Bit Ubuntu 12.04 and I want to use a Canon iR 2022. I've followed the instructions of che_bizarro, used alien -c instead of alien -s but after all, my printer doesn't work.

So I checked each step and found out that step 3 went wrong. Instead of the symbolic link /usr/lib64/, I created the symbolic link /usr/lib64/lib. I think that might have happened because the directory /usr/lib64 already existed. So I renamed /usr/lib64 into /usr/lib64.old, ran ```
sudo ln -s /usr/lib /usr/lib64
``` again to make the needed symbolic link and copied by hand
the files from /usr/lib64.old to /usr/lib
the file from to /usr/lib64.old/cups/backend to /usr/lib/cups/backend
and the file from /usr/lib64.old/cups/filter to /usr/lib/cups/filter.

After that I ran step 4 till 8 again and my printer works. Hope that helps anyone else. Greetings, Bernd

---

### Post by thatisme on 2012-09-29
Sorry for that useless post. Was just desperated.
Ok im running linux mint 13 lts 64bit based on ubuntu 12.
I tried the solution of che_bizarro
I checked the sym links and found that I created symlink in /usr/lib64/lib and /usr/local/lib64/lib
After purging cndrvcups common and cndrvcups ufr2 I found that /usr/lib64 and /usr/local/lib64 were completely empty. So I removed the two directories and just created the symbolic links.
Code: 
sudo ln -s /usr/lib /usr/lib64
sudo ln -s /usr/local/lib /usr/local/lib64
Then again installed the two packages gained by alien -c and installing the printer
Code:
/usr/sbin/lpadmin -p canonmf -m CNCUPSMF4100ZK.ppd -v usb:/dev/usb/lp0 -E
But still when I print I get the message: "Ausführung läuft - Waiting for printer to become available."
Hope that someone can give me a tip and please dont stone me cause Im using mint ;)

---

### Post by pdc on 2012-09-29
I think it gets very weary when folks tag their posts on to what are already huge posts......
]
.......this is enough of an issue for you that you deserve your own thread:

can I suggest you start your own thread?

If you do, leave a message on this thread so we know you have moved;

_________________________________________________________________

......also........ have a think; 

.......just how important is it to you to have a 64bit system;

can you add a small new install of Mint 13 as a 32bit: the UFR driver that you need has debian packages in the 32bit version; I am sure they would be fine;

there is a Mint printing forum too.......did you know that?

[http://forums.linuxmint.com/viewforum.php?f=51](http://forums.linuxmint.com/viewforum.php?f=51)

oh........**copy** and **paste** this command into a terminal

> sudo dpkg -l | grep cndrvcups

and copy and paste the results back here; on in your fresh post

---

### Post by 1clue on 2012-10-01
@pdc,

I started this thread because of my own inability to find any threads for Canon all-in-one solutions.  I meant it to be what it has become, a sort of super-thread on solutions.  Searching on model number of the printer doesn't help because there are so many, and searching on the driver doesn't help because when I got the printer I didn't know about 'UFRII' or any keyword that would locate a driver.  I wanted a way to collect all that information and at least give people more keywords to search.

That said, you're right in that the problem in question could easily be its own thread.

What some people do is post their own thread, and then go post a link to it on a super-thread if they think it can be helpful to someone else.

FWIW I've come back to this thread several times since I started it, since I've re-installed and had to set it up all over again.

---

### Post by thatisme on 2012-10-05
Anyway I just installed mint 13 32 bit.  And of course it works. Maybe I try the 64 bit one time again. But in the moment I dont have the time.

---

### Post by pdc on 2012-10-05
>  And of course it works

............well, that's great; enjoy your printer; I'm not sure we ever heard which particular model of printer you have; but great that it's working

---

### Post by thatisme on 2012-10-15
Mh I thought it is not the matter wich special model I ve got.
But it is a canon mf4120.

---

### Post by xlearner on 2012-10-16
Hello All,

I am looking for a driver for Canon network printer ir2520. I am running ubuntu 12.04. 

The printer works well on windows. Actually this printer comes with built in authentication. It asks for username & password in windows. 

On ubuntu 12.04, the printer is being recognized and getting added. But on sending a document to print to the printer, it does not prompt for username and password. As a result, print is failing. So I am unable to print to it on ubuntu. Any suggestions as to how to get this to work? 

Thanks for your help and cooperation!

Xlearner

---

### Post by 1clue on 2012-10-16
You may be able to turn off authentication for now, just to make sure you have the printer working.

Mine (MF8050CN) has a little web server on it for printer configuration.  It needs a different port I think, it's been awhile and my printer is not accessible from where I am.

Once that works, you can try to get the authentication part going if that's important to you.

---

### Post by pdc on 2012-10-16
Canon say that their UFR II driver is the correct linux driver;

you do not say if you are using 32bit or 64bit linux;

the Canon UFR driver has debian packages for 32bit; (Ubuntu uses .deb packages)

........for 64bit one needs alien to convert the 64bit rpm packages to deb; as detailed earlier in this now long thread

go here

[http://support-in.canon-asia.com/contents/IN/EN/0100270810.html](http://support-in.canon-asia.com/contents/IN/EN/0100270810.html)

and download the [COLOR="SeaGreen"]UFR II Printer Driver for Linux Version 2.50[/COLOR]

.....as you download it, hopefully gdebi installer will leap in and offer to help

---

### Post by xlearner on 2012-10-17
Pdc and 1clue,

Thanks for your replies. I downloaded the UFR II Printer Driver for Linux Version 2.50. Then I temporarily disabled the authentication. Using this printer driver, I was able to print to ir2520 printer. 

But it does not work when the authentication is on.  Our system administrator wants to have the authentication switched on. So I still am not able to print onto this printer. Any suggestions as to what I can do to get around this problem? 

BTW, I forgot to mention in my earlier message. I am using 32 bit version of ubuntu 12.04. 

Thanks
Xlearner

---

### Post by 1clue on 2012-10-17
I'm sorry I haven't found anything about authentication yet and I'm not an expert on this.  Is there by chance a print server somewhere that runs a mainstream OS?

Or is there an LDAP-based authentication?  Or IP-based one?  I'm not familiar with your printer, but if a print server can handle the thing you could allow your Linux box by IP address through the domain controller.

---

### Post by pdc on 2012-10-17
this sounds like you need to get into the wonderful world of samba;

[https://help.ubuntu.com/community/Samba/PrinterSharing](https://help.ubuntu.com/community/Samba/PrinterSharing)

........which I know absolutely nothing about ..

there are folks like swerdna about

[http://www.swerdna.net.au/](http://www.swerdna.net.au/)

who know a lot about it

**[COLOR="Red"][SIZE="3"]you might be best to start a new thread[/SIZE][/COLOR]**;

describe your issues there

and perhaps **_post on the networking forum_**, as the samba experts are likely there

---

### Post by 1clue on 2012-10-18
AND, if your thread has a solution, post a link to it in this thread so the next guy has some place to look.

---

### Post by xlearner on 2012-10-18
Thanks again for the replies. 

For authentication, we do not have any samba or LDAP server. The printer has in-built accounts information. When a new user wants to join, then we manually create a username and password for him/her to use. 

SO any suggestions on how authentication can be performed from linux as well.

Xleaner

---

### Post by pdc on 2012-10-19
what about selecting the printer driver; from the Admin menu

right-click; select Properties

I enclose a thumbnail of what I find by cursory examination;

I suspect you investigate these areas;

you may need to use google but I suspect an Ubuntu wiki somewhere will help

---

### Post by vincegata on 2012-10-27
Hi guys,

The good news is last night, after reading all posts, I managed to install MF4150 on Ubuntu 12.10, printer runs no problem from Unity, GNOME fallback, and Cinnamon. I had been running 11.04 until now, however support for it expires tomorrow hence I decided to make it straight with Ubuntu or to find another distro. I mixed and matched solutions from this thread and voala. Important difference from the previous suggestions is that I do not create symbolic link. Also, I did not try this on 12.04. I plug my printer though USB.

1. Unplug printer if it's plugged.

2. Download drivers, it's v.2.50 as of today. Note I use US drivers.

3. Install dependencies: 
sudo apt-get install libc6-i386 ia32-libs lib32z1					

4. convert drivers rpm package to deb
sudo alien --scripts cndrvcups-common-2.50-1.x86_64.rpm
sudo alien --scripts cndrvcups-ufr2-us-2.50-1.x86_64.rpm				

5. Install drivers:
sudo dpkg -i cndrvcups-common_2.50-2_amd64.deb
sudo dpkg -i cndrvcups-ufr2-us_2.50-2_amd64.deb				

6. Driver install created new folder /usr/lib64/. Copy it contents into /usr/lib:
sudo cp -r /usr/lib64/* /usr/lib							

7. Restart printer service:
sudo service cups restart

8. Plug in printer, you should get a message saying your printer is being added. After that printer should show up in Printers config panel and it should work now.

---

### Post by morepractice on 2012-11-28
Has anyone tried out different ways? I tried all the suggestion on this thread (I think it is the best one out of all the ones I read) and still get a message as follows:
Missing printer driver
No printer drive for Canon D480-D490 (FAX)

I also tried to
*install US/UK version
*copy lib files from the source to lib64 directly (and symlink lib64 in lib)
*use version 1.9 instead of 2.5

---

### Post by vincegata on 2012-11-28
Apparently steps I used for 12.10 do not work with 12.04.

So here are the steps I used with 12.04. Note, I just recompiling the steps already mentioned in this thread. 

1. Unplug printer if it's plugged.

2. Install dependencies: 
sudo apt-get install libc6-i386 ia32-libs lib32z1 libjpeg62:i386

3. Reboot.

4. Create symbolic links.
sudo ln -s /usr/lib /usr/lib64				
sudo ln -s /usr/local/lib /usr/local/lib64			

5. Download drivers, it's v.2.50 as of today. Note I use US drivers.

6. convert drivers rpm package to deb
sudo alien --scripts cndrvcups-common-2.50-1.x86_64.rpm
sudo alien --scripts cndrvcups-ufr2-us-2.50-1.x86_64.rpm	

7. Install drivers:
sudo dpkg -i cndrvcups-common_2.50-2_amd64.deb
sudo dpkg -i cndrvcups-ufr2-us_2.50-2_amd64.deb	

8. Restart printer service:
sudo service cups restart

9. Plug in printer, I did not get any messages saying your printer is being added, but printer should show up in Printers config panel and it should work now.

---

### Post by morepractice on 2012-11-28
Thanks for your reply. I tried that method too but that also did not work. What is the best way to diagnosis what is going on for cups? Because even when I go to to localhost:621 to add printer via cups, all I get is "
  **Add Printer  Error**

  Unable to add printer:[INDENT]Forbidden

Page and I do not see any printer.
[/INDENT]

---

### Post by vincegata on 2012-11-28
Try to purge the drivers

sudo dpkg -P cndrvcups-ufr2-us
sudo dpkg -P cndrvcups-common
sudo service cups restart

then install the drivers again following those steps. I hope this helps.

---

### Post by Iurie on 2012-12-04
So, after I read all thread and tried different suggested solutions (thank you, guys!) I finally managed to make my Canon I-Sensys MF4140 to work in my Ubuntu 12.04 64-Bit version.

My steps:

1. Downloaded the [UFR II Printer Driver for Linux Version 2.50]("http://gdlp01.c-wss.com/gds/0/0100003440/04/Linux_UFRII_PrinterDriver_V250_us_EN.tar.gz") from [Canon U.S.A.]("http://usa.canon.com/cusa/support/consumer/printers_multifunction/imageclass_series/imageclass_mf4150")
2. Extracted from archive and converted the 64-Bit RPM drivers to DEB:
```
sudo alien cndrvcups-ufr2-us-2.50-1.x86_64.rpm --scripts
sudo alien cndrvcups-common-2.50-1.x86_64.rpm --scripts
```
3. Renamed existing '/usr/lib64' to '/usr/lib64.old'
```
sudo mv /usr/lib64 /usr/lib64.old
```
4. Created the symbolic link '/usr/lib64' to '/usr/lib':
```
sudo ln -s /usr/lib /usr/lib64
```
5. Installed dependencies (I do not know if I realy needed all of them [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]):
```
sudo apt-get install libc6-i386 ia32-libs lib32z1
```
6. Installed the .deb packages:
```
sudo dpkg -i cndrvcups-common_2.50-2_amd64.deb
sudo dpkg -i cndrvcups-ufr2-us_2.50-2_amd64.deb
```
7. Plugged the printer and it worked!
(I printed a test page and a page from a PDF document).

---

### Post by E5C4P3 on 2012-12-05
Terminal is telling me, "sudo: alien: command not found".

---

### Post by vincegata on 2012-12-05
> **E5C4P3 said:**
> Terminal is telling me, "sudo: alien: command not found".

You need to install alien.

---

### Post by E5C4P3 on 2012-12-05
I have now installed alien and downloaded the drivers,  but I need some clarification on step 2.

---

### Post by vincegata on 2012-12-05
Navigate to the folder where you downloaded drivers and run those two commands, that's all. You should get two new files with *.deb extension.

---

### Post by pdc on 2012-12-05
so vincegata is telling you it is likely you downloaded the UFR driver.......; if that is what you downloaded...; into the Downloads directory;

so you should open the terminal and copy and paste

> cd Downloads ...hit enter key each time..

then do as per previous posts

---

### Post by E5C4P3 on 2012-12-05
> **pdc said:**
> so vincegata is telling you it is likely you downloaded the UFR driver.......; if that is what you downloaded...; into the Downloads directory;

so you should open the terminal and copy and paste

 ...hit enter key each time..

then do as per previous posts
Terminal is telling me, File "cndrvcups-ufr2-us-2.50-1.x86_64.rpm" not found. I looked and the drivers are in fact in the Downloads directory, so i must be doing something wrong.

---

### Post by pdc on 2012-12-05
so you have typed cd Downloads and hit enter and are in the Downloads directory ............

if you enter the command

> [COLOR="Red"]ls[/COLOR]

that lists the contents of the directory

what you have probably got is

[COLOR="SeaGreen"]Linux_UFRII_PrinterDriver_V250_uk_EN.tar.gz[/COLOR]

so you need a little work on it ........ 

> [COLOR="Red"]tar -zxvf Linux_UFRII_PrinterDriver_V250_uk_EN.tar.gz[/COLOR]

and that creates a directory called Linux_UFRII_PrinterDriver_V250_uk_EN

so your next command is

> [COLOR="Red"]cd Linux_UFRII_PrinterDriver_V250_uk_EN/64-bit_Driver/RPM[/COLOR]

and if you now type

> [COLOR="Red"]ls[/COLOR]

that lists the contents of the directory and it should then be 

[COLOR="SeaGreen"]cndrvcups-common-2.50-1.x86_64.rpm  cndrvcups-ufr2-uk-2.50-1.x86_64.rpm[/COLOR]

.......so that should let you install the [COLOR="Purple"]common driver first[/COLOR] (cndrvcups-common-2.50) and [COLOR="Purple"]then the specific UFR driver[/COLOR] (cndrvcups-ufr2-uk-2.50) as per the instructions in the earlier post

---

### Post by Krovas on 2013-01-16
> **Iurie said:**
> So, after I read all thread and tried different suggested solutions (thank you, guys!) I finally managed to make my Canon I-Sensys MF4140 to work in my Ubuntu 12.04 64-Bit version.

My steps:

1. Downloaded the [UFR II Printer Driver for Linux Version 2.50]("http://gdlp01.c-wss.com/gds/0/0100003440/04/Linux_UFRII_PrinterDriver_V250_us_EN.tar.gz") from [Canon U.S.A.]("http://usa.canon.com/cusa/support/consumer/printers_multifunction/imageclass_series/imageclass_mf4150")
2. Extracted from archive and converted the 64-Bit RPM drivers to DEB:
```
sudo alien cndrvcups-ufr2-us-2.50-1.x86_64.rpm --scripts
sudo alien cndrvcups-common-2.50-1.x86_64.rpm --scripts
```
3. Renamed existing '/usr/lib64' to '/usr/lib64.old'
```
sudo mv /usr/lib64 /usr/lib64.old
```
4. Created the symbolic link '/usr/lib64' to '/usr/lib':
```
sudo ln -s /usr/lib /usr/lib64
```
5. Installed dependencies (I do not know if I realy needed all of them [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]):
```
sudo apt-get install libc6-i386 ia32-libs lib32z1
```
6. Installed the .deb packages:
```
sudo dpkg -i cndrvcups-common_2.50-2_amd64.deb
sudo dpkg -i cndrvcups-ufr2-us_2.50-2_amd64.deb
```
7. Plugged the printer and it worked!
(I printed a test page and a page from a PDF document).


[SIZE="4"]Sexy time! Thank you for this post![/SIZE]

---

### Post by George Heine on 2013-02-15
Searched through this thread and didn't find specific mention of my printer, a  Canon MF4880dw.   Canon claims that it does not support this printer on Linux.  However, I did find the drivers **cndrvcups-ufr2-us_2.50-1_i386** and **cndrvcups-common_2.50-1_i386** on the Canon website (listed under the MF4690 printer).  Was wondering if anyone has had success using these or other drivers with this printer.  Currently running Ubuntu 12.04 LTS, 32-bit.  

Thank you for any assistance.  And thanks also to those who have started and posted to the thread - looks like a wealth of valuable information.

---

### Post by pdc on 2013-02-16
Hi George

this looks a brand new device

[http://www.pcmag.com/article2/0,2817,2412027,00.asp](http://www.pcmag.com/article2/0,2817,2412027,00.asp)

Canon recently released the 2 series in their pixma printers:

ie the 2100 series became the 2200 series, etc ............

.......and after a couple of months, linux drivers were added to their pages

....I can't see this 4880 listed yet: you would need a specific ppd and you would register the printer ..something along the lines of sudo /usr/sbin/lpadmin -p MF4880DW -m canonMF4880DW..whatever.ppd

so I guess a clever soul could edit an existing ppd file; (as they look very similar when you open them with gedit)

.....but hopefully the lads in Japan will release something soon

..........incidentally the new inkjet printers are all google cloud ready so in the future that may allow another to print; (rather than needing printer driver interfaces from a computer)

---

### Post by klettermaxi on 2013-04-17
Hej!
I am trying to set up a Canon C5051i networkprinter. It instals fine using a .ppd file. But when i try to print a page it does not request Abt. ID and PIN and consequently does not print the page. I am using Linux Mint Maya 13.
Any ideas on how to get this to work?

---

### Post by olamina on 2013-05-09
I followed these instructions [http://ubuntuforums.org/showthread.php?t=1723101&p=10657848#post10657848](http://ubuntuforums.org/showthread.php?t=1723101&p=10657848#post10657848) to install this printer but have had no luck. 

When I type ```
/usr/lib/cups/backend/snmp <printer IP address>
```, I get:

```

network socket://192.168.254.4 "Canon iR-ADV C5030/5035 (UFR II)" "Canon  iR-ADV C5030 69.03" "MFG:Canon;MDL:iR-ADV C5030/5035 (UFR  II);CLS:PRINTER;DES:Canon iR-ADV  C5030/5035;CID:;CMD:LIPSLX,CPCA,1284.4-2000;" ""
```

Which shows me that I can detect the printer. Not sure why I can't actually print anything...Job accounting *is* turned on. 

I used the "cnjatool" utility to add ID and password and when I try to print a test page nothing prints.

Thanks i advance for your help!

---

