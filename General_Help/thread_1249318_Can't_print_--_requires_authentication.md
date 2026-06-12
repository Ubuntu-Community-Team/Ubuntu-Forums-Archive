---
title: "Can't print -- requires authentication"
date: 2009-08-25
forum: General Help
---

### Post by HarryM on 2009-08-25
When I try to print documents under Ubuntu 9.04, I get a strange prompt:

"Authentication required for printing document `Test Page' (Job 53)"

with a box that looks like a password box but doesn't mask characters, and the text "none" to the left of it. See screenshot. 

I've tried entering my account password, along with several others, to no avail. Leaving it blank doesn't work either. I've tried rebooting the machine and printer, and reinstalling the driver using the latest version from [http://foo2qpdl.rkkda.com](http://foo2qpdl.rkkda.com). No joy.

Any ideas?

[IMG]http://harrymetcalfe.com/Screenshot-Authentication.png[/IMG]

---

### Post by revnoah on 2009-10-21
I have this problem too. I'm using a Samsung ML-2240 with the drivers installed from the CD. 

I am trying to print over a local network. The PC the printer is connected to prints fine and it is also running the same version of Ubuntu. 

When prompted for authentication, I've tried entering the password of the current remote user, the admin password, leaving the field blank and even going out on a limb and writing 'none', in case that was a prompt default improperly displayed.

I'm sure there must be a simple solution but I have no idea what it might be.

---

### Post by czljxt on 2009-12-06
I have exact same problem. Re-booting or re-logging in sometimes helps, but it's annoying.

I am using the "Samsung Unified Linux Driver". I have a feeling that the trouble started after the last automatic update of CUPS. But don't know for sure.

It makes my wife upset... please help! :-)

---

### Post by ecowan on 2009-12-07
For ehat it's worth...
I just started having the same pop-up, just after I set up some cups classes with users and quotas.
So I'm looking for hints as to what is required int the 'negotiate' box.

---

### Post by mooscape on 2010-01-16
I have a very similar problem. I am asked for username and password though. The problem is: nothing I enter seems to work.

Why are there so many problems with Ubuntu nowadays? Networking and printing is a nightmare. Anyone wishing to use the system must google for days. There are solutions out there, but why should they be "out there" and not resolved within the system in the first place. Authentication is turning into a real dealbreaker. Rather scrap it and let people add security later. We are forced to use windows just so that we can print!

---

### Post by jeSah8ci on 2010-02-04
Suffering from the same problem. I used to enter my own username and password and the job would go through... but now not even that!

Anyone had any luck?

---

### Post by benvanderbeek on 2010-03-15
Same problem, used to work, printing to a Brother HL 2140 attached to a Vista machine

---

### Post by linuxeer on 2010-05-13
I've had this problem on several occasions.  It seems to happen when Cups gets an update - I think it overwrites the configuration file.  The way I sorted it was to log onto the cups server on the print server (I don't have it set up for remote access).  Then select Administration tab.  Under server settings, click box next to 'Share printers connected to this system'.  Then click the 'Change Settings' button which saves the changes and restarts the server.  This did the job for me.

---

### Post by manthony121 on 2010-08-15
I got rid of the "Authentication Required to Print" dialog by directly editing the file, "/etc/cups/printers.conf", as follows:

Step 1. Open a terminal window:

[Applications|Accessories|Terminal]

(In the lines below, '$' is the prompt character. Type what comes after it.)

Step 2. Stop the cups server:

$ sudo service cups stop

Step 3. Edit the printers.conf file. I use 'vim' for text editing; you can use whatever editor you like. 'gedit' comes standard with Ubuntu:

$ sudo vim /etc/cups/printers.conf

Near the top of file "/etc/cups/printers.conf" is a line:

AuthInfoRequired username,password

Insert a "#" char in the first column (or, just delete the line):

#AuthInfoRequired username,password

Step 4. Save edited file
Step 5. Restart cups server:

$ sudo service cups start

This should fix the problem. I ran thru the printer config dialog after this change, and it did not change the line back. It seems there is no way to change it except by directly editing the printers.conf file.

I only have one printer, but you may have to repeat for other printers listed in "/etc/cups/printers.conf".

---

### Post by cander49 on 2010-10-29
For what it's worth, I have this same problem on Fedora (after installing CUPS), so it's not just an ubuntu problem.  I'm not actually sure what went wrong in the install (I let someone else attempt to install a network printer).  Anyone figure out how to authenticate it so printing will work?

---

### Post by pappo on 2010-11-17
> **manthony121 said:**
> I got rid of the "Authentication Required to Print" dialog by directly editing the file, "/etc/cups/printers.conf", as follows:

Step 1. Open a terminal window:
Step 2. Stop the cups server:
Step 3. Edit the printers.conf file.
Step 4. Save edited file
Step 5. Restart cups server:

$ sudo service cups start

This should fix the problem. I ran thru the printer config dialog after this change, and it did not change the line back. It seems there is no way to change it except by directly editing the printers.conf file.

I only have one printer, but you may have to repeat for other printers listed in "/etc/cups/printers.conf".

I followed your directions, by deleting the line referring to Authentication, but it did not fix the problem.  I checked the file "/etc/cups/printers.conf" after restarting cups and it had returned the printers.conf file with the Authentication line back in it.
This all worked when I was using Ubuntu 9.04, but not since I went to Ubuntu 10.04.1 LTS.  
Any help would be appreciated.

[SOLVED] - It wasn't a cups problem after all.  The printer, I was trying to talk to, was on my Windows 7 laptop and it had just decided to not accept my network authentication.  Good old Windows.  I moved the USB cable over to my Ubuntu PC and it was just like how plug-and-play is supposed to work.  Ubuntu saw the printer, configured for it, and shared it out on my network.  All is good again.

---

### Post by The IceMan on 2010-11-22
try SERVER\username

SERVER = the sharing machine name
username = local account on SERVER (or user @SERVER domain)

---

### Post by ascherp on 2011-01-07
> **manthony121 said:**
> I got rid of the "Authentication Required to Print" dialog by directly editing the file, "/etc/cups/printers.conf", as follows:

Step 1. Open a terminal window:

[Applications|Accessories|Terminal]

(In the lines below, '$' is the prompt character. Type what comes after it.)

Step 2. Stop the cups server:

$ sudo service cups stop

Step 3. Edit the printers.conf file. I use 'vim' for text editing; you can use whatever editor you like. 'gedit' comes standard with Ubuntu:

$ sudo vim /etc/cups/printers.conf

Near the top of file "/etc/cups/printers.conf" is a line:

AuthInfoRequired username,password

Insert a "#" char in the first column (or, just delete the line):

#AuthInfoRequired username,password

Step 4. Save edited file
Step 5. Restart cups server:

$ sudo service cups start

This should fix the problem. I ran thru the printer config dialog after this change, and it did not change the line back. It seems there is no way to change it except by directly editing the printers.conf file.

I only have one printer, but you may have to repeat for other printers listed in "/etc/cups/printers.conf".

Quite interesting. I had the same problem, but no "AuthInfoRequired username,password" in my config file. I have ADDED this line and now it works (without asking me for a password). My printer was not connected with Win as reported above. Using Ubuntu 9. *sigh*

---

### Post by SoundFriend on 2011-01-20
I have the same problem, I am running 10.10 64bit. 

If I edit "/etc/cups/printers.conf" as in #9, it works for a while then the printers.conf file is automagically restored to its original state, IN THE SAME SESSION. 

How does that work? It would be nice to say goodbye to this authentication required pop-up, and ideas please?

John

---

### Post by swb711 on 2011-01-24
Thank you this worked great for me, I had a HP windows laserjet 4 installed and it was working great, added a HP laser 4050 and it kept asking for passord. your solution fixed this problem and I can now print
Thank you


> **manthony121 said:**
> I got rid of the "Authentication Required to Print" dialog by directly editing the file, "/etc/cups/printers.conf", as follows:

Step 1. Open a terminal window:

[Applications|Accessories|Terminal]

(In the lines below, '$' is the prompt character. Type what comes after it.)

Step 2. Stop the cups server:

$ sudo service cups stop

Step 3. Edit the printers.conf file. I use 'vim' for text editing; you can use whatever editor you like. 'gedit' comes standard with Ubuntu:

$ sudo vim /etc/cups/printers.conf

Near the top of file "/etc/cups/printers.conf" is a line:

AuthInfoRequired username,password

Insert a "#" char in the first column (or, just delete the line):

#AuthInfoRequired username,password

Step 4. Save edited file
Step 5. Restart cups server:

$ sudo service cups start

This should fix the problem. I ran thru the printer config dialog after this change, and it did not change the line back. It seems there is no way to change it except by directly editing the printers.conf file.

I only have one printer, but you may have to repeat for other printers listed in "/etc/cups/printers.conf".

---

### Post by SoundFriend on 2011-02-21
I have tried editing "/etc/cups/printers.conf", and even setting it read only, but the file always gets rewritten to include the line:

AuthInfoRequired username,password

by something in the system.  Would that be CUPS?

How can I find out and stop this happening, is it a bug, should I post a bug report, it is getting annoying!

---

### Post by sflitman on 2011-04-23
I solved this problem by navigating to [http://localhost:631](http://localhost:631) which is my CUPS server administration page.  Under the Jobs tab I found a stale job from a network printer which had been disconnected and pressed the Cancel Job button.  No more wacky dialog.

Hope that helps,
SSF

---

### Post by SoundFriend on 2011-04-24
> **sflitman said:**
> I solved this problem by navigating to [http://localhost:631](http://localhost:631) which is my CUPS server administration page.  Under the Jobs tab I found a stale job from a network printer which had been disconnected and pressed the Cancel Job button.  No more wacky dialog.

Hope that helps,
SSF

Thanks. Unfortunately I have no stale jobs.  

However I noticed that I can't edit (save) the configuration file from the CUPS configuration pages, which is probably connected with my problem over printer permissions.

---

### Post by Tristan Schmelcher on 2011-05-13
I started getting this same issue after updating CUPS and post #8 from linuxeer was the solution. Thanks!

---

### Post by interrogator on 2011-05-18
I got this error for the first time on Natty, and it was also the first time I used the CUPs driver.  I was connecting to a windows print server via Samba and chose the CUPs driver as it was recommended.  I got a dialog which I tried several different users who all had sudo access and none would work.  

After reinstalling the HP printer with the hpijs drivers everything worked fine and I did not get any prompts.  This does seem to be a CUPs specific issue.  If modifying the printers.conf doesn't work then try a different driver.

---

### Post by dziamid on 2011-05-23
> **The IceMan said:**
> try SERVER\username

SERVER = the sharing machine name
username = local account on SERVER (or user @SERVER domain)

SERVER\username worked for me! Thanks. 

P.s. printer is on windows

---

### Post by vcrpcant on 2011-05-24
Just say that I was facing the same problem after messing my home folder permissions.
I solved it by changing them to 777.

But, now I have to reinstall ubuntu in the next days because I guess having 777 permissions on my home folder is not a good idea :(

---

### Post by oldbread on 2011-06-02
Post #17 fixed my problem.  Looked like an old/stale job was causing all the problems.

Talk about a red herring kind of error!!!

Thanks everyone!!!

---

### Post by Lurk the Turtle on 2011-06-25
Having installed a cheap samsung laser manually with the help of some tutorial somewhere some weeks ago, it worked just fine for...uh..some time, lately I keep getting that authentication pop-up, too, though. Got rid of it for some days with the solution from #9 (thanks!), also having to add the previously non-existent #AuthInfoRequired line (thanks to the other guy, too!). As of now, suddenly I keep getting asked for authentication again, yet when I open the printers.conf the line is unchanged. Someone in for some help? That'd be nice lots.

---

### Post by Jonadab on 2011-06-28
Oh, man, I think I just narrowed down the cause of the problem.  FINALLY.

Scenario:  my print server is Debian lenny and had not been updated for a while (since shortly after lenny was released, in fact).  (It's on a LAN, with no inbound traffic forwarded to it from the internet, so upgrading it was low-priority.)   The printer was set up in CUPS and shared via Samba.  Both Windows XP and Linux clients *had* been able to print, but a recent upgrade on the client side had caused the "Authentication required" issue on the Linux clients, and no auth credentials were good enough to release any of the held jobs.  Windows systems could still print, but they hadn't recently been updated.  (They're all still XP.)  None of the things discussed in this thread so far helped.

But I finally made progress:  on a whim, I did a dist-upgrade on the print server.  It's still using lenny, but it's a somewhat more up-to-date version of lenny now, and several of the CUPS packages *were* updated.  Now, all of a sudden, when my Linux clients give me the "Authentication required" grief, and when I type in the username and password (the one from smbpasswd on the print server), now it actually prints (instead of the former behavior of just prompting me *again* for authentication, ad infinitum, as if the credentials were incorrect).

So I'm guessing what I had was some kind of incompatibility between the newly upgraded stuff on the client and the old not-recently-updated stuff on the server.

Now that I've got that far, I'm going to go back and try some of the things in the thread again and see if I can get it to stop prompting for authentication in the first place.

---

### Post by Jonadab on 2011-06-28
> **Jonadab said:**
> I'm going to go back and try some of the things in the thread again and see if I can get it to stop prompting for authentication in the first place.

Confirmed:  once the server was updated, I was able to finish solving the problem by going into Printers on the client, deleting the printer, adding it new, and specifying the auth details upfront as usual.  Oh, I also restarted CUPS on the client; not certain if that's relevant.

---

### Post by darkspook on 2011-09-19
thanks [manthony121]("http://ubuntuforums.org/member.php?u=452498")

---

### Post by Chris_82 on 2011-10-06
I think [this is the bug]("https://bugs.launchpad.net/cups/+bug/627287") most of you are having.
Unfortunately it is a "won't fix".

I am still having the authentication popups..and I'm having the credentials hardcoded in the printers.conf file.
I am printing to a central samba/cups print server which then prints to the local samba/cups machines having the actual printers attached or being printers themselves..

I'll post back as soon as I have a solution.

ps:a bad solution would be to brutally rewrite the conf file with a cron job :-)

---

### Post by Chris_82 on 2011-12-27
Ok I solved it (no popups any more):
Add this to your printer configuration in /etc/cups/printers.conf:
```
AuthInfoRequired none
```
This is an example of connecting to a printer using samba:
```
DeviceURI smb://user:pwd@server/printer_name
```

cheers.

---

### Post by Glasairman on 2012-05-24
The problem is still there on 12.04, however it seems to be a problem of the particular driver itself.

1. A network-attached HP Laserjet 3200 required an id and password, although duly set at installation time. The /etc/cups/printers.conf file had the AuthInfoRequired line. >>

[I][B]<DefaultPrinter LJ3200>
UUID urn:uuid:d50abb4d-a886-3093-5d28-3058edb11d2e
AuthInfoRequired username,password
Info HP LaserJet 3200
Location Office[/B][/I]

2. A Brother WLAN-attached network printer doesn't request an id/password - and the corresponding entry in (the same) /etc/cups/printers.conf dwas accordingly >>

[B][I]<Printer Brother_DCP-J315W>
UUID urn:uuid:4aece26b-2d36-3d8e-6062-339a80bfe2d1
Info Brother DCP-J315W
Location Wohnzimmer
MakeModel Brother DCP-J315W CUPS
DeviceURI lpd://192.168.1.109/BINARY_P1
State Idle
[/I][/B]


So it's originating from the "Add Printer" process (tested with and without Cups management

---

### Post by oldos2er on 2012-05-24
Old thread closed.

---

