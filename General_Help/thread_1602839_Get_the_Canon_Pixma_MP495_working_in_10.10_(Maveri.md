---
title: "Get the Canon Pixma MP495 working in 10.10 (Maverick)"
date: 2010-10-21
forum: General Help
---

### Post by modsbyus on 2010-10-21
I have finaly gotten the Canon Pixma MP495 working under Ubuntu 10.10, with full resolution capabilities of the printer.
This printer is only advirtised as having a max resolution of 4800x1200 DPI. However, I called Canon to get the full range of print resolutions and was informed that this printer is capable of 9600x2400 DPI.

I haven't tested this below Ubuntu 10.04 but it should work fine.


For setting your MP495 printer up on your network without the use of a Windows or Mac machine (Fresh out of the box with Ubuntu) you will need to match your Routers SSID to the printers default SSID, and remove any security you have enabled. This will allow the printer to connect to your network.
[COLOR="DarkOrange"]Printer Defaults:
SSID: BJNPSETUP
IP ADDRESS: Automatic
[/COLOR]
Once you have done that you will need to activate the wireless lan on the printer.
Press the Maintenance button on the printer 13 times until you see what looks like a capital G without the middle line. Then press the color start button. (refer to page 10 of your [COLOR="DarkOrange"]Network Setup Troubleshooting[/COLOR] manual for an actual picture of the symbol) You should see the wifi light on the front of the printer turn on and be solid not be blinking. (If it is blinking check your routers SSID settings and match the Default SSID of the printer as listed above.

Now download angryipscanner [AngryIPScanner]("http://sourceforge.net/project/downloading.php?group_id=25534&filename=ipscan_3.0-beta4_i386.deb") and install it by double clicking it. It should open in the Software center or with the Gdebi installer. (this may take a few minutes to install.)
Once you have installed AngryIPScanner, run it and change the ip range to include from 1 - 254 in the last octet. Then click start. 
When it finishes look for an active connection with a Hostname like A001BF000000.local. Yours may be different but should be very simular.
The IP address given for that hostname is the IP address of your printer. Open Firefox and type that address in the address bar and press enter. From there you can configure you printer for the SSID, and encryption that you had on your router before the change, and set a static IP for the printer so you can manage it easily.
After you change the SSID and encryption on the printer you will have to go back to your router and change the SSID and encryption back to what it was before so your printer can connect again.

Now your network should be back the way it was and your printer should be connected

Now that you have successfully connected the printer to your wireless network continue with the rest of the installation.

Download the drivers for the [MP495]("http://support-au.canon.com.au/contents/AU/EN/0100301501.html") .

You will be downloading cnijfilter-mp495series-3.40-1-deb.tar.gz. 
[COLOR="Red"]
Try this method first![/COLOR]
Extract cnijfilter-mp495series-3.40-1-deb.tar.gz to your Home directory.
Change the permissions of the install.sh file to run and an executable by Right licking on install.sh and then left clicking Properties.
Click on the Permissions tab and put a check mark in the [COLOR="DarkOrange"]Allow Executing file as program[/COLOR] box.
Then open a terminal and type:
```
sudo ./install.sh[CODE]
Follow the prompts and if you are using the printer over the network select network when prompted. I you are using it via USB choose USB.
 Don't forget to scroll down to complete setting up your printer to use full resolution and set up the scanner.

[COLOR="Red"] If the first method didnt work try this.[/COLOR]
Open a terminal and enter [CODE]cd /home/*/cnijfilter-mp495series-3.40-1-deb/packages
``` . (Enter your username where the astride is.)

> For 64 bit systems you need to replace cnijfilter-common_3.40-1_i386.deb, and cnijfilter-mp495series_3.40-1_i386.deb with cnijfilter-common_3.40-1_amd64.deb, and
cnijfilter-mp495series_3.40-1_amd64.deb. For the printer setup.
For the scanner replace scangearmp-common_1.60-1_i386.deb, and scangearmp-mp495series_1.60-1_i386.deb with scangearmp-common_1.60-1_amd64.deb, scangearmp-mp495series_1.60-1_amd64.deb. Everything else is the same.

Now enter ```
sudo dpkg -i cnijfilter-common_3.40-1_i386.deb
``` and press enter.

Now enter ```
sudo dpkg -i cnijfilter-mp495series_3.40-1_i386.deb
``` and press enter.

After that is complete go to System-Administration-Printing and click on Add.

If you have set up your printer on your network you should find it listed under Network Printing after a moment. (It takes a second for Ubuntu to find it on the network.)
Select the Canon-MP495-series_XX-XX-XX-XX-XX then click [Forward].
It will tell you that it is searching for Drivers. (wait for it.....)
In just a second a new window will appear asking for the Description of the Printer. Give it a name in the Location Field.

Now that you have a functioning MP495 printer, printing at a meager 600 DPI, lets make it better!

[COLOR="Red"]Change the Available Resolutions for Printing[/COLOR]

Open another terminal and edit the first of two postscript files for this printer. ```
gksudo gedit /etc/cups/ppd/Canon-MP495.ppd
```

Find: *OpenUI *Resolution/Output Resolution: PickOne

Then we are going to replace the text from: *OpenUI *Resolution/Output Resolution: PickOne to: *CloseUI: *Resolution
With: 
*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 4800dpi
*Resolution 600dpi/600 DPI: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200dpi/1200 DPI: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400dpi/2400 DPI: "<</HWResolution[2400 2400]>>setpagedevice"
*Resolution 2400dpi/4800 DPI: "<</HWResolution[2400 4800]>>setpagedevice"
*Resolution 2400dpi/9600 DPI: "<</HWResolution[2400 9600]>>setpagedevice"
*CloseUI: *Resolution

Save and close gedit. 

Open another terminal and edit the second postscript file for this printer. ```
gksudo gedit /usr/share/ppd/canonmp495.ppd

```
Find: *OpenUI *Resolution/Output Resolution: PickOne

Then we are going to replace the text from: *OpenUI *Resolution/Output Resolution: PickOne to: *CloseUI: *Resolution
With: 
*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 4800dpi
*Resolution 600dpi/600 DPI: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200dpi/1200 DPI: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400dpi/2400 DPI: "<</HWResolution[2400 2400]>>setpagedevice"
*Resolution 2400dpi/4800 DPI: "<</HWResolution[2400 4800]>>setpagedevice"
*Resolution 2400dpi/9600 DPI: "<</HWResolution[2400 9600]>>setpagedevice"
*CloseUI: *Resolution

Save and close gedit.

Now restart the cups service.
with ```
sudo service cups restart
``` in Ubuntu 10.10 and I think 10.04 too.
or ```
sudo /etc/init.d/cups restart
``` in previous verions.

You can now print with resolutions ranging from 600 DPI to 9600 DPI!
Enjoy.

For getting the scanner working download the drivers from [here]("http://support-au.canon.com.au/contents/AU/EN/0100302801.html").

extract scangearmp-mp495series-1.60-1-deb.tar.gz into your home directory.
Open terminal and type. (Replace the astride with your user name.)
```
cd /home/*/scangearmp-mp495series-1.60-1-deb
```
```
sudo ./install.sh
```
Then to use your scanner, open terminal and type.
```
scangearmp
```
A Big thanks goes to BartmanMN for finding the Scanner drivers.
Enjoy!

---

### Post by j4play on 2010-11-01
thanks for that writeup!  works a treat.

---

### Post by modsbyus on 2010-11-01
Glad I could help.

---

### Post by Loosehead01 on 2010-11-05
Check this out: among others you will find debian and rpm package-archives:
[download linux software]("http://support-au.canon.com.au/P/search?model=PIXMA+MP495&menu=download&filter=0&tagname=g_os&g_os=Linux")
Those archives contain install scripts which automatically handles setup and architecture.
Corresponding manuals are archived under the [manuals tab]("http://support-au.canon.com.au/P/search?model=PIXMA+MP495&filter=0&menu=manual").

---

### Post by modsbyus on 2010-11-05
Thank you. Those are good resourses. I, like others have tried those solutions and found them to unsatisfactorly get this printer working. Sometimes they would work and not others. In my personal experience I was able to print a test page but not be able to print from within any other software.  Also, I added getting full printing resolution instead of just 600 dpi. There may have been more to getting those drivers to function properly but I didn't find it.

---

### Post by ganda99 on 2010-11-22
Well, I was excited about finding this guide until I encountered this:

sudo dpkg -i cnijfilter-common_3.40-1_i386.deb
dpkg: error processing cnijfilter-common_3.40-1_i386.deb (--install):
 **package architecture (i386) does not match system (amd64)**
Errors were encountered while processing:
 cnijfilter-common_3.40-1_i386.deb


Ouch. 

Any ideas?

---

### Post by ganda99 on 2010-11-22
Duh, 

Never mind. I didn't even notice the amd64 files in the package.

---

### Post by modsbyus on 2010-11-22
I'm sorry for that. I didn't even think about putting in instructions for 64 bit, but Im glad you figured it out.

---

### Post by BartmanMN on 2010-12-10
Thanks for the info.  I have downloaded the driver and set up my printer with the enhanced settings.  Any idea how to get SimpleScan to find the MP495 as a Scanner?

---

### Post by modsbyus on 2010-12-10
Not yet but I can look into it. I haven't had the need yet. I can look at it thusday night after I get back from vacation. Check back friday

---

### Post by BartmanMN on 2010-12-10
Sounds good. Thanks

---

### Post by 0260n5 on 2010-12-12
Hi there, I am new here and don't have much experience with this type of thing at all.  I followed your post and I keep coming up with "cannot fine file or directory."  I have checked and I downloaded the files to the home folder.  Any suggestions????

---

### Post by modsbyus on 2010-12-12
> **0260n5 said:**
> Hi there, I am new here and don't have much experience with this type of thing at all.  I followed your post and I keep coming up with "cannot fine file or directory."  I have checked and I downloaded the files to the home folder.  Any suggestions????

What exactly did you type in terminal when you got the error?
What distribution are you using?

---

### Post by 0260n5 on 2010-12-13
I typed in exactly as what you have posted as well as different variations including my user name after /home/

I believe I have the latest version installed.

---

### Post by modsbyus on 2010-12-13
Can you post the output?

---

### Post by 0260n5 on 2010-12-13
this is what i get.....
steve@Laptop:~$ cd /home/*/cnijfilter-mp495series-3.40-1-deb/packages
bash: cd: /home/*/cnijfilter-mp495series-3.40-1-deb/packages: No such file or directory
steve@Laptop:~$

---

### Post by 0260n5 on 2010-12-13
Forgot to change the username....

steve@Laptop:~$ cd /home/steve/cnijfilter-mp495series-3.40-1-deb/packages
bash: cd: /home/steve/cnijfilter-mp495series-3.40-1-deb/packages: No such file or directory
steve@Laptop:~$

I am running 10.04

---

### Post by modsbyus on 2010-12-13
> **0260n5 said:**
> Forgot to change the username....

steve@Laptop:~$ cd /home/steve/cnijfilter-mp495series-3.40-1-deb/packages
bash: cd: /home/steve/cnijfilter-mp495series-3.40-1-deb/packages: No such file or directory
steve@Laptop:~$

I am running 10.04

Well, something is amiss. Type ```
cd /home/steve
```
then ```
ls
```
You should see the folder cnijfilter-mp495series-3.40-1-deb listed there. If you do not, then you dont have it in the right directory.
Just double check everything.

---

### Post by 0260n5 on 2010-12-13
steve@Laptop:~$ cd /home/steve
steve@Laptop:~$ ls
cnijfilter-mp495series-3.40-1-deb  examples.desktop  Pictures   Ubuntu One
Desktop                            G8 Manual         Public     Videos
Documents                          Jacki docs        resources
Downloads                          Music             Templates
steve@Laptop:~$

---

### Post by 0260n5 on 2010-12-13
ok so I dropped /packages and got this.  The only problem now is that it will not show my password.  The cursor just blinks at me.  It is kind of like it is saying are you stupid, to which I reply....uh yeah!

steve@Laptop:~$ cd /home/steve
steve@Laptop:~$ ls
cnijfilter-mp495series-3.40-1-deb  examples.desktop  Pictures   Ubuntu One
Desktop                            G8 Manual         Public     Videos
Documents                          Jacki docs        resources
Downloads                          Music             Templates
steve@Laptop:~$ cd /home/steve/cnijfilter-mp495series-3.40-1-deb
steve@Laptop:~/cnijfilter-mp495series-3.40-1-deb$ sudo dpkg -i cnijfilter-common_3.40-1_i386.deb
[sudo] password for steve:

---

### Post by modsbyus on 2010-12-13
Firstly you need to make sure that the .deb package is there where I origonaly posted.  It wont be in the root of the first folder it will be in /packages. Secondly,when it asks for your password just type it and press enter. It doesn't show any output as you type passwords in terminal. If you can't find everything where I said it would be try redownloading the file and extracting it to /home/steve . Then just going for it again.

---

### Post by modsbyus on 2010-12-13
Did you get my PM?

---

### Post by BartmanMN on 2010-12-18
I am still looking for help with getting ubuntu 10.10 to recognize my Canon Pixma MP495 as a Scanner from the Simple Scan software.  Any help would be appreciated. 

Thanks

---

### Post by modsbyus on 2010-12-18
> **BartmanMN said:**
> I am still looking for help with getting ubuntu 10.10 to recognize my Canon Pixma MP495 as a Scanner from the Simple Scan software.  Any help would be appreciated. 

Thanks

I am very sorry. I will look into it this evening. Sorry, with the holidays things are very busy.

---

### Post by modsbyus on 2010-12-18
OK, So I have done quite a bit of research and found that there is no support or even mention of future support for the scanning function of the printer.Unfortunately in order to build a driver for linux for this printer it will require some special equipment for scanning the ***munication between the printer an a windows system... Or at least that the way that I understand it. There is support for several other MP series canon scanners though xsane but they haven't made it to this one or even mentioned it on the site.

---

### Post by BartmanMN on 2010-12-19
Could I load a different MP driver and use xsane instead?  I don't need anything fancy, just the ability to scan.

---

### Post by modsbyus on 2010-12-19
I don't know. Some printers use the same commands. You may be able to but I didn't find one. Read up on xsanes mp series drivers. You might find something I missed.

---

### Post by BartmanMN on 2010-12-20
Looks like there are Scanning drivers in here.
[FONT=Arial][SIZE=2][http://support-au.canon.com.au/P/search?model=PIXMA+MP495&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-au.canon.com.au/P/search?model=PIXMA+MP495&menu=download&filter=0&tagname=g_os&g_os=Linux)[/SIZE][/FONT]
  
I will play with them

---

### Post by modsbyus on 2010-12-20
> **BartmanMN said:**
> Looks like there are Scanning drivers in here.
[FONT=Arial][SIZE=2][http://support-au.canon.com.au/P/search?model=PIXMA+MP495&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-au.canon.com.au/P/search?model=PIXMA+MP495&menu=download&filter=0&tagname=g_os&g_os=Linux)[/SIZE][/FONT]
  
I will play with them
Excellent,  I'm really glad you found that. I searched their site but didn't come across those drivers.
Ill test these when I get home also and post my findings. If this works Ill edit the first post to include it.

Great find

---

### Post by BartmanMN on 2010-12-20
I unpacked the scangear common first similarly to your instructions on page 1 and then I unpacked the scangear for MP495 driver and restarted the cups service, however after that I still could not get xsane or simple scan to recognize the scanner.  Hopefully you come up with something.

---

### Post by modsbyus on 2010-12-20
Got the scanner working. You had the right drivers and were on the right track. All you were missing was the command to bring up the software.
In terminal type.
```
scangearmp
```
Im glad you found those drivers. That was bothering me. Ive updated the main post.
Thanks

---

### Post by BartmanMN on 2010-12-21
> **modsbyus said:**
> Got the scanner working. You had the right drivers and were on the right track. All you were missing was the command to bring up the software.
In terminal type.
```
scangearmp
```Im glad you found those drivers. That was bothering me. Ive updated the main post.
Thanks


Sweet thanks.  Still not recognized by Simple Scan, however using scangearmp should be sufficient.

---

### Post by inameiname on 2010-12-21
I just got this printer today, and after looking at this thread so far, it seems to full work with Ubuntu 10.10 after a couple little installations of drivers and such. 

So from all of it, can anybody confirm that the printer works just fine with Ubuntu, and all of the functions work, notably as a basic printer and scanner? It's just a read a lot on this thread and it seems to be complete, but I just would like to know for sure from those that have been successful with it, so I can feel content on keeping it and using it. Thanks.

---

### Post by BartmanMN on 2010-12-22
Yes, if you follow the instructions on the first page you will be able to print with dpi up to 9600 and you will be able to scan with the scangearmp command.

---

### Post by cpendj on 2010-12-28
I have received an error: 

dpkg: error processing cnijfilter-common_3.40-1_i386.deb
package architecture (i386) does not match system (amd64)

can someone help me fix this please I'm a new user to ubuntu

---

### Post by modsbyus on 2010-12-28
You need to replace cnijfilter-common_3.40-1_i386.deb, and cnijfilter-mp495series_3.40-1_i386.deb with cnijfilter-common_3.40-1_amd64.deb, and
cnijfilter-mp495series_3.40-1_amd64.deb. For the printer setup.
And scangearmp-common_1.60-1_i386.deb, and scangearmp-mp495series_1.60-1_i386.deb with scangearmp-common_1.60-1_amd64.deb, scangearmp-mp495series_1.60-1_amd64.deb for the scanner. You will always look for the amd64 files for your 64 bit OS. Everything else is the same.

---

### Post by ademeda on 2010-12-28
I had this printer working fine. I have a wifi I would like to put it on now, my computer found it but wouldn't print so i removed it and now I can't even pick it up without telling it where to find it. And still the processing error persists. Any Ideas, but the scanner works fine over wifi so ...

---

### Post by modsbyus on 2010-12-28
Try running the install.sh inside if the folder for the printer drivers. Run like: ```
sudo ./install.sh
```

---

### Post by ademeda on 2010-12-28
Thanks worked like a charm.

---

### Post by inameiname on 2010-12-30
Awesome...thank you all for your assistance.

---

### Post by modsbyus on 2010-12-30
You're Welcome. I'm glad you got it working to your satisfaction.

---

### Post by mark.0 on 2011-01-01
Has anyone sucessfully setup the canon Pixma 495 as a network printer without a windows or mac workstation handy? The directions in this thread are great, but I can't see a way to setup the printer as network printer without one, and the directions here assume that the printer is already setup...

The directions that come with the printer use the wizard-like intall utility on the setup cd that configures the access point. I've tried using wine, but the only way to get to the utility is to select to install the mp drivers, which causes wine to crash.

---

### Post by modsbyus on 2011-01-01
> **mark.0 said:**
> Has anyone sucessfully setup the canon Pixma 495 as a network printer without a windows or mac workstation handy? The directions in this thread are great, but I can't see a way to setup the printer as network printer without one, and the directions here assume that the printer is already setup...

The directions that come with the printer use the wizard-like intall utility on the setup cd that configures the access point. I've tried using wine, but the only way to get to the utility is to select to install the mp drivers, which causes wine to crash.

I have gone through the commands available in the print drivers packages from Canon and not found any network setup. As you can see (from the release notes) This is a very low priority.
> cnijfilter-common (3.40-1) stable; urgency=low

  * Initial Release.

 -- Canon Inc. <sup-debian@list.canon.co.jp>  Thu, 19 Aug 2010 12:00:00 +0900

---

### Post by mark.0 on 2011-01-01
So I guess that's a no. Bummer.

---

### Post by modsbyus on 2011-01-01
> **mark.0 said:**
> So I guess that's a no. Bummer.

I am working on it. Im trying to figure out how the setup in Windows communicates the setup info with the printer. I know that it uses USB, but I dont know how.

---

### Post by modsbyus on 2011-01-01
I got it! I just figured out how to set it up on the network using Ubuntu!
I am going to edit the first post and it will be available momentarily.

---

### Post by inameiname on 2011-01-02
Oh lovely. So you are saying, modsbyus, that since you figured it out (which I noticed is in the first post now, right?), it all works? 

Basically, by following the first post correctly, I should be able to print, scan, and set up as a network printer for several of my wireless internet computers such as my laptop?

Seems from this post, the only issue people are still having if the above works correctly when tried is the ability to use Simple Scan like any other scanner.....but that's something you are working on, if I'm not mistaken. 

I just want to get it all straight for when I do this. Thanks.

Here's the procedure I think it is:

1. Change router settings to default printer network settings
2. Use  [AngryIPScanner]("http://sourceforge.net/project/downloading.php?group_id=25534&filename=ipscan_3.0-beta4_i386.deb") to find the ip address of the printer, so you can change it to a static one (this means you only need this package once, for finding it, and not needed to be installed on all machines)
3. Then a simple installation of both the printer drivers and the scanner drivers that I found in deb form on the links given (and to use the scanner bit, type 'scangearmp' when desired for such
4. Edit the resolutions of the printer so you can have greater range

So for all my machines that wish to use this printer, I really just needed to install those 2 tar files with the deb packages for the printer and scanner part, and edit those two files for the greater printer resolutions? Does that sound about right? After using AngryIPScanner once and finding ip of the printer, of course.


Edit:

One last thing, I read that if you go for a network printing option, you cannot use the USB. Now, I'm guessing that means that ALL computers that want to use the printer MUST be either connected through an ethernet cord or wirelessly to the router....right? So the main one that doesn't have wireless but does connect to the wireless router through a cord will pick up the printer?

---

### Post by modsbyus on 2011-01-02
> **inameiname said:**
> Oh lovely. So you are saying, modsbyus, that since you figured it out (which I noticed is in the first post now, right?), it all works? 

Basically, by following the first post correctly, I should be able to print, scan, and set up as a network printer for several of my wireless internet computers such as my laptop?

Seems from this post, the only issue people are still having if the above works correctly when tried is the ability to use Simple Scan like any other scanner.....but that's something you are working on, if I'm not mistaken. 

I just want to get it all straight for when I do this. Thanks.

Here's the procedure I think it is:

1. Change router settings to default printer network settings
2. Use  [AngryIPScanner]("http://sourceforge.net/project/downloading.php?group_id=25534&filename=ipscan_3.0-beta4_i386.deb") to find the ip address of the printer, so you can change it to a static one (this means you only need this package once, for finding it, and not needed to be installed on all machines)
3. Then a simple installation of both the printer drivers and the scanner drivers that I found in deb form on the links given (and to use the scanner bit, type 'scangearmp' when desired for such
4. Edit the resolutions of the printer so you can have greater range

So for all my machines that wish to use this printer, I really just needed to install those 2 tar files with the deb packages for the printer and scanner part, and edit those two files for the greater printer resolutions? Does that sound about right? After using AngryIPScanner once and finding ip of the printer, of course.


Edit:

One last thing, I read that if you go for a network printing option, you cannot use the USB. Now, I'm guessing that means that ALL computers that want to use the printer MUST be either connected through an ethernet cord or wirelessly to the router....right? So the main one that doesn't have wireless but does connect to the wireless router through a cord will pick up the printer?

Looks like you got everything right except...
You can use the printer with all PCs that have the drivers installed using this tutorial over USB. I have tested this and when the printer/scanner is connected USB Ubuntu detects and installs for you.

As far as Simple Scan... I am not working on using it. I think the provided application (scangear) works fine and I don't think I'm up for porting it over to Simple Scan. Sorry

PS. I made a launcher on my desktop for the scangear command.

---

### Post by inameiname on 2011-01-02
So far so good. I can print and scan using my laptop in another room. At this time, no usb cord is plugged into the printer. It's all working strictly wireless.

Now, I am a little confused by what you mean here:

> 
You can use the printer with all PCs that have the drivers installed  using this tutorial over USB. I have tested this and when the  printer/scanner is connected USB Ubuntu detects and installs for you.
Does that mean that for my desktop, to which has no wireless capability and normally is the only computer that uses a printer, connected through a standard usb, it'll work the same, so long as I install both the printer and scanner drivers for it?

Also, what you are saying above about the usb doesn't apply with how mine's set up now, for use with any wireless network capable laptops and other computers?

Perhaps you mean that when you are installing the drivers and it asks you if you are using a usb or wireless connection, choose the usb option for that particular usb-connected desktop? Is that all you meant?


Oh, and in regards to my installation, one small thing I noticed was that this file:

gksudo gedit /etc/cups/ppd/Canon-MP495.ppd

didn't exist, but was named this instead:

gksudo gedit /etc/cups/ppd/MP495LAN.ppd

AND...

my trendnet router showed the ip address of the printer along with all devices currently connected to it (such as my laptop), so I didn't have to use angryipscanner, though I did anyway just to check.

AND...

thanks for all of the info and help. I just made a launcher as well. Good enough for me. I've never used Simple Scan anyway as of the few scanners I have here none work with Linux....:( So it's nice having this one now.

---

### Post by modsbyus on 2011-01-02
As far as USB is concerned. I just mean that no matter which way you set up any PC, you can still use the USB connection for the printer.

Not sure why you had a different PPD file but I'm glad you got it working.

---

### Post by inameiname on 2011-01-02
Oh, alright. Thanks for the clarification. 

I installed the drivers on my desktop just like my laptop, and without a usb cord, so it all works off wireless now, and all's well. Really, the biggest concern I had was if I had to have my desktop connected through a usb cord or not (and if that would affect the wifi connections to my laptop), but now I know it can all be run wirelessly, so long as my computer is connected wirelessly or wired to my wireless router. All sorted.

Thanks for everything.

---

### Post by inameiname on 2011-01-02
A bit off topic, but did anybody have as much trouble as I did trying to decipher the manual for this printer? :P Well, at least here in the states, it was probably the most poorly laid out one I've ever seen. Instead of the usual English side and a Spanish side on the reverse, this one had both after nearly every paragraph. And to make things worse, this one had another separation after every couple paragraphs with Windows and Macintosh. Oh, and not to mention the pictures randomly thrown in there to 'help'. Hehe

Sorry, I just felt like whining.... :P

Though, I'm glad I'm using Ubuntu and not Windows or Macintosh, as I would've thrown the printer in a wall after a few minutes if I actually had to follow the 'instructions'.

---

### Post by modsbyus on 2011-01-02
I agree with you about the manual. Its very confusing and porly laid out. But, im glad I could help save your wall LOL

---

### Post by inameiname on 2011-01-03
Hehe. And so is my wall. ;)

---

### Post by arguile on 2011-01-19
You might want to change the URL for the scangear download to [http://support-au.canon.com.au/contents/AU/EN/0100302801.html](http://support-au.canon.com.au/contents/AU/EN/0100302801.html) since it's the fifth item on the screen and the people rushing through this might get the wrong download.

Other than that, thank you VERY MUCH for the installation guide.  I went out and bought this printer specifically because I was able to find an easy to understand guide for getting this to work on Linux.

---

### Post by modsbyus on 2011-01-19
> **arguile said:**
> You might want to change the URL for the scangear download to [http://support-au.canon.com.au/contents/AU/EN/0100302801.html](http://support-au.canon.com.au/contents/AU/EN/0100302801.html) since it's the fifth item on the screen and the people rushing through this might get the wrong download.

Other than that, thank you VERY MUCH for the installation guide.  I went out and bought this printer specifically because I was able to find an easy to understand guide for getting this to work on Linux.

Thank you.
I have changed the link in the original post. Good suggestion.

---

### Post by divans on 2011-02-01
thanks,got the mp495 working properly until i did the most recent update of my 10.04 ubuntu ,which from memory included cups ,now you hit print and it only registers the job on status but no print.it registers no error just 'stopped'.scanner works fine.how do i find where the bug is?   divans

---

### Post by modsbyus on 2011-02-01
> **divans said:**
> thanks,got the mp495 working properly until i did the most recent update of my 10.04 ubuntu ,which from memory included cups ,now you hit print and it only registers the job on status but no print.it registers no error just 'stopped'.scanner works fine.how do i find where the bug is?   divans

I would first try to reinstall. I'm on 10.10 and don't have any issues. If that doesn't work let me know.

---

### Post by wickstopher on 2011-02-11
Thanks for the guide!  I can't believe how simple it was to get wireless printing from my Ubuntu laptops up and running.  Kudos to Canon for providing Debian packages for their drivers.  I dual-boot my desktop, so I was able to set up WAN printing from Windows and from there it was a snap thanks to this guide.

My question is this: have any of you figured out how to turn on grayscale printing using this printer?  The full range of resolution is nice, but more often than not I just want a quick and dirty copy of something that uses as little ink as possible, and to preserve the color ink for when I actually need it (well, actually, more like for when my 6-year-old daughter needs it).  Thus far I can only print in color from Ubuntu.  Thanks!

---

### Post by modsbyus on 2011-02-11
> **wickstopher said:**
> Thanks for the guide!  I can't believe how simple it was to get wireless printing from my Ubuntu laptops up and running.  Kudos to Canon for providing Debian packages for their drivers.  I dual-boot my desktop, so I was able to set up WAN printing from Windows and from there it was a snap thanks to this guide.

My question is this: have any of you figured out how to turn on grayscale printing using this printer?  The full range of resolution is nice, but more often than not I just want a quick and dirty copy of something that uses as little ink as possible, and to preserve the color ink for when I actually need it (well, actually, more like for when my 6-year-old daughter needs it).  Thus far I can only print in color from Ubuntu.  Thanks!

I hadn't thought of that. I will look into it and let you know. Ill try to get to it tonght.

---

### Post by Lynx28 on 2011-02-19
Installation went well, but the configuration updates for higher resolution didn't work. I Checked the Printer documentation and saw that it would only support up to 4800 DPI.

Also, when using the values from the original post the GUI interface for Printer Options in Ubuntu (System->Administration->Printing) didn't work correctly. For example; if I selected 4800 it would show 9600, and then I couldn't change anything unless I selected 600 from the dropdown.

So... I played around with the resolution configuration and the following works. I can print at 4800 dpi but the GUI is still flakey. Changing the numbers at the begining of each line to match (4800dpi/4800 DPI) would allow the GUI to work.. but it wouldn't print. However, all you need to do is switch to 600 and then you can switch to another.


```

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 4800dpi
*Resolution 600dpi/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200dpi/1200 DPI: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 1200dpi/2400 DPI: "<</HWResolution[1200 2400]>>setpagedevice"
*Resolution 1200dpi/4800 DPI: "<</HWResolution[1200 4800]>>setpagedevice"
*CloseUI: *Resolution

```

This configuration should be the same in both files:

```

/usr/share/ppd/canonmp495.ppd
/etc/cups/ppd/[Name of Printer].ppd

``` 

The name of the configuration file in cups/ppd comes from the name you used for the printer when installing the drivers.

After making the changes and restarting cups you may also need to go into the GUI and select 4800 from the dropdown before it works correctly.

Hope this helps

---

### Post by bmbigam on 2011-03-12
ubuntu 10.04 will not print if you change the resolution.
But everything else works scanner and all.
Thank you very much for the info!

---

### Post by Rake16 on 2011-03-13
Just wanted to say I really appreciate this thread. Thank you so much for helping me in my first Ubuntu endeavour.

---

### Post by mark.0 on 2011-03-27
I followed the directions explicitly. Makes perfect sense, but I've run into a problem. I changed the SSID on my router to the one listed in the directions but the ip address does not show up in the angryip scan. I've verified several times that the SSID is the same listed. I have a linksys g router.

When I press maintenance on the printer until the "E-like" symbol, the wifi light does not light up. It is NOT blinking and it is NOT constant, it's just simply not on. 

 Not to mention, I print the "Network Configuration" from the printer by pressing maintenance until "n" and pressing "Black start" to print the printers network settings, it prints the following:


[Wireless LAN]     : Disable
Link Status           : Inactive
MAC Address      : xxxxxxxxxxxxxxxxxx (censored)

SSID                     : 
Connection Mode : 
Channel                :
Encryption            :
WEP Key Length  :


Authentication       :
Signl Strength       :

TCP/IP Version    :
IP Address           :
Default Gateway  :
Subnet Mask        :
Subnet Prefix Length:

IPsec                     :
Security Protocol  :
WPS PIN Code     : xxxxxxxxxxxxx (censored)


Also, if I login to my router and look at the DHCP clients table, the printer is not listed there. No surprise, but worth mentioning nonetheless.

Any help is appreciated.

---

### Post by modsbyus on 2011-03-27
> **mark.0 said:**
> I followed the directions explicitly. Makes perfect sense, but I've run into a problem. I changed the SSID on my router to the one listed in the directions but the ip address does not show up in the angryip scan. I've verified several times that the SSID is the same listed. I have a linksys g router.

When I press maintenance on the printer until the "E-like" symbol, the wifi light does not light up. It is NOT blinking and it is NOT constant, it's just simply not on. 

 Not to mention, I print the "Network Configuration" from the printer by pressing maintenance until "n" and pressing "Black start" to print the printers network settings, it prints the following:


[Wireless LAN]     : Disable
Link Status           : Inactive
MAC Address      : xxxxxxxxxxxxxxxxxx (censored)

SSID                     : 
Connection Mode : 
Channel                :
Encryption            :
WEP Key Length  :


Authentication       :
Signl Strength       :

TCP/IP Version    :
IP Address           :
Default Gateway  :
Subnet Mask        :
Subnet Prefix Length:

IPsec                     :
Security Protocol  :
WPS PIN Code     : xxxxxxxxxxxxx (censored)


Also, if I login to my router and look at the DHCP clients table, the printer is not listed there. No surprise, but worth mentioning nonetheless.

Any help is appreciated.



Press the maintenance button 13 time. You will see something that looks like the letter G. When you see that press the color start button. I will check and edit the origonal post for this step.

---

### Post by mark.0 on 2011-03-27
Hey thanks a million! Would have never figured that out, curse canon for not supplying detailed technical documenation with their product! It's kind of absurd to me that there's all kinds of maintenance options like this for the product, and they only ship you moron instructions for how to follow a windows installation wizard, but not important stuff like this!

Just curious, but where are you finding this info? I purused the documentation and was only able to find this "n" option to print out the network configuration.

---

### Post by modsbyus on 2011-03-27
> **mark.0 said:**
> Hey thanks a million! Would have never figured that out, curse canon for not supplying detailed technical documenation with their product! It's kind of absurd to me that there's all kinds of maintenance options like this for the product, and they only ship you moron instructions for how to follow a windows installation wizard, but not important stuff like this!

Just curious, but where are you finding this info? I purused the documentation and was only able to find this "n" option to print out the network configuration.

It took me a while. This will probably irritate you as much as it did me but the maintenance option to turn on the wireless is in the documentation sent with the printer. Its just a verry difficult read. I dont think that they are all in there but it sure would be nice if there were a list of maintenance options with the discription of each. Other than that i just kept changing my search criteria until i came across the printer drivers. I knew they were out there because i called canon to find out if any of their branches in the rest of the worl supported it. They said yes but the couldnt tell me where. Political crap... oh well.

---

### Post by gigabz666 on 2011-04-01
Hi there

I just want to say that thanks to these instructions, the MP495 I bought today, I was able to set up quick and fairly painlessly thanks to these instructions. So thanks modsybus. Your instructions were so incredibly easy to follow and made this so easy to do.

BTW, your link for AngryIPScanner was for the 32 bit version. Since I was on 64 bit I figured I was going to get architecture issues, so I went to this [page]("http://www.angryip.org/w/Download") and used the 64 bit executable jar using:
java -jar <jarfile> and that worked well.

Also for scangearmp, I right clicked on applications to edit the menu and made a new menu entry for scangearmp so you can access it as quickly as you would something like simplescan.

Thanks again!

---

### Post by cazazo on 2011-04-02
> **modsbyus said:**
> I hadn't thought of that. I will look into it and let you know. Ill try to get to it tonght.

I have the same question about the possibility to choose the printer grayscale mode... any news on that? Appreciated!

---

### Post by CWMV on 2011-04-06
Man, what the heck? I just want this thing to print on my home wireless network!:(

Ill preface this by saying I don't have much patience/understanding of computers, and recently installed ubuntu to replace an ailing windows Vista that has become next to unusable. It seemed a better option that opting to buy windows 7 outright as much as I like it on my other computer.

So how exactly do you install these drivers, and which ones need to be installed (Ive got something like 5)? All that happens when I click on any of these given downloads is a install.sh file comes up (whatever that means) and when I open that its meaningless (to me) gibberish and code, what exactly am I supposed to do with that? 

I try adding my network printer with the administrator-printers options, and it reads my network, but I cant select it to go forward. 
This is all very, very confusing.

EDIT: and the links for angryIPscanner don't work for me either, All I get is an incorrect structure statement when it goes to the download screen.

---

### Post by CFury on 2011-04-10
After editing my .ppd files as per the first post I can't seem to print.  Initially after downloading and installing the drivers it printed for me, however now I get an error message.  When I tried to diagnose the issue I seem to be getting a lot of messages about dirty files.  Additionally I see another error that /usr/lib/cups/filter/pstocanonij) crashed on signal 11.

Any ideas?

---

### Post by CFury on 2011-04-10
Additionally this printer is replacing another and I think there's a conflict there.  When I go to print and the print dialog box pops up I get two options- MP495-series with the location of NC6000 (which is the computer name) or MP495USB.  Attempting to print on either result in the same message.

---

### Post by CFury on 2011-04-10
For some reason I got it to work by re-selecting 4800dpi in the printer properties.  Hopefully it continues to work.

---

### Post by Murdoc419 on 2011-04-11
Noob question: When I am scanning something what does each destination choice do? Obviously "Print" will print what is in the scanner but what does "Image Display" and "OCR" do?

---

### Post by Murdoc419 on 2011-04-11
Noob question: When I am scanning something what does each destination choice do? Obviously "Print" will print what is in the scanner but what does "Image Display" and "OCR" do?

By the way thank you very much for this guide. I had installed Ubuntu before and couldn't get this printer to work with it and decided to go back to Windoze, unfortunately. Now I can use Ubuntu hassle free. Thank you!

Sorry for the double post, I tried to stop my browser as it was loading after I hit post the first time so I could add a thank you. I guess it posted anyway and I can't figure out how to delete it.

---

### Post by CFury on 2011-04-11
> **Murdoc419 said:**
> Noob question: When I am scanning something what does each destination choice do? Obviously "Print" will print what is in the scanner but what does "Image Display" and "OCR" do?

By the way thank you very much for this guide. I had installed Ubuntu before and couldn't get this printer to work with it and decided to go back to Windoze, unfortunately. Now I can use Ubuntu hassle free. Thank you!

Sorry for the double post, I tried to stop my browser as it was loading after I hit post the first time so I could add a thank you. I guess it posted anyway and I can't figure out how to delete it.

I haven't played around too much with Scan Gear, however I've noticed that when you preview a scan the destination automatically changes to "Image Display".  I still have yet to figure out "OCR".

---

### Post by Murdoc419 on 2011-04-12
Ok well I may get around to figuring it out today. I'll just do one of each and hope nothing funky happens. When I find out I'll post the results.

---

### Post by Murdoc419 on 2011-04-12
Ok I have encountered a problem. I am unable to print through Open Office. Not sure if it has been addressed. I didn't see anything and a ctrl+f search found nothing. Anyway I can print from a browser but I am also able to select 9600 DPI when I print from a browser, which I cannot seem to do in Open Office. I ran the printer diagnostic and got this error code:

```
D [12/Apr/2011:21:44:05 -0400] cupsdSetBusyState: Dirty files
D [12/Apr/2011:21:44:05 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [12/Apr/2011:21:44:05 -0400] cupsdSetBusyState: Active clients and dirty files
D [12/Apr/2011:21:44:05 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:05 -0400] cupsdReadClient: 12 1.1 Get-Jobs 1
D [12/Apr/2011:21:44:05 -0400] Get-Jobs ipp://localhost/printers/
D [12/Apr/2011:21:44:05 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [12/Apr/2011:21:44:05 -0400] cupsdSetBusyState: Dirty files
D [12/Apr/2011:21:44:05 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [12/Apr/2011:21:44:05 -0400] cupsdSetBusyState: Active clients and dirty files
D [12/Apr/2011:21:44:05 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:05 -0400] cupsdReadClient: 12 1.1 Get-Jobs 1
D [12/Apr/2011:21:44:05 -0400] Get-Jobs ipp://localhost/printers/
D [12/Apr/2011:21:44:05 -0400] [Job 1] Loading attributes...
D [12/Apr/2011:21:44:05 -0400] [Job 2] Loading attributes...
D [12/Apr/2011:21:44:05 -0400] [Job 3] Loading attributes...
D [12/Apr/2011:21:44:05 -0400] [Job 4] Loading attributes...
D [12/Apr/2011:21:44:05 -0400] [Job 5] Loading attributes...
D [12/Apr/2011:21:44:05 -0400] [Job 6] Loading attributes...
D [12/Apr/2011:21:44:05 -0400] [Job 7] Loading attributes...
D [12/Apr/2011:21:44:05 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [12/Apr/2011:21:44:05 -0400] cupsdSetBusyState: Dirty files
D [12/Apr/2011:21:44:05 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [12/Apr/2011:21:44:05 -0400] cupsdSetBusyState: Active clients and dirty files
D [12/Apr/2011:21:44:05 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:05 -0400] cupsdReadClient: 12 1.1 Create-Printer-Subscription 1
D [12/Apr/2011:21:44:05 -0400] Create-Printer-Subscription /
D [12/Apr/2011:21:44:05 -0400] cupsdCreateSubscription(con=0xb7e41668(12), uri="/")
D [12/Apr/2011:21:44:05 -0400] pullmethod="ippget"
D [12/Apr/2011:21:44:05 -0400] notify-lease-duration=86400
D [12/Apr/2011:21:44:05 -0400] notify-time-interval=0
D [12/Apr/2011:21:44:05 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [12/Apr/2011:21:44:05 -0400] Added subscription 8 for server
D [12/Apr/2011:21:44:05 -0400] cupsdMarkDirty(-----S)
D [12/Apr/2011:21:44:05 -0400] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [12/Apr/2011:21:44:05 -0400] cupsdSetBusyState: Dirty files
D [12/Apr/2011:21:44:06 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [12/Apr/2011:21:44:06 -0400] cupsdSetBusyState: Active clients and dirty files
D [12/Apr/2011:21:44:06 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:06 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [12/Apr/2011:21:44:06 -0400] Get-Notifications /
D [12/Apr/2011:21:44:06 -0400] cupsdIsAuthorized: requesting-user-name="shane"
D [12/Apr/2011:21:44:06 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [12/Apr/2011:21:44:06 -0400] cupsdSetBusyState: Dirty files
D [12/Apr/2011:21:44:25 -0400] cupsdAcceptClient: 13 from localhost (Domain)
D [12/Apr/2011:21:44:25 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [12/Apr/2011:21:44:25 -0400] cupsdSetBusyState: Active clients and dirty files
D [12/Apr/2011:21:44:25 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:25 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Printers 1
D [12/Apr/2011:21:44:25 -0400] CUPS-Get-Printers
D [12/Apr/2011:21:44:25 -0400] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [12/Apr/2011:21:44:25 -0400] cupsdSetBusyState: Dirty files
D [12/Apr/2011:21:44:25 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [12/Apr/2011:21:44:25 -0400] cupsdSetBusyState: Active clients and dirty files
D [12/Apr/2011:21:44:25 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:25 -0400] cupsdReadClient: 13 1.1 CUPS-Get-Default 1
D [12/Apr/2011:21:44:25 -0400] CUPS-Get-Default
D [12/Apr/2011:21:44:25 -0400] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [12/Apr/2011:21:44:25 -0400] cupsdSetBusyState: Dirty files
D [12/Apr/2011:21:44:26 -0400] cupsdReadClient: 13 POST /printers/MP495LAN HTTP/1.1
D [12/Apr/2011:21:44:26 -0400] cupsdSetBusyState: Active clients and dirty files
D [12/Apr/2011:21:44:26 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:26 -0400] cupsdReadClient: 13 1.1 Create-Job 1
D [12/Apr/2011:21:44:26 -0400] Create-Job ipp://localhost:631/printers/MP495LAN
D [12/Apr/2011:21:44:26 -0400] cupsdMarkDirty(----J-)
D [12/Apr/2011:21:44:26 -0400] add_job: requesting-user-name="shane"
D [12/Apr/2011:21:44:26 -0400] Adding default job-sheets values "none,none"...
I [12/Apr/2011:21:44:26 -0400] [Job 9] Adding start banner page "none".
D [12/Apr/2011:21:44:26 -0400] cupsdMarkDirty(-----S)
I [12/Apr/2011:21:44:26 -0400] [Job 9] Queued on "MP495LAN" by "shane".
D [12/Apr/2011:21:44:26 -0400] Returning IPP successful-ok for Create-Job (ipp://localhost:631/printers/MP495LAN) from localhost
D [12/Apr/2011:21:44:26 -0400] cupsdSetBusyState: Dirty files
D [12/Apr/2011:21:44:26 -0400] cupsdReadClient: 13 POST /printers/MP495LAN HTTP/1.1
D [12/Apr/2011:21:44:26 -0400] cupsdSetBusyState: Active clients and dirty files
D [12/Apr/2011:21:44:26 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:26 -0400] cupsdReadClient: 13 1.1 Send-Document 1
D [12/Apr/2011:21:44:26 -0400] Send-Document ipp://localhost:631/printers/MP495LAN
D [12/Apr/2011:21:44:26 -0400] cupsdIsAuthorized: requesting-user-name="shane"
D [12/Apr/2011:21:44:26 -0400] [Job 9] Auto-typing file...
D [12/Apr/2011:21:44:26 -0400] [Job 9] Request file type is application/postscript.
D [12/Apr/2011:21:44:26 -0400] cupsdMarkDirty(----J-)
I [12/Apr/2011:21:44:26 -0400] [Job 9] File of type application/postscript queued by "shane".
I [12/Apr/2011:21:44:26 -0400] [Job 9] Adding end banner page "none".
D [12/Apr/2011:21:44:26 -0400] cupsdMarkDirty(----J-)
D [12/Apr/2011:21:44:26 -0400] cupsdMarkDirty(----J-)
D [12/Apr/2011:21:44:26 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [12/Apr/2011:21:44:26 -0400] cupsdMarkDirty(-----S)
D [12/Apr/2011:21:44:26 -0400] [Job 9] job-sheets=none,none
D [12/Apr/2011:21:44:26 -0400] [Job 9] argv[0]="MP495LAN"
D [12/Apr/2011:21:44:26 -0400] [Job 9] argv[1]="9"
D [12/Apr/2011:21:44:26 -0400] [Job 9] argv[2]="shane"
D [12/Apr/2011:21:44:26 -0400] [Job 9] argv[3]="Debate - Singer's Solution to World Poverty"
D [12/Apr/2011:21:44:26 -0400] [Job 9] argv[4]="1"
D [12/Apr/2011:21:44:26 -0400] [Job 9] argv[5]="InputSlot=asf PageSize=Letter job-uuid=urn:uuid:db21c4a7-d05a-38b2-646f-3d0101fe09a0 job-originating-host-name=localhost"
D [12/Apr/2011:21:44:26 -0400] [Job 9] argv[6]="/var/spool/cups/d00009-001"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[8]="HOME=/var/spool/cups/tmp"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[10]="SERVER_ADMIN=root@shane-vaio"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[11]="SOFTWARE=CUPS/1.4.4"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[13]="USER=root"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[16]="IPP_PORT=631"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[17]="CHARSET=utf-8"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[18]="LANG=en_US.UTF-8"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[19]="PPD=/etc/cups/ppd/MP495LAN.ppd"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[20]="RIP_MAX_CACHE=auto"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[21]="CONTENT_TYPE=application/postscript"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[22]="DEVICE_URI=cnijnet:/00-1E-8F-9F-DB-5B"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[23]="PRINTER_INFO=MP495LAN"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[24]="PRINTER_LOCATION="
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[25]="PRINTER=MP495LAN"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[26]="CUPS_FILETYPE=document"
D [12/Apr/2011:21:44:26 -0400] [Job 9] envp[27]="FINAL_CONTENT_TYPE=printer/MP495LAN"
I [12/Apr/2011:21:44:26 -0400] [Job 9] Started filter /usr/lib/cups/filter/pstops (PID 6804)
I [12/Apr/2011:21:44:26 -0400] [Job 9] Started filter /usr/lib/cups/filter/pstocanonij (PID 6805)
I [12/Apr/2011:21:44:26 -0400] [Job 9] Started backend /usr/lib/cups/backend/cnijnet (PID 6806)
D [12/Apr/2011:21:44:26 -0400] cupsdMarkDirty(-----S)
D [12/Apr/2011:21:44:26 -0400] Returning IPP successful-ok for Send-Document (ipp://localhost:631/printers/MP495LAN) from localhost
D [12/Apr/2011:21:44:26 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [12/Apr/2011:21:44:26 -0400] [Job 9] Page = 612x792; 18,14 to 594,784
D [12/Apr/2011:21:44:26 -0400] [Job 9] slow_collate=0, slow_duplex=0, slow_order=0
D [12/Apr/2011:21:44:26 -0400] [Job 9] Before copy_comments - %!PS-Adobe-3.0
D [12/Apr/2011:21:44:26 -0400] [Job 9] %!PS-Adobe-3.0
D [12/Apr/2011:21:44:26 -0400] [Job 9] %%BoundingBox: (atend)
D [12/Apr/2011:21:44:26 -0400] [Job 9] %%Creator: (OpenOffice.org 3.2)
D [12/Apr/2011:21:44:26 -0400] [Job 9] %%For: (shane)
D [12/Apr/2011:21:44:26 -0400] [Job 9] %%CreationDate: (Tue Apr 12 21:44:26 2011)
D [12/Apr/2011:21:44:26 -0400] [Job 9] %%Title: (Debate - Singer's Solution to World Poverty)
D [12/Apr/2011:21:44:26 -0400] [Job 9] %%LanguageLevel: 3
D [12/Apr/2011:21:44:26 -0400] [Job 9] %%DocumentData: Clean7Bit
D [12/Apr/2011:21:44:26 -0400] [Job 9] %%Pages: (atend)
D [12/Apr/2011:21:44:26 -0400] [Job 9] %%Orientation: (atend)
D [12/Apr/2011:21:44:26 -0400] [Job 9] %%PageOrder: Ascend
D [12/Apr/2011:21:44:26 -0400] [Job 9] %%EndComments
D [12/Apr/2011:21:44:26 -0400] [Job 9] Before copy_prolog - %%BeginProlog
D [12/Apr/2011:21:44:26 -0400] [Job 9] Before copy_setup - %%BeginSetup
D [12/Apr/2011:21:44:26 -0400] [Job 9] pstocanonij start.
D [12/Apr/2011:21:44:26 -0400] [Job 9] Before page loop - %%Page: 1 1
D [12/Apr/2011:21:44:26 -0400] [Job 9] Copying page 1...
D [12/Apr/2011:21:44:26 -0400] [Job 9] pagew = 576.0, pagel = 769.3
D [12/Apr/2011:21:44:26 -0400] [Job 9] bboxx = 0, bboxy = 0, bboxw = 612, bboxl = 792
D [12/Apr/2011:21:44:26 -0400] [Job 9] PageLeft = 18.1, PageRight = 594.1
D [12/Apr/2011:21:44:26 -0400] [Job 9] PageTop = 783.5, PageBottom = 14.2
D [12/Apr/2011:21:44:26 -0400] [Job 9] PageWidth = 612.0, PageLength = 792.0
D [12/Apr/2011:21:44:26 -0400] [Job 9] Copying page 2...
D [12/Apr/2011:21:44:26 -0400] [Job 9] pagew = 576.0, pagel = 769.3
D [12/Apr/2011:21:44:26 -0400] [Job 9] bboxx = 0, bboxy = 0, bboxw = 612, bboxl = 792
D [12/Apr/2011:21:44:26 -0400] [Job 9] PageLeft = 18.1, PageRight = 594.1
D [12/Apr/2011:21:44:26 -0400] [Job 9] PageTop = 783.5, PageBottom = 14.2
D [12/Apr/2011:21:44:26 -0400] [Job 9] PageWidth = 612.0, PageLength = 792.0
D [12/Apr/2011:21:44:26 -0400] [Job 9] Wrote 2 pages...
D [12/Apr/2011:21:44:26 -0400] PID 6804 (/usr/lib/cups/filter/pstops) exited with no errors.
I [12/Apr/2011:21:44:26 -0400] [Job 9]
D [12/Apr/2011:21:44:26 -0400] cupsdMarkDirty(-----S)
I [12/Apr/2011:21:44:26 -0400] [Job 9]
D [12/Apr/2011:21:44:26 -0400] cupsdMarkDirty(-----S)
D [12/Apr/2011:21:44:26 -0400] [Job 9] device_uri=(cnijnet:/00-1E-8F-9F-DB-5B)
D [12/Apr/2011:21:44:26 -0400] [Job 9] p_ppd->model_number=(369)
D [12/Apr/2011:21:44:26 -0400] [Job 9] #  p_size->name=Letter , p_size_default->name = Letter #
D [12/Apr/2011:21:44:26 -0400] [Job 9] ### num_opt(lpr optins) = 4 ###
D [12/Apr/2011:21:44:26 -0400] [Job 9]
D [12/Apr/2011:21:44:26 -0400] [Job 9] # ppdPageSize width=612.000000 height=792.000000 ###
D [12/Apr/2011:21:44:26 -0400] [Job 9]
E [12/Apr/2011:21:44:26 -0400] PID 6805 (/usr/lib/cups/filter/pstocanonij) crashed on signal 11!
I [12/Apr/2011:21:44:26 -0400] [Job 9]
D [12/Apr/2011:21:44:26 -0400] cupsdMarkDirty(-----S)
D [12/Apr/2011:21:44:26 -0400] [Job 9] [cnijnetprn] CheckStartPrint(0)
D [12/Apr/2011:21:44:26 -0400] [Job 9] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:26 -0400] [Job 9] [cnijnetprn] getPrinterStatus
D [12/Apr/2011:21:44:26 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [12/Apr/2011:21:44:26 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [12/Apr/2011:21:44:26 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [12/Apr/2011:21:44:26 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:26 -0400] cupsdReadClient: 16 1.1 Get-Jobs 1
D [12/Apr/2011:21:44:26 -0400] Get-Jobs ipp://localhost/printers/
D [12/Apr/2011:21:44:26 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [12/Apr/2011:21:44:26 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [12/Apr/2011:21:44:26 -0400] cupsdReadClient: 16 WAITING Closing on EOF
D [12/Apr/2011:21:44:26 -0400] cupsdCloseClient: 16
D [12/Apr/2011:21:44:26 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [12/Apr/2011:21:44:26 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [12/Apr/2011:21:44:26 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [12/Apr/2011:21:44:26 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:26 -0400] cupsdReadClient: 16 1.1 Get-Notifications 1
D [12/Apr/2011:21:44:26 -0400] Get-Notifications /
D [12/Apr/2011:21:44:26 -0400] cupsdIsAuthorized: requesting-user-name="shane"
D [12/Apr/2011:21:44:26 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [12/Apr/2011:21:44:26 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [12/Apr/2011:21:44:26 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [12/Apr/2011:21:44:26 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [12/Apr/2011:21:44:26 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:26 -0400] cupsdReadClient: 16 1.1 Get-Job-Attributes 1
D [12/Apr/2011:21:44:26 -0400] Get-Job-Attributes ipp://localhost/jobs/9
D [12/Apr/2011:21:44:26 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/9) from localhost
D [12/Apr/2011:21:44:26 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [12/Apr/2011:21:44:26 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [12/Apr/2011:21:44:26 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [12/Apr/2011:21:44:26 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:26 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [12/Apr/2011:21:44:26 -0400] Get-Notifications /
D [12/Apr/2011:21:44:26 -0400] cupsdIsAuthorized: requesting-user-name="shane"
D [12/Apr/2011:21:44:26 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [12/Apr/2011:21:44:26 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [12/Apr/2011:21:44:27 -0400] cupsdAcceptClient: 17 from localhost (Domain)
D [12/Apr/2011:21:44:27 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [12/Apr/2011:21:44:27 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [12/Apr/2011:21:44:27 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:27 -0400] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [12/Apr/2011:21:44:27 -0400] Get-Printer-Attributes ipp://shane-vaio:0/printers/MP495LAN
D [12/Apr/2011:21:44:27 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://shane-vaio:0/printers/MP495LAN) from localhost
D [12/Apr/2011:21:44:27 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [12/Apr/2011:21:44:27 -0400] cupsdReadClient: 17 POST / HTTP/1.1
D [12/Apr/2011:21:44:27 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [12/Apr/2011:21:44:27 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:27 -0400] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [12/Apr/2011:21:44:27 -0400] Get-Job-Attributes ipp://localhost/jobs/9
D [12/Apr/2011:21:44:27 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/9) from localhost
D [12/Apr/2011:21:44:27 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [12/Apr/2011:21:44:27 -0400] cupsdReadClient: 16 WAITING Closing on EOF
D [12/Apr/2011:21:44:27 -0400] cupsdCloseClient: 16
D [12/Apr/2011:21:44:27 -0400] [Job 9] [cnijnetprn] dispatchCommandIVEC Receive(1)
D [12/Apr/2011:21:44:27 -0400] [Job 9] [cnijnetprn] dispatchCommandIVEC Receive(2)
I [12/Apr/2011:21:44:27 -0400] [Job 9] waiting print data ...
D [12/Apr/2011:21:44:27 -0400] cupsdMarkDirty(-----S)
I [12/Apr/2011:21:44:27 -0400] [Job 9]
D [12/Apr/2011:21:44:27 -0400] cupsdMarkDirty(-----S)
D [12/Apr/2011:21:44:27 -0400] [Job 9] [cnijnetprn] dispatchCommandIVEC Receive(3)
D [12/Apr/2011:21:44:27 -0400] [Job 9] [cnijnetprn] CheckExecutePrint
D [12/Apr/2011:21:44:27 -0400] [Job 9] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:27 -0400] [Job 9] [cnijnetprn] getPrinterStatus
D [12/Apr/2011:21:44:28 -0400] [Job 9] [cnijnetprn] CheckExecutePrint
D [12/Apr/2011:21:44:28 -0400] [Job 9] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:28 -0400] [Job 9] [cnijnetprn] getPrinterStatus
D [12/Apr/2011:21:44:29 -0400] [Job 8] Unloading...
D [12/Apr/2011:21:44:29 -0400] [Job 9] [cnijnetprn] CheckExecutePrint
D [12/Apr/2011:21:44:29 -0400] [Job 9] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:29 -0400] [Job 9] [cnijnetprn] getPrinterStatus
D [12/Apr/2011:21:44:30 -0400] [Job 9] [cnijnetprn] CheckExecutePrint
D [12/Apr/2011:21:44:30 -0400] [Job 9] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:30 -0400] [Job 9] [cnijnetprn] getPrinterStatus
D [12/Apr/2011:21:44:31 -0400] [Job 9] [cnijnetprn] CheckExecutePrint
D [12/Apr/2011:21:44:31 -0400] [Job 9] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:31 -0400] [Job 9] [cnijnetprn] getPrinterStatus
I [12/Apr/2011:21:44:32 -0400] Generating printcap /var/run/cups/printcap...
I [12/Apr/2011:21:44:32 -0400] Saving job cache file "/var/cache/cups/job.cache"...
I [12/Apr/2011:21:44:32 -0400] Saving subscriptions.conf...
D [12/Apr/2011:21:44:32 -0400] cupsdSetBusyState: Printing jobs
D [12/Apr/2011:21:44:32 -0400] [Job 9] [cnijnetprn] CheckExecutePrint
D [12/Apr/2011:21:44:32 -0400] [Job 9] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:32 -0400] [Job 9] [cnijnetprn] getPrinterStatus
D [12/Apr/2011:21:44:33 -0400] [Job 9] [cnijnetprn] CheckExecutePrint
D [12/Apr/2011:21:44:33 -0400] [Job 9] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:33 -0400] [Job 9] [cnijnetprn] getPrinterStatus
D [12/Apr/2011:21:44:34 -0400] [Job 9] [cnijnetprn] CheckExecutePrint
D [12/Apr/2011:21:44:34 -0400] [Job 9] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:34 -0400] [Job 9] [cnijnetprn] getPrinterStatus
D [12/Apr/2011:21:44:35 -0400] [Job 9] [cnijnetprn] CheckExecutePrint
D [12/Apr/2011:21:44:35 -0400] [Job 9] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:35 -0400] [Job 9] [cnijnetprn] getPrinterStatus
D [12/Apr/2011:21:44:36 -0400] [Job 9] [cnijnetprn] CheckExecutePrint
D [12/Apr/2011:21:44:36 -0400] [Job 9] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:36 -0400] [Job 9] [cnijnetprn] getPrinterStatus
D [12/Apr/2011:21:44:37 -0400] [Job 9] [cnijnetprn] CheckEndPrint(0)
D [12/Apr/2011:21:44:37 -0400] [Job 9] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:37 -0400] [Job 9] [cnijnetprn] getPrinterStatus
I [12/Apr/2011:21:44:37 -0400] [Job 9]
D [12/Apr/2011:21:44:37 -0400] cupsdMarkDirty(-----S)
D [12/Apr/2011:21:44:37 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [12/Apr/2011:21:44:38 -0400] PID 6806 (/usr/lib/cups/backend/cnijnet) exited with no errors.
D [12/Apr/2011:21:44:38 -0400] cupsdMarkDirty(-----S)
E [12/Apr/2011:21:44:38 -0400] [Job 9] Job stopped due to filter errors; please consult the error_log file for details.
D [12/Apr/2011:21:44:38 -0400] cupsdMarkDirty(----J-)
D [12/Apr/2011:21:44:38 -0400] cupsdMarkDirty(-----S)
D [12/Apr/2011:21:44:38 -0400] cupsdAcceptClient: 15 from localhost (Domain)
D [12/Apr/2011:21:44:38 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [12/Apr/2011:21:44:38 -0400] cupsdSetBusyState: Active clients and dirty files
D [12/Apr/2011:21:44:38 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:38 -0400] cupsdReadClient: 15 1.1 Get-Jobs 1
D [12/Apr/2011:21:44:38 -0400] Get-Jobs ipp://localhost/printers/
D [12/Apr/2011:21:44:38 -0400] [Job 8] Loading attributes...
D [12/Apr/2011:21:44:38 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [12/Apr/2011:21:44:38 -0400] cupsdSetBusyState: Dirty files
D [12/Apr/2011:21:44:38 -0400] cupsdReadClient: 15 WAITING Closing on EOF
D [12/Apr/2011:21:44:38 -0400] cupsdCloseClient: 15
D [12/Apr/2011:21:44:38 -0400] cupsdAcceptClient: 15 from localhost (Domain)
D [12/Apr/2011:21:44:38 -0400] cupsdReadClient: 15 POST / HTTP/1.1
D [12/Apr/2011:21:44:38 -0400] cupsdSetBusyState: Active clients and dirty files
D [12/Apr/2011:21:44:38 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:38 -0400] cupsdReadClient: 15 1.1 Get-Notifications 1
D [12/Apr/2011:21:44:38 -0400] Get-Notifications /
D [12/Apr/2011:21:44:38 -0400] cupsdIsAuthorized: requesting-user-name="shane"
D [12/Apr/2011:21:44:38 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [12/Apr/2011:21:44:38 -0400] cupsdSetBusyState: Dirty files
D [12/Apr/2011:21:44:38 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [12/Apr/2011:21:44:38 -0400] cupsdSetBusyState: Active clients and dirty files
D [12/Apr/2011:21:44:38 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:38 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [12/Apr/2011:21:44:38 -0400] Get-Notifications /
D [12/Apr/2011:21:44:38 -0400] cupsdIsAuthorized: requesting-user-name="shane"
D [12/Apr/2011:21:44:38 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [12/Apr/2011:21:44:38 -0400] cupsdSetBusyState: Dirty files
D [12/Apr/2011:21:44:39 -0400] cupsdAcceptClient: 16 from localhost (Domain)
D [12/Apr/2011:21:44:39 -0400] [Job 9] Unloading...
D [12/Apr/2011:21:44:39 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [12/Apr/2011:21:44:39 -0400] cupsdSetBusyState: Active clients and dirty files
D [12/Apr/2011:21:44:39 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:39 -0400] cupsdReadClient: 16 1.1 Get-Printer-Attributes 1
D [12/Apr/2011:21:44:39 -0400] Get-Printer-Attributes ipp://shane-vaio:0/printers/MP495LAN
D [12/Apr/2011:21:44:39 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://shane-vaio:0/printers/MP495LAN) from localhost
D [12/Apr/2011:21:44:39 -0400] cupsdSetBusyState: Dirty files
D [12/Apr/2011:21:44:39 -0400] cupsdReadClient: 16 POST / HTTP/1.1
D [12/Apr/2011:21:44:39 -0400] cupsdSetBusyState: Active clients and dirty files
D [12/Apr/2011:21:44:39 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:39 -0400] cupsdReadClient: 16 1.1 Get-Job-Attributes 1
D [12/Apr/2011:21:44:39 -0400] Get-Job-Attributes ipp://localhost/jobs/9
D [12/Apr/2011:21:44:39 -0400] [Job 9] Loading attributes...
D [12/Apr/2011:21:44:39 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/9) from localhost
D [12/Apr/2011:21:44:39 -0400] cupsdSetBusyState: Dirty files
D [12/Apr/2011:21:44:39 -0400] cupsdReadClient: 15 WAITING Closing on EOF
D [12/Apr/2011:21:44:39 -0400] cupsdCloseClient: 15
D [12/Apr/2011:21:44:49 -0400] cupsdAcceptClient: 15 from localhost (Domain)
D [12/Apr/2011:21:44:49 -0400] cupsdReadClient: 15 POST /printers/MP495LAN HTTP/1.1
D [12/Apr/2011:21:44:49 -0400] cupsdSetBusyState: Active clients and dirty files
D [12/Apr/2011:21:44:49 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:49 -0400] cupsdReadClient: 15 1.1 Print-Job 1
D [12/Apr/2011:21:44:49 -0400] Print-Job ipp://localhost/printers/MP495LAN
D [12/Apr/2011:21:44:49 -0400] [Job ???] Auto-typing file...
I [12/Apr/2011:21:44:49 -0400] [Job ???] Request file type is application/vnd.cups-banner.
D [12/Apr/2011:21:44:49 -0400] cupsdMarkDirty(----J-)
D [12/Apr/2011:21:44:49 -0400] add_job: requesting-user-name="shane"
D [12/Apr/2011:21:44:49 -0400] Adding default job-sheets values "none,none"...
I [12/Apr/2011:21:44:49 -0400] [Job 10] Adding start banner page "none".
D [12/Apr/2011:21:44:49 -0400] cupsdMarkDirty(-----S)
D [12/Apr/2011:21:44:49 -0400] cupsdMarkDirty(----J-)
I [12/Apr/2011:21:44:49 -0400] [Job 10] Adding end banner page "none".
I [12/Apr/2011:21:44:49 -0400] [Job 10] File of type application/vnd.cups-banner queued by "shane".
D [12/Apr/2011:21:44:49 -0400] [Job 10] hold_until=0
I [12/Apr/2011:21:44:49 -0400] [Job 10] Queued on "MP495LAN" by "shane".
D [12/Apr/2011:21:44:49 -0400] cupsdMarkDirty(----J-)
D [12/Apr/2011:21:44:49 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [12/Apr/2011:21:44:49 -0400] cupsdMarkDirty(-----S)
D [12/Apr/2011:21:44:49 -0400] [Job 10] job-sheets=none,none
D [12/Apr/2011:21:44:49 -0400] [Job 10] argv[0]="MP495LAN"
D [12/Apr/2011:21:44:49 -0400] [Job 10] argv[1]="10"
D [12/Apr/2011:21:44:49 -0400] [Job 10] argv[2]="shane"
D [12/Apr/2011:21:44:49 -0400] [Job 10] argv[3]="Test Page"
D [12/Apr/2011:21:44:49 -0400] [Job 10] argv[4]="1"
D [12/Apr/2011:21:44:49 -0400] [Job 10] argv[5]="job-uuid=urn:uuid:80a46575-6263-397b-50bb-7645e9e688a1 job-originating-host-name=localhost"
D [12/Apr/2011:21:44:49 -0400] [Job 10] argv[6]="/var/spool/cups/d00010-001"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[8]="HOME=/var/spool/cups/tmp"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[10]="SERVER_ADMIN=root@shane-vaio"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[11]="SOFTWARE=CUPS/1.4.4"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[13]="USER=root"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[16]="IPP_PORT=631"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[17]="CHARSET=utf-8"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[18]="LANG=en_US.UTF-8"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[19]="PPD=/etc/cups/ppd/MP495LAN.ppd"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[20]="RIP_MAX_CACHE=auto"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[21]="CONTENT_TYPE=application/vnd.cups-banner"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[22]="DEVICE_URI=cnijnet:/00-1E-8F-9F-DB-5B"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[23]="PRINTER_INFO=MP495LAN"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[24]="PRINTER_LOCATION="
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[25]="PRINTER=MP495LAN"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[26]="CUPS_FILETYPE=document"
D [12/Apr/2011:21:44:49 -0400] [Job 10] envp[27]="FINAL_CONTENT_TYPE=printer/MP495LAN"
I [12/Apr/2011:21:44:49 -0400] [Job 10] Started filter /usr/lib/cups/filter/bannertops (PID 6813)
I [12/Apr/2011:21:44:49 -0400] [Job 10] Started filter /usr/lib/cups/filter/pstops (PID 6814)
I [12/Apr/2011:21:44:49 -0400] [Job 10] Started filter /usr/lib/cups/filter/pstocanonij (PID 6815)
I [12/Apr/2011:21:44:49 -0400] [Job 10] Started backend /usr/lib/cups/backend/cnijnet (PID 6816)
D [12/Apr/2011:21:44:49 -0400] cupsdMarkDirty(-----S)
D [12/Apr/2011:21:44:49 -0400] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/MP495LAN) from localhost
D [12/Apr/2011:21:44:49 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [12/Apr/2011:21:44:49 -0400] [Job 10] pstocanonij start.
I [12/Apr/2011:21:44:49 -0400] [Job 10]
D [12/Apr/2011:21:44:49 -0400] cupsdMarkDirty(-----S)
I [12/Apr/2011:21:44:49 -0400] [Job 10]
D [12/Apr/2011:21:44:49 -0400] cupsdMarkDirty(-----S)
D [12/Apr/2011:21:44:49 -0400] [Job 10] load_banner(filename="/var/spool/cups/d00010-001")
D [12/Apr/2011:21:44:49 -0400] [Job 10] Page = 612x792; 18,14 to 594,784
D [12/Apr/2011:21:44:49 -0400] [Job 10] Page = 612x792; 18,14 to 594,784
D [12/Apr/2011:21:44:49 -0400] [Job 10] slow_collate=0, slow_duplex=0, slow_order=0
D [12/Apr/2011:21:44:49 -0400] [Job 10] Before copy_comments - %!PS-Adobe-3.0
D [12/Apr/2011:21:44:49 -0400] [Job 10] %!PS-Adobe-3.0
D [12/Apr/2011:21:44:49 -0400] [Job 10] %%BoundingBox: 18 14 594 784
D [12/Apr/2011:21:44:49 -0400] [Job 10] %cupsRotation: 0
D [12/Apr/2011:21:44:49 -0400] [Job 10] %%Creator: bannertops/CUPS v1.4.4
D [12/Apr/2011:21:44:49 -0400] [Job 10] %%CreationDate: Tue 12 Apr 2011 09:44:49 PM EDT
D [12/Apr/2011:21:44:49 -0400] [Job 10] %%LanguageLevel: 2
D [12/Apr/2011:21:44:49 -0400] [Job 10] %%DocumentData: Clean7Bit
D [12/Apr/2011:21:44:49 -0400] [Job 10] %%Title: (Test Page)
D [12/Apr/2011:21:44:49 -0400] [Job 10] %%For: (shane)
D [12/Apr/2011:21:44:49 -0400] [Job 10] %%Pages: 1
D [12/Apr/2011:21:44:49 -0400] [Job 10] %%DocumentSuppliedResources: font Monospace
D [12/Apr/2011:21:44:49 -0400] [Job 10] %%+ font Monospace-Bold
D [12/Apr/2011:21:44:49 -0400] [Job 10] %%+ font Monospace-BoldOblique
D [12/Apr/2011:21:44:49 -0400] [Job 10] %%+ font Monospace-Oblique
D [12/Apr/2011:21:44:49 -0400] [Job 10] %%EndComments
D [12/Apr/2011:21:44:49 -0400] [Job 10] Before copy_prolog - %%BeginProlog
I [12/Apr/2011:21:44:49 -0400] [Job 10]
D [12/Apr/2011:21:44:49 -0400] cupsdMarkDirty(-----S)
D [12/Apr/2011:21:44:49 -0400] [Job 10] [cnijnetprn] CheckStartPrint(0)
D [12/Apr/2011:21:44:49 -0400] [Job 10] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:49 -0400] [Job 10] [cnijnetprn] getPrinterStatus
D [12/Apr/2011:21:44:49 -0400] [Job 10] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
D [12/Apr/2011:21:44:49 -0400] [Job 10] PNG image: 192x128x8, color_type=2 (RGB)
D [12/Apr/2011:21:44:49 -0400] [Job 10] Before copy_setup - %%Page: coverpage 1
D [12/Apr/2011:21:44:49 -0400] [Job 10] Before page loop - %%Page: coverpage 1
D [12/Apr/2011:21:44:49 -0400] [Job 10] Copying page 1...
D [12/Apr/2011:21:44:49 -0400] [Job 10] pagew = 576.0, pagel = 769.3
D [12/Apr/2011:21:44:49 -0400] [Job 10] bboxx = 0, bboxy = 0, bboxw = 612, bboxl = 792
D [12/Apr/2011:21:44:49 -0400] [Job 10] PageLeft = 18.1, PageRight = 594.1
D [12/Apr/2011:21:44:49 -0400] [Job 10] PageTop = 783.5, PageBottom = 14.2
D [12/Apr/2011:21:44:49 -0400] [Job 10] PageWidth = 612.0, PageLength = 792.0
D [12/Apr/2011:21:44:49 -0400] PID 6813 (/usr/lib/cups/filter/bannertops) exited with no errors.
D [12/Apr/2011:21:44:49 -0400] [Job 10] Wrote 1 pages...
D [12/Apr/2011:21:44:49 -0400] PID 6814 (/usr/lib/cups/filter/pstops) exited with no errors.
D [12/Apr/2011:21:44:49 -0400] [Job 10] device_uri=(cnijnet:/00-1E-8F-9F-DB-5B)
D [12/Apr/2011:21:44:49 -0400] [Job 10] p_ppd->model_number=(369)
D [12/Apr/2011:21:44:49 -0400] [Job 10] #  p_size->name=Letter , p_size_default->name = Letter #
D [12/Apr/2011:21:44:49 -0400] [Job 10] ### num_opt(lpr optins) = 2 ###
D [12/Apr/2011:21:44:49 -0400] [Job 10]
D [12/Apr/2011:21:44:49 -0400] [Job 10] # ppdPageSize width=612.000000 height=792.000000 ###
D [12/Apr/2011:21:44:49 -0400] [Job 10]
E [12/Apr/2011:21:44:49 -0400] PID 6815 (/usr/lib/cups/filter/pstocanonij) crashed on signal 11!
D [12/Apr/2011:21:44:49 -0400] cupsdAcceptClient: 19 from localhost (Domain)
D [12/Apr/2011:21:44:49 -0400] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Apr/2011:21:44:49 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [12/Apr/2011:21:44:49 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:49 -0400] cupsdReadClient: 19 1.1 Get-Jobs 1
D [12/Apr/2011:21:44:49 -0400] Get-Jobs ipp://localhost/printers/
D [12/Apr/2011:21:44:49 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [12/Apr/2011:21:44:49 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [12/Apr/2011:21:44:49 -0400] cupsdReadClient: 19 WAITING Closing on EOF
D [12/Apr/2011:21:44:49 -0400] cupsdCloseClient: 19
D [12/Apr/2011:21:44:49 -0400] cupsdAcceptClient: 19 from localhost (Domain)
D [12/Apr/2011:21:44:49 -0400] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Apr/2011:21:44:49 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [12/Apr/2011:21:44:49 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:49 -0400] cupsdReadClient: 19 1.1 Get-Notifications 1
D [12/Apr/2011:21:44:49 -0400] Get-Notifications /
D [12/Apr/2011:21:44:49 -0400] cupsdIsAuthorized: requesting-user-name="shane"
D [12/Apr/2011:21:44:49 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [12/Apr/2011:21:44:49 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [12/Apr/2011:21:44:49 -0400] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Apr/2011:21:44:49 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [12/Apr/2011:21:44:49 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:49 -0400] cupsdReadClient: 19 1.1 Get-Job-Attributes 1
D [12/Apr/2011:21:44:49 -0400] Get-Job-Attributes ipp://localhost/jobs/10
D [12/Apr/2011:21:44:49 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/10) from localhost
D [12/Apr/2011:21:44:49 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [12/Apr/2011:21:44:49 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [12/Apr/2011:21:44:49 -0400] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [12/Apr/2011:21:44:49 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:44:49 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [12/Apr/2011:21:44:49 -0400] Get-Notifications /
D [12/Apr/2011:21:44:49 -0400] cupsdIsAuthorized: requesting-user-name="shane"
D [12/Apr/2011:21:44:49 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [12/Apr/2011:21:44:49 -0400] cupsdSetBusyState: Printing jobs and dirty files
D [12/Apr/2011:21:44:49 -0400] cupsdReadClient: 19 WAITING Closing on EOF
D [12/Apr/2011:21:44:49 -0400] cupsdCloseClient: 19
D [12/Apr/2011:21:44:50 -0400] [Job 10] [cnijnetprn] dispatchCommandIVEC Receive(1)
D [12/Apr/2011:21:44:50 -0400] [Job 10] [cnijnetprn] dispatchCommandIVEC Receive(2)
I [12/Apr/2011:21:44:50 -0400] [Job 10] waiting print data ...
D [12/Apr/2011:21:44:50 -0400] cupsdMarkDirty(-----S)
I [12/Apr/2011:21:44:50 -0400] [Job 10]
D [12/Apr/2011:21:44:50 -0400] cupsdMarkDirty(-----S)
D [12/Apr/2011:21:44:50 -0400] [Job 10] [cnijnetprn] dispatchCommandIVEC Receive(3)
D [12/Apr/2011:21:44:50 -0400] [Job 10] [cnijnetprn] CheckExecutePrint
D [12/Apr/2011:21:44:50 -0400] [Job 10] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:50 -0400] [Job 10] [cnijnetprn] getPrinterStatus
D [12/Apr/2011:21:44:51 -0400] [Job 10] [cnijnetprn] CheckExecutePrint
D [12/Apr/2011:21:44:51 -0400] [Job 10] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:51 -0400] [Job 10] [cnijnetprn] getPrinterStatus
D [12/Apr/2011:21:44:52 -0400] [Job 10] [cnijnetprn] CheckExecutePrint
D [12/Apr/2011:21:44:52 -0400] [Job 10] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:52 -0400] [Job 10] [cnijnetprn] getPrinterStatus
D [12/Apr/2011:21:44:53 -0400] [Job 10] [cnijnetprn] CheckExecutePrint
D [12/Apr/2011:21:44:53 -0400] [Job 10] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:53 -0400] [Job 10] [cnijnetprn] getPrinterStatus
D [12/Apr/2011:21:44:54 -0400] [Job 10] [cnijnetprn] CheckExecutePrint
D [12/Apr/2011:21:44:54 -0400] [Job 10] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:54 -0400] [Job 10] [cnijnetprn] getPrinterStatus
D [12/Apr/2011:21:44:55 -0400] [Job 10] [cnijnetprn] CheckExecutePrint
D [12/Apr/2011:21:44:55 -0400] [Job 10] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:55 -0400] [Job 10] [cnijnetprn] getPrinterStatus
D [12/Apr/2011:21:44:56 -0400] [Job 10] [cnijnetprn] CheckExecutePrint
D [12/Apr/2011:21:44:56 -0400] [Job 10] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:56 -0400] [Job 10] [cnijnetprn] getPrinterStatus
D [12/Apr/2011:21:44:57 -0400] [Job 10] [cnijnetprn] CheckExecutePrint
D [12/Apr/2011:21:44:57 -0400] [Job 10] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:57 -0400] [Job 10] [cnijnetprn] getPrinterStatus
D [12/Apr/2011:21:44:58 -0400] [Job 10] [cnijnetprn] CheckExecutePrint
D [12/Apr/2011:21:44:58 -0400] [Job 10] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:58 -0400] [Job 10] [cnijnetprn] getPrinterStatus
D [12/Apr/2011:21:44:59 -0400] [Job 10] [cnijnetprn] CheckExecutePrint
D [12/Apr/2011:21:44:59 -0400] [Job 10] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:44:59 -0400] [Job 10] [cnijnetprn] getPrinterStatus
D [12/Apr/2011:21:45:00 -0400] [Job 10] [cnijnetprn] CheckEndPrint(0)
D [12/Apr/2011:21:45:00 -0400] [Job 10] [cnijnetprn] IsPrinterWorking
D [12/Apr/2011:21:45:00 -0400] [Job 10] [cnijnetprn] getPrinterStatus
I [12/Apr/2011:21:45:00 -0400] [Job 10]
D [12/Apr/2011:21:45:00 -0400] cupsdMarkDirty(-----S)
D [12/Apr/2011:21:45:01 -0400] PID 6816 (/usr/lib/cups/backend/cnijnet) exited with no errors.
D [12/Apr/2011:21:45:01 -0400] cupsdMarkDirty(-----S)
E [12/Apr/2011:21:45:01 -0400] [Job 10] Job stopped due to filter errors; please consult the error_log file for details.
D [12/Apr/2011:21:45:01 -0400] cupsdMarkDirty(----J-)
D [12/Apr/2011:21:45:01 -0400] cupsdMarkDirty(-----S)
D [12/Apr/2011:21:45:02 -0400] cupsdAcceptClient: 18 from localhost (Domain)
D [12/Apr/2011:21:45:02 -0400] [Job 10] Unloading...
D [12/Apr/2011:21:45:02 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [12/Apr/2011:21:45:02 -0400] cupsdSetBusyState: Active clients and dirty files
D [12/Apr/2011:21:45:02 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:45:02 -0400] cupsdReadClient: 18 1.1 Get-Jobs 1
D [12/Apr/2011:21:45:02 -0400] Get-Jobs ipp://localhost/printers/
D [12/Apr/2011:21:45:02 -0400] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [12/Apr/2011:21:45:02 -0400] cupsdSetBusyState: Dirty files
D [12/Apr/2011:21:45:02 -0400] cupsdReadClient: 18 WAITING Closing on EOF
D [12/Apr/2011:21:45:02 -0400] cupsdCloseClient: 18
D [12/Apr/2011:21:45:02 -0400] cupsdAcceptClient: 18 from localhost (Domain)
D [12/Apr/2011:21:45:02 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [12/Apr/2011:21:45:02 -0400] cupsdSetBusyState: Active clients and dirty files
D [12/Apr/2011:21:45:02 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:45:02 -0400] cupsdReadClient: 18 1.1 Get-Notifications 1
D [12/Apr/2011:21:45:02 -0400] Get-Notifications /
D [12/Apr/2011:21:45:02 -0400] cupsdIsAuthorized: requesting-user-name="shane"
D [12/Apr/2011:21:45:02 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [12/Apr/2011:21:45:02 -0400] cupsdSetBusyState: Dirty files
D [12/Apr/2011:21:45:02 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [12/Apr/2011:21:45:02 -0400] cupsdSetBusyState: Active clients and dirty files
D [12/Apr/2011:21:45:02 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:45:02 -0400] cupsdReadClient: 12 1.1 Get-Notifications 1
D [12/Apr/2011:21:45:02 -0400] Get-Notifications /
D [12/Apr/2011:21:45:02 -0400] cupsdIsAuthorized: requesting-user-name="shane"
D [12/Apr/2011:21:45:02 -0400] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [12/Apr/2011:21:45:02 -0400] cupsdSetBusyState: Dirty files
D [12/Apr/2011:21:45:02 -0400] cupsdAcceptClient: 19 from localhost (Domain)
D [12/Apr/2011:21:45:02 -0400] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Apr/2011:21:45:02 -0400] cupsdSetBusyState: Active clients and dirty files
D [12/Apr/2011:21:45:02 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:45:02 -0400] cupsdReadClient: 19 1.1 Get-Printer-Attributes 1
D [12/Apr/2011:21:45:02 -0400] Get-Printer-Attributes ipp://shane-vaio:0/printers/MP495LAN
D [12/Apr/2011:21:45:02 -0400] Returning IPP successful-ok for Get-Printer-Attributes (ipp://shane-vaio:0/printers/MP495LAN) from localhost
D [12/Apr/2011:21:45:02 -0400] cupsdSetBusyState: Dirty files
D [12/Apr/2011:21:45:02 -0400] cupsdReadClient: 19 POST / HTTP/1.1
D [12/Apr/2011:21:45:02 -0400] cupsdSetBusyState: Active clients and dirty files
D [12/Apr/2011:21:45:02 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:45:02 -0400] cupsdReadClient: 19 1.1 Get-Job-Attributes 1
D [12/Apr/2011:21:45:02 -0400] Get-Job-Attributes ipp://localhost/jobs/10
D [12/Apr/2011:21:45:02 -0400] [Job 10] Loading attributes...
D [12/Apr/2011:21:45:02 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/10) from localhost
D [12/Apr/2011:21:45:02 -0400] cupsdSetBusyState: Dirty files
D [12/Apr/2011:21:45:02 -0400] cupsdReadClient: 18 WAITING Closing on EOF
D [12/Apr/2011:21:45:02 -0400] cupsdCloseClient: 18
D [12/Apr/2011:21:45:03 -0400] Report: clients=6
D [12/Apr/2011:21:45:03 -0400] Report: jobs=10
D [12/Apr/2011:21:45:03 -0400] Report: jobs-active=3
D [12/Apr/2011:21:45:03 -0400] Report: printers=1
D [12/Apr/2011:21:45:03 -0400] Report: printers-implicit=0
D [12/Apr/2011:21:45:03 -0400] Report: stringpool-string-count=6687
D [12/Apr/2011:21:45:03 -0400] Report: stringpool-alloc-bytes=11056
D [12/Apr/2011:21:45:03 -0400] Report: stringpool-total-bytes=128192
I [12/Apr/2011:21:45:08 -0400] Saving job cache file "/var/cache/cups/job.cache"...
I [12/Apr/2011:21:45:08 -0400] Saving subscriptions.conf...
D [12/Apr/2011:21:45:08 -0400] cupsdSetBusyState: Not busy
D [12/Apr/2011:21:45:08 -0400] [Job 1] Unloading...
D [12/Apr/2011:21:45:08 -0400] [Job 2] Unloading...
D [12/Apr/2011:21:45:08 -0400] [Job 3] Unloading...
D [12/Apr/2011:21:45:08 -0400] [Job 4] Unloading...
D [12/Apr/2011:21:45:08 -0400] [Job 5] Unloading...
D [12/Apr/2011:21:45:08 -0400] [Job 6] Unloading...
D [12/Apr/2011:21:45:08 -0400] [Job 7] Unloading...
D [12/Apr/2011:21:45:09 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [12/Apr/2011:21:45:09 -0400] cupsdSetBusyState: Active clients
D [12/Apr/2011:21:45:09 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:45:09 -0400] cupsdReadClient: 12 1.1 Get-Job-Attributes 1
D [12/Apr/2011:21:45:09 -0400] Get-Job-Attributes ipp://localhost/jobs/9
D [12/Apr/2011:21:45:09 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/9) from localhost
D [12/Apr/2011:21:45:09 -0400] cupsdSetBusyState: Not busy
D [12/Apr/2011:21:45:09 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [12/Apr/2011:21:45:09 -0400] cupsdSetBusyState: Active clients
D [12/Apr/2011:21:45:09 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:45:09 -0400] cupsdReadClient: 12 1.1 Get-Job-Attributes 1
D [12/Apr/2011:21:45:09 -0400] Get-Job-Attributes ipp://localhost/jobs/10
D [12/Apr/2011:21:45:09 -0400] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/10) from localhost
D [12/Apr/2011:21:45:09 -0400] cupsdSetBusyState: Not busy
D [12/Apr/2011:21:45:09 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [12/Apr/2011:21:45:09 -0400] cupsdSetBusyState: Active clients
D [12/Apr/2011:21:45:09 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:45:09 -0400] cupsdReadClient: 12 1.1 Cancel-Subscription 1
D [12/Apr/2011:21:45:09 -0400] Cancel-Subscription /
D [12/Apr/2011:21:45:09 -0400] cupsdIsAuthorized: requesting-user-name="shane"
D [12/Apr/2011:21:45:09 -0400] cupsdMarkDirty(-----S)
D [12/Apr/2011:21:45:09 -0400] cupsdSetBusyState: Active clients and dirty files
D [12/Apr/2011:21:45:09 -0400] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [12/Apr/2011:21:45:09 -0400] cupsdSetBusyState: Dirty files
D [12/Apr/2011:21:45:09 -0400] cupsdReadClient: 19 WAITING Closing on EOF
D [12/Apr/2011:21:45:09 -0400] cupsdCloseClient: 19
D [12/Apr/2011:21:45:09 -0400] cupsdReadClient: 12 PUT /admin/conf/cupsd.conf HTTP/1.1
D [12/Apr/2011:21:45:09 -0400] cupsdSetBusyState: Active clients and dirty files
D [12/Apr/2011:21:45:09 -0400] cupsdAuthorize: No authentication data provided.
D [12/Apr/2011:21:45:09 -0400] cupsdIsAuthorized: username=""
D [12/Apr/2011:21:45:09 -0400] cupsdSendHeader: 12 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [12/Apr/2011:21:45:09 -0400] cupsdCloseClient: 12
D [12/Apr/2011:21:45:09 -0400] cupsdSetBusyState: Dirty files
D [12/Apr/2011:21:45:09 -0400] cupsdAcceptClient: 12 from localhost (Domain)
D [12/Apr/2011:21:45:09 -0400] cupsdReadClient: 12 PUT /admin/conf/cupsd.conf HTTP/1.1
D [12/Apr/2011:21:45:09 -0400] cupsdSetBusyState: Active clients and dirty files
D [12/Apr/2011:21:45:09 -0400] cupsdAuthorize: Authorized as shane using PeerCred
D [12/Apr/2011:21:45:09 -0400] cupsdIsAuthorized: username="shane"
I [12/Apr/2011:21:45:09 -0400] Installing config file "/etc/cups/cupsd.conf"...
D [12/Apr/2011:21:45:09 -0400] cupsdSetBusyState: Dirty files
D [12/Apr/2011:21:45:09 -0400] cupsdCloseClient: 13
D [12/Apr/2011:21:45:09 -0400] cupsdCloseClient: 17
D [12/Apr/2011:21:45:09 -0400] cupsdCloseClient: 16
D [12/Apr/2011:21:45:09 -0400] cupsdCloseClient: 15
D [12/Apr/2011:21:45:09 -0400] cupsdCloseClient: 12
I [12/Apr/2011:21:45:09 -0400] Saving subscriptions.conf...
D [12/Apr/2011:21:45:09 -0400] cupsdSetBusyState: Not busy
```


Ok I also just remembered that I did print a document from Open Office yesterday so I don't know why it won't now. I don't believe I made any changes that would affect it. Doesn't seem to make sense that I can print from a browser but not Open Office.

---

### Post by zorglub58 on 2011-04-13
Thanks for this VERY helpfull thread.
Nevertheless, after having done everything , I got it working, but now after few days I always have error messages !!.

This is the content of the troubleshoot file that I cannot undestand (sorry):

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest MP495LAN (default)>,
 'cups_instance': None,
 'cups_queue': 'MP495LAN',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'cnijnet',
 'cups_printer_dict': {'device-uri': u'cnijnet:/88-87-17-1B-C2-BE',
                       'printer-info': u'MP495LAN',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Canon MP495 series Ver.3.40',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 8556556,
                       'printer-uri-supported': u'ipp://localhost:631/printers/MP495LAN'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'color-supported': True,
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.4.4',
                                 'device-uri': u'cnijnet:/88-87-17-1B-C2-BE',
                                 'document-format-default': u'application/octet-stream',
                                 'document-format-supported': [u'application/octet-stream',
                                                               u'application/openofficeps',
                                                               u'application/pdf',
                                                               u'application/postscript',
                                                               u'application/vnd.cups-banner',
                                                               u'application/vnd.cups-pdf',
                                                               u'application/vnd.cups-postscript',
                                                               u'application/vnd.cups-raw',
                                                               u'application/vnd.hp-hpgl',
                                                               u'application/x-cshell',
                                                               u'application/x-csource',
                                                               u'application/x-perl',
                                                               u'application/x-shell',
                                                               u'image/gif',
                                                               u'image/jpeg',
                                                               u'image/png',
                                                               u'image/tiff',
                                                               u'image/x-bitmap',
                                                               u'image/x-photocd',
                                                               u'image/x-portable-anymap',
                                                               u'image/x-portable-bitmap',
                                                               u'image/x-portable-graymap',
                                                               u'image/x-portable-pixmap',
                                                               u'image/x-sgi-rgb',
                                                               u'image/x-sun-raster',
                                                               u'image/x-xbitmap',
                                                               u'image/x-xpixmap',
                                                               u'image/x-xwindowdump',
                                                               u'text/css',
                                                               u'text/html',
                                                               u'text/plain'],
                                 'finishings-default': 3,
                                 'finishings-supported': [3],
                                 'generated-natural-language-supported': [u'en-us'],
                                 'ipp-versions-supported': [u'1.0',
                                                            u'1.1',
                                                            u'2.0',
                                                            u'2.1'],
                                 'ippget-event-life': 15,
                                 'job-creation-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'ipp-attribute-fidelity',
                                                                       u'job-hold-until',
                                                                       u'job-name',
                                                                       u'job-priority',
                                                                       u'job-sheets',
                                                                       u'media',
                                                                       u'media-col',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'output-bin',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
                                 'job-hold-until-default': u'no-hold',
                                 'job-hold-until-supported': [u'no-hold',
                                                              u'indefinite',
                                                              u'day-time',
                                                              u'evening',
                                                              u'night',
                                                              u'second-shift',
                                                              u'third-shift',
                                                              u'weekend'],
                                 'job-k-limit': 0,
                                 'job-page-limit': 0,
                                 'job-priority-default': 50,
                                 'job-priority-supported': [100],
                                 'job-quota-period': 0,
                                 'job-settable-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'job-hold-until',
                                                                       u'job-name',
                                                                       u'job-priority',
                                                                       u'media',
                                                                       u'media-col',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'output-bin',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
                                 'job-sheets-default': (u'none', u'none'),
                                 'job-sheets-supported': [u'none',
                                                          u'classified',
                                                          u'confidential',
                                                          u'secret',
                                                          u'standard',
                                                          u'topsecret',
                                                          u'unclassified'],
                                 'marker-change-time': 0,
                                 'media-bottom-margin-supported': [499,
                                                                   0,
                                                                   3250],
                                 'media-col-supported': [u'media-bottom-margin',
                                                         u'media-left-margin',
                                                         u'media-right-margin',
                                                         u'media-size',
                                                         u'media-source',
                                                         u'media-top-margin',
                                                         u'media-type'],
                                 'media-default': u'iso_a4_210x297mm',
                                 'media-left-margin-supported': [639, 0, 340],
                                 'media-right-margin-supported': [630,
                                                                  35,
                                                                  356,
                                                                  330,
                                                                  343,
                                                                  340,
                                                                  329,
                                                                  323,
                                                                  342,
                                                                  346,
                                                                  352,
                                                                  347],
                                 'media-source-supported': [u'asf'],
                                 'media-supported': [u'na_letter_8.5x11in',
                                                     u'om_letter.bl_216.25x279.75mm',
                                                     u'na_legal_8.5x14in',
                                                     u'iso_a5_148x210mm',
                                                     u'iso_a4_210x297mm',
                                                     u'om_a4.bl_210.25x297.39mm',
                                                     u'jis_b5_182x257mm',
                                                     u'oe_4-x6_4x6in',
                                                     u'om_4-x6.bl_101.95x152.75mm',
                                                     u'oe_4-x8_4x8in',
                                                     u'om_4-x8.bl_101.95x203.55mm',
                                                     u'oe_5-x7_5x7in',
                                                     u'om_5-x7.bl_127.35x178.15mm',
                                                     u'oe_8-x10_8x10in',
                                                     u'om_8-x10.bl_203.55x254.35mm',
                                                     u'oe_l_3.5x5in',
                                                     u'om_l.bl_89.25x127.35mm',
                                                     u'om_2l_127x178.15mm',
                                                     u'om_2l.bl_127.35x178.5mm',
                                                     u'om_postcard_99.83x148.16mm',
                                                     u'om_postcard.bl_100.18x148.51mm',
                                                     u'om_postdbl_200.02x148.16mm',
                                                     u'om_envelop10p_104.77x241.3mm',
                                                     u'om_envelopdlp_110.06x220.13mm',
                                                     u'om_envj4p_105.12x234.95mm',
                                                     u'om_envj6p_98.07x190.14mm',
                                                     u'om_businesscard_55.03x91.01mm',
                                                     u'om_businesscard.bl_55.38x91.36mm',
                                                     u'om_wide_101.6x180.62mm',
                                                     u'om_wide.bl_101.95x180.97mm',
                                                     u'custom_min_55x91mm',
                                                     u'custom_max_215.9x676mm'],
                                 'media-top-margin-supported': [299,
                                                                35,
                                                                290,
                                                                303,
                                                                317,
                                                                315,
                                                                316,
                                                                800,
                                                                813,
                                                                795,
                                                                814,
                                                                301,
                                                                300],
                                 'media-type-supported': [u'stationery',
                                                          u'photographic-glossy',
                                                          u'proplatinum',
                                                          u'semigloss',
                                                          u'photographic-glossy',
                                                          u'photographic-matte',
                                                          u'highres',
                                                          u'postcardaddress',
                                                          u'ijpostcard',
                                                          u'photographic-glossy',
                                                          u'postcard',
                                                          u'tshirt',
                                                          u'envelope',
                                                          u'otherphoto'],
                                 'multiple-document-handling-supported': [u'separate-documents-uncollated-copies',
                                                                          u'separate-documents-collated-copies'],
                                 'multiple-document-jobs-supported': True,
                                 'multiple-operation-time-out': 300,
                                 'natural-language-configured': u'en-us',
                                 'notify-attributes-supported': [u'printer-state-change-time',
                                                                 u'notify-lease-expiration-time',
                                                                 u'notify-subscriber-user-name'],
                                 'notify-events-default': [u'job-completed'],
                                 'notify-events-supported': [u'job-completed',
                                                             u'job-config-changed',
                                                             u'job-created',
                                                             u'job-progress',
                                                             u'job-state-changed',
                                                             u'job-stopped',
                                                             u'printer-added',
                                                             u'printer-changed',
                                                             u'printer-config-changed',
                                                             u'printer-deleted',
                                                             u'printer-finishings-changed',
                                                             u'printer-media-changed',
                                                             u'printer-modified',
                                                             u'printer-restarted',
                                                             u'printer-shutdown',
                                                             u'printer-state-changed',
                                                             u'printer-stopped',
                                                             u'server-audit',
                                                             u'server-restarted',
                                                             u'server-started',
                                                             u'server-stopped'],
                                 'notify-lease-duration-default': 86400,
                                 'notify-lease-duration-supported': (0,
                                                                     2147483647),
                                 'notify-max-events-supported': [100],
                                 'notify-pull-method-supported': [u'ippget'],
                                 'notify-schemes-supported': [u'dbus',
                                                              u'mailto',
                                                              u'rss'],
                                 'number-up-default': 1,
                                 'number-up-supported': [1, 2, 4, 6, 9, 16],
                                 'operations-supported': [2,
                                                          4,
                                                          5,
                                                          6,
                                                          8,
                                                          9,
                                                          10,
                                                          11,
                                                          12,
                                                          13,
                                                          16,
                                                          17,
                                                          18,
                                                          19,
                                                          20,
                                                          21,
                                                          22,
                                                          23,
                                                          24,
                                                          25,
                                                          26,
                                                          27,
                                                          28,
                                                          34,
                                                          35,
                                                          37,
                                                          38,
                                                          16385,
                                                          16386,
                                                          16387,
                                                          16388,
                                                          16389,
                                                          16390,
                                                          16391,
                                                          16392,
                                                          16393,
                                                          16394,
                                                          16395,
                                                          16396,
                                                          16397,
                                                          16398,
                                                          16399,
                                                          16423],
                                 'orientation-requested-default': None,
                                 'orientation-requested-supported': [3,
                                                                     4,
                                                                     5,
                                                                     6],
                                 'output-bin-default': u'face-down',
                                 'output-bin-supported': [u'face-down'],
                                 'page-ranges-supported': True,
                                 'pages-per-minute': 1,
                                 'pages-per-minute-color': 1,
                                 'pdl-override-supported': [u'not-attempted'],
                                 'port-monitor': u'none',
                                 'port-monitor-supported': [u'none'],
                                 'print-quality-default': 4,
                                 'print-quality-supported': [4],
                                 'printer-commands': [u'AutoConfigure',
                                                      u'Clean',
                                                      u'PrintSelfTestPage'],
                                 'printer-current-time': '(IPP_TAG_DATE)',
                                 'printer-error-policy': u'retry-job',
                                 'printer-error-policy-supported': [u'abort-job',
                                                                    u'retry-current-job',
                                                                    u'retry-job',
                                                                    u'stop-printer'],
                                 'printer-info': u'MP495LAN',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'',
                                 'printer-make-and-model': u'Canon MP495 series Ver.3.40',
                                 'printer-more-info': u'http://localhost:631/printers/MP495LAN',
                                 'printer-name': u'MP495LAN',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-resolution-supported': ['(unknown IPP tag)',
                                                                  '(unknown IPP tag)',
                                                                  '(unknown IPP tag)',
                                                                  '(unknown IPP tag)',
                                                                  '(unknown IPP tag)'],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1302681925,
                                 'printer-state-message': u'',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 8556556,
                                 'printer-up-time': 1302681939,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/MP495LAN'],
                                 'queued-job-count': 28,
                                 'server-is-sharing-printers': True,
                                 'sides-default': u'one-sided',
                                 'sides-supported': [u'one-sided'],
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'CNExtension': u'2',
                                            u'ColorModel': u'rgb',
                                            u'InputSlot': u'asf',
                                            u'MediaType': u'plain',
                                            u'PageRegion': u'A4',
                                            u'PageSize': u'A4',
                                            u'Resolution': u'4800dpi'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
                          'BrowseRemoteProtocols': '',
                          'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '1',
                          '_remote_printers': '0',
                          '_share_printers': '1',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 12311L,
 'error_log_debug_logging_set': True}
Page 7 (Print test page):
{'test_page_attempted': '13/avril/2011:10:06:16 +0000',
 'test_page_job_id': [110],
 'test_page_job_status': [(True,
                           110,
                           'MP495LAN',
                           'Test Page',
                           'Arr\xc3\xaat\xc3\xa9',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'fr-fr',
                            'document-count': 1,
                            'document-format': u'application/vnd.cups-banner',
                            'job-hold-until': u'no-hold',
                            'job-id': 110,
                            'job-k-octets': 1,
                            'job-media-progress': 0,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/110',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'michel',
                            'job-preserved': True,
                            'job-printer-state-message': u'/usr/lib/cups/filter/pstocanonij failed',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1302681997,
                            'job-printer-uri': u'ipp://Ordinateur-filles:631/printers/MP495LAN',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/110',
                            'job-uuid': u'urn:uuid:bc5b1f69-07a8-337f-7015-5b73a926ffc0',
                            'printer-uri': u'ipp://localhost/printers/MP495LAN',
                            'time-at-completed': None,
                            'time-at-creation': 1302681976,
                            'time-at-processing': 1302681976})],
 'test_page_jobs_cancelled': True,
 'test_page_successful': False}
Page 8 (Error log fetch):
{'error_log': ['D [13/Apr/2011:10:06:00 +0200] cupsdSetBusyState: Dirty files',
               'D [13/Apr/2011:10:06:00 +0200] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:00 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Apr/2011:10:06:00 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:00 +0200] cupsdReadClient: 13 1.1 Get-Jobs 1',
               'D [13/Apr/2011:10:06:00 +0200] Get-Jobs ipp://localhost/printers/',
               'D [13/Apr/2011:10:06:00 +0200] [Job 109] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [13/Apr/2011:10:06:00 +0200] cupsdSetBusyState: Dirty files',
               'D [13/Apr/2011:10:06:00 +0200] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:00 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Apr/2011:10:06:00 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:00 +0200] cupsdReadClient: 13 1.1 Get-Jobs 1',
               'D [13/Apr/2011:10:06:00 +0200] Get-Jobs ipp://localhost/printers/',
               'D [13/Apr/2011:10:06:00 +0200] [Job 1] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 2] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 3] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 4] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 5] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 6] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 7] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 9] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 10] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 11] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 12] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 13] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 15] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 16] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 17] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 18] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 19] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 20] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 21] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 22] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 23] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 24] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 25] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 27] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 28] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 29] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 30] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 31] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 32] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 33] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 34] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 35] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 36] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 37] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 38] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 39] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 40] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 41] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 42] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 43] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 44] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 45] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 46] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 47] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 48] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 49] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 50] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 51] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 52] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 53] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 54] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 55] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 56] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 59] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 60] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 62] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 63] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 64] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 65] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 66] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 67] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 68] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 69] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 70] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 71] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 72] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] [Job 74] Loading attributes...',
               'D [13/Apr/2011:10:06:00 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [13/Apr/2011:10:06:00 +0200] cupsdSetBusyState: Dirty files',
               'D [13/Apr/2011:10:06:00 +0200] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:00 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Apr/2011:10:06:00 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:00 +0200] cupsdReadClient: 13 1.1 Create-Printer-Subscription 1',
               'D [13/Apr/2011:10:06:00 +0200] Create-Printer-Subscription /',
               'D [13/Apr/2011:10:06:00 +0200] cupsdCreateSubscription(con=0x20356bc0(13), uri="/")',
               'D [13/Apr/2011:10:06:00 +0200] pullmethod="ippget"',
               'D [13/Apr/2011:10:06:00 +0200] notify-lease-duration=86400',
               'D [13/Apr/2011:10:06:00 +0200] notify-time-interval=0',
               'D [13/Apr/2011:10:06:00 +0200] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [13/Apr/2011:10:06:00 +0200] Added subscription 83 for server',
               'D [13/Apr/2011:10:06:00 +0200] cupsdMarkDirty(-----S)',
               'D [13/Apr/2011:10:06:00 +0200] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [13/Apr/2011:10:06:00 +0200] cupsdSetBusyState: Dirty files',
               'D [13/Apr/2011:10:06:01 +0200] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:01 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Apr/2011:10:06:01 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:01 +0200] cupsdReadClient: 13 1.1 Get-Notifications 1',
               'D [13/Apr/2011:10:06:01 +0200] Get-Notifications /',
               'D [13/Apr/2011:10:06:01 +0200] cupsdIsAuthorized: requesting-user-name="michel"',
               'D [13/Apr/2011:10:06:01 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [13/Apr/2011:10:06:01 +0200] cupsdSetBusyState: Dirty files',
               'D [13/Apr/2011:10:06:14 +0200] [Job 75] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 76] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 77] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 78] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 79] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 80] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 81] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 82] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 83] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 84] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 85] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 86] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 87] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 88] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 89] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 90] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 91] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 92] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 93] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 94] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 95] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 96] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 97] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 98] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 99] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 100] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 103] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 104] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 105] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 106] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 107] Unloading...',
               'D [13/Apr/2011:10:06:14 +0200] [Job 108] Unloading...',
               'D [13/Apr/2011:10:06:16 +0200] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [13/Apr/2011:10:06:16 +0200] cupsdReadClient: 14 POST /printers/MP495LAN HTTP/1.1',
               'D [13/Apr/2011:10:06:16 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Apr/2011:10:06:16 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:16 +0200] cupsdReadClient: 14 1.1 Print-Job 1',
               'D [13/Apr/2011:10:06:16 +0200] Print-Job ipp://localhost/printers/MP495LAN',
               'D [13/Apr/2011:10:06:16 +0200] [Job ???] Auto-typing file...',
               'I [13/Apr/2011:10:06:16 +0200] [Job ???] Request file type is application/vnd.cups-banner.',
               'D [13/Apr/2011:10:06:16 +0200] cupsdMarkDirty(----J-)',
               'D [13/Apr/2011:10:06:16 +0200] add_job: requesting-user-name="michel"',
               'D [13/Apr/2011:10:06:16 +0200] Adding default job-sheets values "none,none"...',
               'I [13/Apr/2011:10:06:16 +0200] [Job 110] Adding start banner page "none".',
               'D [13/Apr/2011:10:06:16 +0200] cupsdMarkDirty(-----S)',
               'D [13/Apr/2011:10:06:16 +0200] cupsdMarkDirty(----J-)',
               'I [13/Apr/2011:10:06:16 +0200] [Job 110] Adding end banner page "none".',
               'I [13/Apr/2011:10:06:16 +0200] [Job 110] File of type application/vnd.cups-banner queued by "michel".',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] hold_until=0',
               'I [13/Apr/2011:10:06:16 +0200] [Job 110] Queued on "MP495LAN" by "michel".',
               'D [13/Apr/2011:10:06:16 +0200] cupsdMarkDirty(----J-)',
               'D [13/Apr/2011:10:06:16 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [13/Apr/2011:10:06:16 +0200] cupsdMarkDirty(-----S)',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] job-sheets=none,none',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] argv[0]="MP495LAN"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] argv[1]="110"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] argv[2]="michel"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] argv[3]="Test Page"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] argv[4]="1"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] argv[5]="job-uuid=urn:uuid:bc5b1f69-07a8-337f-7015-5b73a926ffc0 job-originating-host-name=localhost"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] argv[6]="/var/spool/cups/d00110-001"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[8]="HOME=/var/spool/cups/tmp"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[10]="SERVER_ADMIN=root@Ordinateur-filles"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[11]="SOFTWARE=CUPS/1.4.4"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[12]="TMPDIR=/var/spool/cups/tmp"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[13]="USER=root"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[16]="IPP_PORT=631"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[17]="CHARSET=utf-8"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[18]="LANG=fr_FR.UTF-8"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[19]="PPD=/etc/cups/ppd/MP495LAN.ppd"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[20]="RIP_MAX_CACHE=auto"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[21]="CONTENT_TYPE=application/vnd.cups-banner"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[22]="DEVICE_URI=cnijnet:/88-87-17-1B-C2-BE"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[23]="PRINTER_INFO=MP495LAN"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[24]="PRINTER_LOCATION="',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[25]="PRINTER=MP495LAN"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[26]="CUPS_FILETYPE=document"',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] envp[27]="FINAL_CONTENT_TYPE=printer/MP495LAN"',
               'I [13/Apr/2011:10:06:16 +0200] [Job 110] Started filter /usr/lib/cups/filter/bannertops (PID 2387)',
               'I [13/Apr/2011:10:06:16 +0200] [Job 110] Started filter /usr/lib/cups/filter/pstops (PID 2388)',
               'I [13/Apr/2011:10:06:16 +0200] [Job 110] Started filter /usr/lib/cups/filter/pstocanonij (PID 2389)',
               'I [13/Apr/2011:10:06:16 +0200] [Job 110] Started backend /usr/lib/cups/backend/cnijnet (PID 2390)',
               'D [13/Apr/2011:10:06:16 +0200] cupsdMarkDirty(-----S)',
               'D [13/Apr/2011:10:06:16 +0200] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/MP495LAN) from localhost',
               'D [13/Apr/2011:10:06:16 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] pstocanonij start.',
               'I [13/Apr/2011:10:06:16 +0200] [Job 110]',
               'D [13/Apr/2011:10:06:16 +0200] cupsdMarkDirty(-----S)',
               'I [13/Apr/2011:10:06:16 +0200] [Job 110]',
               'D [13/Apr/2011:10:06:16 +0200] cupsdMarkDirty(-----S)',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] load_banner(filename="/var/spool/cups/d00110-001")',
               'I [13/Apr/2011:10:06:16 +0200] [Job 110]',
               'D [13/Apr/2011:10:06:16 +0200] cupsdMarkDirty(-----S)',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] Page = 595x842; 10,14 to 586,833',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] [cnijnetprn] CheckStartPrint(0)',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] [cnijnetprn] IsPrinterWorking',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] [cnijnetprn] getPrinterStatus',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] Page = 595x842; 10,14 to 586,833',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] slow_collate=0, slow_duplex=0, slow_order=0',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] Before copy_comments - %!PS-Adobe-3.0',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] %!PS-Adobe-3.0',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] %%BoundingBox: 10 14 586 833',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] %cupsRotation: 0',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] %%Creator: bannertops/CUPS v1.4.4',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] %%CreationDate: mer. 13 avril 2011 10:06:16 CEST',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] %%LanguageLevel: 2',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] %%DocumentData: Clean7Bit',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] %%Title: (Test Page)',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] %%For: (michel)',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] %%Pages: 1',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] %%DocumentSuppliedResources: font Monospace',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] %%+ font Monospace-Bold',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] %%+ font Monospace-BoldOblique',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] %%+ font Monospace-Oblique',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] %%EndComments',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] Before copy_prolog - %%BeginProlog',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] PNG image: 192x128x8, color_type=2 (RGB)',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] Before copy_setup - %%Page: coverpage 1',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] Before page loop - %%Page: coverpage 1',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] Copying page 1...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] pagew = 576.0, pagel = 819.2',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] bboxx = 0, bboxy = 0, bboxw = 595, bboxl = 842',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] PageLeft = 9.6, PageRight = 585.6',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] PageTop = 833.4, PageBottom = 14.2',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] PageWidth = 595.0, PageLength = 842.0',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] device_uri=(cnijnet:/88-87-17-1B-C2-BE)',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] p_ppd->model_number=(369)',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] #  p_size->name=A4 , p_size_default->name = A4 #',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] ### num_opt(lpr optins) = 2 ###',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110]',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] # ppdPageSize width=595.000000 height=842.000000 ###',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110]',
               'D [13/Apr/2011:10:06:16 +0200] PID 2387 (/usr/lib/cups/filter/bannertops) did not catch or ignore signal 13.',
               'D [13/Apr/2011:10:06:16 +0200] PID 2388 (/usr/lib/cups/filter/pstops) did not catch or ignore signal 13.',
               'E [13/Apr/2011:10:06:16 +0200] PID 2389 (/usr/lib/cups/filter/pstocanonij) crashed on signal 11!',
               'D [13/Apr/2011:10:06:16 +0200] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [13/Apr/2011:10:06:16 +0200] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:16 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [13/Apr/2011:10:06:16 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:16 +0200] cupsdReadClient: 17 1.1 Get-Notifications 1',
               'D [13/Apr/2011:10:06:16 +0200] Get-Notifications /',
               'D [13/Apr/2011:10:06:16 +0200] cupsdIsAuthorized: requesting-user-name="michel"',
               'D [13/Apr/2011:10:06:16 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [13/Apr/2011:10:06:16 +0200] cupsdAcceptClient: 18 from localhost (Domain)',
               'D [13/Apr/2011:10:06:16 +0200] cupsdReadClient: 18 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:16 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:16 +0200] cupsdReadClient: 18 1.1 Get-Jobs 1',
               'D [13/Apr/2011:10:06:16 +0200] Get-Jobs ipp://localhost/printers/',
               'D [13/Apr/2011:10:06:16 +0200] [Job 75] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 76] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 77] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 78] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 79] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 80] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 81] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 82] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 83] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 84] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 85] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 86] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 87] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 88] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 89] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 90] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 91] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 92] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 93] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 94] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 95] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 96] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 97] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 98] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 99] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 100] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 103] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 104] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 105] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 106] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 107] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] [Job 108] Loading attributes...',
               'D [13/Apr/2011:10:06:16 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [13/Apr/2011:10:06:16 +0200] cupsdReadClient: 18 WAITING Closing on EOF',
               'D [13/Apr/2011:10:06:16 +0200] cupsdCloseClient: 18',
               'D [13/Apr/2011:10:06:16 +0200] cupsdAcceptClient: 18 from localhost (Domain)',
               'D [13/Apr/2011:10:06:16 +0200] cupsdReadClient: 18 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:16 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:16 +0200] cupsdAcceptClient: 19 from localhost (Domain)',
               'D [13/Apr/2011:10:06:16 +0200] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:16 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:16 +0200] cupsdReadClient: 18 1.1 Get-Notifications 1',
               'D [13/Apr/2011:10:06:16 +0200] Get-Notifications /',
               'D [13/Apr/2011:10:06:16 +0200] cupsdIsAuthorized: requesting-user-name="michel"',
               'D [13/Apr/2011:10:06:16 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [13/Apr/2011:10:06:16 +0200] cupsdReadClient: 19 1.1 Get-Printer-Attributes 1',
               'D [13/Apr/2011:10:06:16 +0200] Get-Printer-Attributes ipp://localhost/printers/MP495LAN',
               'D [13/Apr/2011:10:06:16 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/MP495LAN) from localhost',
               'D [13/Apr/2011:10:06:16 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [13/Apr/2011:10:06:16 +0200] cupsdReadClient: 18 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:16 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [13/Apr/2011:10:06:16 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:16 +0200] cupsdReadClient: 18 1.1 Get-Job-Attributes 1',
               'D [13/Apr/2011:10:06:16 +0200] Get-Job-Attributes ipp://localhost/jobs/110',
               'D [13/Apr/2011:10:06:16 +0200] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/110) from localhost',
               'D [13/Apr/2011:10:06:16 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [13/Apr/2011:10:06:16 +0200] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:16 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [13/Apr/2011:10:06:16 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:16 +0200] cupsdReadClient: 13 1.1 Get-Notifications 1',
               'D [13/Apr/2011:10:06:16 +0200] Get-Notifications /',
               'D [13/Apr/2011:10:06:16 +0200] cupsdIsAuthorized: requesting-user-name="michel"',
               'D [13/Apr/2011:10:06:16 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [13/Apr/2011:10:06:16 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] [cnijnetprn] dispatchCommandIVEC Receive(1)',
               'D [13/Apr/2011:10:06:16 +0200] cupsdReadClient: 17 WAITING Closing on EOF',
               'D [13/Apr/2011:10:06:16 +0200] cupsdCloseClient: 17',
               'D [13/Apr/2011:10:06:16 +0200] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:16 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [13/Apr/2011:10:06:16 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:16 +0200] cupsdReadClient: 19 1.1 CUPS-Get-Printers 1',
               'D [13/Apr/2011:10:06:16 +0200] CUPS-Get-Printers',
               'D [13/Apr/2011:10:06:16 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [13/Apr/2011:10:06:16 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [13/Apr/2011:10:06:16 +0200] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:16 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [13/Apr/2011:10:06:16 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:16 +0200] cupsdReadClient: 19 1.1 CUPS-Get-Classes 1',
               'D [13/Apr/2011:10:06:16 +0200] CUPS-Get-Classes',
               'D [13/Apr/2011:10:06:16 +0200] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [13/Apr/2011:10:06:16 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [13/Apr/2011:10:06:16 +0200] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:16 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [13/Apr/2011:10:06:16 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:16 +0200] cupsdReadClient: 19 1.1 CUPS-Get-Default 1',
               'D [13/Apr/2011:10:06:16 +0200] CUPS-Get-Default',
               'D [13/Apr/2011:10:06:16 +0200] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [13/Apr/2011:10:06:16 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] [cnijnetprn] dispatchCommandIVEC Receive(2)',
               'I [13/Apr/2011:10:06:16 +0200] [Job 110] waiting print data ...',
               'I [13/Apr/2011:10:06:16 +0200] [Job 110]',
               'D [13/Apr/2011:10:06:16 +0200] cupsdMarkDirty(-----S)',
               'D [13/Apr/2011:10:06:16 +0200] [Job 110] [cnijnetprn] dispatchCommandIVEC Receive(3)',
               'D [13/Apr/2011:10:06:17 +0200] cupsdReadClient: 18 WAITING Closing on EOF',
               'D [13/Apr/2011:10:06:17 +0200] cupsdCloseClient: 18',
               'D [13/Apr/2011:10:06:17 +0200] [Job 110] [cnijnetprn] CheckExecutePrint',
               'D [13/Apr/2011:10:06:17 +0200] [Job 110] [cnijnetprn] IsPrinterWorking',
               'D [13/Apr/2011:10:06:17 +0200] [Job 110] [cnijnetprn] getPrinterStatus',
               'D [13/Apr/2011:10:06:18 +0200] [Job 110] [cnijnetprn] CheckExecutePrint',
               'D [13/Apr/2011:10:06:18 +0200] [Job 110] [cnijnetprn] IsPrinterWorking',
               'D [13/Apr/2011:10:06:18 +0200] [Job 110] [cnijnetprn] getPrinterStatus',
               'D [13/Apr/2011:10:06:19 +0200] [Job 110] [cnijnetprn] CheckExecutePrint',
               'D [13/Apr/2011:10:06:19 +0200] [Job 110] [cnijnetprn] IsPrinterWorking',
               'D [13/Apr/2011:10:06:19 +0200] [Job 110] [cnijnetprn] getPrinterStatus',
               'D [13/Apr/2011:10:06:20 +0200] [Job 110] [cnijnetprn] CheckExecutePrint',
               'D [13/Apr/2011:10:06:20 +0200] [Job 110] [cnijnetprn] IsPrinterWorking',
               'D [13/Apr/2011:10:06:20 +0200] [Job 110] [cnijnetprn] getPrinterStatus',
               'D [13/Apr/2011:10:06:21 +0200] [Job 110] [cnijnetprn] CheckExecutePrint',
               'D [13/Apr/2011:10:06:21 +0200] [Job 110] [cnijnetprn] IsPrinterWorking',
               'D [13/Apr/2011:10:06:21 +0200] [Job 110] [cnijnetprn] getPrinterStatus',
               'D [13/Apr/2011:10:06:22 +0200] [Job 110] [cnijnetprn] CheckExecutePrint',
               'D [13/Apr/2011:10:06:22 +0200] [Job 110] [cnijnetprn] IsPrinterWorking',
               'D [13/Apr/2011:10:06:22 +0200] [Job 110] [cnijnetprn] getPrinterStatus',
               'D [13/Apr/2011:10:06:23 +0200] [Job 110] [cnijnetprn] CheckExecutePrint',
               'D [13/Apr/2011:10:06:23 +0200] [Job 110] [cnijnetprn] IsPrinterWorking',
               'D [13/Apr/2011:10:06:23 +0200] [Job 110] [cnijnetprn] getPrinterStatus',
               'D [13/Apr/2011:10:06:24 +0200] [Job 110] [cnijnetprn] CheckExecutePrint',
               'D [13/Apr/2011:10:06:24 +0200] [Job 110] [cnijnetprn] IsPrinterWorking',
               'D [13/Apr/2011:10:06:24 +0200] [Job 110] [cnijnetprn] getPrinterStatus',
               'D [13/Apr/2011:10:06:25 +0200] [Job 110] [cnijnetprn] CheckExecutePrint',
               'D [13/Apr/2011:10:06:25 +0200] [Job 110] [cnijnetprn] IsPrinterWorking',
               'D [13/Apr/2011:10:06:25 +0200] [Job 110] [cnijnetprn] getPrinterStatus',
               'D [13/Apr/2011:10:06:26 +0200] [Job 110] [cnijnetprn] CheckExecutePrint',
               'D [13/Apr/2011:10:06:26 +0200] [Job 110] [cnijnetprn] IsPrinterWorking',
               'D [13/Apr/2011:10:06:26 +0200] [Job 110] [cnijnetprn] getPrinterStatus',
               'I [13/Apr/2011:10:06:27 +0200] Generating printcap /var/run/cups/printcap...',
               'I [13/Apr/2011:10:06:27 +0200] Saving job cache file "/var/cache/cups/job.cache"...',
               'I [13/Apr/2011:10:06:27 +0200] Saving subscriptions.conf...',
               'D [13/Apr/2011:10:06:27 +0200] cupsdSetBusyState: Printing jobs',
               'D [13/Apr/2011:10:06:27 +0200] [Job 110] [cnijnetprn] CheckEndPrint(0)',
               'D [13/Apr/2011:10:06:27 +0200] [Job 110] [cnijnetprn] IsPrinterWorking',
               'D [13/Apr/2011:10:06:27 +0200] [Job 110] [cnijnetprn] getPrinterStatus',
               'I [13/Apr/2011:10:06:27 +0200] [Job 110]',
               'D [13/Apr/2011:10:06:27 +0200] cupsdMarkDirty(-----S)',
               'D [13/Apr/2011:10:06:27 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [13/Apr/2011:10:06:28 +0200] PID 2390 (/usr/lib/cups/backend/cnijnet) exited with no errors.',
               'D [13/Apr/2011:10:06:28 +0200] cupsdMarkDirty(-----S)',
               'E [13/Apr/2011:10:06:28 +0200] [Job 110] Job stopped due to filter errors; please consult the error_log file for details.',
               'D [13/Apr/2011:10:06:28 +0200] cupsdMarkDirty(----J-)',
               'D [13/Apr/2011:10:06:28 +0200] cupsdMarkDirty(-----S)',
               'D [13/Apr/2011:10:06:28 +0200] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:28 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Apr/2011:10:06:28 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 16 1.1 Get-Notifications 1',
               'D [13/Apr/2011:10:06:28 +0200] Get-Notifications /',
               'D [13/Apr/2011:10:06:28 +0200] cupsdIsAuthorized: requesting-user-name="michel"',
               'D [13/Apr/2011:10:06:28 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [13/Apr/2011:10:06:28 +0200] cupsdSetBusyState: Dirty files',
               'D [13/Apr/2011:10:06:28 +0200] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:28 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Apr/2011:10:06:28 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:28 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 19 1.1 Get-Printer-Attributes 1',
               'D [13/Apr/2011:10:06:28 +0200] Get-Printer-Attributes ipp://localhost/printers/MP495LAN',
               'D [13/Apr/2011:10:06:28 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/MP495LAN) from localhost',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 17 1.1 Get-Jobs 1',
               'D [13/Apr/2011:10:06:28 +0200] Get-Jobs ipp://localhost/printers/',
               'D [13/Apr/2011:10:06:28 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 17 WAITING Closing on EOF',
               'D [13/Apr/2011:10:06:28 +0200] cupsdCloseClient: 17',
               'D [13/Apr/2011:10:06:28 +0200] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:28 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 17 1.1 Get-Notifications 1',
               'D [13/Apr/2011:10:06:28 +0200] Get-Notifications /',
               'D [13/Apr/2011:10:06:28 +0200] cupsdIsAuthorized: requesting-user-name="michel"',
               'D [13/Apr/2011:10:06:28 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [13/Apr/2011:10:06:28 +0200] cupsdSetBusyState: Dirty files',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:28 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Apr/2011:10:06:28 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 13 1.1 Get-Notifications 1',
               'D [13/Apr/2011:10:06:28 +0200] Get-Notifications /',
               'D [13/Apr/2011:10:06:28 +0200] cupsdIsAuthorized: requesting-user-name="michel"',
               'D [13/Apr/2011:10:06:28 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [13/Apr/2011:10:06:28 +0200] cupsdSetBusyState: Dirty files',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 16 WAITING Closing on EOF',
               'D [13/Apr/2011:10:06:28 +0200] cupsdCloseClient: 16',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:28 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Apr/2011:10:06:28 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 19 1.1 CUPS-Get-Printers 1',
               'D [13/Apr/2011:10:06:28 +0200] CUPS-Get-Printers',
               'D [13/Apr/2011:10:06:28 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [13/Apr/2011:10:06:28 +0200] cupsdSetBusyState: Dirty files',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:28 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Apr/2011:10:06:28 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 19 1.1 CUPS-Get-Classes 1',
               'D [13/Apr/2011:10:06:28 +0200] CUPS-Get-Classes',
               'D [13/Apr/2011:10:06:28 +0200] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [13/Apr/2011:10:06:28 +0200] cupsdSetBusyState: Dirty files',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:28 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Apr/2011:10:06:28 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 19 1.1 CUPS-Get-Default 1',
               'D [13/Apr/2011:10:06:28 +0200] CUPS-Get-Default',
               'D [13/Apr/2011:10:06:28 +0200] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [13/Apr/2011:10:06:28 +0200] cupsdSetBusyState: Dirty files',
               'D [13/Apr/2011:10:06:28 +0200] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 14 WAITING Closing on EOF',
               'D [13/Apr/2011:10:06:28 +0200] cupsdCloseClient: 14',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:28 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Apr/2011:10:06:28 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 16 1.1 Get-Printer-Attributes 1',
               'D [13/Apr/2011:10:06:28 +0200] Get-Printer-Attributes ipp://Ordinateur-filles:631/printers/MP495LAN',
               'D [13/Apr/2011:10:06:28 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://Ordinateur-filles:631/printers/MP495LAN) from localhost',
               'D [13/Apr/2011:10:06:28 +0200] cupsdSetBusyState: Dirty files',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:28 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Apr/2011:10:06:28 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 16 1.1 Get-Job-Attributes 1',
               'D [13/Apr/2011:10:06:28 +0200] Get-Job-Attributes ipp://localhost/jobs/110',
               'D [13/Apr/2011:10:06:28 +0200] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/110) from localhost',
               'D [13/Apr/2011:10:06:28 +0200] cupsdSetBusyState: Dirty files',
               'D [13/Apr/2011:10:06:28 +0200] cupsdReadClient: 17 WAITING Closing on EOF',
               'D [13/Apr/2011:10:06:28 +0200] cupsdCloseClient: 17',
               'D [13/Apr/2011:10:06:29 +0200] [Job 110] Unloading...',
               'D [13/Apr/2011:10:06:37 +0200] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:37 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Apr/2011:10:06:37 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:37 +0200] cupsdReadClient: 13 1.1 Get-Job-Attributes 1',
               'D [13/Apr/2011:10:06:37 +0200] Get-Job-Attributes ipp://localhost/jobs/110',
               'D [13/Apr/2011:10:06:37 +0200] [Job 110] Loading attributes...',
               'D [13/Apr/2011:10:06:37 +0200] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/110) from localhost',
               'D [13/Apr/2011:10:06:37 +0200] cupsdSetBusyState: Dirty files',
               'D [13/Apr/2011:10:06:37 +0200] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [13/Apr/2011:10:06:37 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Apr/2011:10:06:37 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:37 +0200] cupsdReadClient: 13 1.1 Cancel-Subscription 1',
               'D [13/Apr/2011:10:06:37 +0200] Cancel-Subscription /',
               'D [13/Apr/2011:10:06:37 +0200] cupsdIsAuthorized: requesting-user-name="michel"',
               'D [13/Apr/2011:10:06:37 +0200] cupsdMarkDirty(-----S)',
               'D [13/Apr/2011:10:06:37 +0200] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [13/Apr/2011:10:06:37 +0200] cupsdSetBusyState: Dirty files',
               'D [13/Apr/2011:10:06:37 +0200] cupsdReadClient: 13 PUT /admin/conf/cupsd.conf HTTP/1.1',
               'D [13/Apr/2011:10:06:37 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Apr/2011:10:06:37 +0200] cupsdAuthorize: No authentication data provided.',
               'D [13/Apr/2011:10:06:37 +0200] cupsdIsAuthorized: username=""',
               'D [13/Apr/2011:10:06:37 +0200] cupsdSendHeader: 13 WWW-Authenticate: Basic realm="CUPS", trc="y"',
               'D [13/Apr/2011:10:06:37 +0200] cupsdCloseClient: 13',
               'D [13/Apr/2011:10:06:37 +0200] cupsdSetBusyState: Dirty files',
               'D [13/Apr/2011:10:06:37 +0200] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [13/Apr/2011:10:06:37 +0200] cupsdReadClient: 13 PUT /admin/conf/cupsd.conf HTTP/1.1',
               'D [13/Apr/2011:10:06:37 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [13/Apr/2011:10:06:37 +0200] cupsdAuthorize: Authorized as michel using PeerCred',
               'D [13/Apr/2011:10:06:37 +0200] cupsdIsAuthorized: username="michel"',
               'I [13/Apr/2011:10:06:37 +0200] Installing config file "/etc/cups/cupsd.conf"...',
               'D [13/Apr/2011:10:06:37 +0200] cupsdSetBusyState: Dirty files',
               'D [13/Apr/2011:10:06:37 +0200] cupsdCloseClient: 19',
               'D [13/Apr/2011:10:06:37 +0200] cupsdCloseClient: 16',
               'D [13/Apr/2011:10:06:37 +0200] cupsdCloseClient: 13',
               'D [13/Apr/2011:10:06:37 +0200] cupsdDeregisterPrinter(p=0x202fa430(Canon-MP150), removeit=1)',
               'D [13/Apr/2011:10:06:37 +0200] cupsdDeregisterPrinter(p=0x20636e70(MP495LAN), removeit=1)',
               'D [13/Apr/2011:10:06:37 +0200] cupsdDeregisterPrinter(p=0x20455d40(MP495USB), removeit=1)',
               'I [13/Apr/2011:10:06:37 +0200] Saving job cache file "/var/cache/cups/job.cache"...',
               'I [13/Apr/2011:10:06:37 +0200] Saving subscriptions.conf...',
               'D [13/Apr/2011:10:06:37 +0200] cupsdSetBusyState: Not busy'],
 'error_log_debug_logging_unset': True}
Page 9 (Locale issues):
{'printer_page_size': u'A4',
 'system_locale_lang': None,
 'user_locale_ctype': 'fr_FR',
 'user_locale_messages': 'fr_FR'}

A VERY VERY BIG thanks in advance for your help.

---

### Post by ninjahippie on 2011-04-13
Thanks for such a great writeup!  A little bit fiddly but I am really happy with my $58 printer/scanner.  Kudos to Cannon for actually supporting us with drivers and software.

---

### Post by Dracona on 2011-05-02
Thx for the info on getting the canon printer working,
as i am always looking for the easiest way to do things ( im lazy ) i chose to give [Loosehead01]("http://ubuntuforums.org/member.php?u=526267") suggestion a try first. i would like to say that it worked for me.
I have not tryied the scanner as of yet, but i am able to print from ubuntu now.
a BIG thank you for all the info and help you guys have offered.

---

### Post by Andy.C on 2011-05-09
Just wanted to say thanks for the guide and writeup. I can confirm that the Canon prints and scans via USB with my  HPs5701f machine (64 bit AMD processor) running 11.04 Natty. I am not running a wireless network so I didn't bother with the wireless setup. 

:KS:KS:KS:KS:KS

---

### Post by arguile on 2011-05-14
> **modsbyus said:**
> I would first try to reinstall. I'm on 10.10 and don't have any issues. If that doesn't work let me know.

I'm having the same issue that was mentioned a while ago:

I upgraded to Ubuntu 11.04 and now jobs will not print.  Jobs will spool correctly, register on the printer, but nothing will come out of the printer.  Everything was working correctly before the upgrade to 11.04.

Any ideas on what I should be checking for and how I can try to resolve the issue?

EDIT:
It's the PPD modifications that are causing the inability to print.  Has something changed in the way that cups handles the PPDs that the modifications cause a conflict?  Either way, it seems that I've found a resolution, but I'm unsure as to why it's happening.  haha

---

### Post by modsbyus on 2011-05-15
Remove the printer and reinstall using the ppd file to get the printer working. Beyond that im not sure i just upgraded last night and havent check the printer yet.

---

### Post by inameiname on 2011-05-16
I've been having issues with it printing as well on Natty. And on multiple installations. 

It installs fine, says it is printing, and then gives an error, and that's that.

I will look into the PPD as being the issue, but IDK.

---

### Post by sleepy3103 on 2011-07-07
Thank you modsbyus, great write up. Got my printer and scanner working on natty. 

  I have a question though. Does anyone know why it would work when I'm logged in, but not my gf? I put a check in publish printer and allow all users in server settings, and the scanner works on hers, but it won't print. 
 Thanks for the help.

---

### Post by Hurky on 2011-08-23
Thanks for the guide, installation was faster with my linux box as another W7 laptop using the HUGE CD installation...

But I noticed a problem, I cannot change the color settings to print in monocrome a certain job or default. In System > Admin > Printers > Job Options I change output-mode to monochrome but pressing Apply or OK button resets the option to color and the printer always print in color.  I can however print some documents in monochrome depending on the software I use for printing as some support changing color before sending the actual job to the printer itself.  But for example printing PDF with Document Viewer don't give you the option to change color mode...

Another question, is 600 DPI the lowest possible resolution ? I like to have an economy / draft mode using less ink for less-important documents...

Thanks !

---

### Post by inameiname on 2011-08-24
> **Hurky said:**
> Thanks for the guide, installation was faster with my linux box as another W7 laptop using the HUGE CD installation...

But I noticed a problem, I cannot change the color settings to print in monocrome a certain job or default. In System > Admin > Printers > Job Options I change output-mode to monochrome but pressing Apply or OK button resets the option to color and the printer always print in color.  I can however print some documents in monochrome depending on the software I use for printing as some support changing color before sending the actual job to the printer itself.  But for example printing PDF with Document Viewer don't give you the option to change color mode...

I'm with you here. I do not like having it only print in color all the time. That needs to be changed as most of the time I just don't need color, and even worse, the times when I do, I don't want my color to be wasted on making black.



ALSO, for those who may have had similar trouble as I was having my last few threads, on it just not printing, even though it did once upon a time ago, it was all resolved simply by reinstalling things. There must've been an update that disabled it, and I had to 'refresh' by reinstalling the printer drivers. Just an FYI, for those who might find similar woes.

---

### Post by paolora on 2011-08-31
hello,

same problems here...

I found this helpful link: [http://www.math.ucla.edu/~jimc/canon-mp495/](http://www.math.ucla.edu/~jimc/canon-mp495/)

bye

Paolo

---

### Post by silverstroller on 2011-10-10
Thanks for this brilliant and comprehensive answer. Glad to say it worked in Natty.

---

### Post by DavidS on 2011-10-22
I am trying to set up an MP495 on a 64-bit computer running Ubuntu 10.04.  It is tricky, considering that I am doing it remotely, for a friend who lives 300 miles away!

I have managed to get the printer recognized on the wifi network, using the excellent instructions in this thread.  I can ping the printer from the host computer, and cups recognizes the printer.

Unfortunately, when I try to print something, nothing much happens.  The Cups page shows 'MP495LAN(Idle, Accepting Jobs, Shared, Server Default)', but against the job, under "State" it shows 'stopped "/usr/lib/cups/filter/pstocanonij failed"'

What should I do to try to solve this problem?

David

---

### Post by jswhite on 2011-11-13
For those curious, I just wanted to confirm that this does in fact work with Oneiric. I did see some people reporting problems earlier with Natty, but it must've either been user error or they fixed whatever the problem was with the PPD's. I set everything up, changed the 2 PPD files to add new resolutions, and they all showed up just as they should when I restarted CUPS.

---

### Post by inameiname on 2011-11-14
> **jswhite said:**
> For those curious, I just wanted to confirm that this does in fact work with Oneiric. I did see some people reporting problems earlier with Natty, but it must've either been user error or they fixed whatever the problem was with the PPD's. I set everything up, changed the 2 PPD files to add new resolutions, and they all showed up just as they should when I restarted CUPS.

+1 for it working in Oneiric for me as well.

It actually works for me just fine in both Oneiric AND Natty. No better or worse. Personally, I did have one issue while using Natty, in which I had to occasionally reinstall the printer drivers after a Remastersys-backed-up live install on a wiped machine, even though it was installed in the backup image, but other than that, I can say it seems to work fine for both for me on multiple machines.



However, there is one thing I have yet to figure out: does anybody know if it is possible to set the printer itself to only print black and white? I know such a thing is often possible with most printers, but on the printer options for this one there doesn't seem to be a place where I can do that. I do know some programs have that option inside them, in which case it is just a matter of changing that setting to BW on them, but not all programs. Just curious.

---

### Post by buztay on 2011-11-16
have been trying to get mp495 working all day. 1.- after angryip tried to change ssid but got 'no reply' msg repeatedly, so left it at bjnpsetup.
2.- unable to load drivers.
have printer working on the windows side (computer partitioned btween ubuntu and pc)
but, after reviewing and trying the several (and apparently conflicting) install methods, no joy.
when trying to add printer from the sys-admin-printer, mp495 is recognized, but no drivers are on board, and although msg says drivers are available to download they won't, and i can't successfully open extracted drivers in home folder, trying to open drivers returns an error msg.
1st tried to setup w/ wireless, gave up and tried usb, and still no joy.
any help would be much appreciated, but plse make it step-by-step, as i don't understand what terms like yyy and code mean.
thanks

---

### Post by inameiname on 2011-11-17
> **buztay said:**
> have been trying to get mp495 working all day. 1.- after angryip tried to change ssid but got 'no reply' msg repeatedly, so left it at bjnpsetup.
2.- unable to load drivers.
have printer working on the windows side (computer partitioned btween ubuntu and pc)
but, after reviewing and trying the several (and apparently conflicting) install methods, no joy.
when trying to add printer from the sys-admin-printer, mp495 is recognized, but no drivers are on board, and although msg says drivers are available to download they won't, and i can't successfully open extracted drivers in home folder, trying to open drivers returns an error msg.
1st tried to setup w/ wireless, gave up and tried usb, and still no joy.
any help would be much appreciated, but plse make it step-by-step, as i don't understand what terms like yyy and code mean.
thanks


This was the method that worked for me. From what I recall, it is pretty much the same as what is mentioned at the beginning of this thread:

```

##################################################
# Use the 'MP495_Drivers.rar' stuff for easier   #
# installation (along with 'customizations.deb') #
##################################################

MP495 Wireless Printer/Scanner/Copier Installation Instructions:

    Get the Canon Pixma MP495 working in Ubuntu Maverick 10.10 and up
        (driver website: http://support-au.canon.com.au/P/search?model=PIXMA+MP495&menu=download&filter=0&tagname=g_os&g_os=Linux)

    1. Temporarily change Router's SSID to the printer's default SSID:
        Printer Defaults:
        SSID: BJNPSETUP
        IP ADDRESS: Automatic

    2. Activate the wireless lan on the printer, by either pressing Maintenance button on the printer 14-15 times, until you see a capital 'E' without the top line, OR by holding the Maintenance button for 5 seconds or so. If correctly done, and network is found, it shouldn't be blinking.

    3. Find printer's IP address
        Trendnet router shows ip address of it automatically
        If using AngryIPScanner, install, run it, change the ip range to include from 1 - 254 in the last octet, and then click start, to find IP address of printer. When it finishes look for an active connection with a Hostname like A001BF000000.local.
        The IP address given for that hostname is the IP address of your printer. Open Firefox and type that address in the address bar and press enter. From there you can configure you printer for the SSID, and encryption that you had on your router before the change, and set a static IP for the printer so you can manage it easily.
        After you change the SSID and encryption on the printer you will have to go back to your router and change the SSID and encryption back to what it was before so your printer can connect again.
        Now your network should be back the way it was and your printer should be connected

    ...Do the steps below for each computer you wish to use the printer on...

    4. Install both the printer and scanner drivers for it:
        cnijfilter-mp495series-3.40-1-deb and scangearmp-mp495series-1.60-1-deb folders
        for each folder, open a terminal in it and type:
        sudo ./install.sh
        follow the on-screen stuff, and choose the correct type of connection, usb or wireless

    5. Change the available resolutions for printing:
        Open another terminal and edit two postscript files for this printer:
        gksudo gedit /etc/cups/ppd/MP495LAN.ppd (gksudo gedit /etc/cups/ppd/Canon-MP495.ppd, if doesn't exist)
            Change:
            *OpenUI *Resolution/Output Resolution: PickOne
            .......whatever it says here......
            *CloseUI: *Resolution
            With:
            *OpenUI *Resolution/Output Resolution: PickOne
            *DefaultResolution: 4800dpi
            *Resolution 600dpi/600 DPI: "<</HWResolution[600 600]>>setpagedevice"
            *Resolution 1200dpi/1200 DPI: "<</HWResolution[1200 1200]>>setpagedevice"
            *Resolution 2400dpi/2400 DPI: "<</HWResolution[2400 2400]>>setpagedevice"
            *Resolution 2400dpi/4800 DPI: "<</HWResolution[2400 4800]>>setpagedevice"
            *Resolution 2400dpi/9600 DPI: "<</HWResolution[2400 9600]>>setpagedevice"
            *CloseUI: *Resolution
        gksudo gedit /usr/share/ppd/canonmp495.ppd
            Change:
            *OpenUI *Resolution/Output Resolution: PickOne
            .......whatever it says here......
            *CloseUI: *Resolution
            With:
            *OpenUI *Resolution/Output Resolution: PickOne
            *DefaultResolution: 4800dpi
            *Resolution 600dpi/600 DPI: "<</HWResolution[600 600]>>setpagedevice"
            *Resolution 1200dpi/1200 DPI: "<</HWResolution[1200 1200]>>setpagedevice"
            *Resolution 2400dpi/2400 DPI: "<</HWResolution[2400 2400]>>setpagedevice"
            *Resolution 2400dpi/4800 DPI: "<</HWResolution[2400 4800]>>setpagedevice"
            *Resolution 2400dpi/9600 DPI: "<</HWResolution[2400 9600]>>setpagedevice"
            *CloseUI: *Resolution
        Save and close gedit.
        Now restart the cups service.
            With:
            sudo service cups restart    # in Ubuntu 10.10 and I think 10.04 too
            Or:
            sudo /etc/init.d/cups restart    # in previous verions
        You can now print with resolutions ranging from 600 DPI to 9600 DPI!

    6. To use the scanner, open terminal and type:
        scangearmp
        To make it easier, just make a launcher for such

```

---

### Post by Hurky on 2011-12-31
Hi, I've installed these drivers correctly a few month ago but still then I can only print in full colour and un normal ink quality. 

What I cannot do is print in grayscale and/or in low quality draft as I print a lot of mass copies that use a lot of ink and don't need to be that good quality prints.


I've done the modifications to the config file so that 600 DPI option gets avialable but this is still too good quality for drafts.

Regards,

---

### Post by Hurky on 2011-12-31
Well I researched myself a bit (should do it before asking I know :rolleyes:
Here is the solution for freyscale and economy prints:

Found it in [**This thread**]("http://ubuntuforums.org/showthread.php?t=1656821") from user [**ashv3524**]("http://ubuntuforums.org/showpost.php?p=10604116&postcount=10").

For completion, simply edit both your ppd files, in my case /etc/cups/ppd/Canon-MP495.ppd and /usr/share/ppd/canonmp495.ppd to contain these lines:

> **ashv3524 said:**
> Thanks to Yann2's advice, I was able to make grayscale and quality settings work. To get this to work for you in Lucid 10.04, first follow the original poster antonyhand's steps to install the MG6100 series printer drivers. If you choose all the defaults and do a network (wireless) install, you should have a printer called MG6100LAN in your System-> Administration-> Printing view. Also, you should have a file MG6100LAN.ppd in /etc/cups/ppd. Edit this PPD file and replace the following lines

```

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 600dpi
*Resolution 600dpi/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*CloseUI: *Resolution

*OpenUI *ColorModel/Color Model: PickOne
*DefaultColorModel: rgb
*ColorModel rgb/RGB: "<</cupsColorOrder 0/cupsColorSpace 1/cupsCompression 0/cupsBitsPerColor 8>>setpagedevice"
*CloseUI: *ColorModel

```

with

```

*OpenUI *Resolution/Output Resolution: PickOne
*DefaultResolution: 300dpi
*Resolution 300dpi/300 dpi: "<</HWResolution[300 300]>>setpagedevice"
*Resolution 600dpi/600 dpi: "<</HWResolution[600 600]>>setpagedevice"
*Resolution 1200/1200 dpi: "<</HWResolution[1200 1200]>>setpagedevice"
*Resolution 2400/2400 dpi: "<</HWResolution[2400 2400]>>setpagedevice"
*CloseUI: *Resolution

*OpenUI *ColorModel/Color Model: PickOne
*DefaultColorModel: rgb
*ColorModel rgb/RGB: "<</cupsColorOrder 0/cupsColorSpace 1/cupsCompression 0/cupsBitsPerColor 8>>setpagedevice"
*ColorModel RGB16/RGB 16-bit: "<</cupsColorOrder 0/cupsColorSpace 1/cupsCompression 0/cupsBitsPerColor 16>>setpagedevice"
*ColorModel Black/Grayscale Fast: "<</cupsColorOrder 0/cupsColorSpace 3/cupsCompression 0/cupsBitsPerColor 1>>setpagedevice"
*ColorModel Gray/Grayscale: "<</cupsColorOrder 0/cupsColorSpace 0/cupsCompression 0/cupsBitsPerColor 8>>setpagedevice"
*CloseUI: *ColorModel

*OpenUI *CNQuality/Quality: PickOne
*DefaultCNQuality: 4
*CNQuality 2/High: "2"
*CNQuality 3/Normal: "3"
*CNQuality 4/Economy: "4"
*CloseUI: *CNQuality

*OpenUI *CNGrayscale/Grayscale: Boolean
*DefaultCNGrayscale: True
*CNGrayscale True/Yes: True
*CNGrayscale False/No: False
*CloseUI: *CNGrayscale


```

Save the edited PPD file and you should now be able to print in grayscale and economy (those have been set as defaults).

After editing simply restart CUPS service with:
```
sudo service cups restart
```
 And that's it, now you can print in low resolution 300DPI, grayscale, and economy mode :P :)


Good luck !

---

### Post by krakra on 2011-12-31
Thank you guys (specially to modsbyus and also Hurky). 
I sucessfully installed my new MG6250 with your help. Before finding this howto, i was afraid that I'll have to use the stinkin' win$ again :(
The basic printing and scanning works, but I'll still need to test everything. 
THANKS!!! :)

---

### Post by ogenchev on 2012-01-13
Thanks a million! Made my day! :)

---

### Post by trubadour on 2012-02-02
i followed the instructions and now are able to get a scan out of the machine using a wifi connection. 

but to any attempt of getting a print out of it, the only response are the wandering lines on the display - meaning it gets the task but nothing more. 

i assume it is a problem with the drivers - the printer being not able to "understand" what ubuntu tries to tell it. the printer itself is able to make copys - so I assume it is not a problem with the paper or the ink or what. It does not show any error-signs. It just does not respond anymore after the processing-symbol at the display.

I am using 11.10, which means I had to use the command 
 
sudo system-config-printer

to add the printer. Do you have any idea how I could get on and get it working?

---

### Post by Cole3G on 2012-02-23
While searching for the printers IP address, it wasn't detecting it.
I figured this was because I had it setup with windows.

But, after reading the online-manual I discovered that you can reset all wireless settings in the printer by going to the "t" looking letter (the one after the G-shaped letter) and pressing Color.

This will reset all previous settings related to the wi-fi, in the printer.
I was then able to detect the printer with IPscan.

Just posting this if anyone else experienced the same problem.

---

### Post by jwstolk on 2012-04-01
Thank you, I was able to scan with the pixma495 on Ubuntu 11.04 using these instructions.
My only problem is that the scanner only works with scangearmp, which does not work well on the eee-pc-900 1024x600 pixels screen.
On every click the program switches between the top half and the bottom half of the dialog. Hitting the "scan" button must be done by guessing where it is going to be after the click. This also makes dragging a box to define the scan area impossible, but full-page scanning works, so I just crop it in Gimp.

---

### Post by beepeezy1 on 2012-04-20
hi all!

very informative thread--i have managed to get the printer working in precise-lts, but i cannot get the scanner to recognize.  upon entering the scangearmp command in the terminal--i receive this morsel of joy:
"Cannot find available scanners. Cable may be disconnected or scanner may be turned off. Check the scanner status and then try again."

While I'm not really that much of a noob when it comes to ubuntu, i'm still learning the ropes in command based procedures.

I desperately need some help, guys! ](*,)

thanx in advance.

---

### Post by venator260 on 2012-04-23
Mine did the same thing. When you click away from that dialog, a second came up for me that allowed me to click "find scanners" I did that and it detected my scanner and I was able to scan.

Edit: The option that you want is "Update Scanner List"

---

### Post by beepeezy1 on 2012-04-30
> **venator260 said:**
> Mine did the same thing. When you click away from that dialog, a second came up for me that allowed me to click "find scanners" I did that and it detected my scanner and I was able to scan.

Edit: The option that you want is "Update Scanner List"

Have done that already, and it still does not detect the scanner. Is there a chance that the driver is installed in a not-so-kosher location? I've followed all of the terminal commands.:???:

---

### Post by MADJX on 2012-05-17
Thank you for information on ppd (Grayscale).
Really great thread :KS

---

### Post by Krakois on 2012-05-17
Hi,

Unable to get Canon MP495 scanner to work in Ubuntu 12.04. I installed the scanner drivers as per your instructions. Installation went fine, but scanner won't work. Here's what happens after executing "scangearmp" in the terminal window.

A ScanGear notice window pops up informing me that ScanGear cannot find scanners.
I click ok.
Another window called "Select Scanner" pops up.
I click "Update Scanner List".
ScanGear searches for scanners for some time, then times-out saying it can not find available scanners.

How can I get "scangearmp" to work with Canon MP495 in my 32-bit system? Any help is appreciated.

By the way, the printer functionality works fine.

---

### Post by allg on 2012-05-19
In Ubuntu 12.04 the wireless-printer works out of the box by Printers->Add new printer->Network Printer. Then selecting the right printer model and it is important using URI **lpd://[printer-ip]:515** :)

Search for network-printers didn't find anything :(

---

### Post by dmaxwell81 on 2012-06-19
I can confirm that the scanner no longer works with these instructions/drivers.  Note that before Ubuntu 12.04 it DID work just fine, I had this thread bookmarked for that reason but now its unable to detect the scanner, exactly as the other posters have said. 

Printer seems fine, but now I have to boot into Windows to do scanning :(.

---

### Post by Sinsinnati on 2012-06-27
Thank you, Modsbyus. This worked perfectly on my PIXMA MP499 + 10.04LTS combo.

Printer and scanner are both working splendidly now.

---

### Post by tamiveldura on 2012-07-05
> **trubadour said:**
> i followed the instructions and now are able to get a scan out of the machine using a wifi connection. 

but to any attempt of getting a print out of it, the only response are the wandering lines on the display - meaning it gets the task but nothing more. 

i assume it is a problem with the drivers - the printer being not able to "understand" what ubuntu tries to tell it. the printer itself is able to make copys - so I assume it is not a problem with the paper or the ink or what. It does not show any error-signs. It just does not respond anymore after the processing-symbol at the display.

I am using 11.10, which means I had to use the command 
 
sudo system-config-printer

to add the printer. Do you have any idea how I could get on and get it working?


Aside from needing the sysconfig command this is the problem I'm having straight out of the box. I click print and I get wandering lines. 

I've downloaded the drivers but they cannot see the printer either over wifi or USB.  :confused:

I'm extremely new at linux so any help is appreciated.

---

### Post by Hairyloon on 2012-08-31
I have just bought one of these printers, partly on the strength of this thread, and was pleasantly surprised to find it worked OK pretty much straight out of the box (I downloaded the drivers from Canon).
At least, it does on USB.  I rather naively assumed that I could connect direct to it through Wi-Fi, but the instructions say it does not support Ad-hoc networks.
I assume that this is true, but I thought it worth an ask in case anyone has found a workaround to it.

---

### Post by dmaxwell81 on 2012-11-16
Could the OP please update this?  Ive tried a few different setups, using the newer drivers, and I still cannot get the scanner to work.

---

### Post by pdc on 2012-11-16
hi dmaxwell81;

to use the scanner, Canon supply a programme called scangearmp

you can get it from here

[http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/PIXMA_MP495.aspx?DLtcmuri=tcm:14-822924&page=1&type=download](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/PIXMA_MP495.aspx?DLtcmuri=tcm:14-822924&page=1&type=download)

it comes down as a .tar file

........ but archive manager is there to help you .......

.....so as you click on the download button, you can either "open with archive manager" or save file ....... 

.....if you select "open with archive manager"

.....you get a view like in the thumbnail below....

..click on the debian.tar.gz file and open with archive manager and you get a debian package ..

.....left click on the debian package ..... gdebi installer should leap in and offer to install.......let it ...........

...now to open scangearmp ....copy and paste the command below into a terminal

> [COLOR="Red"]scangearmp[/COLOR]

you can do that each time you scan or create a "launcher" 

[http://followthegeeks.com/how-to-manually-create-application-launcher-in-ubuntu-12-04-unity/](http://followthegeeks.com/how-to-manually-create-application-launcher-in-ubuntu-12-04-unity/)

....here's how to create a launcher..............

......it probably needs some interpretation so post back as needed ...............

---

### Post by gtr225 on 2012-11-17
Thank you very much for this post, it helped me get my MP495 working on Ubuntu 12.10

---

### Post by pdc on 2012-11-17
by chance on line: 

........great! .........enjoy!

---

### Post by Balthazar_Droid on 2013-02-17
> **Cole3G said:**
> While searching for the printers IP address, it wasn't detecting it.
I figured this was because I had it setup with windows.

But, after reading the online-manual I discovered that you can reset all wireless settings in the printer by going to the "t" looking letter (the one after the G-shaped letter) and pressing Color.

This will reset all previous settings related to the wi-fi, in the printer.
I was then able to detect the printer with IPscan.

Just posting this if anyone else experienced the same problem.

Thank-you!! I thought I was going crazy. I could not get the damn thing to connect for anything. Got her all set up now.

---

### Post by brons2 on 2013-05-14
Sorry to dig up this old thread, but it might help someone else.  On my MP495 printer I was not able to connect to it via WiFi with Ubuntu 12.04 LTS at all until I connected to the web server on the printer's ip address, clicked on Other Settings in the left hand column, and set LPR Service Notification to ON.  It had been set OFF.  Once I changed that setting, it showed up in the list of network printers automagically somehow.  It then tried to download an older driver (5.0.1) which was weird but then when I canceled out of that and manually chose the driver from the list, it used 5.2.8 and printing seems to work fine so far.

I have not tried scanning as of yet.

---

### Post by scbingham on 2013-05-23
Great thread & still relevant.
Set my mp495 up today on 12.04 LTS. Scan & printing working well.:D

Only problems I had was the printer not attaching to the router, then it 'just decided to'. Easy to pick out the ip & MAC address via the router but also found it with Angry IP Scanner.
Also couldn't get the scangearmp install script to run so just installed the two .debs which are in the packages directory, via the Software Centre.

Happy days!

---

### Post by HiImTye on 2013-05-23
in 12.10 I haven't gotten the scanner to work in Ubuntu, but as a workaround I use XP in VirtualBox and scan there. printing works perfectly fine

---

### Post by -=gr!n=- on 2013-06-21
[LIST]
[*]Delete all canon programs (cnijfilter, scangearmp) 
[*]Go to System -> Administration -> Printing 
[*]Add a printer 
[*]Choose &#8220;Network Printer&#8221; 
[*]Choose "LPD/LPR Host or Printer" 
[*]In the host field, put the IP adress of your printer (ex. 192.168.0.2) 
[*]Then choose &#8220;Probe&#8221; 
[*]At &#8220;Queue&#8221;, select &#8220;ps&#8221; 
[*]Click on &#8220;Forward&#8221; 
[*]Select printer from database (Canon -> PIXMA MP495) 
[*]Add the printer! 
[/LIST]
[http://blog.widodh.nl/tag/mp495/](http://blog.widodh.nl/tag/mp495/)

---

### Post by D8r4bwQ on 2013-08-05
Greetings - and WooHoo!!!  Hope it works for your Canon printer/system, too.
Been using Ubuntu since Koala, and getting help form the forum - but THIS discovery made me register and make my first post in order to share and give back!
After a year and a half of struggling to get my Canon ImageClass D420 to work with 64-bit Ubuntu, I can report both success and GREAT NEWS!
Thank you all for the help and suggestions in the past - got it to work with 32-bit versions, and limited success after much tribulation with 64-bit.

NOW! (August 5, 2013)  It was so easy, my jaw dropped. Didn't even need terminal.
1) Downloaded the driver package from [Canon]("http://usa.canon.com/cusa/support/consumer/printers_multifunction/imageclass_series/imageclass_d420") (first browse to page for your printer). For my D420 they now have version 2.7 (June 2, 2013).
2) Right-click on downloaded file in your file manager and open with "Archive Manager".  They have a 32-bit and 64-bit folder.  Each of these has a folder for RPM and Debian (yeah - no need to convert!).  Open the Debian folder.
3) Right-click on the cndrvcups-common file first and open with "Ubuntu Software Manager"; click "Install".
4) Repeat Step 3 for the condrvcups-UFR2 file.
5) Turn on the printer, go to settings manager for printers, click add and wait for list to appear.
6) At the top of my listed options was * Canon blah-blah * randon-stuff * "connected to USB".  I almost picked the second choice cuz it looked better, but selected #1. 
7) It worked!!  Selected "Test Print" and it actually PRINTED.
I'll follow up on this and report on the scanner later - but don't see much hope for that.

Moderators - I wasn't sure whether to post in this mega-thread or start a new one - your choice to bump or not.

Xubuntu Ted
RH Linux --> Ubuntu --> Lubuntu --> Mint XFCE --> Xubuntu (Home Sweet Home!)
Still using various versions of Ubuntu, Lubuntu, and Mint (in combination) on three other computers.
Primary: Asus M4A785-M; AMD Phenom 9850 Quad; 4GB 6400 DDR2; Xubuntu 13.04

---

### Post by EBWQNHD on 2013-08-05
well done; 

so you used the Canon UFR driver that covers a big number of their printers; thanks for the details of what you did;

_______________________________

for the scanner side of things; Sane is the open source area for scanners

[http://www.sane-project.org/](http://www.sane-project.org/)

for the Canon ImageClass D480 one gets

[http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON) (if you search on D480)

.........so one can only hope the D420 is recognised as well; sane is the back-end and xsane is the front-end; if you have those installed

_____________________________________________________

so let us know how it goes but I would hope this would work for you

---

