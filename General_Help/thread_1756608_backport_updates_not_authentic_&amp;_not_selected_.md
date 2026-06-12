---
title: "backport updates not authentic &amp; not selected for."
date: 2011-05-12
forum: General Help
---

### Post by heron7 on 2011-05-12
Why am i getting backport updates ; that are'nt carrying a vaid authentitcation & i do not have the backport update setting selected ?

---

### Post by heron7 on 2011-05-13
So you're telling me that from 60 viewers Not 1 know an answer?... yet  here i have again the same issue ..trying to install unetbootin  . 

oooih busy bees or ?... 

is this forum actually active or what?..  is there a new one : / :KS yippie  , where where ?... 
Neo ; stop trying to save mankind ,they're doomed and they know it ; asteriod no. OOOI/O is moving flashy fast in the direction of cold Dark loneyly space ... 

..but I'm here now , so don't despair you can be my hero ...hahah  :guitar: 

 :confused: 
 eyhh MOoD van mijn ....

---

### Post by heron7 on 2011-05-14
ok guys ,now i am 'wooried' about break down in tears but i will restrain myself for now and finish writing this plea first.
 Am i on some black list or locked up in a bad boy's vault or what? 
 I only asked why am i getting the backports when i have not selected them? 
I have attached a pic so you dont even have to read the post.

lets try again , fellow Ubuntities .
 it's Saturday , weekend , show you care : )

---

### Post by mc4man on 2011-05-14
> **heron7 said:**
> Why am i getting backport updates ; that are'nt carrying a vaid authentitcation & i do not have the backport update setting selected ?
You are getting the current apt update for lucid - has nothing to do with the backports repo
"backported" is a term, not a repo

---

### Post by heron7 on 2011-05-20
You are right after looking again at them png.'s . I have uploaded the wrong pic ,somehow. 
I had seen a warning telling me that there was Not a valid authen... for the updates in upt man at that very moment. It said backpoorts too . I know very well what backpoorts mean ,hell try reading an intro to Linux without not reading about the philo . Not poss . 
 I have made a screw up of uploading the pic's and the second tie i came lokijng for a reply ,like two weeks ltr. I was still in ,..emm .... shock?..  and had'nt paid attention to what i uploaded again that day ,maybe also because I had lost most of the incentive of reporting a flaw or maybe a security breach .. from my side Not Ubuntu's .
  But thanks for you're reply mate. :D
Atleast now i know that i had misreported & Not just bein ignored by 'my' commun.
Now i have only to figure out how the hell did i screw up that screen shot not once but 3x effectively uploaded them .The reason was that i had taken multile scrn shts to show the whole set up i had apt man in at that time ,but the first warning had slipped by me while refusing to be photographed . :confused:

---

### Post by linuxinstalledfromhdd on 2011-05-20
sudo gedit  /etc/apt/*sources*.[I]list

Maybe post a copy of what you have enabled at this point. 
[/I]

---

### Post by heron7 on 2011-05-20
Here you go, I found the one png that showed what the update entailed +- and backports i had seen once i opened the details + Requires installation of untrusted packages ) : come again .. [IMG]http://img828.imageshack.us/i/yepa.png/[/IMG]  
 and while I'm at it I'll post todays mishap .Mia culpa .. I have yet to fully learn how to use the countless cd's that come with the mags every month. Unless it's a live cd with only one distro on each side, I have diff with downloading software from it. I aint sure if I would have to have the cd always by everytime it asks for an update. 
I have'nt looked into it yet because I had more important stuff to learn ,i figured .If The apt man cache is handled by the os anyways. 
It is not all to evident as to what you can install on one os and not on another . 
For ex. I have Suse on machine or partition and Ubuntu on another and a new cd in d drive packed with all sorts of goodies : ( ... .
 I would'nt know what I can install on Debian for e.x that even runs well on Ubuntu. Debian is very strict ,very diff from Ubuntu. so is Kubuntu for that matter.

---

### Post by linuxinstalledfromhdd on 2011-05-20
in terminal:

sudo gedit  /etc/apt/*sources*.[I]list

post results

[/I]

---

### Post by heron7 on 2011-05-20
linuxinstalledfromhdd thanks for the reply/--help.
here's the out put of :horus@horus-laptop:~$ sudo gedit/etc/apt/sources.list
sudo: gedit/etc/apt/sources.list: command not found  

I tried to as root with su but that does'nt work too well .I'll check again to be sure before I let out other wind...
Confirmed =su: Authentication failure
horus@horus-laptop:~$ 

fedora& others' has that sort of power/control , right?..

---

### Post by linuxinstalledfromhdd on 2011-05-20
sudo apt-get install gedit

then try again.. :)

---

### Post by mc4man on 2011-05-20
One thing you can do is open your software sources and disable the 'cdrom ' source - that should take care of one of your screens - about failed to fetch... cdrom

---

