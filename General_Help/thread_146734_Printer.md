---
title: "Printer"
date: 2006-03-18
forum: General Help
---

### Post by terranz on 2006-03-18
I have replaced my printer with a new one, a Epson CX3700

Anyone know where I could get drivers or instruction for getting ubuntu to print to it?

---

### Post by todak on 2006-03-18
You can try this link. 
[http://linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX3700](http://linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX3700)
It will show a compatible printer driver that you can choose under the printing manager in Ubuntu.
Hope this helps:D

---

### Post by learning curve on 2006-03-18
Try the Epson website to see if they have a linux driver available.  If not then e-mail there technical support team for answers.

"If you strike me down I shall become more powerful than you can possibly imagine."  Obewan

Hope this helped you.  Learning Curve!:D

---

### Post by terranz on 2006-03-18
Thanks for the link, I'm having a look.

---

### Post by terranz on 2006-03-19
I have this page
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)

My problem is I don't know which ones I need and they are source and rpm

---

### Post by Peter41az on 2006-03-19
this should help you...

[http://www.avasys.jp/english/linux_e/dl_spc.html](http://www.avasys.jp/english/linux_e/dl_spc.html)

you can also download gutenprint, which is the successor to gimp-print, which supports the printer, and possibly the scanner under sane

---

### Post by terranz on 2006-03-19
that's the beginning point of the link I posted in post 5

I don't know how to install rpms in a deb system

---

### Post by spearfish on 2006-03-19
I'm not very good at this, but I am prettu sure you want the .rpm files

once you get it, you might need to un-tar the rpm's too.  (uncompress)

Then, you should read the README file.  Hopefully they have one which includes install instructions.  It would be stuff you type into the terminal window, like:

tar -xvf whateverTheDriverNameIs.tar.gz

rpm -ivh epsonSomething.src.rpm

Then, in Ubuntu, try to install the printer with: System->Administration->Printing

info on tar is at:
[http://www.gnu.org/software/tar/](http://www.gnu.org/software/tar/)
[http://www.washington.edu/computing/unix/tar.html](http://www.washington.edu/computing/unix/tar.html)

info on rpm is at:
[http://www.rpm.org/RPM-HOWTO/use.html](http://www.rpm.org/RPM-HOWTO/use.html)
[http://www.tldp.org/LDP/lame/LAME/linux-admin-made-easy/using-rpm.html](http://www.tldp.org/LDP/lame/LAME/linux-admin-made-easy/using-rpm.html)

good luck!

p.s.  I agree... go to Epson's web site.  Click on SUPPORT and read all the stuff they have on the page.  I'm sure there are install instructions there.

---

### Post by Peter41az on 2006-03-19
on that one i sent you, theres a debian package in there, you can install debs easy.

---

### Post by terranz on 2006-03-19
[QUOTE=Peter41az]on that one i sent you, theres a debian package in there, you can install debs easy.[/QUOTE]

I wish you were right.  I've looked and can't find one.

---

### Post by terranz on 2006-03-19
[QUOTE=spearfish]I'm not very good at this, but I am prettu sure you want the .rpm files

once you get it, you might need to un-tar the rpm's too.  (uncompress)

Then, you should read the README file.  Hopefully they have one which includes install instructions.  It would be stuff you type into the terminal window, like:

tar -xvf whateverTheDriverNameIs.tar.gz

rpm -ivh epsonSomething.src.rpm

Then, in Ubuntu, try to install the printer with: System->Administration->Printing

info on tar is at:
[http://www.gnu.org/software/tar/](http://www.gnu.org/software/tar/)
[http://www.washington.edu/computing/unix/tar.html](http://www.washington.edu/computing/unix/tar.html)

info on rpm is at:
[http://www.rpm.org/RPM-HOWTO/use.html](http://www.rpm.org/RPM-HOWTO/use.html)
[http://www.tldp.org/LDP/lame/LAME/linux-admin-made-easy/using-rpm.html](http://www.tldp.org/LDP/lame/LAME/linux-admin-made-easy/using-rpm.html)

good luck!

p.s.  I agree... go to Epson's web site.  Click on SUPPORT and read all the stuff they have on the page.  I'm sure there are install instructions there.[/QUOTE]

I'm new to a debian based distro but I do know that rpms need to be converted to deb somehow before installing.  Epson only has links to other sites when you click on linux drivers.

---

### Post by Peter41az on 2006-03-19
if you pull down the pull down menus in that page, theres one there for a debian install...

---

### Post by terranz on 2006-03-19
[QUOTE=Peter41az]if you pull down the pull down menus in that page, theres one there for a debian install...[/QUOTE]

I was about to say "what pull down menus?" and then I saw what you're talking about.  If you select debian it still takes you to a page full of rpm files.

-------------------------------------

Does anyone speak french? This looks like information on how to install those rpms but it's in french.
[http://forum.ubuntu-fr.org/viewtopic.php?pid=170877](http://forum.ubuntu-fr.org/viewtopic.php?pid=170877)

---

### Post by terranz on 2006-03-19
[QUOTE=terranz]Does anyone speak french? This looks like information on how to install those rpms but it's in french.
[http://forum.ubuntu-fr.org/viewtopic.php?pid=170877](http://forum.ubuntu-fr.org/viewtopic.php?pid=170877)[/QUOTE]

I shouldn't have put this below a dashed line.  It's not a signiture.

---

### Post by NZ-Wanderer on 2006-03-22
Hokay, I have a rather interesting question, and since it is about this printer (CX3700) I figured I would leave it here instead of starting a new thread, hope that's ok :)

I just bought the CX3700, and have it connected to my XP machine..
What I would like to be able to do is connect through the network to the printer from Ubuntu machine to the XP machine..

Without getting too technical can someone tell me what I need to do..

What I did so far was:

Goto setup new printer, tell setup it a network printer and that it's a windows Printer (SMB)
It finds the host
It finds the printer (epson)
It then gives me a list of printers however the CX3700 is NOT in that list of Epson printers, so the only thing I can do is exit back out by hitting cancel...

Can anyone help me please?? do I have to install anything??

(Please not too technical, a do this, do that would be perfect :) :) )

---

### Post by terranz on 2006-03-23
I now have the driver installed and here's how.

Go here [http://www.avasys.jp/english/linux_e/dl_spc.html](http://www.avasys.jp/english/linux_e/dl_spc.html) and fill in the form which will take you here [http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do) (you can't go straight here though).

Download pips-scx3700-cups-2.6.3-1.i386.rpm in the cups section at the top of the page.  Easiest if you download it to your desktop.

Make sure to install **alien** from synaptic package manager.

In the terminal type this, each line seperately.
```
cd Desktop
alien -d pips-scx3700-cups-2.6.3-1.i386.rpm
sudo dpkg -i pips-scx3700-cups-2.6.3-1.i386.deb
```

and then the driver is installed.

Then go to Printing which is under Administration on the System menu.  It will auto detect a local printer but has network location too.

](*,)  Now I have a different problem.  I try to print something and the printer tool says printer stopped and gives me the option to unpause printer but it goes back to paused.
See attached.

NZ-Wanderer where did you buy yours, dicksmith? harvey norman?

---

### Post by NZ-Wanderer on 2006-03-23
Got mine from Dick Smith ($149)
Pity I won't have time to try to get it running through the network this weekend tho, gots to take my computers out to Wigram for a display...

Ohwell, hopefully by the time I get back my networking problem and your paused problem will both be answered :)

[QUOTE=terranz]NZ-Wanderer where did you buy yours, dicksmith? harvey norman?[/QUOTE]

---

### Post by NZ-Wanderer on 2006-03-26
** Points up 3 messages.... **

Anyone had any bright ideas over the weekend on how I can solve my little network printer problem??

---

### Post by terranz on 2006-03-26
I don't think anyone is watching anymore ](*,)

---

### Post by NZ-Wanderer on 2006-03-26
Yea, it starting to look like we got forgotton... ](*,) ](*,) 

I have progressed a little since last week, I followed your instructions and now can setup my printer through the network, and Ubuntu has the drivers, but when I try to print a test page I get a "A4 test page has been sent to Stylus-CX3700", but nothing happens, the printer on the windows machine doesn't print...

[QUOTE=terranz]I don't think anyone is watching anymore ](*,)[/QUOTE]

---

### Post by terranz on 2006-03-26
[QUOTE=NZ-Wanderer]Yea, it starting to look like we got forgotton... ](*,) ](*,) 

I have progressed a little since last week, I followed your instructions and now can setup my printer through the network, and Ubuntu has the drivers, but when I try to print a test page I get a "A4 test page has been sent to Stylus-CX3700", but nothing happens, the printer on the windows machine doesn't print...[/QUOTE]

Smells like the same problem as I have.  I've found something in a blog and that person used LPR (which sounds familar but I'd have to look for).

> Printing to a Epson AcuLaser C900 over the network in Ubuntu
Submitted by Karin on Fri, 2005-04-22 19:41. Ubuntu

Today the next challenge arised. A year and a half ago, we bought a 'cheap' Epson color laser printer, that only supported Windows printing. It's hooked up to the Windows 2000 PC that is also the router and firewall for the network I'm on. Back then I didn't think it much of a problem that it was basically a 'windows only' printer, but today it hit me... It would be really annoying if I couldn't print.
I fired up the printing dialog (System->Administration) and tried "Add new printer". All the AcuLasers where there, except of course the C900, the only one who doesn't know any 'real' printer languages....
So, on to Google. Through the Linux Printing.org page on the C900 I found a reference to the ALC900-cups project at SourceForge. The Readme included in the tar file was pretty clear, and the process reasonably painless. I did have to install some packages to get the install script to continue all the way, but they where all available through the Ubuntu repositories. The packages I had to install where:
a2ps
psutils (which contains things like psnup, psresize, psmerge, psselect, which the ACL900-cups package needed)

After that the install script downloaded everything else it needed (things like pipsplus packages).

So it was all installed. The readme told me to run lpadmin -p -v smb://192.168.25.23/AcuLaserC900
The last part I think should be the printer's name on the Windows host but I'm not sure. In any case, this didn't work well for me. The printer appeared in the printing dialog, but trying to run a test page gave me an error: "Printing to 'Aculaser900' failed with error code: 1286
is the printer paused ?"
I posted a message to the Forum of the project at SourceForge, and the owner of the project responded very quickly, where I could look for error messages (/var/log/alc900.log and /var/log/cups/error_log). The alc900.log didn't show much in the way of errors, and the cups error log gave this: "I [22/Apr/2005:12:10:02 +0200] print_job: destination 'Aculaser900' is not accepting jobs."

Not much clue there. My boyfriend pointed out to me I could try adding the printer as an LPR printer instead. So I went to the print dialog, selected LPR printer, filled in the Windows machine's IP and selected the C900 driver (which, undoubtedly thanks to the acl900-cups package was now in the list) and tried a test page. No error this time, and it appeared in the Windows Machine's queue, but it didn't print.... For the heck of it I tried printing an email... and it printed! It printed!!

So, happy again, another challenge succesfully completed, full printing capabilities under Ubuntu with a 'Windows only' printer. Ubuntu++ !!


---

### Post by NZ-Wanderer on 2006-03-26
Hmmmm, found this

 Short for line printer daemon/line printer remote, a printer protocol that uses TCP/IP to establish connections between printers and workstations on a network. The technology was developed originally for BSD UNIX and has since become the de facto cross-platform printing protocol.

The LPD software typically is stored in the printer or print server and the LPR software must be installed in the client device. The LPR client sends the print request to the IP address of the LPD printer/server, which in turn queues the file and prints it when the printer becomes available.

========================
Can't see anything in Ubuntu about it tho...

---

### Post by terranz on 2006-03-26
That probably won't help, not me anyway.

I've left a message here for what looks like a similar problem.
[http://ubuntuforums.org/showthread.php?p=864968#post864968](http://ubuntuforums.org/showthread.php?p=864968#post864968)

---

### Post by NZ-Wanderer on 2006-03-26
oops, missed a step, will get back to you :)

---

### Post by terranz on 2006-03-26
Which step?

---

### Post by NZ-Wanderer on 2006-03-26
step in trying to setup this LPR thing...

Nope, that didn't work...

Installed LPR to the windows machine, then setup new printer on Ubuntu, but it still just sits there looking stupid and not printing anything...

---

### Post by terranz on 2006-03-27
I'm going to try the sudo thing.

---

### Post by terranz on 2006-03-27
I did it, the sudo thing

```

sudo  cp /etc/cups/cupsd.conf  /etc/cups/cupsd.conf.backup
sudo gedit /etc/cups/cupsd.conf
sudo /etc/init.d/cupsys restart

```

Change RunAsUser to NO

Now it's no longer paused but now I have print jobs that just sit in the queue. Surely now we've done the hard work, someone can come along and help finish off.

---

### Post by NZ-Wanderer on 2006-03-27
Glad you managed to get to the next step.. :)

---

### Post by terranz on 2006-03-27
I have a new screenshot

---

### Post by terranz on 2006-04-05
I have the problem solved :cool: 

After trying everything I read incuding installing the latest gimp print which I had to alien from rpm.  I also went to a good forum that I frequent [http://pressf1.co.nz](http://pressf1.co.nz) but I found the solution on the linspire forums.

Select USB Printer # 1 from connections

Select Epson C64 gimp print from the drivers list.

---

### Post by NZ-Wanderer on 2006-04-05
and thanks to you I have now got the network problem solved as well...

I used the Connection "Windows SMB Printer" in network, and just did the second part of what you did and changed the driver to "C64" and hey presto, it is now printing from the Ubuntu Machine to the Windows machine. :) :)

Thank you very much :)

---

### Post by terranz on 2006-04-05
You probably felt as happy as I did when it spat out a page.  Now I have a linux distro that does everything I need except my games which I'll reboot to windows for.

I'll write something for this.

---

### Post by NZ-Wanderer on 2006-04-21
Well I all unhappy again :(

Installed Dapper.. - Promptly lost my printer..

Sees the network, connects to the network, printer won't print, says printing page 1, then says it pausing.. - Printer does nothing....

The list of printers has changed and I dunno what to do about it...

next to CX3700 it says:

Stylus CX3700 - CUPS+Gutenprint v5.0.0-rc2

Next to C64 it says:

Stylus C64 - CUPS+Gutenprint v5.0.0-rc2

There is no-where to choose gimpprint like we were using :( :(

[QUOTE=terranz]You probably felt as happy as I did when it spat out a page.  Now I have a linux distro that does everything I need except my games which I'll reboot to windows for.
I'll write something for this.[/QUOTE]

---

### Post by WelterPelter on 2006-04-21
Every time I get my printer working, the daily Dapper update nukes it again. 

I'm hoping I figure this out. I want to keep updating.

---

### Post by terranz on 2006-04-23
so why the move to dapper?

What does it offer that breezy doesn't?

I was hoping that Dapper would give me better printer support.  Have you tried c64 reguardless of what it doesn't say?

---

### Post by NZ-Wanderer on 2006-04-23
well I really like the look of dapper, it got cool new features (one of which I didcovered this morning and that is it got a auto deb installer, plus it seems a lot faster than Breezy :) )

yup, tried the C64, but it just said printing and then pause... - Printing seems to be the only thing I can't get to work now...

---

### Post by terranz on 2006-04-23
faster is always a bonus.  Have you downloaded the newest gimpprint and installed it?

---

### Post by NZ-Wanderer on 2006-04-23
Ummm nope..- gimpprint is already installed according to synaptic... (5.0.0 RC2 )

[QUOTE=terranz]faster is always a bonus.  Have you downloaded the newest gimpprint and installed it?[/QUOTE]

---

### Post by openmind on 2006-04-23
Have you checked that the lp module is loaded? (lsmod)

---

### Post by arundel on 2006-04-23
I'm having very similar problems....

---

### Post by NZ-Wanderer on 2006-04-24
Ummm I dunno :)

Found your message about it in another thread so did a 

```
lsmod | less
```

and lp didn't show up - so looked in /dev but lp0 isn't in there either.. - so typed:

```
modprobe lp
```
 into root terminal since normal terminal gave me an error and then did another lsmod | less and this was in the list at the top:

Module                  Size  Used by
lp                     11844  0

however, printer on windows machine still didn't print (Ubuntu said it was printing, but then immediatly went to pause), and when I rebooted Dapper, that line had disappeared again from lsmod | less

Hope that makes sense, I only good at following instructions, I really don't know what I talking about or doing most of the time :)

[QUOTE=openmind]Have you checked that the lp module is loaded? (lsmod)[/QUOTE]

---

### Post by openmind on 2006-04-24
yes, apparently (I didn't know this at the time) you have to add 'lp' to '/etc/modules' for it to reload at boot up.

After loading 'lp' did you go and set up your printer again?

---

### Post by NZ-Wanderer on 2006-04-24
yup, but still no go....

I at the stage now I've tried soo many things I am pondering reinstalling dapper just to get rid of all the stuff I must of changed :)

I do notice quite a lot of others are having the same type of problem trying to print through network, and a bug report is now marked as major
[https://launchpad.net/distros/ubuntu/+bug/39484/+index](https://launchpad.net/distros/ubuntu/+bug/39484/+index)

Kinda wierd tho, I would have assumed that Printing would have been one of the first things to be got working correctly in a new version, but I guess it can't be all that important.. :)

---

### Post by NZ-Wanderer on 2006-04-25
UPDATE:

I now have printer Epson CX3700 working properly in Dapper :)

As I mentioned above, there was a bug report filed... - Now Sorren suggested in that bug report to: "you can add our repository to your sources.list:
deb [http://www.linux2go.dk/ubuntu](http://www.linux2go.dk/ubuntu) dapper main"

So I did that, then installed all the samba stuff from that repository and now I have a perfect printer through my network..

---

### Post by terranz on 2006-07-19
I took the wait and I installed dapper a few days ago and my CX3700 works there 'out of the box'

---

