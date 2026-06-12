---
title: "Open Source Office Solution"
date: 2009-07-14
forum: General Help
---

### Post by majdi on 2009-07-14
I'm working on a new project for an Office setup with the following requirements;

[LIST=1]
[*]15 users with desktops running Office Applications and accessing an ERP on the LAN.

[*]5 users with laptops running windows Vista

[*]1 file and print server

[*]1 Server running ERP and Database

[*]1 backup server
[/LIST]

I usually work with Red Hat and Fedora but I am thinking of implementing an ubuntu solution for this office setup. 

I'm looking for advise on the following;

Users
Which desktop is best for office use KDE or Genome

Hardware
PowerEdge R200
PowerEdge 2950
Optiplex 740 Small Form Factor

Applications
Backup solution
3 Users using Autocad (Must run on ubuntu)

Support
I have never used Canonical Global Support Services, so I would appreciate any feedback from anyone for supporting such a solution.

---

### Post by kogger on 2009-07-14
Ubuntu comes with Gnome, so it would probably be best to stick with that unless you have a good reason to switch to KDE (which I've never actually used, so I'm not sure which one would work better). And the OpenOffice programs should work fine for office use.

---

### Post by triplesquarednine on 2009-07-14
ubuntu may or may not run autocad, obviously wine is required so i would test
autocad under wine(and test it well!!) before making any decision....

as for ERP, it will work fine. install OpenERP. works in 8.10 and 9.04.

as for office, you could use open-office. it should work great, and you could use evolution for your calenders(if you use them, most MSoffice folks do)...

or you could use MSoffice, however if you go that route, stay away from outlook express, as it has weak security, and might eventually cause hassles in wine. although,
it wouldn't harm your linux system overall, it still might mess wine up...
also, be aware that Access for MSoffice won't work without what is called "winetricks",
to allow the Access 200 runtime to work. and winetricks is bleeding edge, and may not be solid...

you could also use CodeWeavers - "crossover" - which is more stable than wine,
and more specialised for products like MSoffice and Adobe...in fact, they employ the wine developers.

if it were me i would stick with the open source stuff, and only use the windows apps,
if you had no choice, and i would test it all on a system or two before
actually commiting to using it in a "production envirnment" AKA: your office....

hope that helps with atleast clarifying/putting some options out there!

---

### Post by lukeiamyourfather on 2009-07-14
> **majdi said:**
> 
3 Users using Autocad (Must run on ubuntu)


Houston, we have a problem. That's a Windows only application, processor and memory intensive, requires 3D acceleration, and would be unsupported by Autodesk. I doubt WINE will handle it very well if at all, be sure to test it for an extended period of time before implementing it.

The best option if WINE doesn't work out would be to run a virtual machine for Windows in VirtualBox (version 3.0.0 or newer) which has direct access to the host graphics card for 3D acceleration. Granted, that's experimental at best and shouldn't be relied up in a production environment and that's assuming the small form factor systems even have a graphics card capable of running Autocad.

If there's already some Windows systems in use why not just make it a few more and bypass all the headache of trying to get Autocad to work in Linux. If those users still need access to applications in Linux they could use a virtual machine in Windows which would be easier since no 3D acceleration would be required for the guest.

Like already mentioned, Open Office and GNOME would do just fine. Cheers!

---

### Post by LepeKaname on 2009-07-14
> ubuntu may or may not run autocad, obviously wine is required so i would test autocad under wine(and test it well!!) before making any decision....

I agree with **triplesquarednine**, first try AutoCAD before anything else. Is there any special reason why to use AutoCAD?

In my personal experience, AutoCAD have never played well with Linux. And newer versions are less possible to make them work properly. Maybe AutoCAD 14 and previous versions may work...

There are some OSS or Commercial alternatives that works under Linux. Not all of them as handly and easy to use as AutoCAD (all depends on your requirements).

Some of the best: Blender (available at default repositories) and Maya.
Check this threads:  

[http://ubuntuforums.org/showthread.php?t=148488](http://ubuntuforums.org/showthread.php?t=148488)
[http://ubuntuforums.org/showthread.php?t=141735](http://ubuntuforums.org/showthread.php?t=141735)

---

### Post by margni on 2009-07-14
> **lukeiamyourfather said:**
> Houston, we have a problem. That's a Windows only application, processor and memory intensive, requires 3D acceleration, and would be unsupported by Autodesk. I doubt WINE will handle it very well if at all, be sure to test it for an extended period of time before implementing it.

The best option if WINE doesn't work out would be to run a virtual machine for Windows in VirtualBox (version 3.0.0 or newer) which has direct access to the host graphics card for 3D acceleration. Granted, that's experimental at best and shouldn't be relied up in a production environment and that's assuming the small form factor systems even have a graphics card capable of running Autocad.

If there's already some Windows systems in use why not just make it a few more and bypass all the headache of trying to get Autocad to work in Linux. If those users still need access to applications in Linux they could use a virtual machine in Windows which would be easier since no 3D acceleration would be required for the guest.

Like already mentioned, Open Office and GNOME would do just fine. Cheers!

I agree with Running Virtualbox - but download the full version from sun.  [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

The version of virtualbox (virtualbox-ose)with ubuntu doesn't have full access all external devices on the host box i.e. USB device passthrough from the guest back into the host  (or at least in my experience with it.)

---

### Post by lukeiamyourfather on 2009-07-15
> **LepeKaname said:**
> 
Some of the best: Blender (available at default repositories) and Maya.
Check this threads:  

[http://ubuntuforums.org/showthread.php?t=148488](http://ubuntuforums.org/showthread.php?t=148488)
[http://ubuntuforums.org/showthread.php?t=141735](http://ubuntuforums.org/showthread.php?t=141735)

Both are good applications, but neither are computer aided design applications. =;

[http://lmgtfy.com/?q=linux+alternative+autocad](http://lmgtfy.com/?q=linux+alternative+autocad)

I'm a Maya user by the way. Cheers!

---

### Post by majdi on 2009-07-15
Thanks for the feedback.

So after, some research to solve the Autocad problem, I can see three options;

[LIST]
[*]Virtualbox. No support for Boot Camp partition, USB or DirectX acceleration. Do I need these to run Autocad?

[*]VMware. The feedback on this software is good, not sure how it will handle Autocad though.

[*]Parallels. Has all the features Virtualbox is missing, and feedback for running Autocad using it is good. [http://www.autocadforlinux.com/](http://www.autocadforlinux.com/)
[/LIST]

So, out of the three options, I'm not sure which one would be the best for the office solution. 

YOUR FEEDBACK IS APPRECIATED.....

---

### Post by DownTown22 on 2009-07-15
May I ask what you need AutoCAD for?
This could help in determining a solution or an alternative piece of software.

---

### Post by sigurnjak on 2009-07-15
Since CAD stuff is so important you may try this
[http://www.varicad.com/en/home/](http://www.varicad.com/en/home/)

and this


[http://www.ribbonsoft.com/qcad.html](http://www.ribbonsoft.com/qcad.html)
.

---

### Post by LepeKaname on 2009-07-15
VariCAD looks a good alternative... for $700 USD (compared to 2,000 USD for AutoCAD).

I have tried QCAD in the past and unless you do very basic stuff, I don't see it as a viable alternative to AutoCAD.

VMWare should handle it as well as in any Windows (cause you will be runing Windows). VMWare (or any other virtual box) its fine if you will use AutoCAD not so often. If you must use AutoCAD and you will use it often, then follow **lukeiamyourfather** recommendation:

> If there's already some Windows systems in use why not just make it a few more and bypass all the headache of trying to get Autocad to work in Linux.

---

### Post by raronson on 2009-07-15
I know that 'Genome' was a typo, but I really like it.  'Gnome' doesn't make sense as an acronym or a noun for what it's describing.  While I'm on my soapbox, and totally not helping the OP'er at all, let's get rid of the that stupid foot and replace it with a double-helix.

---

### Post by majdi on 2009-07-24
Is setting up the following on one server asking for too much;

[LIST]
[*]LAMP
[*]LDAP
[*]File & Print Server
[/LIST]

---

### Post by LepeKaname on 2009-07-24
> Is setting up the following on one server asking for too much;
LAMP
LDAP
File & Print Server

I don't think is too much unless you expect a very high traffic. BTW, I think you should open other thread for this question.

---

