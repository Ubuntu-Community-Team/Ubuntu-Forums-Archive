---
title: "SiS mirage 3 graphics solution w/e I got is here..."
date: 2010-08-02
forum: General Help
---

### Post by rational-lover on 2010-08-02
Well, I Experimented informations available on the net and got solution for my sis mirage 3 graphics.Its really worked wonderfully.I hope It will work for you too.If you get problem for finding driver mail me; I will send you the new link for driver and how to install the driver again.My email address is; [email]sbinod2004@gmail.com,binod.narayan.sethi@gmail.com[/email]
 
Driver link: [http://www.megaupload.com/?d=OCCEQ5OQ](http://www.megaupload.com/?d=OCCEQ5OQ)
 
Here is the Steps you have to follow;
1.Login as root administrator.
2.Copy the given 3 files named "sis671_drv.la","sis671_drv.lai","sis671_drv.so" to 
 
/usr/lib/xorg/modules/drivers/
 
3.Copy the xorg.conf file given in the folder to /etc/X11/
4.If you don't want to copy the xorg.conf file and you want to make change yourself then edit 
 
/etc/X11/xorg.conf as follows:
 
-----------------------------------------------------------
Section "Device"
Identifier "Configured Video Device"
Driver "sis671"
EndSection
Section "Monitor"
Identifier "Configured Monitor"
Horizsync 31.5-61.0
Vertrefresh 50-60
EndSection
Section "Screen"
Monitor "Configured Monitor"
SubSection "Display"
Modes "1024x768"
Virtual 1024 768
Depth 24
EndSubSection
Identifier "Default Screen"
Device "Configured Video Device"
EndSection
-----------------------------------------------------------
I tried for 1024x768 screen resolution you can try as per your requirements with your monitor supporting resolutions and refreshing rate by editing.
5.Restart the machine and set your desired display resolution;Thats it.......
6.If you are failure then try to fix it again; If it does not work take help from the Internet :popcorn:
7.If you got xserver failure dont worry in command line interface login as root and type:
 
$sudo dpkg-reconfigure -phigh xserver-xorg
 
It will restore your xorg.conf to default and give you another chance ;)
8.Then you can try again and again.;)
9.If you get failure keep trying again and again, Dont worry google is there........BTW I experimented in Ubantu Ultimate edition.
10.Hope it will work for you; Keep Enjoying if it works.I felt better when I got this simple solution.:D
 
:KSThanx to all OPEN Source Community and helping friends on the Internet.:D

---

