---
title: "Intermittent CUPS startup at boot Lucid Lynx"
date: 2010-05-05
forum: General Help
---

### Post by kentechy on 2010-05-05
I have been having intermittent printing problems and am using Lucid Lynx at present.  I have nailed it down to CUPS not starting properly on each boot.  If it starts properly I will have my printer show up and it works.  On some boots it is not there.  This is in spite of it being listed in the boot-up manager.  I have tried changing the priority higher and lower with no effect.  If I boot up and the printer is missing I can start the CUPS service and the printer will then show up and print fine.  I have been using Turbo-print for several versions of Ubuntu and am using it now as well.  I also use a wireless print server.  Could it be related to a delayed wireless network connection on some boots?  I am pretty novice at Ubuntu but I can get around in Terminal pretty well.  Any help would be appreciated.  It seems like it should be a simple fix...yeah right!!  Thanks in advance.  

:p

---

### Post by Souris on 2010-05-05
Hi, same problem here !!!

On bootup CUPS is often not loaded, but sometimes it is and then it works.

I don't use any print server, my CUPS server is on localhost.
I have a network printer (HP LaserJet 1320n) connected via HP Jetdirect : socket://192.168.0.126:9100
Everything is wired, no Wifi.

It is a vanilla lucid (new install)

Help apreciated!!!

---

### Post by Morbius1 on 2010-05-05
I have a feeling that john newbuntu's post is going to be very useful until this problem is resolved: [http://ubuntuforums.org/showpost.php?p=9226244&postcount=7](http://ubuntuforums.org/showpost.php?p=9226244&postcount=7)

In his example he talks about automounting a remote samba share but you might try removing his "mount -t cifs" entry and replace it with:

**service cups restart**

---

### Post by MM0AMV on 2010-05-05
And here also.
I have no network, just computer hard wired into a router.
Sometimes CUPS works, sometimes it doesnt.
I also have Cool'n'Quiet selected in my bios to give me CPU scaling.
Sometimes it works, and sometimes it doesn't.
It all worked flawlessly under 9.10 Karmic.
Maybe, I should abandon 10.4 and go back to 9.10.

Wallace

---

### Post by kentechy on 2010-05-07
Nobody seems to know how to fix CUPS problems in lucid lynx.  CUPS starts up on about every other boot, on my laptop, and sometimes Blue-tooth does the same thing.  I can manually start CUPS when it fails and then printing is fine.  Anybody out there have a fix?  This is an old problem.  Thanks.

---

### Post by powerofpi on 2010-05-07
sudo apt-get install bum

Then open the boot up manager and make sure that bluetooth and cups services are selected for startup and see if your problem persists.

---

### Post by lisati on 2010-05-07
Threads merged

---

### Post by kentechy on 2010-05-07
> **powerofpi said:**
> sudo apt-get install bum

Then open the boot up manager and make sure that bluetooth and cups services are selected for startup and see if your problem persists.

I already have bum installed and I see CUPS listed in the boot up manager.  I have even messed with the priorities in the boot up manager but CUPS stills fails to load about half of the time.  I can go into the boot up manager and start it successfully and then my printer works fine.  I can also start it manually from Terminal.  So, even though bum is trying to start it, sometimes it fails...

---

### Post by MM0AMV on 2010-05-08
Well, I uninstalled 10.4LTS and re-installed it but the problems remain.
The intermittent startups seem to be CUPS, Bluetooth, hddtemp and Cool'n'Quiet.
The mysterious thing is, that all four either startup or all four fail to start.
If you get one you get all four.
I suspect that they all live together in a folder which Lynx is intermittently missing during boot, but I am a Linux noob and wouldn't know where to start looking or what to do once I got there.
Anyone any thoughts??

Wallace

---

### Post by MM0AMV on 2010-05-11
After many hours of searching forums and reading up on CUPS failure to start problems, it seemed (to me anyway), that the problem was  caused by some other service/s loading at the same time during boot and stopping CUPS starting for some reason.
So I started switching services off and re-booting to see what happened. Eventually the finger of guilt pointed at Conky, which I use to monitor my temps/fan speeds etc. Switch off Conky, boot is perfect, I get CUPS, Bluetooth, Cool'n'Quiet and hddtemp all running. Switch it on, and the problem returns.
Many reboots later and my system, without Conky, is running flawlessly.
Oh happy days!

---

### Post by scorpio74 on 2010-05-14
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/554172](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/554172)

is related to this issue.

---

### Post by tacantara on 2010-05-28
This problems appears to be a launchpad "in the works" issue, with no immediate solution on the horizon.  Accepting that, I decided to write a simple script that will run the command

```
 sudo service cups start 
```I placed a launcher on the top panel that will run the script.  If I go to print, and my network printer isn't given as a choice, I just click the launcher and attempt to print again.  This isn't a long-term solution, but it beats opening a terminal and typing in the command every time I need to start the CUPS service.

If you'd like a copy of the script, drop me a PM.

---

### Post by Amzer zo on 2010-05-29
Works if you have root privileges.
Wouldn't it work to start a cron job shortly after boot to restart services (if needed)?  I believe that would work for users who don't have root privileges, trouble is that I am not sure how to do this...

---

### Post by tacantara on 2010-05-29
The use of the sudo command gives the user temporary root privileges, thus it can be executed without going into full root mode.

---

### Post by Morbius1 on 2010-05-29
Assuming it's not starting at boot rather than stopping randomly after you boot you could try to force a restart in **/etc/rc.local**:

Add [COLOR=#0000ff]service cups restart[/COLOR] to **/etc/rc.local**  ::
[INDENT]> #!/bin/sh -e
#
#  rc.local
#
# This script is executed at the end of each multiuser  runlevel.
# Make sure that the script will "exit 0" on success or any  other
# value on error.
#
# In order to enable or disable this  script just change the execution
# bits.
#
# By default this  script does nothing.

[COLOR=Blue]**service  cups restart**[/COLOR]

exit 0Just make sure to place the line before the "exit 0" statement.

[/INDENT]

---

### Post by M4xC4v413r4 on 2010-05-29
> **tacantara said:**
> This problems appears to be a launchpad &quot;in the works&quot; issue, with no immediate solution on the horizon.  Accepting that, I decided to write a simple script that will run the command

```
 sudo service cups start 
```I placed a launcher on the top panel that will run the script.  If I go to print, and my network printer isn't given as a choice, I just click the launcher and attempt to print again.  This isn't a long-term solution, but it beats opening a terminal and typing in the command every time I need to start the CUPS service.

If you'd like a copy of the script, drop me a PM.

 That script will still ask for the root password, right?

  Is there any way of making it not ask for it? Because i'm having this problem in my little sister's PC and she will just forget the password if i give it to her. 

 Anyway, can you send me the script either way? Thanks

---

### Post by bumparocky on 2010-07-12
thanks,

I have been experiencing the exact same problem (on 2 desktops and 1 laptop) and I too am a conky user....has the root conflict been determined yet? workaround to make them co-habit peacefully?...rocky

---

### Post by Morbius1 on 2010-07-12
I truly believe the problem is upstart. Services are being started in the wrong order or started before the network is up. I posted this workaround in other posts and it seems to work: [http://ubuntuforums.org/showthread.php?p=9405854#post9405854](http://ubuntuforums.org/showthread.php?p=9405854#post9405854)

Create a script:[FONT=sans-serif]
[/FONT]    ```
gksu gedit /etc/network/if-up.d/cups 
```With this content:
     ```
#!/bin/sh
service  cups restart 
```Save the file and make it executable:
    ```
sudo chmod +x /etc/network/if-up.d/cups 
```Reboot

---

### Post by libssd on 2010-07-12
I'm trying to further my own knowledge with this. It seems like a script in either rc.local or /etc/network/if-up.d/cups would do the job, although the latter seems cleaner.

But I don't understand why the cups script would be in if-up.d, rather than if-down.d. :?: 

It seems like the purpose of the script is to run if cups is down, rather than up, so shouldn't it be in if-down.d?

---

### Post by Morbius1 on 2010-07-12
> But I don't understand why the cups script would be in if-up.d, rather  than if-down.d. :?: 

It seems like the purpose of the script is to run if cups is down,  rather than up, so shouldn't it be in if-down.d?     Any script placed in /etc/network/if-up.d will execute only after the network is up. That's when you want the CUPS server to start. Anything in if-down.d will execute only after the network is shut down.

---

### Post by courtier on 2010-07-25
I am no expert but
On installing Lucid on our ubuntu computers one of the three could not find the network printer. The system told me that CUPS was not running. I opened synaptic and reinstalled CUPS. On restart the computer found the printer and installed it, and has continued to do so since. Too simple? probably but it definitely worked here.

---

### Post by BrianB2 on 2010-07-25
My wife has been having this problem since upgrading to lucid - sometimes her list of printers is empty (cups didn't start at boot, but NOTHING is logged), and sometimes cups starts OK and she finds her printers.

This can always resolved without rebooting with:
```
sudo /etc/init.d/cups start
```

I installed the temporary circumvention (add lo:0 to /etc/network/interfaces) described in [https://bugs.launchpad.net/bugs/604283]("https://bugs.launchpad.net/bugs/604283"), and since making that change the printers have been located on all 5 of the system boots.

---

