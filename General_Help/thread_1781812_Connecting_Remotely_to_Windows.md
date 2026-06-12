---
title: "Connecting Remotely to Windows"
date: 2011-06-14
forum: General Help
---

### Post by PsyclonJohn on 2011-06-14
Is it possible to connect remotely to a Windows PC from Ubuntu.

I know these people that are constantly receiving Malware on their PC's and I'm always glad to help them when I'm around. The problem is, they are over 200 Miles away, and I won't be in the area until a very long time. 

Would it be possible to connect to their PC remotely with Ubuntu and remove their viruses via ClamAV?

Thanks!

---

### Post by katykat on 2011-06-14
Unfortuantely its probably the Remote Desktop functions that are part of the problem. 

While the simplest sol,ution may be to boot into Win and use Netmeeting, I really, really would not trust a running system with today's buggers. 

I am not impressed by Clamav. its a decent AV but in reality Avast seems much better, and even that cant stop the newer malware. 

What I would do, and have done, in this situation is find a good boot disk like Hiren's, or google for Avast and BootCD (BART CD ) , burn it, and send them that. The C: drive really needs to be dismounted before it can be cleaned.

After cleaning also have them install Hijackthis, rename the executable to something else, make a link to the desktop, and send the logfile to: 
[http://www.hijackthis.de/#anl](http://www.hijackthis.de/#anl)

After that the next time you visit check out the hard drive after booting off a floppy into DOS, or else use one of the Hiren's utilities. To see the directory structure in its raw format (there are a bunch of 'normal' hidden directories not visible in the NTFS file system). Do it on your own system first to get an idea of what is 'normal' for Win , and then look for rootkits. 

If these people are just normally surfing the net and using common P2P sites they REALLY should be on Linux and Firefox. 

Plus remote desktop functions would probably be much safer, though I personally disable them on all my Linux/Win systems. (But provide for loading them manually if necessary).

Also: Make sure they are behind a hardware firewall. If just using a cable modem, insist on the necessity of getting a good router with NAT, at least.

---

### Post by PsyclonJohn on 2011-06-14
I totally agree with you, and I've tried to get them using Ubuntu or Linux Mint and they tell me it sounds all great, but they know nothing about it and won't even bother to give it a try. 

They aren't computer nerds like us people, and last time I was up in that area I removed so much stuff, and as soon as I left things started back up with them. I mention cleaning up cookies and temporarily Internet files and they look at me like they don't know what I'm talking about. Good chance that they don't! 

I also understand how ClamAV is not the best, but it was just an example. I could get commercial AV built for servers, as I am thinking of turning my desktop into a public Ubuntu Server some time in the future, could come in handy!

---

### Post by PsyclonJohn on 2011-06-14
I just found a program called Team Viewer, I'll have them download it for a secure connection.

---

### Post by Mark Phelps on 2011-06-14
Realize that even IF you do get remote connection to work, the likelyhood that you will be able to use that to remove malware is slim to none.

You need to be able to run antivirus cleaners while NOT running Windows, that way, they can't stop the tools from doing their work.

You should go to the Kaspersky site, download and burn the Rescue CD.  Then, send that to the folks, tell them to boot from it and use it to clean their machines.

---

### Post by collisionystm on 2011-06-14
> **PsyclonJohn said:**
> I just found a program called Team Viewer, I'll have them download it for a secure connection.


I was going to suggest team viewer! That is what I use!

The programs I use to fix things like this are...

A good hosts file to block KNOWN bad websites.
[http://winhelp2002.mvps.org/hosts.htm](http://winhelp2002.mvps.org/hosts.htm) 

SpyBot Search and Destroy 
[http://www.safer-networking.org/index2.html](http://www.safer-networking.org/index2.html)

HijackThis
[http://free.antivirus.com/hijackthis/](http://free.antivirus.com/hijackthis/)

Avast Anti Virus
[http://www.avast.com/index](http://www.avast.com/index)

Vipre Rescue
[http://live.sunbeltsoftware.com/](http://live.sunbeltsoftware.com/)


And make this registry file. This will repair issues where exe files cannot be ran. It really came in handy today when a windows 7 machine was infected with the fake antivirus and the user could not longer load msconfig or cmd prompt... etc.

Just copy this entry and name it as a .reg file

> Windows Registry Editor Version 5.00 
 
[-HKEY_CLASSES_ROOT\.exe\shell] 
 
[-HKEY_CLASSES_ROOT\.exe\DefaultIcon] 
 
[HKEY_CLASSES_ROOT\.exe] 
@="exefile" 
 
[HKEY_CLASSES_ROOT\exefile] 
"Content Type"=- 
 
[HKEY_CLASSES_ROOT\exefile\shell\open\command] 
@="\"%1\" %*" 
"IsolatedCommand"=- 
 
[HKEY_CLASSES_ROOT\exefile\shell\runas\command] 
"IsolatedCommand"=- 
 
[HKEY_CLASSES_ROOT\.bat] 
@="batfile" 
 
[HKEY_CLASSES_ROOT\batfile\shell\open\command] 
@="\"%1\" %*" 
 
[-HKEY_CURRENT_USER\SOFTWARE\Classes\.exe] 
 
[-HKEY_CURRENT_USER\Software\Classes\exefile] 
 
[-HKEY_CLASSES_ROOT\secfile] 
 
[-HKEY_CURRENT_USER\Software\Classes\secfile] 
 
[-HKEY_CLASSES_ROOT\pezfile] 
 
[-HKEY_CURRENT_USER\Software\Classes\pezfile] 
 
[-HKEY_CLASSES_ROOT\sezfile] 
 
[-HKEY_CURRENT_USER\Software\Classes\sezfile] 
 
[HKEY_LOCAL_MACHINE\SOFTWARE\Clients\StartMenuInternet\FIREFOX.EXE\shell\open\command] 
@="firefox.exe" 
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Clients\StartMenuInternet\FIREFOX.EXE\shell\safemode\command] 
@="firefox.exe" 
 
[HKEY_LOCAL_MACHINE\SOFTWARE\Clients\StartMenuInternet\IEXPLORE.EXE\shell\open\command] 
@="iexplore.exe"



Oh and dont forget CCLEANER

[http://www.piriform.com/CCLEANER](http://www.piriform.com/CCLEANER)

---

### Post by collisionystm on 2011-06-14
In my experience, here is the best method for cleaning a windows machine.

First,

Run MSCONFIG

Start, RUN, msconfig, ENTER

if you cannot start MSCONFIG run that .reg file I specified already.

Go to Services tab,

check box for HIDE ALL MICROSOFT SERVICES

Now it disable all. APPLY

Go to startup tab, hit disable all, APPLY

Restart the computer

NOW, 

Run CCleaner and clean the machine, this will erase all the temp files. This is where alot of viruses and malware like to host themselves because they are generally downloaded from a website.

Do a registry clean inside of ccleaner

Run Hijack this

Check the box for anything suspicious that is NOT windows related. Be careful you can break your computer!

Hit FIX CHECKED

Delete your old hosts file and replace it with the one from the website i specified

C:\windows\system 32\drivers\etc\

Now run spybot search and destroy.

DO NOT INSTALL TEATIMER.exe

use the search for problems function and fix.

You can also use immunize for IE

NOTE: 

With windows 7, right click on the spybot icon and hit run as administrator

The vipre rescue comes in handy as an 'all else fails' tool

Avast is my favorite free anti virus. make sure to register for a key, it is good for 15 months at a time.

Good luck!

---

### Post by PsyclonJohn on 2011-06-14
Thanks, I have tested Team Viewer from a laptop in my house and it works great. I haven't contacted the people yet, since it was only hours ago I caught this idea. 

I'll give your answer a shot, although I can only test it on their computer because I no longer use Windows in my house hold. 

Has anyone had any experience with Remote Desktop Client?

---

