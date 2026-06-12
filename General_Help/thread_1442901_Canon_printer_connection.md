---
title: "Canon printer connection"
date: 2010-03-30
forum: General Help
---

### Post by flyfishingphil on 2010-03-30
I have the Toshiba L350-S5933, Intel Pentium Dual CPU T3400 @ 2.16GHZ, 3GB RAM, 32 bit OpSys, BIOS Ver 2.10.

Installed 9.10 as a dual boot.

Printer shows as default printer but have tried with both the wireless network and the USB connection but can't get it to print. Any ideas?

---

### Post by flyfishingphil on 2010-03-30
Toshiba Laptop L350-S5933, Intel Pentium Dual CPU T3400 @2.16 GHz, Ram 3.o GB, ACPI x86 32 bit OpSys, Canon MP560, Dual Boot installed Karmic (Vista other OS), Canon is logged into wireless network using Actiontec.

Ubuntu shows the printer as the default printer. Listed as 
Make & Model: Canon Pixma MP500 - cups+ Gutenprint v5.4
Under devices: Network Printer: Canon-MP560-series_00-1E-8F-5E-53-82

Have tried print test page-no print
Tried OO.org page test print-no print

I went to Canon Asia and downloaded/installed the x86 Linux drivers update.

Can't figure out why it recognizes the printer, but won't "talk" to it.

Brand new so don't want to have to replace it!

Any ideas on how to get these to "talk" to each other?](*,)

Interesting additional findings. Tried hooking it up via USB. It printed a test page from OpenOffice with that hooked up but then printed the Ubuntu test page using wireless. Now I'm even more confused!

---

### Post by quadproc on 2010-03-30
> **flyfishingphil said:**
> 
Printer shows as default printer but have tried with both the wireless network and the USB connection but can't get it to print. Any ideas?
Hm.  I wonder if this is the same problem that I found:

My situation is that I have a Canon i860 printer which I have used on a parallel port for years with no problems.  I also have an HP J2591A print server which I would really like to use with this printer, but the printer completely ignores the print server.  Yet the print server works fine on other printers.  I also tried a D-Link DP301P+ (I think that I got that number right) which is also a print server and found that the printer completely ignores it also, even though the D-Link works with other printers.

I tried to contact Canon about this problem and was ignored.

I am suspecting that Canon did something like putting an anti-glitch filter on their interface port which requires an unusually long strobe pulse, and that the print servers furnish a strobe pulse which is IEEE-1284 compliant.  In other words, the printer is not 1284 compliant.

If you have any success in getting your printer to work then I would appreciate reading about it.  Thanks.

quadproc

---

### Post by Daveth on 2010-03-30
you haven't actually told us which model Canon printer it is:confused:

---

### Post by flyfishingphil on 2010-03-30
> **Daveth said:**
> you haven't actually told us which model Canon printer it is:confused:
Sorry about that. As I spend more time here I notice more things I need to do in the posts. The printer is a Canon MP560.

Looked to see if I could get help in hardware and laptops and posted some other info there. So far no assist replies.

Here are the problems I've found:

On wireless the printer will print the Ubuntu test page, with the color bars, but will not print something from OpenOffice.

Plug in the USB cord and it will print what is sent from OpenOffice.

Have tried everything I can think of including resetting the wireless set-up (about 5 times) but cannot get it to accept anything but the Ubuntu test page on wirless.

Totally confused now!

---

### Post by flyfishingphil on 2010-03-30
Don't see one I tried to post earlier so will try again.

Have a Toshiba Laptop L350-S5933 and an Atheros AR5BXB63 Wi-Fi and the network set up using Actiontec, Canon MP560 printer.

Problems: Ubuntu recognizes MP560 as default printer. On wireless it will print the Ubuntu test page but won't print from OpenOffice. On USB it will print from OpenOffice, but not Ubuntu. Also Xsane Image doesn't recognize the MP560.

After trying about everything I can think of to try I was looking around on the 'net and came across one that said there were updates at Canon Asia that made it work perfectly. I went and downloaded all of the updates I could find that had MP560 in the label. These are:
cnij-MP560series-3.20-1-i386-rpm.tar.gz
scangearamp-mp560series-140.1-i386-rpm.tar.gz
cnijfilter-mp5560series-1.40-1-i386-deb.tar.gz

Questions: Is there a different way to do the rpm.tar.gz and the deb.tar.gz?

I have them, untouched, in the download file and opened in a folder on desktop. How do I "install" these to see if it corrects the problems?

Simple step-by-step works best. (I know where Terminal is, but that's about as far as it goes!:redface:)

Any assist appreciated.

---

### Post by uRock on 2010-03-31
Do you mean this one? [http://ubuntuforums.org/showthread.php?p=9051423#post9051423](http://ubuntuforums.org/showthread.php?p=9051423#post9051423) Or this one? [http://ubuntuforums.org/showthread.php?t=1442901](http://ubuntuforums.org/showthread.php?t=1442901)

---

### Post by cariboo on 2010-03-31
Please don't create multiple threads on the same subject. I have merged your 3 threads.

---

### Post by flyfishingphil on 2010-03-31
Apologies again. It didn't show when I came back to look for answers so I figured I forgot to post. I'll get this figured out before long.

Now back to the post. Don't know what I did but it seems to be printing OK now on the wireless side to OpenOffice. That's important, but it still won't scan using Xsane. I downloaded an update file, scangearamp-mp560series-1.40-1-i386-rpm.tar.gz but don't remember how to "install" the update. 

Anbody have a step-by-step guide on doing this? Any special needs for an rpm.tar.gz update?

Thanks again.

---

### Post by klytu on 2010-03-31
> **flyfishingphil said:**
> Apologies again. It didn't show when I came back to look for answers so I figured I forgot to post. I'll get this figured out before long.

Now back to the post. Don't know what I did but it seems to be printing OK now on the wireless side to OpenOffice. That's important, but it still won't scan using Xsane. I downloaded an update file, scangearamp-mp560series-1.40-1-i386-rpm.tar.gz but don't remember how to "install" the update. 

Anbody have a step-by-step guide on doing this? Any special needs for an rpm.tar.gz update?

Thanks again.

Since Ubuntu is based on Debian, I think you'll find it simpler to install using a .deb package for scangearamp. You can download one for the MP560 here:

[http://software.canon-europe.com/software/0037286.asp](http://software.canon-europe.com/software/0037286.asp)


The package you'll download is MP560_Linux_scangear.tar Open that with Archive Manager (should open automatically if you double-click the file) and extract the file scangearmp-mp560series-1.40-1-i386-deb.tar.gz .  Now double-click scangearmp-mp560series-1.40-1-i386-deb.tar.gz and extract the contents into your home directory. You should see a new directory named "scangearmp-mp560series-1.40-1-i386.deb" Go into that directory and right-click "install.sh", selecting "Run in terminal". (You may be prompted for your password during the installation.)  When this completes open a terminal and type ```
scangearmp

``` The scangear interface should open and you should be able to use your scanner.

FYI, I installed scangear for the Canon PIXMA MX330  last weekend following steps similar to the procedure I outlined for you and scanning works perfectly for me. If you have any difficulty, I'll try to help. Please keep in mind that my ability to assist you may be limited by the fact that I use a different model than yours.

---

### Post by flyfishingphil on 2010-03-31
Many thanks Klytu!!! (Recognize the image on your name.) Printed out your steps and will now try to "install" it. Will post a solved if I get it to work. Thanks again.

Followed instructions. Typed in scangearmp in terminal and screen showed "Command not found" Now what?

---

### Post by flyfishingphil on 2010-03-31
Although it doesn't seem to want to scan I messed around a little, while waiting for a response, and found it's really easy to scan to a USB flash and transfer to the computer. A little more time consuming but I'm sure the world won't end because of that.

If you've heard the quote: "If anything can go wrong, it will!" I think it was written for me when it comes to "confusers". 

Cheer up, things could get worse! I did and they did!

Guess this one is closed!

---

### Post by klytu on 2010-03-31
> **flyfishingphil said:**
> Many thanks Klytu!!! (Recognize the image on your name.) Printed out your steps and will now try to "install" it. Will post a solved if I get it to work. Thanks again.

Followed instructions. Typed in scangearmp in terminal and screen showed "Command not found" Now what?

Sorry you're having difficulty. If you're not at your wit's end yet, we might be able to figure what's going wrong. Assuming neither you nor I made a typing error (If I typed the command incorrectly, I apologize. I'm at work and doing this from memory, but I'm pretty sure I got it right), the "Command not found" error means that either scangearmp didn't install or the directory where scangearmp lives is not in your PATH (the list of directories where Ubuntu's terminal shell looks for comands). On my machine, scangearmp is installed in /usr/bin. You could try typing this in a terminal: ```
/usr/bin/scangearmp
``` If that doesn't work also try: ```
/usr/local/bin/scangearmp
``` If neither of those tries bring joy, you can search your directory to see if scangearmp was installed at all with: ```
sudo updatedb
``` Wait for that to finish, then do ```
locate scangearmp
```
In you can find where scangearmp is installed, it's a simple matter to set-up a clickable short-cut; I can walk you through how to do that if you don't know how.

If scangearmp is not found by locate, that means it never installed properly. If that's the case, let me know and we can try to troubleshoot the installation.

---

### Post by flyfishingphil on 2010-03-31
More than happy to keep trying, even if it's only to learn more about how Linux works.

Tried first 2 searchs you listed above and found nothing. Went to "sudo updatedb" all it did was this: 

flyfishingphil@flyfishingphil-laptop:~$ sudo updatedb
flyfishingphil@flyfishingphil-laptop:~$ 

The file "installsh" is in the home directory. Does that need to be moved somewhere else, or do I just need to do another download to see if something was missing from this one?

Another question just popped in. Do I use the same password for the sudo updatedb search as I use to sign in, or od I need to do something else to get to that point?

---

### Post by klytu on 2010-03-31
> **flyfishingphil said:**
> More than happy to keep trying, even if it's only to learn more about how Linux works.

Tried first 2 searchs you listed above and found nothing. Went to "sudo updatedb" all it did was this: 

flyfishingphil@flyfishingphil-laptop:~$ sudo updatedb
flyfishingphil@flyfishingphil-laptop:~$ 


That's what should happen after updatedb finishes. Did you then do: ```
locate scangearmp
``` and get no result? 

> **flyfishingphil said:**
> The file "installsh" is in the home directory. Does that need to be moved somewhere else, or do I just need to do another download to see if something was missing from this one?

It's OK if "install.sh" is in your home directory provided that's where you also extracted all the rest of the files from "scangearmp-mp560series-1.40-1-i386-deb.tar.gz" But if you really extracted all of the files in the way I suggested in my first post, the extraction should have created a new sub-directory named "scangearmp-mp560series-1.40-1-i386-deb" within your home directory and "install.sh" should be located within that sub-directory. In other words, the "install.sh" that's in your home directory might not be the same one that's in the sub-directory (for example, it might be the one that you used to install your printer driver files earlier ...)

> **flyfishingphil said:**
> Another question just popped in. Do I use the same password for the sudo updatedb search as I use to sign in, or od I need to do something else to get to that point?

Yes, its the same password. I'll check in with you in about an hour or so when I get home from work and hopefully will figure this out (if you haven't sorted it out by then yourself).

---

### Post by flyfishingphil on 2010-03-31
Klytu,
Figured out I had only taken the "installsh" to the home directory. Took the whole package this time and followed the installation steps. Appeared to install this time. I'll shut down the system for a few, let it "recover" then restart it and see if it will work via the wireless. (That's one of the steps I forget to do when doing stuff like this: After installing shut down the computer, start it back up and let it finish what it was doing. Understand it may take up to 5 minutes before it "recognizes" the printer. 4:13 PDT now. Back in a bit.

Shut down for a few, restarted, ran the "locate scangearmp" (didn't copy all of the stuff I sent to the trash) here's the "report" I got back:
/home/flyfishingphil/Desktop/Ubuntu files/scangearmp-mp560series-1.40-1-i386-deb
/home/flyfishingphil/Desktop/Ubuntu files/scangearmp-mp560series-1.40-1-i386-deb/packages
/home/flyfishingphil/Desktop/Ubuntu files/scangearmp-mp560series-1.40-1-i386-deb/packages/scangearmp-mp560series_1.40-1_i386.deb
/home/flyfishingphil/Downloads/scangearmp-mp560series-1.40-1-i386-deb(2).tar.gz
/home/flyfishingphil/Downloads/scangearmp-mp560series-1.40-1-i386-deb.tar.gz
/home/flyfishingphil/scangearmp-mp560series-1.40-1-i386-deb/install.sh
/home/flyfishingphil/scangearmp-mp560series-1.40-1-i386-deb/packages
/home/flyfishingphil/scangearmp-mp560series-1.40-1-i386-deb/packages/scangearmp-common_1.40-1_i386.deb
/home/flyfishingphil/scangearmp-mp560series-1.40-1-i386-deb/packages/scangearmp-mp560series_1.40-1_i386.deb
/usr/bin/scangearmp
/usr/bin/scangearmp-mp560series-pkgconfig.sh
/usr/lib/gimp/2.0/plug-ins/scangearmp
/usr/share/scangearmp
/usr/share/doc/scangearmp-common
/usr/share/doc/scangearmp-mp560series
/usr/share/doc/scangearmp-common/LICENSE-scangearmp-1.40EN.txt.gz
/usr/share/doc/scangearmp-common/LICENSE-scangearmp-1.40FR.txt.gz
/usr/share/doc/scangearmp-common/LICENSE-scangearmp-1.40JP.txt.gz
/usr/share/doc/scangearmp-common/LICENSE-scangearmp-1.40SC.txt.gz
/usr/share/doc/scangearmp-common/changelog.Debian.gz
/usr/share/doc/scangearmp-common/copyright
/usr/share/doc/scangearmp-mp560series/LICENSE-scangearmp-1.40EN.txt.gz
/usr/share/doc/scangearmp-mp560series/LICENSE-scangearmp-1.40FR.txt.gz
/usr/share/doc/scangearmp-mp560series/LICENSE-scangearmp-1.40JP.txt.gz
/usr/share/doc/scangearmp-mp560series/LICENSE-scangearmp-1.40SC.txt.gz
/usr/share/doc/scangearmp-mp560series/changelog.Debian.gz
/usr/share/doc/scangearmp-mp560series/copyright
/usr/share/locale/cs/LC_MESSAGES/scangearmp.mo
/usr/share/locale/da/LC_MESSAGES/scangearmp.mo
/usr/share/locale/de/LC_MESSAGES/scangearmp.mo
/usr/share/locale/el/LC_MESSAGES/scangearmp.mo
/usr/share/locale/es/LC_MESSAGES/scangearmp.mo
/usr/share/locale/fi/LC_MESSAGES/scangearmp.mo
/usr/share/locale/fr/LC_MESSAGES/scangearmp.mo
/usr/share/locale/hu/LC_MESSAGES/scangearmp.mo
/usr/share/locale/id/LC_MESSAGES/scangearmp.mo
/usr/share/locale/it/LC_MESSAGES/scangearmp.mo
/usr/share/locale/ja/LC_MESSAGES/scangearmp.mo
/usr/share/locale/ko/LC_MESSAGES/scangearmp.mo
/usr/share/locale/nb/LC_MESSAGES/scangearmp.mo
/usr/share/locale/nl/LC_MESSAGES/scangearmp.mo
/usr/share/locale/pl/LC_MESSAGES/scangearmp.mo
/usr/share/locale/pt/LC_MESSAGES/scangearmp.mo
/usr/share/locale/ru/LC_MESSAGES/scangearmp.mo
/usr/share/locale/sv/LC_MESSAGES/scangearmp.mo
/usr/share/locale/th/LC_MESSAGES/scangearmp.mo
/usr/share/locale/tr/LC_MESSAGES/scangearmp.mo
/usr/share/locale/zh/LC_MESSAGES/scangearmp.mo
/usr/share/locale/zh_TW/LC_MESSAGES/scangearmp.mo
/usr/share/scangearmp/pixmaps
/usr/share/scangearmp/pixmaps/image_curve_h_grad_226.xpm
/usr/share/scangearmp/pixmaps/image_curve_v_grad_226.xpm
/var/lib/dpkg/info/scangearmp-common.conffiles
/var/lib/dpkg/info/scangearmp-common.list
/var/lib/dpkg/info/scangearmp-common.md5sums
/var/lib/dpkg/info/scangearmp-common.postinst
/var/lib/dpkg/info/scangearmp-common.postrm
/var/lib/dpkg/info/scangearmp-mp560series.list
/var/lib/dpkg/info/scangearmp-mp560series.md5sums
/var/lib/dpkg/info/scangearmp-mp560series.postinst
/var/lib/dpkg/info/scangearmp-mp560series.postrm

Does this translate to properly installed? Checked the scan function at the printer and it only shows a usb connection. What do I use on the computer to do a scan/receive a scan?

---

### Post by klytu on 2010-03-31
> **flyfishingphil said:**
> Klytu,
Figured out I had only taken the "installsh" to the home directory. Took the whole package this time and followed the installation steps. Appeared to install this time. I'll shut down the system for a few, let it "recover" then restart it and see if it will work via the wireless. (That's one of the steps I forget to do when doing stuff like this: After installing shut down the computer, start it back up and let it finish what it was doing. Understand it may take up to 5 minutes before it "recognizes" the printer. 4:13 PDT now. Back in a bit.

Shut down for a few, restarted, ran the "locate scangearmp" (didn't copy all of the stuff I sent to the trash) here's the "report" I got back:
/home/flyfishingphil/Desktop/Ubuntu files/scangearmp-mp560series-1.40-1-i386-deb
/home/flyfishingphil/Desktop/Ubuntu files/scangearmp-mp560series-1.40-1-i386-deb/packages
/home/flyfishingphil/Desktop/Ubuntu files/scangearmp-mp560series-1.40-1-i386-deb/packages/scangearmp-mp560series_1.40-1_i386.deb
/home/flyfishingphil/Downloads/scangearmp-mp560series-1.40-1-i386-deb(2).tar.gz
/home/flyfishingphil/Downloads/scangearmp-mp560series-1.40-1-i386-deb.tar.gz
/home/flyfishingphil/scangearmp-mp560series-1.40-1-i386-deb/install.sh
/home/flyfishingphil/scangearmp-mp560series-1.40-1-i386-deb/packages
/home/flyfishingphil/scangearmp-mp560series-1.40-1-i386-deb/packages/scangearmp-common_1.40-1_i386.deb
/home/flyfishingphil/scangearmp-mp560series-1.40-1-i386-deb/packages/scangearmp-mp560series_1.40-1_i386.deb
/usr/bin/scangearmp
/usr/bin/scangearmp-mp560series-pkgconfig.sh
/usr/lib/gimp/2.0/plug-ins/scangearmp
/usr/share/scangearmp
/usr/share/doc/scangearmp-common
/usr/share/doc/scangearmp-mp560series
/usr/share/doc/scangearmp-common/LICENSE-scangearmp-1.40EN.txt.gz
/usr/share/doc/scangearmp-common/LICENSE-scangearmp-1.40FR.txt.gz
/usr/share/doc/scangearmp-common/LICENSE-scangearmp-1.40JP.txt.gz
/usr/share/doc/scangearmp-common/LICENSE-scangearmp-1.40SC.txt.gz
/usr/share/doc/scangearmp-common/changelog.Debian.gz
/usr/share/doc/scangearmp-common/copyright
/usr/share/doc/scangearmp-mp560series/LICENSE-scangearmp-1.40EN.txt.gz
/usr/share/doc/scangearmp-mp560series/LICENSE-scangearmp-1.40FR.txt.gz
/usr/share/doc/scangearmp-mp560series/LICENSE-scangearmp-1.40JP.txt.gz
/usr/share/doc/scangearmp-mp560series/LICENSE-scangearmp-1.40SC.txt.gz
/usr/share/doc/scangearmp-mp560series/changelog.Debian.gz
/usr/share/doc/scangearmp-mp560series/copyright
/usr/share/locale/cs/LC_MESSAGES/scangearmp.mo
/usr/share/locale/da/LC_MESSAGES/scangearmp.mo
/usr/share/locale/de/LC_MESSAGES/scangearmp.mo
/usr/share/locale/el/LC_MESSAGES/scangearmp.mo
/usr/share/locale/es/LC_MESSAGES/scangearmp.mo
/usr/share/locale/fi/LC_MESSAGES/scangearmp.mo
/usr/share/locale/fr/LC_MESSAGES/scangearmp.mo
/usr/share/locale/hu/LC_MESSAGES/scangearmp.mo
/usr/share/locale/id/LC_MESSAGES/scangearmp.mo
/usr/share/locale/it/LC_MESSAGES/scangearmp.mo
/usr/share/locale/ja/LC_MESSAGES/scangearmp.mo
/usr/share/locale/ko/LC_MESSAGES/scangearmp.mo
/usr/share/locale/nb/LC_MESSAGES/scangearmp.mo
/usr/share/locale/nl/LC_MESSAGES/scangearmp.mo
/usr/share/locale/pl/LC_MESSAGES/scangearmp.mo
/usr/share/locale/pt/LC_MESSAGES/scangearmp.mo
/usr/share/locale/ru/LC_MESSAGES/scangearmp.mo
/usr/share/locale/sv/LC_MESSAGES/scangearmp.mo
/usr/share/locale/th/LC_MESSAGES/scangearmp.mo
/usr/share/locale/tr/LC_MESSAGES/scangearmp.mo
/usr/share/locale/zh/LC_MESSAGES/scangearmp.mo
/usr/share/locale/zh_TW/LC_MESSAGES/scangearmp.mo
/usr/share/scangearmp/pixmaps
/usr/share/scangearmp/pixmaps/image_curve_h_grad_226.xpm
/usr/share/scangearmp/pixmaps/image_curve_v_grad_226.xpm
/var/lib/dpkg/info/scangearmp-common.conffiles
/var/lib/dpkg/info/scangearmp-common.list
/var/lib/dpkg/info/scangearmp-common.md5sums
/var/lib/dpkg/info/scangearmp-common.postinst
/var/lib/dpkg/info/scangearmp-common.postrm
/var/lib/dpkg/info/scangearmp-mp560series.list
/var/lib/dpkg/info/scangearmp-mp560series.md5sums
/var/lib/dpkg/info/scangearmp-mp560series.postinst
/var/lib/dpkg/info/scangearmp-mp560series.postrm

Does this translate to properly installed? Checked the scan function at the printer and it only shows a usb connection. What do I use on the computer to do a scan/receive a scan?

Looks to me as if scangearmp installed properly. In the original "MP560_Linux_Scangear.tar" file you downloaded there is a file named "guidemp560series-sd-1.40-1_en.tar.gz" that you can extract (similar to the way you extracted the scangearmp files). This contains a guide to how to use the software to scan.

You can also just try typing (in a terminal): ```
scangearmp
``` put something to scan on the platen, click "Preview" and hopefully all is well! :-)

---

### Post by flyfishingphil on 2010-03-31
Scanner went active when I clicked "Preview". Is there a way to set that up for the scanning without having to do "terminal" "scangearmp" ? Can't find the guide you mentioned. Even looked at the original download file copy and don't see it there. Maybe one at the Canon site?

---

### Post by flyfishingphil on 2010-03-31
Tried the preview and it brought it in on wireless. Good there. Looked thru the downloads and couldn't find the user guide files. Would that be a file you could send to me? 

Have to figure out where to save the scans to.

Have you set up Xsane, or using something else for the scanning? Is there a way to do it without having to do the Terminal "scangearmp" everytime I want to scan?

(All the bouncing around forgot to "refresh" the page and didn't see my earlier reply. Sorry about the repeat.

---

### Post by klytu on 2010-03-31
> **flyfishingphil said:**
> Scanner went active when I clicked "Preview". Is there a way to set that up for the scanning without having to do "terminal" "scangearmp" ? Can't find the guide you mentioned. Even looked at the original download file copy and don't see it there. Maybe one at the Canon site?

I've attached a copy of the guide. 

You can make a shortcut to scangearmp by simply right-clicking your desktop and selecting "Create Laucher". "Type" is Application.  For NAME Type in "ScanGear" or whatever you like. For COMMAND just type in scangearmp. Then click OK. You should be able to double-click the shortcut and launch scangearmp.

---

### Post by klytu on 2010-03-31
> **flyfishingphil said:**
> Tried the preview and it brought it in on wireless. Good there. Looked thru the downloads and couldn't find the user guide files. Would that be a file you could send to me? 

Have to figure out where to save the scans to.

Have you set up Xsane, or using something else for the scanning? Is there a way to do it without having to do the Terminal "scangearmp" everytime I want to scan?

(All the bouncing around forgot to "refresh" the page and didn't see my earlier reply. Sorry about the repeat.

I didn't set up xsane for my PIXMA MX330 yet. Since I'm using an older  Ubuntu package (Hardy Heron 8.04), I would need to compile an updated version of xsane from source code to use with my scanner. I was lazy last weekend and just wanted to get up and running quickly. scangearmp worked well for my purposes so I didn't bother setting up xsane. I think the version of xsane that's included with the upcoming 10.04 release of Ubuntu may work with my scanner. However, you might want to keep using scangearmp. I'm not sure how xsane interfaces with a wireless scanner.

---

### Post by flyfishingphil on 2010-03-31
What do I open that file with?

---

### Post by klytu on 2010-03-31
> **flyfishingphil said:**
> What do I open that file with?

Just right-click it and select "Extract Here"(second choice from the bottom of the context menu that appears when you right-click the file)

---

### Post by flyfishingphil on 2010-03-31
Doesn't offer that in 9.10 but I still have it open. I'll print everything so I have it avail and try to "polish" mys use. It scanned fine but I'll try to fine tune it.

Thanks a whole lot for the assist. Lots of threads on Canon problems but most answers recommend replacing it with a different one. Saved me a lot of cost and frustration. Maybe you could put together a package for Ubuntu that others could download and have everything they need to find the Linux packages for their printers and get operational.

Guess I can rally call it closed now.

Thanks again.

---

### Post by klytu on 2010-03-31
> **flyfishingphil said:**
> Doesn't offer that in 9.10 but I still have it open. I'll print everything so I have it avail and try to "polish" mys use. It scanned fine but I'll try to fine tune it.

Thanks a whole lot for the assist. Lots of threads on Canon problems but most answers recommend replacing it with a different one. Saved me a lot of cost and frustration. Maybe you could put together a package for Ubuntu that others could download and have everything they need to find the Linux packages for their printers and get operational.

Guess I can rally call it closed now.

Thanks again.

Your welcome - glad I could help! If you want to try something a bit more advanced to extract the guide (in a terminal), navigate to wherever you downloaded the file then type: ```
tar jxvf guidemp560series-sd-1.40-1_en.tar.bz2

``` That should extract the file for you. 

Multi-function printers can be somewhat tricky to set up; especially if it's a fairly new model.Things are simpler if you have a separate printer and scanner. Ubuntu handles a lot of hardware automagically just not ours, unfortunately. Good luck with your unit!

---

