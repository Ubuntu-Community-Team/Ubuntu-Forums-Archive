---
title: "Alternative linux program to a windows program?"
date: 2009-12-02
forum: General Help
---

### Post by spydeyrch on 2009-12-02
got a quick question guys. I am in need of some info. I have was wondering if anyone was aware of a program for linux that is similar in function and features as the windows based [Windows Steady State]("http://www.microsoft.com/windows/products/winfamily/sharedaccess/default.mspx") program. I have a client that currently uses an XP machine and has a list of issues and requirements:
 
1.) The don't want to shell out more funds for Vista or Win7
2.) No funds for new hardware.
3.) Shared computer with daughter (notorious for "accidental" installation of every known tool bar and virus known to the tech world (just clicks yes on EVERYTHING on EVERY webpage))
4.) needs to have a stable system and currently her XP is crashing every few months, due to daughters "internet excursions" and needs a clean install.
 
I was going to install (AGAIN!!) her XP system and everything plus Windows Steady State to try and minimize the damage footprint and keep things somewhat stable for as long as possible but after the 5th time of doing this. I figured that I would just get them hooked on linux with ubuntu. It has all the user permissions needed to minimize the daughters damage wake BUT, the mother is also notorious for falling into her daughters pleas for the admin password, and then the carnage starts again. So I thought that if perhaps there was a similar program as windows steady state but for linux, that would be great! With linux the probability of a virus is very minimal, so no worries there, but the devistating effects of a little 13 year old girl with her parent's admin password can still be devistating, even with routine backups.
 
Any ideas guys? Oh, and sorry about the rant, it is a little frustrating :mad: when they don't understand the work that it takes to get them up and running after what they have done. Thanks again! :-)
 
-Spydey:popcorn:

---

### Post by Bag-O-Stuff on 2009-12-02
If you can't find an alternative and have a Windows OS license, install Windows in VirtualBox.  Get everything updated and patched up and then snapshot it.  If the copy of Windows ever gets messed up, simply go back to the snapshot and you are right where you left off.

You get the best of both worlds.  They use the computer in Ubuntu for all the web browsing, email, etc...  Fire up Windows inside VirtualBox only when you need it.

---

### Post by ed-koala on 2009-12-02
If your plan is to switch from Windows to Ubuntu, and you are looking for a program like Steady State so you can recover when your system gets hosed (am I reading your intentions right?), I don't think it'll be that necessary.  It's a lot tougher to hose Ubuntu than it is Windows, at least in my experience, to the point where you have to reinstall from scratch.

---

### Post by Bigtime_Scrub on 2009-12-02
Well you can always use a Live CD to get stuff back or I would suggest creating different user accounts for each person and YOU as the sole administrator. Put your foot down and say you have the P/W and you are not giving it to them until they learn to be responsible with it. Here is a nice quote:

```
snorri@rimu:~$ sudo vi /etc/resolv.conf

 We trust you have received the usual lecture from the local System
 Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

 Password:
 snorri is not in the sudoers file.  This incident will be reported.
 snorri@rimu:~$
```

I live by it and never have problems.

---

### Post by spydeyrch on 2009-12-02
thanks for the quick reponse. I had thought about using VB but they aren't too familiar with it and I really was looking for a one-stop-shopping kind of a thing. Don't get me wrong, I use VB on my personal system, Win7 & Ubuntu (both as host OS (dual boot system)) and my home server too. I have several different VMs in use at any given time.
 
They don't really have any windows dependant programs. Primarily word processing (OpenOffice), Chatting (Empathy/Pidgin), Internet surfing (Firefox), Media Playing (Rythombox, etc, etc). So they don't really ahve any windows dependant needs. I was just hoping to maybe find some kind of a similar solution in linux as there is in the windows world.
 
Any other input from anyone else would be greatly appreciated. Thanks to all!:D

---

### Post by spydeyrch on 2009-12-02
Wow, while I was replying, about 5 other responses came in befor eI could post mine. I will read and reply if needed. Thanks to everyone! Keep sending those responses my way!
 
 
 
:popcorn::D:):P

---

### Post by SushiR on 2009-12-02
Just have a look at the link and you will get the point...

[http://www.sudo.ws/sudo/sample.sudoers](http://www.sudo.ws/sudo/sample.sudoers)

---

### Post by spydeyrch on 2009-12-02
First off, thanks to everyone for the responses.
 
I thought of something that I could do but in the end it won't work. I do what Bigtime_Scrub mentioned and also setup a VPN so that I could manage anything remotely if needs be. But I remembered, that VPN doesn't work properly right now in 9.10. So that is out of the question.
 
I could do the whole user permissions thing, but that takes time but that might be my only choice. I know that ubuntu is much more difficult to botch than Win-DOH!-s but knowing this girl, she will find a way to kill it. She trashed her previous PC via the BIOS. Said she was "just playing around" So now I have to put an admin pswd on the BIOS and figure out what I am going to do about this steady state thing.
 
OH!!! :idea:
 
 
I just thought of something. Going back Bag-O-Stuff's idea, if I were to create a windows VM through Virtual Box, how could I auto start that specific VM? I know that I could start the Virtual Box app through the Start-up Programs in ubuntu, but that will just start the app and not the windows VM. So this is what I am thinking:
 
1.) Turn on machine
 
2.) Ubuntu boots and automatically logs into a normal user account
 
3.) Windows VM is auto started as soon as user account is auto logged into.
 
Step three is what I don't know how to do as of yet.
 
Thanks guys!

---

### Post by spydeyrch on 2009-12-02
thanks SushiR, I am checking out the link right now.
 
:)

---

### Post by ed-koala on 2009-12-02
Here's a link about auto running VB and the windows gust:

[http://ubuntuforums.org/showthread.php?t=758568]("http://ubuntuforums.org/showthread.php?t=758568")

---

### Post by winh8r on 2009-12-02
I sympathise with your predicament! I experienced a similar situation a few years ago but involving a home network with four computers- three of which were used by teenagers with the "click OK" mentality.
I remedied the situation in two ways- educate the children (truth is that most parents understand less about the computer than their children!)
and install the XP on a Virtual Box as suggested BUT (and here is the good bit) Charge the children a nominal fee every time they mess it up and can't fix the problem themselves.
I found that of the three teenagers, only one of them was still "paying" me £5 every time he screwed up his system after 6 months.

The other two actually learnt to do all the virus scanning and malware removal themselves and one of them only uses Ubuntu now.

Those who are reluctant to leave W*ndows just need the extra encouragement of having the free open source software concept explained to them.

****note**** I always gave the £5 back to his mother before I left, and she inevitably "lent" it to him later that week!!!

So, after all this rambling,I would suggest sitting them down and explaining Ubuntu and give them a Live CD.
Go for the Virtual Box option as a first step, then try the "Invoicing the teenager" trick. It is astonishing how quickly they become more responsible.
Good Luck.

---

### Post by ddarsow on 2009-12-02
I would simply do the following:
Install Ubuntu (separate /home partition)
Install the desired theme 
Install needed apps
Set Cron job to backup /home (& maybe etc/apt/sources.list) daily
Image the disk with CloneZilla

You now have an easy ability to restore to the original configured state at any time as well as to restore /home & re-download any newly installed apps anytime you need.

---

### Post by spydeyrch on 2009-12-02
Thanks everyone for your help, I appreciate it very much. I am going to try the auto start of a VM in VB that we have discussed and will come back later to let you all know how it went. Have a great day!
 
Oh, one other thing. I am going to post another thread here shortly about something compeletly unrelated but figured that since you all were so helpful, maybe you might be able to help me with my other completely random and really non-urgent question. Have a great day!
 
;)

---

### Post by spydeyrch on 2009-12-02
> **winh8r said:**
> I sympathise with your predicament! I experienced a similar situation a few years ago but involving a home network with four computers- three of which were used by teenagers with the "click OK" mentality.
I remedied the situation in two ways- educate the children (truth is that most parents understand less about the computer than their children!)
and install the XP on a Virtual Box as suggested BUT (and here is the good bit) Charge the children a nominal fee every time they mess it up and can't fix the problem themselves.
I found that of the three teenagers, only one of them was still "paying" me £5 every time he screwed up his system after 6 months.

The other two actually learnt to do all the virus scanning and malware removal themselves and one of them only uses Ubuntu now.

Those who are reluctant to leave W*ndows just need the extra encouragement of having the free open source software concept explained to them.

****note**** I always gave the £5 back to his mother before I left, and she inevitably "lent" it to him later that week!!!

So, after all this rambling,I would suggest sitting them down and explaining Ubuntu and give them a Live CD.
Go for the Virtual Box option as a first step, then try the "Invoicing the teenager" trick. It is astonishing how quickly they become more responsible.
Good Luck.
Ha, great idea there Winh8r! Charge the teenager-know-it-all! I think that I will do that!
 
Don't you just love mothers for their sympathy to their children. I remember when my mom would sneak me video games that my dad explicitly said i could not have. hahaha, they are GREAT!!!

---

### Post by spydeyrch on 2009-12-02
> **spydeyrch said:**
> Thanks everyone for your help, I appreciate it very much. I am going to try the auto start of a VM in VB that we have discussed and will come back later to let you all know how it went. Have a great day!
 
Oh, one other thing. I am going to post another thread here shortly about something compeletly unrelated but figured that since you all were so helpful, maybe you might be able to help me with my other completely random and really non-urgent question. Have a great day!
 
;)
This might even be simplier than the whole Win VM in VB thing. Plus it wouldn't use up a lisence key for win xp. Great idea!!! Thanks a ton! Will go with the VM/VB route first and test it out myself and then go with this idea if the vm/vb one doesn't pan out. thanks a ton!

---

### Post by spydeyrch on 2009-12-04
Ok guys, so I am still getting everything set up as was previously discussed. I can get the VM to start automatically once the user is logged on automatically. I do have one other question though.
 
The mother and daughter rarely shutdown their PCs BUT in the event that they do shut it down, with the way that I will have things set up, the VM will shutdown but then they will go straight to the ubuntu desktop, something that I would like to avoid if possible.
 
Any thoughts on what I could do possibly to avoid this issue?
 
I was thinking of a script that would monitor the VM. If the VM is on, the computer stays on. If the VM is off, the machines gets turned off automatically. It was the first idea that came to my mind.
 
Any others?
 
Also, I was thinking about taking away all panels and icons and everything on the ubuntu desktop except for two things:
 
-One large icon that starts the VM (in case the shutdown teh vm or something happens to it and they need to get back into it)
 
-One large shutdown icon. Once they clicked on it it would then bring up the shutdown menu (shutdown, restart, log off, etc.)
 
Any suggestions would be much appreciated. Thanks guys!!
 
-Spydey
 
:popcorn:

---

### Post by bshosey on 2009-12-04
If ubuntu does not satisfy their needs. Create new logon in Windows for the teen and disable Active X controls and remove admin rights from her account.

---

### Post by spydeyrch on 2009-12-04
Yeah, I know that I can disable active x and also disable admin rights on the accounts. Plus I plan on using windows Steady State to limit their ability to damage the system. I just thought that with ubuntu being the underlying system (host) and Windows being the usable OS (guest) then it would make things much easier if I ever had to fix anything. With Windows Steady State I can set user priv. and also what ever changes are made to the windows system, once teh machine is restarted, those changes are lost (on purpose). Let me explan a little:
 
Single computer
one hdd
Install ubuntu 9.04 x64 on HHD 1
Update ubuntu (no upgrading to 9.10 for reasons I can mention if you would like)
Install virtual box
Install microsoft windows xp x32 as a VM in virtual box (this would be vhdd1)
Update XP vm
Install all need programs and update accordingly.
setup a 2nd vhdd (virtual hard disk drive) as media drive (docs, pics, music, videos, etc)
transfer all media/docs to hdd 2
link all the "my ......(documents, music, videos, etc)" to the media drive (vhdd2)
install windows steady state in xp vm
setup steady state to:
 -cache all changes
 -set user permissions
 -allow windows updates
 -allow changes to media drive
 -don't allow changes to main xp drive (really it is a vm (virtual machine))
 -auto restart xp every 5 to 10 days so that the cache will be dumped and any "changes" to the main xp drive will be lost (lost on purpose with exceptions to windows updates)
take snap shot of xp vm in virtual box
take scheduled snap shots of vm per settings in virtual box
setup auto login to ubuntu desktop.
setup auto start of windows xp vm and fullscreen mode
remove all docs, icons, status updates, menus, etc from ubuntu desktop
place two icons on ubuntu desktop
 -Start Windows XP
 -Shutdown Computer
VOILA!!! FINNE!!!
 
By doing this, it will allow me to keep their windows machine more managable, they won't lose any of their documents or pics everytime their windows machine reboots but they won't be able to install any harmful programs. the daughter really likes limewire and kazaa, i.e. virus/malware heaven. She also liked to disable the antivirus. So, she won't be able to do that anymore. 
 
If for some reason she DOES make some kind of a change to the main drive, i.e. installs any programs or anything, those changes will be lost once the computer auto-restarts every week or so. But, it will keep the windows updates that come out every-so-often. Also, if something REALLY bad were to happen, I could just roll everything back to a more recent snapshot that was done in Virtual Box.
 
By having everything on a linux host, they aren't too familiar with linux so that gives me an avantage. It is more secure than win-DOH!-s, and plus, they won't have access to anything in ubuntu. All that they will see is an icon to start the VM if for some reason they get to the ubuntu desktop and the vm isn't running. And they will see a big shutdown button too. It is kind of time consuming but the end result, if it works like I am picturing it, will be very managable and do everything that they want plus the added security that they need.
 
I really don't just want to re-install their xp machine everytime because it is a pain in the ........... donkey (hehe :o) and plus it uses one of their licenses everytime it is done. and they don't pay me enough to do it every 3 months.
 
I understand how I can set it up in windows xp and I could even set everything up the same as mentioned above but without ubuntu and without vb (virtual box). Steady state is great in case something gets installed that shouldn't or if changes were made that shouldn't, but just as a safety net, I would prefer to do it this way.
 
The only other concern that I have is that I just realized, their cpu is an older Pentium 4 HT (Hyper-threaded), 512kb cache, 800Mhz FSB. I don't know I will be able to do virtualization on it!!!!!
 
Anybody know where I could find out if it would be able to support virtualization? I don't think that it has intels virtualization insturctions in it (v-tx, vx-t, vt-x, something like that).
 
Anyone? Thanks!

---

### Post by lykwydchykyn on 2009-12-04
> **spydeyrch said:**
> 
Anybody know where I could find out if it would be able to support virtualization? I don't think that it has intels virtualization insturctions in it (v-tx, vx-t, vt-x, something like that).
 
Anyone? Thanks!

VirtualBox does full virtualization, so no special processor capabilities are required.  XP might run a bit slow on an old processor; my kids run XP virtualized on my old Sempron 64 and it's horridly slow, but that's mostly because the poor beast only has 512 MB of RAM. 

How much RAM does this thing have?

---

### Post by Docaltmed on 2009-12-04
This is a behavioral problem, and the best answer for it is not a technical solution but a behavioral solution. I like the idea of charging the daughter for her "accidents."

---

### Post by lykwydchykyn on 2009-12-04
> **Docaltmed said:**
> This is a behavioral problem, and the best answer for it is not a technical solution but a behavioral solution. I like the idea of charging the daughter for her "accidents."

That may be true, but since these are clients who are presumably hiring the OP for his technical knowledge rather than his child-rearing knowledge, a technical solution is the only appropriate suggestion.

---

### Post by spydeyrch on 2009-12-04
The machine has 1.5 gigs of ddr PC3200 400Mhz. So I think that it shoudl run just fine, as far as ram goes. What do you think?
 
and yes, it is a HUGE behavioral problem. I have known the family for quite some time now. Good friends of my wife and our kids play together often. The oldest daughter (the problem at hand) is the reason for all of these issues and the some what radical way I am approching this.
 
i would LOVE to charge her for every time she screws up but in the end, the mom just pays for the daughters things so she wouldn't really learn her lesson. I GAVE her her own PC so that she would mess it up and learn to live with the consequences but that lasted 3 months and now the pc is in the trash! It was an older pc so really no loss there on my part.
 
But the daughter then went and "attacked" the mothers pc. So I came up with this definative solution. Just trying to work out the kinks.
 
What do you guys think of the solution? What could be the possile downfall(s) or areas of issue that might come up? How would I go about addressing those possible issues?
 
Oh, and thank you everyone for your input. It has helped me think this one through. :D
 
-Spydey

---

### Post by spydeyrch on 2009-12-07
Well, I got everything up and running and man, to be honest, it was AWESOME in thought and would be AWESOME if the machine wasn't really ......... mmmmmmmm.......... limited in it's ability to handle the kind of load that I was putting on it. It is a P4 2.4Ghz HT, 800Mhz FSB, 1.5 Gigs of 400Mhz DDR. I got everything up and running and well, it was pretty slow. It was like running vista on an old 1.0Ghz PIII. Pretty bad. I optimized all the virtual box settings, the host settings, and the guest settings. But still to close a window in the guest os (xp home) would take about 30 seconds. Not acceptable! That was with Windows Steady State installed. So I uninstalled it and decided to start the VM off the same snapshot every time it loaded, basically performing some of the same things that windows steady state does but doing it natively through VirtualBox. That didn't work to well either.
 
Don't get me wrong, Linux is great, and Virtual box is an industry leader in my humble opinion, but the machine just couldn't handle it and put out the kind of results that I was looking for.
 
I tried it on my machine, AMD Phenom 9950 (Quad Core) oc'd 3.2Ghz, 4 gigs DDR2 1066Mhz, and it ran smooth as butter on a baby's hind end!!!! Pure Sweetness and awe inspiring.
 
But her machine just couldn't handle it.
 
So I re-installed xp as the main OS, set some user priv., blocked certain areas of te os, and installed steady state. It has a nice gui to it but it is kind of a little buggy, won't save some of the settings that I have set.
 
I have the machine set to be accessible via a VPN from my machine to theirs and only I have admin rights. I have decided that they can't handle the power of admin and so I will do it until I feel that they are knowledgable enough to maintain their system. If it happens again, I am going full linux, either ubuntu or Mint 8 and that is the end of it.
 
Thanks everyone for your help, advise, and support. Your ideas were very much appreciated. I look forward to looking for guidance from you once again in the near future. Cheers for now!
 
-Spydey [IMG]http://images.zaazu.com/img/male36-male-spiderman-superhero-smiley-emoticon-000088-small.gif[/IMG]

---

