---
title: "questions on Ubuntu"
date: 2010-12-15
forum: General Help
---

### Post by Ben M on 2010-12-15
I'm loving it too.
Its really stable, the bundled software is stable, layouts great but,
1. Constantly asking for passwords.
2. Wireless says its connected but firefox can't find the server.
3. I can't get it working with my Ipod. (biggest issue for me).
Mrs M wants to go back to Vista because of these issues.
Please help.

---

### Post by iosuna86 on 2010-12-15
Hi!

I can only help you out with your first problem.

Try this thread: [http://ubuntuforums.org/showthread.php?t=19236](http://ubuntuforums.org/showthread.php?t=19236)

I think that might prevent Ubuntu from asking passwords everytime you do something important. 

Regarding the second issue, have you tried using other browser (Chrome, Opera...)? Try removing and reinstalling Firefox... I dunno.

Hope I could help with regards to the first issue.

---

### Post by syncmasterpt on 2010-12-15
Regarding 2)

 Do you have an IP assigned? 
 Open up a shell window and execute sudo ifconfig to see if you have an IP of some kind.

 Do you know the IP of your WLAN router? Can you ping it with the command: ping router_ip where router_ip is something like 192.168.2.1

Regarding 3)

 What iPod version are we talking about? I have an iPod nano Generation 5, I think, and it works with no issue.

 What program are you using to manipulate your music collection?

---

### Post by Ben M on 2010-12-15
iosuna86, thanks I'll try that tonight. its not just firefox that can't connect thru wireless though.

syncmasterpt, i'm new to ubuntu and linux etc so am learning as I go.
by shell window i take it you mean terminal?
i  typed sudo ifconfig and it said some stuff including the IP address  which matches the address in the connection information window.
i typed ping IP address into terminal and its still pinging away. i'm not sure what any of this means.

then it just started to work! Idon't know if any of the above sorted it or not but thanks anyway.

just the Ipod issue now. its an 80gig ipod classic. I've tried amarok, rhythmbox and gtkpod.

---

### Post by mmsmc on 2010-12-15
ubuntu constantly asks for passwords because that is basically its security system

---

### Post by cgroza on 2010-12-15
> **Ben M said:**
> iosuna86, thanks I'll try that tonight. its not just firefox that can't connect thru wireless though.

syncmasterpt, i'm new to ubuntu and linux etc so am learning as I go.
by shell window i take it you mean terminal?
i  typed sudo ifconfig and it said some stuff including the IP address  which matches the address in the connection information window.
i typed ping IP address into terminal and its still pinging away. i'm not sure what any of this means.

then it just started to work! Idon't know if any of the above sorted it or not but thanks anyway.

just the Ipod issue now. its an 80gig ipod classic. I've tried amarok, rhythmbox and gtkpod.
Are you behind a firewall or a proxy?

---

### Post by trinitydan on 2010-12-15
> **Ben M said:**
> 
just the Ipod issue now. its an 80gig ipod classic. I've tried amarok, rhythmbox and gtkpod.

I sync music to my 80gb iPod classic using Rhythymbox and photos with GPixPod.

What exactly is happening when you connect your iPod?  Does it show up in Rhythymbox?

---

### Post by Ben M on 2010-12-15
Ok, I just plugged the Ipod in. It shows up on the desktop then rhythmbox opens, I close it and explore the ipod. Double click floola.  Archive manager opens then an error occurs.

Archive:  /media/MELLOR'S IP/Floola.exe
[/media/MELLOR'S IP/Floola.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/MELLOR'S IP/Floola.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/MELLOR'S IP/Floola.exe or
          /media/MELLOR'S IP/Floola.exe.zip, and cannot find /media/MELLOR'S IP/Floola.exe.ZIP, period.

It is an executable not an archive? 
I close that, go to rhythmbox, drag nirvana unplugged from the library to the ipod, rhythmbox window goes dark and its like that for a half hour. I can explore the library or ipod thru rhythmbox or gtkpod fine but if i try and transfer files it all goes **** over tit. I unplug the ipod, it has an apple symbol until i hold the play button long enough to turn it off. I turn it back on and no nirvana.



Download album, Pink Martini (the wifes choice)

---

### Post by Ben M on 2010-12-15
It doesn't like my blackberry either, or dangleberry as the wife calls it. 2 icons show up on desktop, micro sd card and blackberry. SD card no probs, blackberry open folder and cursor spins and nothing happens.

I wish I could offer advice and help on this forum  as well but i don't know enough yet. If anyone wants some advice about house renovations, septic tanks or roofing just ask.

---

