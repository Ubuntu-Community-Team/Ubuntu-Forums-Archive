---
title: "Upgrading ATI RADEON driver caused me to loose compositing"
date: 2010-09-08
forum: General Help
---

### Post by Miki800 on 2010-09-08
I wanted to upgrade my ATI drivers because I believed that I could be one of those people playing Starcraft 2 under Linux so well.
I always forget how whenever I upgrade something that works in Ubuntu everything goes wrong real fast.

I went here:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

Downloaded that version and running it showed me that that version of drivers is "8.762",
(and this is important) running amdcccle showed me that my current driver is "8.723"

After I completed installing the downloaded driver it told me that it has completed successfully.
I am used to that that Installing Graphic drivers needs the OS to be restarted, but oddly this time I was not requested to do that, so I took the initiative and restarted Ubuntu.

the result was - me loosing compositing completely, without being able to enable it through the GUI.
My `xorg.conf` apparently did not change at all during the installing so doing the manual hard work of editing it is not necessary.

When I ran amdcccle again - it told me that I still have version "8.723"


So the installing lied to me when it told me that it has completed successfully.

please assist me.

---

### Post by TwelveGauge on 2010-09-08
I had this problem as well. What i did was remove the driver suite completely then ran the install file provided by ATI. 
 
Additionally you can take the driver off and wait for Ubuntu to tell you that there are drivers availiable and then click "install".

---

### Post by Miki800 on 2010-09-08
> **TwelveGauge said:**
> I had this problem as well. What i did was remove the driver suite completely then ran the install file provided by ATI. 
 
Additionally you can take the driver off and wait for Ubuntu to tell you that there are drivers availiable and then click "install".

Thank you TwelveGauge, this has worked almost perfectly

I 'DeActivated' my drivers, restarted, installed the new drivers, restarted and now amdcccle showed me the new drivers' version installed!


My only problem now is that my resolution is lower then what I used to have.

My 'MAX_RESOLUTION' possibility is not as high as what I used to have, now I have to go through tutorials over the web to find out what I did to solve this problem when I first had it so many years ago.

I'd appreciate it if you can also help me out figuring that out and save me some time :)


EDIT:
I used to have backups of my xorg.conf file, but now that I checked them out I see that what I have is just one huge horrible horrible mess :(

I tried switching couple of my backups xorg.conf files with the current one only winding up having to boot from a recovery mode to change it again when I could not complete booting anymore.


bleh


OK this is my current purpose - I want to have cloned screens with the same resolution of 1680x1050.
nothing more nothing less, and I'm having trouble getting that to work

right now I have two screens on different resolutions over each other.

---

### Post by TwelveGauge on 2010-09-08
No, it's my fault I directed you to the wrong monitor setup. THIS is what you should do:

System -> Prefs -> AIT CCC (Admin -> Display Manager -> Detect Monitors -> Multi-Display -> Single Display Desktop (Multi-Desktop) -> Apply to both monitors if it wants you to. 

THEN

ATI CCC (Admin) -> Display Manager -> Display Settings -> Resolution. 

That SHOULD do what you want it to now. If it doesn't then I do know a fail safe way to get it to work, however this is much, *much* easier and less time consuming so try this first.

---

### Post by Miki800 on 2010-09-08
Discard everything that I have said before, the pleasure of having StarCraft II up and running smoothly in my Ubuntu
worth all the pain of having the reconfigure everything that I have lost due to this upgrade.

Actually right now I was able to configure compiz back with all my previous customizations
and even my clone screens are configured again.

But the problem is that now my 2nd monitor will not accept the same resolution that it would have accepted previously.

My Sharp screen says "Not compatible with this signal",
I don't know whats it's problem, it used to work with that before, maybe the Hz number is wrong this time?
I dunno.

---

