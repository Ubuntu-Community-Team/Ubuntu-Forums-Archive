---
title: "Some Please Create Dapper 6.06 VMware App for us &quot;less techie&quot; people.  Thanks!"
date: 2006-06-05
forum: General Help
---

### Post by luckylucky on 2006-06-05
Hello,

I love VMware & have downloaded the Ubuntu 5.10 pre-made app file from vmware.com and love using Ubuntu!!!  Unfortunately, I need to work within Windoze ](*,)  (don't ask; simple answer is I need special Windows applications for much of the work I do that is not suitably provided *yet* within linux) and find virtualization to be a fabulous option for me (saves me from rebooting into Ubuntu every time).

I've found many great tutorials on how to create an Ubuntu 6.06 VMware app file (provided links below) but doing those things seems a bit beyond my technical abilities. 
[SIZE="4"][COLOR="Red"][B]
Could someone Please (pretty please please	[-o<) make a Dapper VMware file (zipped for us in Windoze) and put it somewhere to download it?  I and I'm sure many others will be eternally grateful to you if you could do it.  Please put link to downloadable file here in this thread.  Thank you thank you and thank you again in advance for whoever :KS actually does this.  [/B][/COLOR][/SIZE]

Thanks again!!!
"Very Lucky"  	\\:D/


[http://johnbokma.com/mexit/2005/11/07/vmware-player-ubuntu-installation.html](http://johnbokma.com/mexit/2005/11/07/vmware-player-ubuntu-installation.html)


[http://johnbokma.com/mexit/2005/10/26/vmware-player-windows-xp.html](http://johnbokma.com/mexit/2005/10/26/vmware-player-windows-xp.html)


[http://arsgeek.wordpress.com/2006/03/29/so-i-have-vm-player-now-what/](http://arsgeek.wordpress.com/2006/03/29/so-i-have-vm-player-now-what/)

[http://www.pcmech.com/show//936/](http://www.pcmech.com/show//936/)

[http://www.vmware.com/vmtn/appliances/directory/ubuntu.html](http://www.vmware.com/vmtn/appliances/directory/ubuntu.html)


[http://www.google.ca/search?hl=en&q=ubuntu+.vmx&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=ubuntu+.vmx&btnG=Google+Search&meta=)


[http://www.3kingdoms.net/forum/showthread.php?threadid=18732](http://www.3kingdoms.net/forum/showthread.php?threadid=18732)

---

### Post by bluenova on 2006-06-05
I used this guide:
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

It was very easy, and every thing is working perfectly.

---

### Post by Sq322 on 2006-06-05
Can you use this to run existing apps from a current window install ?

---

### Post by luckylucky on 2006-06-05
[QUOTE=Sq322]Can you use this to run existing apps from a current window install ?[/QUOTE]

Yeah, it's easy & really useful!!!  Simply download VMware's Player @ vmware.com (& install it in Windows) then go here
[http://www.vmware.com/vmtn/appliances/directory/ubuntu.html](http://www.vmware.com/vmtn/appliances/directory/ubuntu.html)
download the zipped file, and unzip it.

Then just run the VMware player, point it to the file you unzipped (that you just downloaded) and boom... you've got Ubuntu 5.10 running as a window within Windoze!  Now you have the best of both worlds, no rebooting, and you can run everything you want in both OS platforms!!!

**[SIZE="4"][COLOR="Red"]Now, could someone please do us all a favor and create a VMware appliance copy of Ubuntu's 6.06???  Thank you in advance for your help on this matter.[/COLOR][/SIZE]**

---

### Post by Sq322 on 2006-06-06
[QUOTE=luckylucky]Yeah, it's easy & really useful!!!  Simply download VMware's Player @ vmware.com (& install it in Windows) then go here
[http://www.vmware.com/vmtn/appliances/directory/ubuntu.html](http://www.vmware.com/vmtn/appliances/directory/ubuntu.html)
download the zipped file, and unzip it.

Then just run the VMware player, point it to the file you unzipped (that you just downloaded) and boom... you've got Ubuntu 5.10 running as a window within Windoze!  Now you have the best of both worlds, no rebooting, and you can run everything you want in both OS platforms!!!

**[SIZE="4"][COLOR="Red"]Now, could someone please do us all a favor and create a VMware appliance copy of Ubuntu's 6.06???  Thank you in advance for your help on this matter.[/COLOR][/SIZE]**[/QUOTE]
are you sure you can use this to run programs from an existing partition of windows ?? I always thought you needed to install the windows OS from scratch with vmware
and i am talking about running windows on a linux host..not vice versa

---

### Post by givré on 2006-06-06
[QUOTE=Sq322]are you sure you can use this to run programs from an existing partition of windows ?? I always thought you needed to install the windows OS from scratch with vmware
and i am talking about running windows on a linux host..not vice versa[/QUOTE]
Yeah you are right. You have to create a virtual machine, and you install ubuntu or whatever you want on this machine

---

### Post by Sq322 on 2006-06-06
[QUOTE=givré]Yeah you are right. You have to create a virtual machine, and you install ubuntu or whatever you want on this machine[/QUOTE]
and that is where it is killing me..i need to use the apps i already have on this windows install under Ubuntu for it to really work for me
the only other thing i can do is boot windows and run minimally off it and vmware into ubuntu for everything else...but that is just a crappy idea all around

---

### Post by Kilz on 2006-06-06
[QUOTE=Sq322]and that is where it is killing me..i need to use the apps i already have on this windows install under Ubuntu for it to really work for me
the only other thing i can do is boot windows and run minimally off it and vmware into ubuntu for everything else...but that is just a crappy idea all around[/QUOTE]
IMHO its better to do it the other way around. Run Windows VM on Ubuntu. I set it up that way for my brother. Windoz isnt the most stable OS to run vmware on.

---

### Post by Sq322 on 2006-06-06
[QUOTE=Kilz]IMHO its better to do it the other way around. Run Windows VM on Ubuntu. I set it up that way for my brother. Windoz isnt the most stable OS to run vmware on.[/QUOTE]
thx for the suggestion

---

### Post by KillerKiwi on 2006-06-06
Im pretty sure you can you qemu to create images that vmware PLAYER can run (Thats how im running XP under dapper anyway)

---

### Post by Sq322 on 2006-06-07
[QUOTE=KillerKiwi]Im pretty sure you can you qemu to create images that vmware PLAYER can run (Thats how im running XP under dapper anyway)[/QUOTE]

@killerkiwi: I am assuming that even with that method u are not able to access existing partitions...correct?

---

### Post by givré on 2006-06-07
[QUOTE=Sq322]@killerkiwi: I am assuming that even with that method u are not able to access existing partitions...correct?[/QUOTE]
Of course, it is like if you had two cumputer near yeach other, the only way to connect them is by network interface

---

### Post by Sq322 on 2006-06-07
[QUOTE=givré]Of course, it is like if you had two cumputer near yeach other, the only way to connect them is by network interface[/QUOTE]
Except that it in this case the 2 computers in question are actually ONE :D 
The partition exists there and you can read / write from it in Linux...
It just seems strange not to have a way to launch the other OS from within Linux and still retain access to existing info.

Sorry for beating the dead horse

---

### Post by givré on 2006-06-07
If one day we could do that kind of thing, it would be so cool.
But you have to see more what is really virtualization.
There is a good article about this in wikipedia [http://en.wikipedia.org/wiki/Virtualization](http://en.wikipedia.org/wiki/Virtualization)

---

### Post by Sq322 on 2006-06-07
[QUOTE=givré]If one day we could do that kind of thing, it would be so cool.
But you have to see more what is really virtualization.
There is a good article about this in wikipedia [http://en.wikipedia.org/wiki/Virtualization](http://en.wikipedia.org/wiki/Virtualization)[/QUOTE]
Great Link...Thx

---

### Post by cjm5229 on 2006-06-10
For those of you having trouble creating a virtual machine try EasyVMX. Takes about two minutes to set up and you can install whatever OS you want in it. Yes that includes Ubuntu 6.06, Or Edgy Eft if you wish. [http://www.easyvmx.com/ ]("http://www.easyvmx.com/")
It's so easy even I did it;) It will work for VMware Player,  VMware Server, or VMware workstation.

---

### Post by blackjack6.21.91 on 2006-06-10
[http://cdimage.ubuntu.com/vmware/Ubuntu-5.10.zip](http://cdimage.ubuntu.com/vmware/Ubuntu-5.10.zip)

That should be it.  I found it on the Vmware website.

Cheers,
Blackjack

---

