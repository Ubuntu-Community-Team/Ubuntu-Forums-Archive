---
title: "How To: Setup DOD Common Access Card (CAC) for service portals"
date: 2009-07-24
forum: General Help
---

### Post by mole84 on 2009-07-24
I was able to get my government email working from the Air Force portal on the non-gov network today running Ubuntu Jaunty and Firefox 3. I am just hoping to consolidate several previous threads into this one for Jaunty.

(Update) Working on 11.04 - the Natty Narwhal with Firefox 11.0

[LIST=1]
[*]The first step was to purchase an SCR331 CAC Card Reader, they can be found many places. This seems to be most widely supported CAC Reader.
[*]The second step was to install the necessary packages. I ran this command from the terminal (applications -> accessories -> terminal) to install all the packages and their dependencies.

```
sudo apt-get install libpcsclite-dev pcscd pcsc-tools libccid coolkey
```

In case you're wondering what all of those programs do, here's a quick breakdown:
[LIST]
[*]libpcsclite-dev: Middleware to access a smart card using PC/SC (development files)
[*]pcscd: Middleware to access a smart card using PC/SC (daemon side)
[*]pcsc-tools: Some tools to use with smart cards and PC/SC
[*]libccid: PC/SC driver for USB CCID smart card readers
[*]coolkey: Smart Card PKCS #11 cryptographic module
[/LIST]

[*]Next I plugged in my CAC card reader with my CAC card inserted and ran pcsc_scan from the terminal
```
pcsc_scan
``` 
which gave me the following output
```
livingroom@livingroom-laptop:~$ pcsc_scan
PC/SC device scanner
V 1.4.14 (c) 2001-2008, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.99
Scanning present readers
0: SCM SCR 331 00 00

Fri Jul 24 09:39:45 2009
 Reader 0: SCM SCR 331 00 00
  Card state: Card inserted, 
  ATR: 3B 7D 96 00 00 80 31 80 65 B0 83 11 13 AC 83 00 90 00

ATR: 3B 7D 96 00 00 80 31 80 65 B0 83 11 13 AC 83 00 90 00
+ TS = 3B --> Direct Convention
+ T0 = 7D, Y(1): 0111, K: 13 (historical bytes)
  TA(1) = 96 --> Fi=512, Di=32, 16 cycles/ETU (223200 bits/s at 3.57 MHz)
  TB(1) = 00 --> VPP is not electrically connected
  TC(1) = 00 --> Extra guard time: 0
+ Historical bytes: 80 31 80 65 B0 83 11 13 AC 83 00 90 00
  Category indicator byte: 80 (compact TLV data object)
    Tag: 3, len: 1 (card service data byte)
      Card service data byte: 80
        - Application selection: by full DF name
        - EF.DIR and EF.ATR access services: by GET RECORD(s) command
        - Card with MF
    Tag: 6, len: 5 (pre-issuing data)
      Data: B0 83 11 13 AC
    Tag: 8, len: 3 (status indicator)
      LCS (life card cycle): 00 (No information given)
      SW: 9000 (Normal processing.)

Possibly identified card (using /usr/share/pcsc/smartcard_list.txt):
	NONE

Your card is not present in the database.
You can get the latest version of the database from
  http://ludovic.rousseau.free.fr/softwares/pcsc-tools/smartcard_list.txt
or use: wget http://ludovic.rousseau.free.fr/softwares/pcsc-tools/smartcard_list.txt --output-document=/home/livingroom/.smartcard_list.txt

If your ATR is still not in the latest version then please send a mail
to <ludovic.rousseau@free.fr> containing:
- your ATR
- a card description

```
As you can see initially the DOD CAC cards signature is not recognised so we must update the signatures as instructed from the output. [COLOR="Red"]Make sure you copy out the command from your output because it writes the file into your home directory.[/COLOR] For me it was.
```
wget http://ludovic.rousseau.free.fr/softwares/pcsc-tools/smartcard_list.txt --output-document=/home/livingroom/.smartcard_list.txt
```

Another option here is to visit the authors site and download the file manually, just make sure to save it in your home folder as .smartcard_list.txt
[http://ludovic.rousseau.free.fr/softwares/pcsc-tools/smartcard_list.txt](http://ludovic.rousseau.free.fr/softwares/pcsc-tools/smartcard_list.txt)

Now run pcsc_scan again and it should say the card is recognised.


[*] Now we need to setup the various DOD root certificates. I had to do this in two steps.
[LIST=1]
[*] Go to [http://iase.disa.mil/pki-pke/function_pages/tools.html](http://iase.disa.mil/pki-pke/function_pages/tools.html) and download the InstallRoot #.## A file. This is a zip file containing the certificates. Extract it to a folder.
[*] From Firefox Edit-> Preferences -> Advanced -> Encryption
[*] Click Certificates -> Import, browse to the folder you just extracted the zip to and import, set it to trust all settings.
[*]Install additional DOD certificates and put a check-mark on all of them. Just click on each one and Firefox will ask you if it's ok, you may get an error saying its already installed which is fine.
[http://dodpki.c3pki.chamb.disa.mil/rootca.html](http://dodpki.c3pki.chamb.disa.mil/rootca.html)
[/LIST]

[*]Continuing on, now we will make the CAC available to Firefox. Open Firefox and browse to:

[LIST=1]
[*]Edit-> Preferences -> Advanced -> Encryption
[*]Click on the Security Devices button
[*]Click the Load button to load a new module. Name it CAC Module and either type in or browse to /usr/lib/pkcs11/libcoolkeypk11.so
[*]A note here is that if you are running a 64 bit machine the path will be /usr/lib64/pkcs11/libcoolkeypk11.so
[*]From the devices window, Enable FIPS, to do this you will have to click the default Firefox security device and hit "Change Password" (Not on the CAC module) to set the initial password, then you should be able to click Enable FIPS
[*]Restart Firefox
[/LIST]

[*]When you browse to a DOD site it will first ask you for the FIPS password that you set on the default device, then it should ask you for your CAC pin, all certificates should now be available.

[*]In order to make your email work you must use specific portal settings. For the Air Force it required going into My Profile and entering the base specific outlook email server into the email settings field.

[/LIST]

---

### Post by kidux on 2009-07-28
Thank you for this tutorial, it was very helpful. I had a few more hoops to go through to get it working though. I had to flash the bios on my reader to the newest version, which was supposed to be able to be done in a virtual machine, but I could not get Linux to give up control of it and so had to do it on a friends XP machine. After I did that, I was able to follow your instructions and get it working properly. AKO allows access now. I'm still working on getting access to my other work email.

---

### Post by aatyler on 2009-09-05
Wow! Thanks so much. Now that I can login using CAC, I can get rid of my windows partition all together, the CAC was the only reason that I was ever having to keep windows around. :popcorn:

---

### Post by dkermitb on 2009-09-06
I cannot get Step 3 to work: pcsc-scan.  I think it's because I have Windows XP and Jaunty duel working on my computer.  I'm guess that Jaunty is unable to find my newly installed pcsc program/library.  

The error I am getting is:   

bash: pcsc-scan:  command not found.  

I appreciate any advice out there to help.  It fails to load on multiple computers with Win and Ubuntu.  Thanks

Kermie

---

### Post by mole84 on 2009-09-06
> **dkermitb said:**
> I cannot get Step 3 to work: pcsc-scan.  I think it's because I have Windows XP and Jaunty duel working on my computer.  I'm guess that Jaunty is unable to find my newly installed pcsc program/library.  

The error I am getting is:   

bash: pcsc-scan:  command not found.  

I appreciate any advice out there to help.  It fails to load on multiple computers with Win and Ubuntu.  Thanks

Kermie

Kermie,

Make sure that you are using pcsc_scan. There is an underscore there rather than a dash between the two words. One neat way to check your commands is to use the tab auto complete feature in bash. All that takes is to type in the first few letters of a command so pcsc, and then hit tab a few times and it will display all the programs installed on your machine that start with those letters, then you can select the proper command. If the pcsc_scan is not auto completing that means you dont have it installed, so try to go back and re-install it.

---

### Post by dkermitb on 2009-09-08
Mole,

Nice job with the forum!!  I was able to get my CAC Card working with your help, I really appreciate it.  However, I need help the webmail now.

First of all, how do you view your webmail with Jaunty?  On my XP computer, I viewed webmail on Internet Explorer using ActiveX.  Since Ubuntu doesn't have these, how does Ubuntu webmail work?  I can get to the Portal, but I can't get my webmail to work even after I enter my PIN.  I appreciate any advice you have.  I couldn't find anything under "My Profile" to help configure my webmail.  Thanks again for all the help!

v/r,

Kermie

---

### Post by mole84 on 2009-09-08
> **dkermitb said:**
> Mole,

Nice job with the forum!!  I was able to get my CAC Card working with your help, I really appreciate it.  However, I need help the webmail now.

First of all, how do you view your webmail with Jaunty?  On my XP computer, I viewed webmail on Internet Explorer using ActiveX.  Since Ubuntu doesn't have these, how does Ubuntu webmail work?  I can get to the Portal, but I can't get my webmail to work even after I enter my PIN.  I appreciate any advice you have.  I couldn't find anything under "My Profile" to help configure my webmail.  Thanks again for all the help!

v/r,

Kermie

Kermie,

Well the good news if you were able to go to your portal, enter your master pin, and select your certificate you've won most of the battle. Webmail in and of itself is only a function of a web browser, so I am just able to open up my webmail link through firefox. I am not sure which service portal you are using, (I only have experience with the Air Force portal), but for me there is a separate link from the portal to webmail once I use my CAC / PIN to enter the portal. The note about the "my profile" setting was that in the Air Force at least all of our bases have individual (and disjoint) webmail servers so you have to put in the link to your bases server in your settings on the portal in order for it to direct you to the right place and carry your credentials.

---

### Post by zz97 on 2009-09-10
Has anyone successfully gotten this to work with Ubuntu Jaunty 64-bit?

I've installed the required packages--no problem there.  And pcsc_scan says everything's fine.  

But when I try to load the security module libcoolkeypk11.so, Firefox "freezes" and stops responding.  If I insert and remove the CAC a few times it will come back to life.  

But then if I try to access an https:// site, things don't work.  It will attempt to connect to the site for a minute or two, then (sometimes) eventually ask for my master password,  but entering the pin has yet to actually get me into a site. 

I get the same basic result with both Firefox 3.0 and Firefox 3.5.

My card reader is an SCR3310 v2.0.

Any ideas?

---

### Post by dkermitb on 2009-09-12
Mole, 

I'm tracking with you referencing the "My Profile".  I have tried to check my email from the AF Portal and using the separate website.  Both of them ask for the passwords and certificates.  However they don't load, instead I get: 

[COLOR=#000000][FONT=verdana]Error Code: 401 Unauthorized. The server requires authorization to fulfill the request. Access to the Web server is denied. Contact the server administrator. (12209)

I am using Firefox from Jaunty as well.  I think there is something wrong with my Firefox setting.  Got any more tricks on your end about how I should fix this?  Thanks...  

Kermie
[/FONT][/COLOR]

---

### Post by dkermitb on 2009-09-20
Mole,

Good news, I got the webmail working.  I had to use another website that what you had posted to get my certificates.  After playing around with that, everything works.  Thanks for the nice job on here!!  

Kermie

---

### Post by lledurt on 2009-09-29
I got it to work on one computer, but I am have trouble with firefox on another and I think it is something I have done.  Can anyone help me fix it.

In Firefox I went to the >>edit>preferences>>Advanced>>encryption and added one of the /usr/lib/pkcs11/libcoolkeypk11.a modules.  It worked and then I thought I named it wrong so I unloaded the module.  When I tried to reload it (or any other) I get an unable to load module error.
  I tried rebooting, reinstalling firefox, downloading the modules again.  reinstalling koolkey, and nothing seemed to work.
Any thoughts?
Thanks

---

### Post by lledurt on 2009-09-29
I got it to work.  I did a complete removal of coolkey in synaptic and then reinstalled it then removed and replaced the card and it seemed to work.  I think the certs might have been on the card from the other install so I am not sure what fixed it.

---

### Post by Lethedethius on 2009-10-02
Awesome, I'm setting up an AKO Resource for Ubuntu, maybe I'll get questions and I can research how to fix them.  I'm going to make a tutorial on how to create VPN connections and using CAC Reader in Ubuntu Jaunty, I'll be sure to give credit back to this thread, thanks a lot!!!!:popcorn:

---

### Post by Lethedethius on 2009-10-02
> **zz97 said:**
> Has anyone successfully gotten this to work with Ubuntu Jaunty 64-bit?

I've installed the required packages--no problem there.  And pcsc_scan says everything's fine.  

But when I try to load the security module libcoolkeypk11.so, Firefox "freezes" and stops responding.  If I insert and remove the CAC a few times it will come back to life.  

But then if I try to access an https:// site, things don't work.  It will attempt to connect to the site for a minute or two, then (sometimes) eventually ask for my master password,  but entering the pin has yet to actually get me into a site. 

I get the same basic result with both Firefox 3.0 and Firefox 3.5.

My card reader is an SCR3310 v2.0.

Any ideas?

Hey I have Ubuntu Jaunty 64, and Firefox 3.0, and the same card reader... I followed the instructions and it worked flawlessly.  I create CAC Cards for the entire military (I'm a DEERS Rep in the Army), check and make sure your card isn't blocked/locked from trying the wrong PIN too many times.  It may need to be reset, and get the DEERS Rep to update your credentials and certifications... it may help.

---

### Post by arich57 on 2009-10-29
Hello,

My company just switch to CAC cards and I'm trying to get it to work on 9.04 Xubuntu.

I installed everything using apt-get and when I do pcsc_scan my card is found.

When I go to firfox 3.5 though I'm having issues. I loaded the module and my reader is found but the status is "Not Present" even when the card is inserted. I have tried this using a SCR3310 reader and an HP Smart Car Terminal Keyboard, Both give me:
```

Status          Not Present
Description     SCM SCR 3310 [HP USB Smart Card]
Manufacturer    Unknown
HW Version      255.255
FW Version      0.0

```
 
Has anyone else had this issue? Any idea what is going wrong?

Thanks.

---

### Post by arich57 on 2009-10-30
> **arich57 said:**
> Hello,

My company just switch to CAC cards and I'm trying to get it to work on 9.04 Xubuntu.

I installed everything using apt-get and when I do pcsc_scan my card is found.

When I go to firfox 3.5 though I'm having issues. I loaded the module and my reader is found but the status is "Not Present" even when the card is inserted. I have tried this using a SCR3310 reader and an HP Smart Car Terminal Keyboard, Both give me:
```

Status          Not Present
Description     SCM SCR 3310 [HP USB Smart Card]
Manufacturer    Unknown
HW Version      255.255
FW Version      0.0

```
 
Has anyone else had this issue? Any idea what is going wrong?

Thanks.

Also just tried it with a SCR 331 updated to latest firmware. Still no go.

---

### Post by TwistedRotors on 2009-11-01
Mole, 
Thank you for posting this! Followed your directions and the install went flawless. I just used my CAC to log into NMCI email using Firefox on Ubuntu Jaunty. NKO works as well and now I'm off to see if the DTS travel claim website works. If it does, then my XP partition will be a gone pecan!! Thanks again!
-John

---

### Post by Lachlanus on 2009-11-06
I am having trouble.  I am running Ubuntu 9.10 i386 and have the SCR331 card.  I performed the apt-get line you suggested and it seemed to execute without incident; however, when I try to execute pcsc_scan, I get the response "SCardEstablishContext: Service not available"  Where have I gone wrong?

---

### Post by arich57 on 2009-11-09
> **Lachlanus said:**
> I am having trouble.  I am running Ubuntu 9.10 i386 and have the SCR331 card.  I performed the apt-get line you suggested and it seemed to execute without incident; however, when I try to execute pcsc_scan, I get the response "SCardEstablishContext: Service not available"  Where have I gone wrong?

The pcsc daemon is not running. Either reboot are start manually

```

sudo /etc/init.d/pcscd start

```

-Aaron

---

### Post by MI_Diver67 on 2009-11-11
Worked great for me! Thanks for posting it!:popcorn:

---

### Post by roy.kimbrell on 2009-12-07
I have the same problem as arich57.

```
Status          Not Present
Description     SCM SCR 3310 [HP USB Smart Card]
Manufacturer    Unknown
HW Version      255.255
FW Version      0.0
```

I've tried most of the things I've read about in this forum.  

Any ideas?

---

### Post by illinoisbob on 2010-01-25
Hello,
  Thanks for the info.  I have the CAC and can read webmail.  My problem is when I try to open an encrypted e-mail, I get the following:  
The content cannot be displayed because the S/MIME control is not available."

Any ideas on how to fix this?
Thanks
Bob

---

### Post by James_in_Utah on 2010-02-23
This is as far as I get running pcsc_scan:

PC/SC device scanner
V 1.4.15 (c) 2001-2009, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.102
[COLOR=Red]Scanning present readers...
Waiting for the first reader...[/COLOR]

from lsusb, I know the reader is being detected:
Bus 002 Device 005: ID 09c3:0008 ActivCard, Inc. SmartCard Reader

Any ideas on how to get this working?
Thanks,
James

---

### Post by PhillB on 2010-03-29
> **roy.kimbrell said:**
> I have the same problem as arich57.

```
Status          Not Present
Description     SCM SCR 3310 [HP USB Smart Card]
Manufacturer    Unknown
HW Version      255.255
FW Version      0.0
```I've tried most of the things I've read about in this forum.  

Any ideas?

I'm in the same boat. I've tried reinstalling the module in Firefox to no avail. PCSC_SCAN will read the card, but Firefox does not recognize the presence of the card. It used to work because I was able to log on to the AF Portal as well as my base webmail, but now all of a sudden it doesn't work.

The only things that have changed is that I got a new CAC recently, and Update Manager has updated twice. On the same Dell D620, the reader works fine in Windows in both IE and Firefox. I can access both the Portal and Webmail. So my guess is it's the Ubuntu config. Anyone got any ideas? Here is my code from both Firefox and PCSC_SCAN.

```
Status          Not Present
Description     O2 Micro 0Z776 00 00
Manufacturer    Unknown
HW Version      255.255
FW Version      0.0
```
```
PC/SC device scanner
V 1.4.15 (c) 2001-2009, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.102
Scanning present readers...
0: O2 Micro Oz776 00 00

Mon Mar 29 15:54:58 2010
 Reader 0: O2 Micro Oz776 00 00
  Card state: Card inserted, 
  ATR: 3B 7D 96 00 00 80 31 80 65 B0 83 11 17 D6 83 00 90 00

ATR: 3B 7D 96 00 00 80 31 80 65 B0 83 11 17 D6 83 00 90 00
+ TS = 3B --> Direct Convention
+ T0 = 7D, Y(1): 0111, K: 13 (historical bytes)
  TA(1) = 96 --> Fi=512, Di=32, 16 cycles/ETU
    250000 bits/s at 4 MHz, fMax for Fi = 5 MHz => 312500 bits/s
  TB(1) = 00 --> VPP is not electrically connected
  TC(1) = 00 --> Extra guard time: 0
+ Historical bytes: 80 31 80 65 B0 83 11 17 D6 83 00 90 00
  Category indicator byte: 80 (compact TLV data object)
    Tag: 3, len: 1 (card service data byte)
      Card service data byte: 80
        - Application selection: by full DF name
        - EF.DIR and EF.ATR access services: by GET RECORD(s) command
        - Card with MF
    Tag: 6, len: 5 (pre-issuing data)
      Data: B0 83 11 17 D6
    Tag: 8, len: 3 (status indicator)
      LCS (life card cycle): 00 (No information given)
      SW: 9000 (Normal processing.)

Possibly identified card (using /home/phillip/.smartcard_list.txt):
3B 7D 96 00 00 80 31 80 65 B0 83 11 17 D6 83 00 90 00
    DoD CAC card issued Jan 14, 2010
```

Thanks for any ideas.

---

### Post by fatbotgw on 2010-03-30
> **zz97 said:**
> Has anyone successfully gotten this to work with Ubuntu Jaunty 64-bit?

I've installed the required packages--no problem there.  And pcsc_scan says everything's fine.  

But when I try to load the security module libcoolkeypk11.so, Firefox "freezes" and stops responding.  If I insert and remove the CAC a few times it will come back to life.  

But then if I try to access an https:// site, things don't work.  It will attempt to connect to the site for a minute or two, then (sometimes) eventually ask for my master password,  but entering the pin has yet to actually get me into a site. 

I get the same basic result with both Firefox 3.0 and Firefox 3.5.

My card reader is an SCR3310 v2.0.

Any ideas?

I did get it to work under x64 9.10 (Karmic).  I'm fully updated with Firefox 3.5.8 and I got into the AF Portal just fine.  However, I am running an SCR331 which I believe to be the v1.0 reader.

---

### Post by Sgt-Slyde on 2010-04-03
I'm seeing the same thing as PhilB; I had the CAC reader running fine in Jaunty and then had to replace my CAC out at work, now the new one is coming up with that same "Status - Not Present" and "Manufacturer - Unknown" when I check it out in Firefox.  (Edit > Preferences > Advanced > Security Devices").  I've removed/reinstalled Coolkey, libccid, even renamed the .Mozilla folder in my home directory and made Firefox generate a new profile.  So far no luck getting the new CAC to work even though the one I had until Thursday, April 1st worked fine under Karmic, Jaunty, and even the Lucid beta release.  The new card may as well not exist for all Firefox sees of it.

---

### Post by ManBlue on 2010-04-07
I'm trying to install software to make my Common Access Card reader work.
Did this: mkdir -p /usr/cac/lib/pkgconfig

Then this: declare -x PKG_CONFIG_PATH=/usr/cac/lib/pkgconfig

Finally this:  ./configure &#8211;prefix=/usr/cac && make && make install
I get this:


```
cory@cory-desktop:~/downloads/ccid-1.3.11$ ./configure &#8211;prefix=/usr/cac && make && make install
configure: error: invalid variable name: &#8211;prefix
cory@cory-desktop:~/downloads/ccid-1.3.11$ ./configure /usr/cac && make && make install
configure: WARNING: you should use --build, --host, --target
configure: WARNING: invalid host type: /usr/cac
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... Invalid configuration `/usr/cac': machine `/usr/cac' not recognized
configure: error: /bin/bash ./config.sub /usr/cac failed
```

What happened?

I have 9.10 on AMD64

Thanks

---

### Post by LugoffSCUser on 2010-05-16
i am using 10.04 and 3.6.3 of firefox. I had to search for where the drivers were located which were in /usr/lib64/pkcs11.  Also if you are using Synaptic Package manager do a search for CAC it will find the drivers which from AKO the link to the Coolkey is invalid.  I also installed Gscriptor which i find useful to assist in starting/stopping card services  :)

Happy Trails

SSG Morris

---

### Post by fire.for.effect on 2010-05-20
Awesome. Now I can sign my travel docs from Iraq.

---

### Post by tlhodgson on 2010-06-06
I can get my computer set up to do everything except digitally sign pure edge forms. Can anyone out there tell me how to do that? I'm running xubuntu 10.04. 
 
I can sign into AKO, I can view pure edge forms, but I can't actually digitally sign them. Any help would be great. Thanks.

---

### Post by PhillB on 2010-06-06
> **Sgt-Slyde said:**
> I'm seeing the same thing as PhilB; I had the CAC reader running fine in Jaunty and then had to replace my CAC out at work, now the new one is coming up with that same "Status - Not Present" and "Manufacturer - Unknown" when I check it out in Firefox.  (Edit > Preferences > Advanced > Security Devices").  I've removed/reinstalled Coolkey, libccid, even renamed the .Mozilla folder in my home directory and made Firefox generate a new profile.  So far no luck getting the new CAC to work even though the one I had until Thursday, April 1st worked fine under Karmic, Jaunty, and even the Lucid beta release.  The new card may as well not exist for all Firefox sees of it.

I think I figured it out.

Just tested a friend of mine's CAC card in my Ubuntu setup and it seems that not all CAC cards are created equal. My card must be like yours. When running pcsc_scan, the card type that comes up is:

DoD CAC card issued Jan 14, 2010

but my friend's CAC comes up with this

CAC (Common Access Card).

His card detected fine in Firefox and the security device tab was able to pick up his information while mine still said "Not Present". So, I'm thinking about going to the MPF and getting a new CAC card to try. The thing I'll look for is the difference in the chip electrical contacts. My friend's had all straight divider lines between all contacts. The center contact on my card resembles a mastercard logo. It looks like two adjacent circles overlapping in the center. If the new card has that style contact, I'm going to ask for a different one. We'll see happens.

---

### Post by charlesairman on 2010-06-29
Thank you for this great tutorial. I receive the following message when I insert the CAC:


Tue Jun 29 17:41:20 2010
 Reader 0: SCM SCR 3310 00 00
  Card state: Card inserted, Unresponsive card, 


Any Ideas? I have 2 different card readers (scr3310 and st-1000) both give same result. 

I can use the card when on base. 

thanks in advance

---

### Post by karlitux on 2010-08-25
:p Hey Thanks a lot!! It worked!

---

### Post by JT3 on 2010-08-30
Anyone have any luck with DTS?  My CAC card is working fine for everything else but I cannot seem to get into DTS.  When I first set it up I got a window asking me to point to a library..may have been associated with coolkey.  I think I put in the wrong information but I never do get that window anymore and can not figure out how to modify it.  I have uninstalled and reinstalled the CAC card reader and associated packages and did the same thing with the java packages.  Now I just get the DTS login error[B]:
[/B]**There has been a problem with login **     
The site is experiencing technical difficulties.  Please try again later or contact your DTS site administrator for assistance. 



Any ideas?  :confused:     Thanks!

---

### Post by Thystra on 2010-09-09
Anyone had any luck with getting one of the Gemalto 144k cards to work?  My card is detected but doesn't show the certificates to Firefox.

---

### Post by downindm on 2010-09-16
I'm trying to get this working on Lucid running on a PowerMac G4.  I basically followed the instructions here: [https://help.ubuntu.com/community/CommonAccessCard](https://help.ubuntu.com/community/CommonAccessCard)

Since there was no cackey for my system, I downloaded the source and compiled - which seemed to go fine once I also installed libpcsclite-dev

I am able to run pcsc_scan and get the following:
```
PC/SC device scanner
V 1.4.16 (c) 2001-2009, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.5.3
Scanning present readers...
0: SCM SCR 331 (21120751G19521) 00 00

Thu Sep 16 08:19:43 2010
 Reader 0: SCM SCR 331 (21120751G19521) 00 00
  Card state: Card inserted, 
  ATR: 3B DB 96 00 80 1F 03 00 31 C0 64 77 E3 03 00 82 90 00 C1

ATR: 3B DB 96 00 80 1F 03 00 31 C0 64 77 E3 03 00 82 90 00 C1
+ TS = 3B --> Direct Convention
+ T0 = DB, Y(1): 1101, K: 11 (historical bytes)
  TA(1) = 96 --> Fi=512, Di=32, 16 cycles/ETU
    250000 bits/s at 4 MHz, fMax for Fi = 5 MHz => 312500 bits/s
  TC(1) = 00 --> Extra guard time: 0
  TD(1) = 80 --> Y(i+1) = 1000, Protocol T = 0 
-----
  TD(2) = 1F --> Y(i+1) = 0001, Protocol T = 15 - Global interface bytes following 
-----
  TA(3) = 03 --> Clock stop: not supported - Class accepted by the card: (3G) A 5V B 3V 
+ Historical bytes: 00 31 C0 64 77 E3 03 00 82 90 00
  Category indicator byte: 00 (compact TLV data object)
    Tag: 3, len: 1 (card service data byte)
      Card service data byte: C0
        - Application selection: by full DF name
        - Application selection: by partial DF name
        - EF.DIR and EF.ATR access services: by GET RECORD(s) command
        - Card with MF
    Tag: 6, len: 4 (pre-issuing data)
      Data: 77 E3 03 00
    Mandatory status indicator (3 last bytes)
      LCS (life card cycle): 82 (Proprietary)
      SW: 9000 (Normal processing.)
+ TCK = C1 (correct checksum)

Possibly identified card (using /usr/share/pcsc/smartcard_list.txt):
3B DB 96 00 80 1F 03 00 31 C0 64 77 E3 03 00 82 90 00 C1
    CAC (Common Access Card)
```The issue I'm having is getting the module installed in Firefox (3.6.9).  When I browse to the libcackey.so file and click OK - Firefox just simply quits.  When I go back in and look to see if it maybe installed, it didn't.  Any ideas?

---

### Post by Thystra on 2010-09-16
> **Thystra said:**
> Anyone had any luck with getting one of the Gemalto 144k cards to work?  My card is detected but doesn't show the certificates to Firefox.


I found the solution to  my problem - As i got a new card recently, it was with DOD CA 25, and  my root certificates did not have those installed.  Update to the latest root certificates and you will be able to connect to the sites again.  Just make sure to download them before you get a new(er) card.


As far as it crashing, you might want to try the DOD xpi addon for PKI from [https://www.forge.mil](https://www.forge.mil)

---

### Post by ponga on 2010-10-20
I too had my CAC working perfectly in CentOS - but 2 days ago had to get a new CAC because the old one expired. This one is a GEMAL TO 144 card and does *NOT* work.
Running: CentOS 5.4 with the following relevant packages:

```

pcsc-lite-libs-1.4.4-0.1.el5
pcsc-lite-devel-1.4.4-0.1.el5
pcsc-lite-acr38u-1.7.9-2.el5.rf
pcsc-lite-1.4.4-0.1.el5
coolkey-1.1.0-14.el5

```In addition, I installed the latest root certs (including the CA that signed/issued my card) - no luck. A co-worker in the office still has the older card with WORKS. The older card shows up as expected in the Gnome Smart Card Manager, and in Firefox + Thunderbird. The card - nothing - "No Cards Present".

Still looking for a solution for these new CAC's, and am ALL ears if anyone has any suggestions. TIA

--ponga

---

### Post by ponga on 2010-10-20
RESOLVED

Evidently it's simply a problem with the coolkey library not being able to interrupt the new 144k cards. Our fine DoD fellows have the solution:
<[https://software.forge.mil/sf/frs/do/viewRelease/projects.community_cac/frs.cackey.0_5_12](https://software.forge.mil/sf/frs/do/viewRelease/projects.community_cac/frs.cackey.0_5_12)>

Simply get the RPM or DEB or SRC from there (CAC required, ironically) - install and within Firefox or Thunderbird or whatever, point to the .so file that the package installed and... viola!

Still trying to figure out how to get that working with the gnome-keyring and gnome smart card manager... but that's another project for another day I suppose.

FYI, Fedora has some updated source RPM's... I think I try that too, I've heard that the latest coolkey supports the new cards as well. Anyway...

Cheers.

--ponga

---

### Post by mkruza on 2010-10-21
> **JT3 said:**
> Anyone have any luck with DTS?  My CAC card is working fine for everything else but I cannot seem to get into DTS.  When I first set it up I got a window asking me to point to a library..may have been associated with coolkey.  I think I put in the wrong information but I never do get that window anymore and can not figure out how to modify it.  I have uninstalled and reinstalled the CAC card reader and associated packages and did the same thing with the java packages.  Now I just get the DTS login error[B]:
[/B]**There has been a problem with login **     
The site is experiencing technical difficulties.  Please try again later or contact your DTS site administrator for assistance. 



Any ideas?  :confused:     Thanks!
"rm -rf ~/.DBSign" from your home directory and then try logging in to DTS again. 

Then the "DBSign Universal Web Signer" should finally come back up again. On my machine the settings are:
PKCS#11 Library:  /usr/lib/pkcs11/libcoolkeypk11.so
PKCS #11 Password:  <YOUR CAC PIN>

---

### Post by Sgt-Slyde on 2010-10-26
> **ponga said:**
> RESOLVED

Evidently it's simply a problem with the coolkey library not being able to interrupt the new 144k cards. Our fine DoD fellows have the solution:
<[https://software.forge.mil/sf/frs/do/viewRelease/projects.community_cac/frs.cackey.0_5_12](https://software.forge.mil/sf/frs/do/viewRelease/projects.community_cac/frs.cackey.0_5_12)>

Simply get the RPM or DEB or SRC from there (CAC required, ironically) - install and within Firefox or Thunderbird or whatever, point to the .so file that the package installed and... viola!

Still trying to figure out how to get that working with the gnome-keyring and gnome smart card manager... but that's another project for another day I suppose.

FYI, Fedora has some updated source RPM's... I think I try that too, I've heard that the latest coolkey supports the new cards as well. Anyway...

Cheers.

--ponga
Thanks, ponga!  That worked fine - just went in out at work and downloaded the rpm file from software.forge and copied the .so file into my pkcs11 folder and now it's reading my GEMALTO 144 card like a champ!

---

### Post by darkdragn on 2010-10-30
Compiled the latest release of coolkey source, with about 7 extra patches, all put out by fedora (Mainly ripped from their source rpm, up to date as of 28 SEP 2010). This is working perfectly for me, so far i've tested it with a DOD issued cac, using ActivIdentity usb reader v3, ubuntu 10.04, on a i386 environment. If anyone thinks this would be easier than the other option (Or without this you cannot access the alternate option considering it requires a cac, lol) you are free to use it. For some reason i couldn't attach it as a .deb, so i just gzip tarred the debs.

---

### Post by shambotics on 2010-11-08
Thanks to mole84 for the tut and to ponga for the fix.  I'm one step closer to never having to boot in to windows again.

---

### Post by sgtlake on 2010-11-20
Ok i have a similar problem. Im trying to get my scr 3310 to read.. i got to your tutorial and it was helpful but i think my problem lies where pcsc saves the smartcard.text file its looking for it in the following location

Possibly identified card (using /usr/share/pcsc/smartcard_list.txt):
    NONE
I am able to get the latest text file by clicking the link but i cant save it in the above location due to permission faults.

Any ideas?

Thanks
Pt make it hurt

---

### Post by windowsh8r on 2010-11-23
I got my CAC card working fine on everything except webmail.  When I go to AF portal, I can select between the email certificate and the regular one, but when I try to access my base's webmail it says that it requires authentication without even asking for a certificate.

I found that these instructions worked great for installing the driver and getting firefox to recognize it.  Except my base's webmail, which does work through windows XP.

[http://www.hrgeeks.com/2008/11/21/using-a-dod-cac-with-ubuntu-and-firefox/](http://www.hrgeeks.com/2008/11/21/using-a-dod-cac-with-ubuntu-and-firefox/)

---

### Post by sgtlake on 2010-11-23
> **zz97 said:**
> Has anyone successfully gotten this to work with Ubuntu Jaunty 64-bit?

I've installed the required packages--no problem there.  And pcsc_scan says everything's fine.  

But when I try to load the security module libcoolkeypk11.so, Firefox "freezes" and stops responding.  If I insert and remove the CAC a few times it will come back to life.  

But then if I try to access an https:// site, things don't work.  It will attempt to connect to the site for a minute or two, then (sometimes) eventually ask for my master password,  but entering the pin has yet to actually get me into a site. 

I get the same basic result with both Firefox 3.0 and Firefox 3.5.

My card reader is an SCR3310 v2.0.

Any ideas?
Im having the exact same problem. Im thinking its the card reader. As soon as i put my id card in reader firefox closes. works fine without reader plugged in.

---

### Post by spaznrq on 2010-12-02
> **windowsh8r said:**
> I got my CAC card working fine on everything except webmail.  When I go to AF portal, I can select between the email certificate and the regular one, but when I try to access my base's webmail it says that it requires authentication without even asking for a certificate.

I found that these instructions worked great for installing the driver and getting firefox to recognize it.  Except my base's webmail, which does work through windows XP.

[http://www.hrgeeks.com/2008/11/21/using-a-dod-cac-with-ubuntu-and-firefox/](http://www.hrgeeks.com/2008/11/21/using-a-dod-cac-with-ubuntu-and-firefox/)

I also have issues with webmail, but I think it may be different than yours.  I actually got webmail working earlier today, but now, it's asking me to enter my "master password" (pin) multiple times over and over and over again.  Then it never brings me to my inbox.  I have a feeling my CAC is locked so I'll have to check on a Windows machine...

I'm hoping what I did earlier today to make it work would help you, but I'm not exactly sure how I can help... btw, using Ubuntu 10.10 here.

---

### Post by lingenfr on 2010-12-13
I am back at work today, so I downloaded the deb and the src. Has anyone used these on 64-bit 10.10? If I don't hear back, I will try the deb and see if it throws an error.

---

### Post by lingenfr on 2010-12-13
> **sgtlake said:**
> Ok i have a similar problem. Im trying to get my scr 3310 to read.. i got to your tutorial and it was helpful but i think my problem lies where pcsc saves the smartcard.text file its looking for it in the following location

Possibly identified card (using /usr/share/pcsc/smartcard_list.txt):
    NONE
I am able to get the latest text file by clicking the link but i cant save it in the above location due to permission faults.

Any ideas?

Thanks
Pt make it hurt

gksudo nautilus
(enter your password)

I expect the downloaded file is in your home directory. You should be able to copy it to the /usr/share/pcsc folder now.

---

### Post by Sgt-Slyde on 2010-12-13
[lingenfr]("http://ubuntuforums.org/member.php?u=22502"), I've used it on 10.10 and it's worked fine.  The install script wouldn't run but I was able the "un-zip" the RPM file and manually copy the libcackey.so into the /usr/lib64/pkcs11 directory.

---

### Post by lingenfr on 2010-12-13
> **lingenfr said:**
> I am back at work today, so I downloaded the deb and the src. Has anyone used these on 64-bit 10.10? If I don't hear back, I will try the deb and see if it throws an error.

OK, as expected, when I tried to install the deb it wouldn't saying 'wrong architecture'. So, I unzipped the src and tried to compile. The ./configure failed. I wasn't sure what needed to be installed in order to compile. I have build-essential, but didn't know what else I needed. The config.log is attached.

---

### Post by Sgt-Slyde on 2010-12-13
Did you try to "un-zip" the RPM file and manually copy the libcackey.so into the /usr/lib64/pkcs11 directory?  That's what worked for me on the 64-bit install on my Intel i3.

---

### Post by rwslippey on 2010-12-27
Great post, thanks for sharing you hard work and knowledge. Was hoping someone could help me a bit though. I my CAC working on ubuntu previously Ubuntu 10.04  ... now for some reason I decided to take my laptop to the next level....  So now I'm running 10.10 64 bit....

Everything seemed to install correctly, however I can't access anything. When I go to my portal (AKO) I just get an access denied error. any ideas?


thanks Rob

---

### Post by Spc 4 on 2011-02-10
> **tlhodgson said:**
> I can get my computer set up to do everything except digitally sign pure edge forms. Can anyone out there tell me how to do that? I'm running xubuntu 10.04. 
 
I can sign into AKO, I can view pure edge forms, but I can't actually digitally sign them. Any help would be great. Thanks.
I have the same problem also. I tried using wine, but it just got too tricky.Now Im trying to get this to work for DTS, but I think it will only work in explorer.

---

### Post by Spc 4 on 2011-02-10
> **rwslippey said:**
> Great post, thanks for sharing you hard work and knowledge. Was hoping someone could help me a bit though. I my CAC working on ubuntu previously Ubuntu 10.04  ... now for some reason I decided to take my laptop to the next level....  So now I'm running 10.10 64 bit....

Everything seemed to install correctly, however I can't access anything. When I go to my portal (AKO) I just get an access denied error. any ideas?


thanks Rob
Try deleting your cookies and stuff in firefox.

---

### Post by mangurt on 2011-06-05
Ok, I'm having a major problem getting this working with ubuntu 11.04 and the stock firefox that comes with it.  I've set this up a bunch of times before, and it was pretty simple.

Here's my problem, as soon as I insert my CAC card into the CAC reader, firefox crashes.  Any ideas?
Thanks

---

### Post by ken_23434 on 2011-06-09
I am having trouble, too.  I also am running 11.04 64-bit version.  

I can use the scan command in the terminal and it will identify my CAC.

Firefox will "hang" and then give a crash report any time I try to access a site using PKI.

I tried to unload the CAC Module to try and load the cackey version from the .mil software portal mentioned in this thread.  Everytime I try to reload the CAC Module, Firefox gives an error "Cannot load Module".  It will give me this same error if I try to point it to the coolkey module also.

---

### Post by bubbafhett on 2011-06-13
I have the same problem. I was able to get around the initial crash from just loading the firefox module (just take out your CAC when you select the module). So, even though I finally got the module loaded in firefox, it crashes when I insert a CAC.

> **ken_23434 said:**
> I am having trouble, too.  I also am running 11.04 64-bit version.  

I can use the scan command in the terminal and it will identify my CAC.

Firefox will "hang" and then give a crash report any time I try to access a site using PKI.

I tried to unload the CAC Module to try and load the cackey version from the .mil software portal mentioned in this thread.  Everytime I try to reload the CAC Module, Firefox gives an error "Cannot load Module".  It will give me this same error if I try to point it to the coolkey module also.

---

### Post by aggiemarine07 on 2011-07-02
same problem here. does anyone have a solution for this yet?

---

### Post by cyanidin on 2011-09-01
I was having problems getting my card reader to work as well. I tried upgrading the card reader firmware, installing a newer version of coolkey, pointing to the 64bit shared objects (.so), adding the module directly with modutil, and installing cackey.
I removed the modutil configuration I had added it still crashed. I removed coolkey and the libckyapplet1 and Firefox stopped crashing.

I know this is not a definitive answer, but, for DoD users, I recommend uninstalling coolkey and installing cackey. You will need to go to a system that allows CAC login to download the OS specific package you need from [https://software.forge.mil/sf/frs/do/listReleases/projects.community_cac/frs.cackey](https://software.forge.mil/sf/frs/do/listReleases/projects.community_cac/frs.cackey). If it is impossible for you to access [www.forge.mil]("http://www.forge.mil"), contact your signal support personnel and ask for them to email a current version of cackey to your .mil email address.

Viola! Violin! Cello!

---

### Post by Spc 4 on 2011-10-19
> **cyanidin said:**
> I was having problems getting my card reader to work as well. I tried upgrading the card reader firmware, installing a newer version of coolkey, pointing to the 64bit shared objects (.so), adding the module directly with modutil, and installing cackey.
I removed the modutil configuration I had added it still crashed. I removed coolkey and the libckyapplet1 and Firefox stopped crashing.

I know this is not a definitive answer, but, for DoD users, I recommend uninstalling coolkey and installing cackey. You will need to go to a system that allows CAC login to download the OS specific package you need from [https://software.forge.mil/sf/frs/do/listReleases/projects.community_cac/frs.cackey](https://software.forge.mil/sf/frs/do/listReleases/projects.community_cac/frs.cackey). If it is impossible for you to access [www.forge.mil]("http://www.forge.mil"), contact your signal support personnel and ask for them to email a current version of cackey to your .mil email address.

Viola! Violin! Cello!
Can you update the tutorial? I can copy-paste ino terminal, but all this stuff is way over my head. Ubuntu 11.10 broke my CAC card. It worked fine until I updated.

---

### Post by perro68 on 2012-02-16
> **sgt-slyde said:**
> thanks, ponga!  That worked fine - just went in out at work and downloaded the rpm file from software.forge and copied the .so file into my pkcs11 folder and now it's reading my gemalto 144 card like a champ!


hope this works for me

---

### Post by blipside on 2012-03-08
Thanks for all of the information.  I had to get the CACkey from work & send it home using G-mails draft option (the servers at work stripped the file).  I put the libcackey.so in the lib64/pkcs11 folder & loaded it.  Now Firefox recognizes my card & I can log into the AF Portal.  My next thing is to get IT Learning working, that's the whole reason I did this.

---

### Post by mole84 on 2012-03-29
Updated the tutorial, a key step now is to install certificates from the new site and enable FIPS in the security devices window. Working on Firefox 11.0 64 bit system.

---

