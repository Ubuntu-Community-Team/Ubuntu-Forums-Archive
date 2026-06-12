---
title: "NEW to ubuntu need help opening some programs"
date: 2010-03-15
forum: General Help
---

### Post by shaun67 on 2010-03-15
Hi all, just wiped out xp and micro crap for ubuntu :p can anyone help me and explain how i can open my software that i backed up firewalls,antivirus etc when i double click them it just opens archive manager but then i cannot get any further could do with this sorting as i have a few stuff that is in rar files and win zip..any help appreciated.:)

---

### Post by wojox on 2010-03-15
Antivirus you don't really need. Firewall (ufw) is installed you just need to activate it: [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by shaun67 on 2010-03-15
How do i get my other programs to open off of my discs ,thought i'd just double click them and they would open ..can i not use my own firewall etc ..Thanks

---

### Post by Admiral Yi on 2010-03-15
It depends. The stuff you ahve on your disks is probably for windows, which is why it doesn't work.

Try going to System>administration>synaptic package manager and searching there for whatever programs you need.

---

### Post by OMJD on 2010-03-15
Most routers have a firewall built in. These will protect you from annoying DoS attacks etc.

To be honest, a software firewall on Linux isn't always necessary unless you're running a server etc. Some may argue with that, but that's my opinion. I'm willing to bet that most desktop users on here are not running a firewall on their Linux box.

---

### Post by shikhar_sharma on 2010-03-15
Hey can u give us a list of programs that u wanna open up.Then we will tell u all the possible alternatives of those programs.Because in linux exe files doesnt work and believe me u dont need them.Linux softwares comes in packages and believe me the variety of packages is great.Just tell us which softwares u wanna open and we'll help u out

---

### Post by Failboat88 on 2010-03-15
What software did you back-up? You may need to use wine to virtualize it if it does not support Linux or download the Linux version. 
 
Just make sure you keep all your files that you use with the program ,ie. .xls (excel spreadsheet).
 
I'm in a similar possition as you I just got ubuntu and I want to run MS Office, which I heard can be virtualized.

---

### Post by audiomick on 2010-03-15
you should be able to unpack a zip with a right click and "unpack here" or "decompress here". I am not sure what it is called in English, I have my Ubuntu in German for my girlfriend's sake.

---

### Post by shikhar_sharma on 2010-03-15
failboat as far as ur problem is concerned i wouldnt recommend using msoffice with wine.See wine is used in the case when there is no alternative available.As far as ms office is concerned openoffice 3 is a perfect replacement for it giving u about 90% of the features of msoffice.plus its free.also if u have a legitimate copy of windows software that u r using on linux system in a virutal environment u r not eligible for tech support from OEM.so when u have switched to open source i think u should stick to it and try to search for alternatives.

---

### Post by J V on 2010-03-15
Don't need antivirus, don't need firewall (unless you run a server of some sort), don't bother with your programs, there isn't a single one you can't get a replacement for... the only problem is when you need files made in windows, and they can probably be opened in linux apps (osalt.com)

---

### Post by shaun67 on 2010-03-15
I need to add  auto data  and tis  and some pdfs i have on disc i want to put them on my pc...auto data is an automotive program..for some reason i keep losing my connection since installing this os ..My pc uses a modem ..i do have avast pro,superantispyware and outpost firewall pro ..so you are saying i don't need these security programs? 

How can i open up my firewall to make sure is all right ,i cannot find it  lol.

Thanks it's much appreciated.

---

### Post by nitstorm on 2010-03-15
You do not need an antivirus or need to enable your firewall unless you are on an insecure connection. 

This gives you the status of the inbuilt awesome Linux firewall :
```

sudo ufw status
```

This turns on ur firewall:
```

sudo ufw enable

```
This turns off ur firewall:
```

sudo ufw disable

```

If you find this too tough, type the following into terminal (Applications->Accessories->Terminal) or you can also download it from Applications--> Ubuntu Software Center

```

sudo apt-get install firestarter

```

Firestarter is a GUI program that helps you configure your firewall and yes all your Windows programs are a waste unless you want to use Wine, which is a Windows Compatibility Layer for Linux allowing users to use Windows programs on Linux, but you don't have to coz u'll find almost anything in linux equivalent and often more than surpassing the Windows software. Linux rules!!!!!!   :D

---

### Post by shaun67 on 2010-03-15
Thanks all for the advice ,i am just getting to grips with ubuntu and i like it  ! How do i make all my web pages fonts bigger as they are small and i have to click on zoom lol.Managed to get some of my  files on pc so that's good.. so when i installed ubuntu from this live cd it already put the firewall on right ? I guess i should have looked some things up but wanted to rid myself of micro crap lol.

I know i have asked this question before but are you guys sure i don't need any spware or antivirus software ,i am just a home user..I have to ask as i have always been used to xp and all the scanning for stuff lol. Only don't want any one ripping my paypal account off.

Thanks once again

---

### Post by audiomick on 2010-03-15
Hi.
As far as you web pages go, look at extras> prefernces in firefox. Or maybe options instead of preferences; mine is in German. On the third tab, which should be called "content" or something similar, there is an adjustment for the default font in firefox. If you make that bigger, it should solve your problem.

Regarding security: Linux is of course not invulnerable, but it is considerably more secure than windows, if only because it's market share makes it a less tempting target. That isn't the only reason, though.

For instance, look at this:
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
the page contains a list of (allegedely) all Linux viruses. On one page. Think about that in comparison to windows.

Also have a look here:
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

A few thoughts:
Assuming you have a router, your router will have a firewall in it, almost certainly. I haven't changed my settings in the router, and according to one of those sites that look from outside (sorry, can't remember the name) my computer is invisible to the outside world.

As in windows, so in linux: think about what you click on in the net, and what you download. If in doubt, don't.

As far as your paypal goes: firefox has a function to erase the chronicle. If you do that every time you have done something in the net that you don't want to get spread around, you increase your security by a couple of steps.

---

### Post by shaun67 on 2010-03-15
Hi thank you  for your help.. sorted and now i am up and running:popcorn:

---

### Post by Failboat88 on 2010-03-15
Should I run a firewall if I'm not using a router? I just have my modem straight into the pc atm.

Edit: I just turned it on anyhow. Thanks for code nitstorm.

---

