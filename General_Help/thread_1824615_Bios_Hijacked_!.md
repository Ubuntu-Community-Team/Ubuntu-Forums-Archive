---
title: "Bios Hijacked !?"
date: 2011-08-14
forum: General Help
---

### Post by Actonix on 2011-08-14
I started playing about with Ubuntu initially running off a CD and then moved on to installing on an SD card. All appeared fine till a Windows Network suddenly appeared in Nautilus where before I noticed none, I clicked on it as a user to find out more but had no joy so I switched over to an Administrative User session and clicked on it whereupon it disappeared and Nautilus said something to the effect it had no access to Network components - following this my Ethernet connection has started to flash persistently every 3 seconds. In an attempt t resolve this I removed my SD card ad resorted back to running just of the CD but the Windows Network remains as does the persistent flashing at my Ethernet jack.

I tried searching everywhere on the net for solution and came across a utility called Flashrom which I compiled and ran in order to try and backup my Bios but it aborted the run complaining of an Embedded Controller which might interfere with the process but I noticed a change it had made almost immediately - if I switch to a none-X session using Ctrl-Alt-Fx I see "SH: getcwd() failed : No such file or directory" appear above the ~$ prompt. I understand this to be an attempt at getting hold of a working directory but as I am only running off a CD I do not really have one which possibly attributes to the fail - but where is this command coming from ?.

My question is in multiples :roll:
... how do I get rid of whatever this Flashrom :twisted: has done as well as this silly Windows Network :evil: which appeared out of nowhere and is of absolutely no use to me - and am I right in considering both to be Bios rootkits of sorts  :confused:

---

### Post by asomad on 2011-08-14
^EEEK^.......... don't even know where to begin with this one. Please don't kill your computer, sir.......

---

### Post by kerry_s on 2011-08-14
The windows network is normal if you have a windows machine on the network. 
By default it's set to share but is empty if you haven't shared any folders. 

You should not be messing with the bios, you can brick the machine. 
I doubt flashrom did anything.

---

### Post by Actonix on 2011-08-14
I do not have a Windows Network or Windows machines on my network, just the one machine. And flashrom most definitely did something, played around with Ubuntu long enough to notice the immediate change and appearance of the getcwd() that appeared immediately after running flashrom - it was the only process I ran at the time - I cannot figure out why else the change and as I have no hard-disk or other storage attached to the machine I can only conclude that this info is held in the bios or on some other firmware on the machine as shuting down completely and restarting up does not get rid of this latest addition - as I said earlier on I have resorted to running Ubuntu just off the CD ie Not installed.

The Windows Network appeared of it's own accord, I have not attempted as yet to play around with samba shares or shares of any kind, quite the contrary, I have tried to ensure I have no shares and am not serving anything to the internet or network as my computer serves as more of a standalone workstation than a server of any sorts

In addition, where before Nautilus denied me any access to the Network properties of this "Windows Network" from Nautilus, after shutdown and reboot I can now access the properties but all it gives me is

Type:         unknown type (application/octet-stream)
Size :         unknown

Location:   network:///
Volume:     unknown

Accessed: unknown
Modified:    unknown


I now also notice when running System Monitor that several bash processes have appeared that where not there prior to running Flashrom with the Waiting Channel n_tty_read

---

### Post by asomad on 2011-08-14
cant you just pretend you dont see the windows network in there?

---

### Post by kerry_s on 2011-08-14
:lolflag:

i've seen lots a people do that after trying a different os. they "suddenly" notice something an flip out. its a windows mind set.

---

### Post by Actonix on 2011-08-14
> **asomad said:**
> cant you just pretend you dont see the windows network in there?

> **kerry_s said:**
> :lolflag:

i've seen lots a people do that after trying a different os. they "suddenly" notice something an flip out. its a windows mind set.


I appreciate your kind comments and attempts to help but despite your kind intentions you offer me no genuine help of any sorts - if you do not have the specialist knowledge to deal with or are unable to offer genuine help with a problem it would be most helpful that you ignore the existence of that problem rather than trying to get the problem holder to ignore it.

---

### Post by kerry_s on 2011-08-14
see pic, is that what your seeing?

if so, like i said its normal.

---

### Post by 3rdalbum on 2011-08-14
On Linux, the BIOS does practically nothing. It sets the mode for your integrated chipsets, it handles fan speeds and it starts up GRUB. Nothing in the BIOS would cause the "getcwd" to fail - that's a purely OS-level function that has no need for anything to do with the BIOS.

Remember, BIOS is only on x86 computers, and Linux is made to work on all sorts of computers, most of which don't have BIOS.

I don't think your BIOS has been altered. If it was altered I'm pretty sure it wouldn't work for booting up your computer. It certainly wouldn't cause the error message you report.

---

### Post by Actonix on 2011-08-14
> **kerry_s said:**
> see pic, is that what your seeing?

if so, like i said its normal.

So, from Nautilus have you ever clicked on you Windows Network and have it disappear on you and deny you access ?

... and do you also have your Ethernet connection flashing every 3 seconds even when there is no activity going on ? - eg you are not actively browsing and have no other apps running, in fact you could even exit your browser just to make sure.

I ran Ubuntu day in and day out for over 6 weeks with none of this happening even after retrieving all the updates, playing around with UFW and Firestarter and another python based firewall gui to determine which offered me the best functionality, and hardened my security in many different ways. Only using an app like Streamer to listen to i-radio would cause as much activity on my Ehternet port as I am seeing and as soon as I would shut that down it would quit flashing - not the case now, it's continually flashing even if I disconnect my internet connection it continues to flash - all this since the Windows Network appeared of it's own accord and gave me the access denied message and temporarily disappeared when I tried to access it - and it shows no details on the property page either but Nautilus is not complaining about me trying to view it's properties, nor is it disappearing as it did that one time.

And these new Bash processes that are sleeping with waiting channel n_tty_read are just compounding the problem though they appeared much further down the line after the Windows network incident as did the getcwd() failure - both of which I separately attribute to Flashrom

 Admittedly I am relatively new to Ubuntu but I'm no novice to computing having worked i the industry for over 2 decades and I know I have an issue here which I also believe it is beyond your understanding so all I can do at this point is thank you for your attempts at helping me thus far and hope that someone that is more capable of understanding and getting to grips with my problems comes to my assistance

---

### Post by kerry_s on 2011-08-14
Alright then, good luck.

---

### Post by VipX1 on 2011-08-14
I also have worked in computers for over ten years and I know for a fact that an OS can NOT modify a BIOS Flash. In order for the BIOS memory to be modified the computer must switch of and load a temp BIOS to RAM. Then the temp BIOS Flashes the actual BIOS pulling in the new files from a predefined position then the PC reboots a second time this time using the new modified BIOS.

Even in doing this the BIOS update software is on a per-motherboard basis. It would be an amazing Virus that could change your BIOS in between boots.

If you worked in computers so long you should know that!

---

### Post by grahammechanical on 2011-08-14
First things first. There are many more Windows machines in the world than Ubuntu machines. So, to make it easier to network or share files with a Windows machine Ubuntu has folder called Network and in it a folder called Windows Network. What a person does with this I have no idea as I have no need to share files over a network with a Windows machine.

When I click on that folder my ethernet light flashes. This is because machine is trying to connect to a Windows machine. This is what it is programmed to do to make things easier. I get an error message saying that folder cannot be opened. I guess that if I had set up my machine to connect to a Windows machine then that folder would open and I would be able to access files on the windows machine. And I would be glad that Ubuntu made things that easy.

You have Ubuntu installed on a SD. Then you removed the SD. Did you shutdown Ubuntu first? Were you also dual booting with another OS? If so, then removing a drive that the booting process expects to see there would produce errors. Would it not?

Think about the action that you have taken. It may help work out what has happened and what to do to put it right.

---

### Post by VipX1 on 2011-08-14
If you a concerned about your network traffic the install EtherApe. Close/Exit any Browser, Instant Message  and Network Sync Software. Then look at EtherApe to see what IP Addresses you connected to and note the color code in order to interpret the type of protocol.
This will help you figure out what the flashing LAN is doing.

```
sudo apt-get install etherape
```
```
gksudo etherape
```

Note: Set your interface to the flashing LAN connection, probably eth0.

---

### Post by Actonix on 2011-08-14
> **VipX1 said:**
> I also have worked in computers for over ten years and I know for a fact that an OS can NOT modify a BIOS Flash. In order for the BIOS memory to be modified the computer must switch of and load a temp BIOS to RAM. Then the temp BIOS Flashes the actual BIOS pulling in the new files from a predefined position then the PC reboots a second time this time using the new modified BIOS.

Even in doing this the BIOS update software is on a per-motherboard basis. It would be an amazing Virus that could change your BIOS in between boots.

If you worked in computers so long you should know that!

> **3rdalbum said:**
> On Linux, the BIOS does practically nothing. It  sets the mode for your integrated chipsets, it handles fan speeds and  it starts up GRUB. Nothing in the BIOS would cause the "getcwd" to fail -  that's a purely OS-level function that has no need for anything to do  with the BIOS.

Remember, BIOS is only on x86 computers, and Linux is made to work on all sorts of computers, most of which don't have BIOS.

I don't think your BIOS has been altered. If it was altered I'm pretty  sure it wouldn't work for booting up your computer. It certainly  wouldn't cause the error message you report.


Not  bothered about the getcwd() call failing - I am bothered about the  getcwd call being made in the first place where before it wasn't being  made - if Ubuntu was installed (on my SD card which - as I have tried to explain - is no longer  attached to the System) the getcwd() would not fail as I would in fact  have a verifiable working directory to be called on - not the case here,  thus the failing.

 - and you are missing the fact that I have  sleeping bash processes which I associate with the getcwd() where before  I had none - I count one for each of the possible non-X sessions I  could have via Ctrl-Alt-Fx or maybe Ctrl-Alt-t is closer to Linux speak -  in other words I now have 7 sleeping bash processes where before I had  none - one for each of the 7 possible non-X based or should I say  command-line tty sessions and System monitor reports them as being on  Waiting Channel n_tty_read.

I don't not understand what is bringing this stuff up about modifying the Bios in btw boots and neither do I understand where the OS modifying the Bios came from !!? ... already said I ran a utility called flashrom. maybe you ought to download, compile and run it yourself, I have examined parts of the code since and I can tell you that I am impressed at the extensive list of different Roms it can flash as well as it's cross-platform-ability (all you need to do is read the comments against the coding or even just what's available in the change-logs, 
... I thought I was behind the times but I see I am not alone there, I think quite a few people here too could do with learning just what is out there, but I digress. 

But before I go on, I think maybe people need to  realise that the Bios does that bit more, Yes, it basically serves as a  library of basic input/output functions used to  operate and control the peripherals such as the keyboard, text display  functions and so forth, but these software library functions function  independently of any OS and can as well be callable by external hardware and  software which naturally includes but is not restricted to your OS - the fact that your Bios has been added to or altered does not mean it should stop  functioning any more than you putting a Hat on your head should stop you  from functioning.

As I have tried to explain, I am running off a  CD - If the getcwd() is not being stored on firmware and on shutdown  and reboot it is still making it's calls and causing these 7 Bash  processes to show up in System Monitor where for 6 to 8 weeks weeks of  prior playing around with Ubuntu they did not - where is it being stored  !? ... on my CD perhaps or non-existent boot-loader ?

... why am I not getting the default Ubuntu setup I had played and become intimately familiar with for the prior 6 to 8 weeks after a reboot ?

In that period if anything went wrong all I had to do was shutdown and startup again and it was back to normal - not the case now.

---

### Post by SoFl W on 2011-08-14
Do you have a networked printer?  My networked printer has an SD card to save scans.  To access the SD card on the network printer in uses...a Windows share.

---

### Post by Actonix on 2011-08-14
> **SoFl W said:**
> Do you have a networked printer?  My networked printer has an SD card to save scans.  To access the SD card on the network printer in uses...a Windows share.

Nope, no network printers, systems or peripherals of any sort apart from my router ...

... but I do notice one thing I am not sure about, the zeitgeist-datah process is a Zombie with do_exit as the waiting channel which I do not think was the case before and I did notice a few duplicate processes with different IDs over a few days before the Windows network incident, not exactly sure about which ones they were but they had each lost a character ie where a process ended with the name ...daemon it became daemo and they eventually all became Zombies too

... and these 7 new bash processes with n_tty_read as the Waiting Channel still leave me somewhat perplexed

---

### Post by Duncan Williams on 2011-08-14
stated > *On Linux, the BIOS does practically nothing. It sets the mode for your integrated chipsets, it handles fan speeds and it starts up GRUB. Nothing in the BIOS would cause the "getcwd" to fail - that's a purely OS-level function that has no need for anything to do with the BIOS.*

Every setting in the bios will affect whatever operating system you are booting.
One incorrect setting can cause your system to crash, stumble or fail.

Bios rootkits or other malware can wreak havoc and cause failure.
Flashing a bios is a bit of a gamble especially if it doesn't complete.

---

### Post by Actonix on 2011-08-14
> **grahammechanical said:**
> First things first. There are many more Windows machines in the world than Ubuntu machines. So, to make it easier to network or share files with a Windows machine Ubuntu has folder called Network and in it a folder called Windows Network. What a person does with this I have no idea as I have no need to share files over a network with a Windows machine.

When I click on that folder my ethernet light flashes. This is because machine is trying to connect to a Windows machine. This is what it is programmed to do to make things easier. I get an error message saying that folder cannot be opened. I guess that if I had set up my machine to connect to a Windows machine then that folder would open and I would be able to access files on the windows machine. And I would be glad that Ubuntu made things that easy.

You have Ubuntu installed on a SD. Then you removed the SD. Did you shutdown Ubuntu first? Were you also dual booting with another OS? If so, then removing a drive that the booting process expects to see there would produce errors. Would it not?

Think about the action that you have taken. It may help work out what has happened and what to do to put it right.

I had Ubuntu installed on an SD. I no longer have an SD card or any other storage media attached to my PC other than the CD-Rom drive with the Ubuntu CD in it which I boot off. As far as I am aware there is no other medium to hold a boot manager or keep any boot code apart from the boot code on the CD itself, if there is then that could be were my problem lies.

My Ethernet port starts flashing persistently as soon as I plug a cable into it, was the not the case before. It would only start flashing when I instigated a Network connection - it is not set to Connect  Automatically.

Samba was created to enable one setup Windows shares, back in the day when I started playing with Linux one had to set up those shares themselves, apparently not the case today but why I should have a Windows share setup for me when I do not need it baffles me, neither does it really help in isolating and identifying just what is going on here.

---

### Post by Actonix on 2011-08-14
> **Duncan Williams said:**
> stated > *On Linux, the BIOS does  practically nothing. It sets the mode for your integrated chipsets, it  handles fan speeds and it starts up GRUB. Nothing in the BIOS would  cause the "getcwd" to fail - that's a purely OS-level function that has  no need for anything to do with the BIOS.*

Every setting in the bios will affect whatever operating system you are booting.
One incorrect setting can cause your system to crash, stumble or fail.

Bios rootkits or other malware can wreak havoc and cause failure.
Flashing a bios is a bit of a gamble especially if it doesn't complete.

Slight correction - Every setting in the bios can affect whatever operating system you are booting.

Yes, taken for granted - but it not completing does not explain why a getcwd() call is being issued on all tty's after a failed attempt that allegedly did nothing but abort due to EC possibly being present, neither does it explain the 7 new bash processes listed in System Monitor, especially as I'm running off a CD and a reboot should give me a fresh start - but I guess your statement just prior takes care of that ;) - Bios rootkits or other malware can wreak havoc and cause failure

 ... how to recover from it remains the question, any capable experts in the forum !?

---

### Post by Duncan Williams on 2011-08-14
some bios's have an option to purge and re-install bios defaults.
I had a friend who had a bios affected by rootkit and he ended up sorting it out in this sort of way.
Have a look around here:
[http://www.google.com.au/search?client=opera&rls=en&q=reset+bios&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest](http://www.google.com.au/search?client=opera&rls=en&q=reset+bios&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest)

---

### Post by Duncan Williams on 2011-08-14
also > info > bios malware:
[http://www.google.com.au/search?client=opera&rls=en&q=reset+bios&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest#sclient=psy&hl=en&client=opera&rls=en&channel=suggest&source=hp&q=bios+malware&aq=f&aqi=&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=9423ea04b8339924&biw=1258&bih=622](http://www.google.com.au/search?client=opera&rls=en&q=reset+bios&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest#sclient=psy&hl=en&client=opera&rls=en&channel=suggest&source=hp&q=bios+malware&aq=f&aqi=&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=9423ea04b8339924&biw=1258&bih=622)

In there you will see that the flashrom can cause the rootkit (amongst other things)

Don't get paranoid though .  It may be something else...

---

### Post by Actonix on 2011-08-14
> **Duncan Williams said:**
> also > info > bios malware:
[http://www.google.com.au/search?client=opera&rls=en&q=reset+bios&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest#sclient=psy&hl=en&client=opera&rls=en&channel=suggest&source=hp&q=bios+malware&aq=f&aqi=&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=9423ea04b8339924&biw=1258&bih=622](http://www.google.com.au/search?client=opera&rls=en&q=reset+bios&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest#sclient=psy&hl=en&client=opera&rls=en&channel=suggest&source=hp&q=bios+malware&aq=f&aqi=&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=9423ea04b8339924&biw=1258&bih=622)

In there you will see that the flashrom can cause the rootkit (amongst other things)

Don't get paranoid though .  It may be something else...


Paranoid !!? ... whas dat !!?  ... I'm only phreaking out here ;)

Thanks for providing those links (y)
... tried to access them but with both Mozzy-ff tells me :-

The connection was reset
          
          The connection to the server was reset while the page was loading   			[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]  :confused:


... any possibility you can post the contents that would be of interest ?

---

### Post by bkratz on 2011-08-14
Read the posting date (when you can get back on it). It appears that this is not new and has been around a long time.

---

### Post by asomad on 2011-08-14
> **Actonix said:**
> I appreciate your kind comments and attempts to help but despite your kind intentions you offer me no genuine help of any sorts - if you do not have the specialist knowledge to deal with or are unable to offer genuine help with a problem it would be most helpful that you ignore the existence of that problem rather than trying to get the problem holder to ignore it.


I'm not really sure what it is you need help with? You have a problem with something thats supposed to show there... Add in that your running your Ubuntu "Live" or with "Casper", I can't understand why your trying to troubleshoot an OS with limited capabilities meant mainly for trial and simple operations. If I were you, I'd decide to do an actual HD install of Ubuntu before you worry about every little inner working, especially things you should not be playing with, without proper experience. I was offering advice, I said "Please dont kill your computer", meaning stop doing what you were doing.

Edit, on second thought, leave your Ubuntu on your memory card, DONT install it anywhere! I wouldn't want any innocent HDDs to get hurt in the process...

---

### Post by Duncan Williams on 2011-08-15
Don't want to freak anyone out, but, if you check the **latest**
Linux security sites, and the **latest** anti malware sites.
Android, chrome, linux and mac's are getting hit with nu-age rootkits and malware. as well as some serious hacks and keylogging...

---

### Post by Zill on 2011-08-15
> **Duncan Williams said:**
> Don't want to freak anyone out, but, if you check the **latest**
Linux security sites, and the **latest** anti malware sites.
Android, chrome, linux and mac's are getting hit with nu-age rootkits and malware. as well as some serious hacks and keylogging...
Rather than such glib statements I suggest it would be more helpful if you would post appropriate links to this "latest" info (not just a Google search link!)

It would be interesting to see if there is actually a single instance of a compromised fully-updated Linux system.  Such details would, of course, be invaluable to the gurus in helping to remove such vulnerabilities.

---

### Post by Duncan Williams on 2011-08-15
I am not going to spend the time digging up all the recent security articles I have read.
Suffice to say that I have seen quite a few over the last couple of months.
Android and smartphones recalled, appstores with malware onboard their apps,  Apple freaking over the fact that has been accused of being less secure than windows.
Constantly fixed and updated linux issues.

I am not saying anything more than rootkits and malware exist and not just for windows.

one of many sources that I tend to read :
[http://www.linuxsecurity.com/content/view/155635?rdf](http://www.linuxsecurity.com/content/view/155635?rdf)

---

### Post by Actonix on 2011-08-15
> **asomad said:**
> I'm not really sure what it is you need help  with? You have a problem with something thats supposed to show there...  Add in that your running your Ubuntu "Live" or with "Casper", I can't  understand why your trying to troubleshoot an OS with limited  capabilities meant mainly for trial and simple operations. If I were  you, I'd decide to do an actual HD install of Ubuntu before you worry  about every little inner working, especially things you should not be  playing with, without proper experience. I was offering advice, I said  "Please dont kill your computer", meaning stop doing what you were  doing.

Edit, on second thought, leave your Ubuntu on your memory card, DONT  install it anywhere! I wouldn't want any innocent HDDs to get hurt in  the process...


Well, what can I do to get you to understand what it is I need help with !!?

*Sigh* - Let me try, I will only stick to one of the problems for now in the hopes of simplifying things, I think I have need to clarify myself again so forgive me if I appear to be parroting myself ;(

First of, I feel the need to address your quote :-"* ... Add in that your running your Ubuntu "Live" or with "Casper", I can't  understand why your trying to troubleshoot an OS with limited  capabilities meant mainly for trial and simple operations. If I were  you, I'd decide to do an actual HD install of Ubuntu before you worry  about every little inner working, especially things you should not be  playing with, without proper experience*."

!!!? - I don't know what you  consider to be proper experience under the circumstance, perhaps you can  expand on that having read my prior postings, then again you do not  appear to have taken in anything I have posted otherwise you would  already have a relatively clear understanding of my problem and would  not have made this posting.

 - are you trying to say that  despite my having identified a problem, because I currently lack the  ability or sufficient knowledge to deal with the problem I should simply  desist from looking for a solution in the form of advice from people  that might be in the know and neither should I pursue any furthering of  my knowledge in the area in question - in other words I should roll over  and kick the bucket ?

Further Clarification (have to try my parrot alter-ego here)
 - Yes, I am running of a Live CD and Yes, it does appear to be Casper I am running.
 - and as explained in earlier postings - Prior to resorting back to the Live CD I did have the full install of  Ubuntu which was patched and fully Updated - but events led me to wipe  that out and resort back to the Live CD - despite this the events that  made me resort to reverting back to the Live CD persist while running  the Live CD.
- I do not have any other normal storage mediums attached to my PC that is apart from the external-CD-Rom drive holding the Live-CD, and yes, that includes the CD card, and any hard drives.

Here is an excerpt I just read from -> [http://www.linuxsecurity.com/content/view/154709/171/](http://www.linuxsecurity.com/content/view/154709/171/)
===================================
" **Detecting and Removing Rootkits**
The problem with detecting good rootkits are that you can't even trust  the kernel and operating system in which the rootkit is installed on.   So this makes it hard to detect them by installing detection software  directly on the affected operating system.  A better solution is to  install a packet sniffer on an unaffected machine to look at the  information being sent to and from the machine which might have a  rootkit installed on it. Looking at the local log files will not always  allows the system administrator to detect an attacker using a rootkit  because the rootkit can delete the entries the attacker makes. _***Another  way to detect rootkits are to boot from a live CD.  This allows you to  trust the kernel and the software running on the linux CD to investigate  the files on the possibly affected computer for rootkits.***_ Also there  are programs which try to find rootkits locally like chkrootkit however  this program depends on the local ps command to find them. As we know a  rootkit can change the ps command to what it likes.  Another problem  with this approach is that the rootkit can detect and change the  chkrootkit software.  If the user finds the rootkit sometimes it is very  hard to make sure that it has been removed.  Most experts recommend  that one should just reformat the system and start over.  If using  backups make sure that the backed up files don't contain harmful files.  There is software which tries to remove rootkits called  Rkdetector  v2.0.  Detecting and removing is so hard because they are designed to be  hard to detect and remove. "
===================================

Now, the area I underlined & highlighted is of particular significance here. 

Why !!? ... well, let's examine the underlined section !?

I  am running off the Live CD - but the changes I mention which occurred  on my prior install to SD card "persist" even though I am running off  the Live CD - now if I cannot even trust the Kernel and Software running off  the Live CD what does that tell you !?

***** ***Does that in any way help you understand one area that I am looking for assistance in !!?*** *****

Just to avoid having you shoot of at a tangent let me further clarify - I am not trying to trouble shoot  an OS with limited  capabilities meant mainly for trial and simple operations - I am trying  to get to grips with and eradicate what I can only determine to be a  BIOS Rootkit of sorts - this has deeper implications than just an install of Ubuntu but includes virtually any other OS I might  choose to install down the line - with so little experience atm in just what  is going on I can only conclude that is  where my problem lies - and no matter how you read that, that does not say I have or do not have more experience  than you in areas outside this that are OS or I.T. related, nor does it give rise for you to try and pigeon-hole, question or belittle me and/or my experience simply because I am seeking advice .

The mere fact that I  have mentioned the getcwd() calls that resulted from the Flashrom and am still getting even though I have resorted to and am now booting and running off the CD - and where before  there where none being made either with the Live CD or my prior install  onto SD before the Flashrom incident - implies that whatever it is is  more than likely embedded in firmware.

My concluding this to be the case is further  backed up by the fact that I also have at least 7 bash processes showing  up in my System Monitor where before there where none - and these are  just the notable changes that I am aware off, there is no saying the  extent off the encroachment/infestation that has occurred.

Forgive  me for asking but I have to question just how much consideration you actually put into providing the advice you do and what exactly is your motivation for doing so !!?

 - are you really trying to help or is there some ulterior motive here !!?  ... so far that consideration only appears as an after thought and in withdrawal of prior posted advice neither of which, in anyway that I can see, help me anyhow.

And what  exactly do you mean when you make the suggestion, and I quote :-  *"If I  were you, I'd decide to do an actual HD install of Ubuntu before you  worry about every little inner  working, especially things you should not be playing with ..."* !!!?

...  do you mean there is some significant difference in installing to a HD  rather than an SD other than the performance advantages to be thus  gained ?  ... I am glad you thought to withdraw that advice but I cannot  help but be curious about the reasons why you gave the advice in the  first place, perhaps there is something I am missing that would serve me  well to know about seeing as I should not be playing around at trying  to deal with what I can see to be a very obvious problem !?

 - please, feel free to enlighten me  further, actually I'd be most appreciative if you did, especially if it  in anyway assists me in dealing with my problems - or maybe you should  learn to take your advice and steer away from problems where the only  solution you can provide is for the  problem holder  not to deal with but instead stick their head in the sand in an attempt to ignore the presence of a problem and perhaps hopefully revert  to and thereafter remain in blissful ignorance of ongoings.

---

### Post by asomad on 2011-08-20
one, the windows network icon is normal.

two, You think somethings wrong with you BIOS, when I'm guessing, it's your USB ubuntu installation that has been altered.

three, Why did you start messing with your bios in the first place? You could have ruined your motherboard, and you are lucky it's in one piece.

four, rootkitting is getting common, but, I doubt it's what happened here. (to a lone usb boot pc, on a lone network, not being used for any real purpose?.... come on.....)

five, what happened here is user curiosity leading blindly to using utilities, to blindly altering your Ubuntu installation.

Six, you describe trying to do alot of things with your usb installation, that would be better done on a "real HDD install"

Seven, I advised against a real HDD install in your case, because a hard drive install, means more hardware at risk of user-destruction. And I feel all hardware is entitled to life, liberty, and the pursuit of happiness....    However, here's instructions to doing so, if you would like your ubuntu to be full function (and much faster). Buy a HDD, install in your pc (usually a SATA cable between your HDD and motherboard, and sata-power connecter to the power supply). Boot Ubuntu from a Live CD or USB stick, chosing the "install ubuntu" option on startup (or alternatively on the desktop there may be an icon titled "install Ubuntu") follow the next buttons. the end.

Eight, Im not offering advice, perhaps you really do have a virus or rootkit, However, I highly highly doubt it. see one through five above for my educated opinion.

---

### Post by asomad on 2011-08-20
and one more note, The live CD, and what you would have installed on a Memory stick, should be the same thing. Unless your prior install was on SD card acting as a HDD (which is BAD, kills ur stick) why would you expect any difference between each?

And after reading through this entire thread again, I still don't know why you think you have a rootkit or "virus". Im not saying ignore a virus, Im saying WHY do you think you even have one? Besides noticing a "new" icon, that wasn't "new", it was already there. and when you start clicking around, in any OS, strange things happen. I can click around my laptop in the wrong fashion and make share folders disappear in windows and do other weird things. OH MY I MUST HAVE A COMPROMISED BIOS, I gotta go fix that! ttyl

And if something IS persisting between installs, It could be a mem-stick based worm, (which is technically a root-kit), however it is NOT the type of rootkit you think you have. and any decent free AV software can remove it, but if your infected, you'll need a clean pc to aid you in your adventure. best wishes

---

### Post by Duncan Williams on 2011-08-20
stated: *`three, Why did you start messing with your bios in the first place? You could have ruined your motherboard, and you are lucky it's in one piece.'*

Erm, you might be losing the plot a bit here, it's pretty near impossible to ruin your motherboard through bios settings.

You can, however, create an unstable or unusable computer with incorrect settings in the bios.

And also, just because things are rare. It doesn't mean they don't exist. (have you ever won the lottery)

---

### Post by asomad on 2011-08-20
> **Duncan Williams said:**
> stated: *`three, Why did you start messing with your bios in the first place? You could have ruined your motherboard, and you are lucky it's in one piece.'*

Erm, you might be losing the plot a bit here, it's pretty near impossible to ruin your motherboard through bios settings.

You can, however, create an unstable or unusable computer with incorrect settings in the bios.

And also, just because things are rare. It doesn't mean they don't exist. (have you ever won the lottery)

changing bios settings is not what the gentleman was doing. bios FLASHING is what he was attempting. (but, nice try...)

If your flashing software, or your system (power fluctuation etc.) has even the smallest error, during the flashing of the CMOS, you** absolutely** can destroy your bios, and thus your motherboard, unless your an expert with Jtag or rom chips in general.

If i'm wrong here then i'm wrong. But that is why any tech will tell you, you never flash BIOS or any rom chip, without GOOD cause, and even with good cause, YOU MUST BE CAREFUL.

---

### Post by asomad on 2011-08-20
> **VipX1 said:**
> I also have worked in computers for over ten years and I know for a fact that an OS can NOT modify a BIOS Flash. In order for the BIOS memory to be modified the computer must switch of and load a temp BIOS to RAM. Then the temp BIOS Flashes the actual BIOS pulling in the new files from a predefined position then the PC reboots a second time this time using the new modified BIOS.
not entirely correct.... There are utilities that run in a booted OS, that can and DO flash CMOS. However these utilities are buggy and risky, even the ones released by motherboard manufacturers for their own products.. And I will bet this is exactly the type of utility our gentleman here was using...

---

### Post by asomad on 2011-08-20
can we change the thread title to, "techs discuss things in detail"... this is an interesting thread and I'd hate for half of it to be considered as off-topic.       :-)

---

### Post by Actonix on 2011-08-20
_> **asomad said:**
> one, the windows network icon is normal.*_> **asomad said:**
> 

I don't doubt the Windows Network icon is normal, if you go and read  back I questioned the behaviour associated with the icon -> it's  disappearance when I clicked on it as an Administrative user and the  subsequent denial message from Nautilus telling me that it could not  access network properties but later allowing me to do so 

_*two, You think somethings wrong with you BIOS, when I'm guessing, it's your USB ubuntu installation that has been altered.*_

No, You are the one doing a whole load of guessing without much by way of  comprehension either even though more than enough detail has been provided, I know something is wrong with my BIOS and have  actually since accessed a copy of my BIOS, pinpointed the ROM modules  affected and am working on a fix.

[I]_three, Why did you start messing with your bios in the first place?  You could have ruined your motherboard, and you are lucky it's in one  piece._
[/I] 
Why !!? ... because I have a problem that I am seeking to resolve and  with the lack of support in this area and the only forthcoming advice is  from people like you telling me to turn a blind eye to it, fortunately I  don't have to rely on people like you - and I am still messing with my  BIOS because I am capable of doing so, I ask again, what exactly are you hoping to achieve here ?[I]
 - If you are looking for Brownie points I would advice that you go join the Brownies.
  
_ four, rootkitting is getting common, but, I doubt it's what happened  here. (to a lone usb boot pc, on a lone network, not being used for any  real purpose?.... come on.....)_[/I]

Right or wrong, You are entitled to you opinion but I think you ought to  learn when best to keep it to yourself or dig deeper to confirm your  beliefs especially when you really don't have a clue especially as  regards my setup.

_*five, what happened here is user curiosity leading blindly to using utilities, to blindly altering your Ubuntu installation.*_

Blindly you say, but you don't know how much study of "the" (singular -  meaning one) utility went on prior to using it, not to talk of all the  other avenues investigated prior to doing so and the ongoing collective  study that persists. Feel free to continue try in vain to belittle ones  attempts at finding a resolution to their problem, but if you seek  success at bringing one down to your level you would do better to look  elsewhere - but feel free to make a complete fool of yourself.

[I]_Six, you describe trying to do alot of things with your usb installation, that would be better done on a "real HDD install"_
 [/I]
Sad that you continue to make stupendous claims and base your  non-objective responses on pure  assumption instead of the brief laid  out before you. Why do you hesitate to back that last statement up with  something tangible despite being asked to do so - once again please  explain and help me better understand what difference a HDD install will  bring to the table over an SD install - I have more than enough drives  for the sacrifice all the way down from MFM's to the latest SSD's  available today, inclusive of SCSI's too  - but not while you remain  clueless and bring nothing to the table.

[I]_Seven, I advised against a real HDD install in your case, because a  hard drive install, means more hardware at risk of user-destruction. And  I feel all hardware is entitled to life, liberty, and the pursuit of  happiness....    However, here's instructions to doing so, if you would  like your ubuntu to be full function (and much faster). Buy a HDD,  install in your pc (usually a SATA cable between your HDD and  motherboard, and sata-power connecter to the power supply). Boot Ubuntu  from a Live CD or USB stick, chosing the "install ubuntu" option on  startup (or alternatively on the desktop there may be an icon titled  "install Ubuntu") follow the next buttons. the end._
[/I] 
Forget performance - I am happy with what I get out of an SD install in  that regards, at least for now - but as for your claim of full function  which I take to mean full functionality of sorts - I am very much  interested in finding out more, might just be the way to go and I would  be willing to do so if I knew more !!

... sadly it sounds more like a waste of my time, actually I know it's a  waste of my time but I'll remain open to be convinced otherwise.

_*Eight, Im not offering advice, perhaps you really do have a virus or  rootkit, However, I highly highly doubt it. see one through five above  for my educated opinion.*_
... educated opinion !!!!!!? ... sorry to say, you are found sadly lacking and wanting, seek further education.

---

### Post by Actonix on 2011-08-20
> **asomad said:**
> changing bios settings is not what the gentleman was doing. bios FLASHING is what he was attempting. (but, nice try...)

If your flashing software, or your system (power fluctuation etc.) has even the smallest error, during the flashing of the CMOS, you** absolutely** can destroy your bios, and thus your motherboard, unless your an expert with Jtag or rom chips in general.

If i'm wrong here then i'm wrong. But that is why any tech will tell you, you never flash BIOS or any rom chip, without GOOD cause, and even with good cause, YOU MUST BE CAREFUL.

lol - Thanks for your advice - Just FYI, I have successfully flashed my BIOS from within and outside of Linux, I have even succecfully taken my BIOS configuration backwards which many have claimed impossible to do as the manufacturer does not provide the means to do so - and if I failed and bricked up my computer it would not be the first time and not necessarily the last either.

Added to that. in this instance, I have successfully identified and removed a ROM module which has code I did not order with nor was I informed existed on my PC as I am not interested in having it on my PC. What I have not succeeded in doing as of yet is modifying particular ROM modules as I am being as careful as I can be in doing so as it is intermingled with original code from the manufacturer which would adversely affect functionality.

---

### Post by dave01945 on 2011-08-20
> **Actonix said:**
> lol - Thanks for your advice - Just FYI, I have successfully flashed my BIOS from within and outside of Linux, 

why would you flash it twice anyone that knows about computers knows bios flashing is **not advised**

good luck anyway this thread is fun to watch

also if you've flashed your bios that bios rootkit should be gone

---

### Post by asomad on 2011-08-20
The difference between a real install (on a HDD), versus an install on a memory card, is not just an issue of perfomance. Casper is the way a "live" install acts like a "real" install. It creates a file on the memory stick which is used to store all of your data. 

When you are running a live install like that, And you make changes within the operating system, those changes are applied because "casper" makes a copy of any file you edit and stores it in its own folder. Upon boot the folder is accessed, and any files found in it, are substituted for the files on your memory sitck (this is a simplification of the process just to illustrate the point). The files within the Operating system itself are NOT actually modified, ever, they are treated as read-only. Casper gives you the illusion of a normally working operating system, while using only read-only files that are never actually altered. This is great for on-the go convenience, but limits certain things you can do to your system's configuration, especially at boot. There are instances when a changed file (i.e. changed system setting) can not be dealt with properly by casper. I'm sure you'd love a specific example, please refer to the **HUNDREDS** of bugs with casper not saving or loading certain changes the user has applied, and many many other issues.

Hence the reason why I don't think anyone would or should spend too much time trying to troubleshoot a "live" installation

and I did offer advice to you, if you had read the next few posts after the one you replied to. And if you have bad CMOS chips on your board, I'm sorry to hear that, but I'll bet money you and your utility you used, were the cause.

---

### Post by Actonix on 2011-08-20
> **asomad said:**
> and one more note, T.... blah-di-blah-blah-blah .... Im not saying ignore a virus, Im saying WHY do you think you even have one? .... and when you start clicking around, in any OS, strange things happen .... And if something IS persisting between installs, It could be a mem-stick based worm, (which is technically a root-kit) .... blah-blah 

Already explained all that, and I do not see how a mem-stick based worm can persist without the PC having access to the stick and the only attached storage medium being the CD-Rom drive !!!?

... do you read with blinkers on ?

---

### Post by Actonix on 2011-08-20
> **asomad said:**
> The difference between a real install (on a HDD), versus an install on a memory card, is not just an issue of perfomance. Casper is the way a "live" install acts like a "real" install. It creates a file on the memory stick which is used to store all of your data. 

When you are running a live install like that, And you make changes within the operating system, those changes are applied because "casper" makes a copy of any file you edit and stores it in its own folder. Upon boot the folder is accessed, and any files found in it, are substituted for the files on your memory sitck (this is a simplification of the process just to illustrate the point). The files within the Operating system itself are NOT actually modified, ever, they are treated as read-only. Casper gives you the illusion of a normally working operating system, while using only read-only files that are never actually altered. This is great for on-the go convenience, but limits certain things you can do to your system's configuration, especially at boot. There are instances when a changed file (i.e. changed system setting) can not be dealt with properly by casper. I'm sure you'd love a specific example, please refer to the **HUNDREDS** of bugs with casper not saving or loading certain changes the user has applied, and many many other issues.

Hence the reason why I don't think anyone would or should spend too much time trying to troubleshoot a "live" installation

and I did offer advice to you, if you had read the next few posts after the one you replied to. And if you have bad CMOS chips on your board, I'm sorry to hear that, but I'll bet money you and your utility you used, were the cause.

Sorry but none of the advice you have thus far provided has been of any useful help to me in any way, I again repeat that I am not trying to trouble-shoot a "live" install - my SD card performs the function any HD would albeit without the benefit of a cache or a faster bus, apart from an earlier purging of Samba and tweaking a few Network related settings in order to isolate things, nothing I have done in the OS has been related to dealing with my problem.

And I am running off SD atm :-
Distributor ID:    Ubuntu
Description:    Ubuntu 11.04
Release:    11.04
Codename:    natty

And why are you being such a parrot, I already declared that I thought the utility I used caused the problem - actually, from working on the code I now believe otherwise but I'll keep that to myself knowing that it does not change or help things along.

---

### Post by cryptotheslow on 2011-08-20
Out of interest - you say you have identified and removed an unwanted ROM module. You mean you have physically removed a ROM chip from the mobo or other device? Or you found a section of code in ROM that was unwanted and you removed the code?

What was unwanted about the ROM or its behaviour? Did you consider it to be malicious?

More details needed here please :)

---

### Post by Actonix on 2011-08-20
> **cryptotheslow said:**
> Out of interest - you say you have identified and removed an unwanted ROM module. You mean you have physically removed a ROM chip from the mobo or other device? Or you found a section of code in ROM that was unwanted and you removed the code?

What was unwanted about the ROM or its behaviour? Did you consider it to be malicious?

More details needed here please :)

Nope, just removed the code - I think it's a matter of personal opinion/interest, some think it worthwhile to have on their PC's which is all well and good as it has and can perform a number of legitimate and useful functions, while others like me find it intrusive especially as one did not ask for, nor were adviced of it being present, and the fact that some unscrupulous elements are able to hijack it to their own ends does not help my opinion,  so yes, from that POV I considered it malicious - I cannot however provide any further details on this but have to take the stance of others in this regards as doing otherwise could allow for abuse which I don't personally condone or support.

---

### Post by cryptotheslow on 2011-08-20
Well that's a nice attitude. Push people on here for advice, then lambast them when they try to help, then refuse to share any info about what you found, on what particular ROM within the machine and what it may be doing that could be considered malicious.

Surely a generalised summary would not be abusable. Those who already possess the capability to manipulate on board ROM code to their own ends are not going to be any further forward in their endeavours by a small summary.

A little info might help others in the same situation do their own investigation on their own equipment. The security by obscurity model just doesn't work, those who want the information will already have it. Unless of course you intend to take the manufacturers to task and wish to give them some time to take measures to address the issue before disclosure?

---

### Post by asomad on 2011-08-20
> **Actonix said:**
> Already explained all that, and I do not see how a mem-stick based worm can persist without the PC having access to the stick and the only attached storage medium being the CD-Rom drive !!!?

... do you read with blinkers on ?

No, I read with my eyes, think with my brain, and don't act on impulse.

If you did have a virus (and i dont think you do) it could have moved from the memory card to your pc, when you were using the memory card as your boot device. (according to you that's when your problems started.)

however, it's not a virus, it never was. 

The "mystery ghostly vanishing virus windows network icon" was probably just a weird bug you experienced, and it probably had to do with your install being "live" 

The problem persists between installs, not because it's a virus, but because you have corrupted your CMOS

[SOLVED]

lmfao, this thread is indeed fun. hope it lasts forever. and with this guy ^ it just might

---

### Post by asomad on 2011-08-20
> **Actonix said:**
> Sorry but none of the advice you have thus far provided has been of any useful help to me in any way, I again repeat that I am not trying to trouble-shoot a "live" install - my SD card performs the function any HD would albeit without the benefit of a cache or a faster bus, apart from an earlier purging of Samba and tweaking a few Network related settings in order to isolate things, nothing I have done in the OS has been related to dealing with my problem.

And I am running off SD atm :-
Distributor ID:    Ubuntu
Description:    Ubuntu 11.04
Release:    11.04
Codename:    natty

And why are you being such a parrot, I already declared that I thought the utility I used caused the problem - actually, from working on the code I now believe otherwise but I'll keep that to myself knowing that it does not change or help things along.
so your using a "real" installation, that you installed onto what exactly? a solid state drive? or a memory card? cause if your running a real installation, off of a regular memory card, then you may in fact be beyond helping.

---

### Post by Actonix on 2011-08-20
> **cryptotheslow said:**
> Well that's a nice attitude. Push people on here for advice, then lambast them when they try to help, then refuse to share any info about what you found, on what particular ROM within the machine and what it may be doing that could be considered malicious.

Surely a generalised summary would not be abusable. Those who already possess the capability to manipulate on board ROM code to their own ends are not going to be any further forward in their endeavours by a small summary.

A little info might help others in the same situation do their own investigation on their own equipment. The security by obscurity model just doesn't work, those who want the information will already have it. Unless of course you intend to take the manufacturers to task and wish to give them some time to take measures to address the issue before disclosure?

I'm sorry you see things that way, yes I did ask for help but as you look at things in the right light you will  see that I have not really had any assistance in this regard and was told my problems were non-existent and to ignore things, and actually the only advice in other areas of the forum was to go back to the manufacturers for assistance and for good reason, hence my stance.

As for lambasting anyone, I think I had enough good reason to do so when I did but you are entitled to your opinion on the matter, I do not think I really need to justify or defend myself here, among the few that did try to help one of the best attempts at genuine help I appreciated came from someone citing an example and suggesting something like a printer on the network might possibly be the cause and another by providing links that were directly related to my problem even though most of those links were inaccessible to me - others in the know, and I know there are quite a few, held back from rendering any help.

What I did was seek out as much info elsewhere and that too to no avail - what I did find was what little there was available by way of software and firmware from the manufacturers themselves as per the advice given, the downside here was that it only served to further deepen my problem as flashing into higher versions with what was provided lost me access to other areas of added functionality within CMOS and without the possibility of taking my BIOS backwards - with all this going on I was highly motivated and had little choice but to take the initiative to find other methods which fortunately worked for me, I must say though that finding old firmware upgrades (no longer provided by the manufacturer) was the biggest help of all but I did have to work at reinstating them - all I can advice before you make any moves is ensure you find the right tool to back up and reinstate your current BIOS in full before attempting to go any further, you could play around with that probably with an editor capable of allowing you examine the contents but you really are on your own there as it is a highly risky venture - please bear in mind that though behind the times I have and am using the benefit of relatively extensive experience in the industry and as a programmer.

---

### Post by Thewhistlingwind on 2011-08-20
> **Actonix said:**
> 

As for lambasting anyone, I think I had enough good reason to do so when I did but you are entitled to your opinion on the matter, I do not think I really need to justify or defend myself here, among the few that did try to help one of the best attempts at genuine help I appreciated came from someone citing an example and suggesting something like a printer on the network might possibly be the cause and another by providing links that were directly related to my problem even though most of those links were inaccessible to me - others in the know, and I know there are quite a few, held back from rendering any help.



It helps to remember everyone here is a troll.

---

### Post by Actonix on 2011-08-20
> **asomad said:**
> No, I read with my eyes, think with my brain, and don't act on impulse.

If you did have a virus (and i dont think you do) it could have moved from the memory card to your pc, when you were using the memory card as your boot device. (according to you that's when your problems started.)

however, it's not a virus, it never was. 

The "mystery ghostly vanishing virus windows network icon" was probably just a weird bug you experienced, and it probably had to do with your install being "live" 

The problem persists between installs, not because it's a virus, but because you have corrupted your CMOS

[SOLVED]

lmfao, this thread is indeed fun. hope it lasts forever. and with this guy ^ it just might


[SOLVED] !!? ... my foot !! - lmfao, I will close and mark this as solved when it is just so.

You know what, stick with your weird bugs, IMO you have much in common, I won't be wasting time replying you anymore - CMOS !!!? ... whasdat !? ...  no need to latch onto what you don't have a clue about and parrot, then again feel free to google and post your findings ;)

What a plonk ...!! ... Solved but keep open forever !!!

> **asomad said:**
> No, I read with my eyes, think with my brain, and don't act on impulse.

[SOLVED]

lmfao, this thread is indeed fun. hope it lasts forever. and with this guy ^ it just might

---

### Post by Actonix on 2011-08-20
> **Thewhistlingwind said:**
> It helps to remember everyone here is a troll.

Ahhh, I'd hate to think so, and when I offer assistance I try to be as objective as I can in doing so even with limited knowledge - I'd actually go out of my way to investigate a problem I haven't enough of a clue about, post back possible solutions and track the problem to resolution, but that's just because it's second nature to do so when one has worked supporting IT infrastructure  and it helps me to bolster and acquire knowledge and keep a good foot in.

... but I'll take your point aboard. (Y)

---

### Post by dave01945 on 2011-08-20
> CMOS !!!? ... whasdat !? ... no need to latch onto what you don't have a clue about and parrot, then again feel free to google and post your findings 

you shouldn't question someone's intelligence when you don't know what you are on about your self here is a small explanation of CMOS which from your post's i thought you would already understand

[http://www.computerhope.com/jargon/c/cmos.htm](http://www.computerhope.com/jargon/c/cmos.htm)

---

### Post by hansdown on 2011-08-20
Hi Actonix.

It appears to be a mime.

[http://www.google.ca/search?q=%28application%2Foctet-stream%29&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.ca/search?q=%28application%2Foctet-stream%29&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

It may have come with a mail attachment.

---

### Post by Actonix on 2011-08-20
> **dave01945 said:**
> you shouldn't question someone's intelligence when you don't know what you are on about your self here is a small explanation of CMOS which from your post's i thought you would already understand

[http://www.computerhope.com/jargon/c/cmos.htm](http://www.computerhope.com/jargon/c/cmos.htm)

Do I really need to question yours !!? ... have you intentionally missed the point or just want to try parroting or perhaps this is a lame attempt at Trolling ?

... please feel free to continue, enjoy =D>:P

---edited---

Ahhh, a mime, almost thought it was a parrot but I prefer mime, a miming Troll or is that a Trolling mime, thanks Hansdown

---

### Post by dave01945 on 2011-08-20
i already am enjoying, this thread has been one of the most entertaining i've seen in a while.

no trolling just stating my opinion, you was the one writing as if CMOS was not even part of a computer

also you are the most arrogant poster i have ever seen on this forum

---

### Post by hansdown on 2011-08-20
> **Actonix said:**
> Do I really need to question yours !!? ... have you intentionally missed the point or just want to try parroting or perhaps this is a lame attempt at Trolling ?

... please feel free to continue, enjoy =D>:P

---edited---

Ahhh, a mime, almost thought it was a parrot but I prefer mime, a miming Troll or is that a Trolling mime, thanks Hansdown

You're welcome, Actonix.

It's not a problem.

This link explains it best.

[http://mimeapplication.net/octet-stream](http://mimeapplication.net/octet-stream)

---

### Post by Actonix on 2011-08-20
> **dave01945 said:**
> why would you flash it twice anyone that knows about computers knows bios flashing is **not advised**

good luck anyway this thread is fun to watch

also if you've flashed your bios that bios rootkit should be gone

Thanks Dave, I had good reason to flash more than twice as access to some tweaks in CMOS was lost with the updates which I would rather hang onto until I can incorporate that functionality with the latest updates

... and no, my problem is not quite resolved yet, can't say more just yet, might do down the line but I can say this much, it's a beaut :D

---

### Post by cryptotheslow on 2011-08-20
> **Actonix said:**
> I'm sorry you see things that way, yes I did ask for help but as you look at things in the right light you will  see that I have not really had any assistance in this regard and was told my problems were non-existent and to ignore things, and actually the only advice in other areas of the forum was to go back to the manufacturers for assistance and for good reason, hence my stance.

As for lambasting anyone, I think I had enough good reason to do so when I did but you are entitled to your opinion on the matter, I do not think I really need to justify or defend myself here, among the few that did try to help one of the best attempts at genuine help I appreciated came from someone citing an example and suggesting something like a printer on the network might possibly be the cause and another by providing links that were directly related to my problem even though most of those links were inaccessible to me - others in the know, and I know there are quite a few, held back from rendering any help.

What I did was seek out as much info elsewhere and that too to no avail - what I did find was what little there was available by way of software and firmware from the manufacturers themselves as per the advice given, the downside here was that it only served to further deepen my problem as flashing into higher versions with what was provided lost me access to other areas of added functionality within CMOS and without the possibility of taking my BIOS backwards - with all this going on I was highly motivated and had little choice but to take the initiative to find other methods which fortunately worked for me, I must say though that finding old firmware upgrades (no longer provided by the manufacturer) was the biggest help of all but I did have to work at reinstating them - all I can advice before you make any moves is ensure you find the right tool to back up and reinstate your current BIOS in full before attempting to go any further, you could play around with that probably with an editor capable of allowing you examine the contents but you really are on your own there as it is a highly risky venture - please bear in mind that though behind the times I have and am using the benefit of relatively extensive experience in the industry and as a programmer.


Fair enough. I am genuinely interested in what it is you found. I get strangely spooked when I read things about the likes of Intel incorporating encryption chips into their mobo chipsets. However lack the skills needed to delve into BIOS code. For some reason I'd rather rely on open-source encryption utilities that are subject to peer review than proprietary stuff - even if it does make things faster. As unlikely as it is that backdoors have been put in place, the possibility leaves me cold.

From the sound of it, you downloaded an older version of firmware from somewhere other than the manufacturer. How do you know you can trust the source not to have meddled with it? At least it seems you have the necessary capabilities to ascertain that.

Good luck with your endeavours.

---

### Post by Actonix on 2011-08-20
> **dave01945 said:**
> i already am enjoying, this thread has been one of the most entertaining i've seen in a while.

no trolling just stating my opinion, you was the one writing as if CMOS was not even part of a computer

also you are the most arrogant poster i have ever seen on this forum

Follow the threads then maybe you will understand what was meant by that posting instead of jumping to conclusions and heading off at a tangent, as for my being arrogant, you as everyone else is entitled to their own opinion but if your attempt here is going to be as helpful as some others I can handle that in anyway I deem best fit, my entitlement too.

---

### Post by dave01945 on 2011-08-20
ok and good luck with finding the cause and hopefully you will post your indings so the rest of us can learn how you solved the problem.

just out of curiosity it was not a problem with ubuntu but something within your bios and was this problem always there or was it corruption caused by the flashrom program

---

### Post by Actonix on 2011-08-20
> **cryptotheslow said:**
> Fair enough. I am genuinely interested in  what it is you found. I get strangely spooked when I read things about  the likes of Intel incorporating encryption chips into their mobo  chipsets. However lack the skills needed to delve into BIOS code. For  some reason I'd rather rely on open-source encryption utilities that are  subject to peer review than proprietary stuff - even if it does make  things faster. As unlikely as it is that backdoors have been put in  place, the possibility leaves me cold.

From the sound of it, you downloaded an older version of firmware from  somewhere other than the manufacturer. How do you know you can trust the  source not to have meddled with it? At least it seems you have the  necessary capabilities to ascertain that.

Good luck with your endeavours.

Thanks, and I'm glad you see reason. And what I found is nothing  new, new to me and you perhaps but already know to a wider audience  which is what lead me to it in the first place while on my quest to  resolve my particular problem, best explained in one word Zeitgeist -  and  yeah, your not the only one spooked, I have one such motherboard - and  though I hate to say this, digging deeper doesn't really help matters  along as all sorts of conspiracy theories can arise that can be  attributed to the origins of that one word, then Spooked becomes an  understatement and we head of into the heady stuff of fantasy perhaps, a realm where of an age old war is taking place right here in our  own time taking on and using unwitting recruits who don't have a clue of  that anything underhand is taking place talk-less what awaits most just  around the corner, a world where ignorance could really be blissful at  least for a time as the more one finds out the more incomprehensible  they appear to become when it comes to speaking out, so much so that they can so easily be declared as  being merely delusional, paranoid or both and easily discredited and  their claims dismissed in a tick - a world where in the bigger picture  it does not really matter who or what the source of the utilities you  use to protect your confidential data is as it is all laid bare to mythical giants  irrespective - one is after all working with their so called data  unencrypted or decrypted at one time or another and if one can access it  then can one really be assured of any privacy unless their systems are  in total isolation and even then?.

Personally I think not, all  one is doing is hiding that data from individual, unscrupulous and  opportunistic elements that are, in the grand scheme of things, mere fry  and only serve as a distraction that affects the individuals in his/her  daily life - and it all becomes one long story - sorry, but I just had  to let go, but it matters not though as it's all inconsequential until  ... ;(
... BTW, have you ever had a dream where you wake up screaming  "Wake up People, Open your Eyes, see and comprehend" ? - lmao -  Personally, I think we live in a hysterical age, make what you want out  of all I've said - but open your eyes.

.... And, back to reality, virtual though it may be ;)

Hard  to ascertain and be sure of any code one gets especially today  especially if it's a rarity, all one can do is grab a hold of it where and  when one can get it and check it out as best as one can - just like some people d/l cracked software known to be infected with a virus and simply get rid of the virus with available tools and make make use of the software, who knows what else was lurking within, too many viruses in the wild with more +variants coming out every day, we share concerns ;)

---

### Post by Actonix on 2011-08-20
> **dave01945 said:**
> ok and good luck with finding the cause and hopefully you will post your indings so the rest of us can learn how you solved the problem.

just out of curiosity it was not a problem with ubuntu but something within your bios and was this problem always there or was it corruption caused by the flashrom program


Nope, well, as far as I know it was not there all along, at least not in it's current state, one could say it simply happened along but I really cannot be definite about anything, I'm still trying to comprehend.

---

### Post by Actonix on 2011-08-20
> **hansdown said:**
> You're welcome, Actonix.

It's not a problem.



Thanks, most grateful ;)

 ](*,)

---

### Post by asomad on 2011-08-20
I think you missed that someone here put an educated head in on your issue, and told you what kind of virus you may have or had..... Be happy!

I'd recommend a new motherboard, and maybe a hard drive also. best luck

---

### Post by asomad on 2011-08-21
oh please please please can we change the title to "geeks and wanageeks attack and barrate each other for fun" and then, make it the primary thread of Ubuntuforums..? please? lmfao

---

### Post by Actonix on 2011-08-21
lol - your measure of intelligence amuses me, you trying to call yourself a geek based on exactly what may I ask !!!?

... I knew from the start you were trying to bring me down to your level but I still can't help but laugh at your latest attempt :D

My problems still persist and the area affected remains the same as I have already pinpointed, hasn't changed irrespective of what you may think - so keep yourself amused with that for now, I think you will have difficulty learning much more here.

Actually, if you have the old free Assembler compiler ASL.exe from Microsoft that would be of great assistance.

... But somehow I doubt it so please, kindly run along and continue your aimless Trolling elsewhere, not that you need much bidding, can't help but notice as I'm posting right behind you in some instances.

---

### Post by asomad on 2011-08-21
> **Actonix said:**
> lol - your measure of intelligence amuses me, you trying to call yourself a geek based on exactly what may I ask !!!?

... I knew from the start you were trying to bring me down to your level but I still can't help but laugh at your latest attempt :D

My problems still persist and the area affected remains the same as I have already pinpointed, hasn't changed irrespective of what you may think - so keep yourself amused with that for now, I think you will have difficulty learning much more here.

Actually, if you have the old free Assembler compiler ASL.exe from Microsoft that would be of great assistance.

... But somehow I doubt it so please, kindly run along and continue your aimless Trolling elsewhere, not that you need much bidding, can't help but notice as I'm posting right behind you in some instances.

acutally I dont call myself a geek, im a blue collar guy, with twenty five plus years of tinkering with computers. Starting with a commodore64, to today, where at home we have about 20tb of server shares, 8 machines, 2 laptops. Including os's win95, 2000, xp, and 7. and ubuntu, and dual and triple booters with lucid, (gnome and cli) and backtrack. pretty extensive gigabit network, and my specialty, secure wifi, everywhere.  etc etc. Im not a programmer, I'm a linux noob, but don't ever test what I do know, cause you may be surprised, I may in fact be a geek after all. . 

I had not been being rude to you, since an expert chimed in with a valid cause of your problem. And even though I do not see your reasoning for continuing with the same project, Ive been being nice. AND THEN YOU COME IN WITH YOUR ATTITUDE AGAIN. wtf dude.

If you want to continue to attempt to get your board working, that's your choice. Don't be mad at me cause I actually have a personaility, and don't be rude to people... poking a little fun, and being rude, are very different things. and you sir are a RUDE mother effer. Did you even look into what handsdown reccomended it could be? Or just brush it off, and continue hacking away at your poor bios's code? it doesn't matter how much you know, If you choose to keep working on that, its a real good indicator of what you know. lol. Ill give you a MOBO for free if you want, just to save everyone a headache.

---

### Post by Actonix on 2011-08-21
> **asomad said:**
> oh please please please can we change the title  to "geeks and wanageeks attack and barrate each other for fun" and then,  make it the primary thread of Ubuntuforums..? please? lmfao

Then, uhm, forgive me from arriving at the conclusion I did, came about purely from what you posted, and contrary to what you may believe it's no fun replying to your posts, the only example that comes to mind is a dog trying scratching in vain attempt at getting rid of a lousy flea.

And if you think calling me ignorant is complimentary then have another think.

 But I'd graciously accept and make do with the old Microsoft Assembler compiler I mentioned if you have can dig it out from you vast array of shares, that would greatly assist what I'm doing, I'm happy to continue dig away here, thank you.

By the way, my board is not faulty, it works fine, it just has a bit more functionality than I'd like it to have.

---

### Post by cryptotheslow on 2011-08-21
I won't quote your reply as it would result in a massive post.

My eyes are well and truely open to the possibilities and realities. I'm also well aware of my own limitations in being able to unpick them having never been anywhere near assembly. Only coding I've done relies on compilers, which then relies on a OS which then relies on the firmware on the supplied hardware. The OS I use is open source and open to peer review - as for the firmware, I have to take a punt on that.

But then all I need to encrypt is my personal data to protect against losing a usb stick, or having my laptop or desktop stolen. I've no need to hide things, I'm just securing them from opportunists so they don't stumble across my file of passwords and cause me a great deal of inconvenience. I'm in no way delusional - I don't think that 'somewhere' 'someone' is watching everything I type as I type it :D I'll leave that to the tin hat brigade,

Theoretically I suppose a compromised BIOS or say a ROM on a graphics card could be leveraged to render encryption useless by accessing data while unencrypted and in use. Would take a great deal of effort to craft and as I have no reason to believe that my mundane existence warrants such attention, I sleep easy.

---

### Post by asomad on 2011-08-21
> **Actonix said:**
> By the way, my board is not faulty, it works fine

!!!!!!!!??????????!!!!!!WTF!!!!!!!!!!!!!!!!!!

then what the H is the problem! ..... WOW

---

### Post by asomad on 2011-08-21
If i was at home, I'd dig up the asl for you. Unfortunately I'm hospital bound (which is the only reason I'm even giving you the time of day =P, cause I have nothing better to do right now), and what I can access from outside my network, does not include what you need... sorry

---

### Post by Duncan Williams on 2011-08-21
Well I suppose this is an interesting thread.
But it is not a constructive one, I personally have pretty much given up on getting assistance from forums in general and tend to resolve issues by myself.
Why? > because quite often I can.

A lot of forums including this one seem to have a few addicted individuals that can't help but put their two bobs worth in.
This is of course no real use to anyone but their own ego.

A few points.
Call a spade a spade > usb stick, ssd drive, bios chip, etc, etc.
anything else leads to confusion.

Don't offer advice if you don't have experience with the issue (or at least know of a reliable source or remedy)

Don't let people get to you and in frustration deflect from actually resolving the problem.

I hope the OP resolves his problem, mind you after reading this thread right through, I have lost contact with the basics of the problem.

A classic personal experience with bad forum advice: (my other dog is called mimi)
[http://peppermintos.net/viewtopic.php?f=9&t=3936](http://peppermintos.net/viewtopic.php?f=9&t=3936)


good luck, and yes it is an interesting thread

---

### Post by asomad on 2011-08-21
> **Duncan Williams said:**
> Well I suppose this is an interesting thread.
But it is not a constructive one, I personally have pretty much given up on getting assistance from forums in general and tend to resolve issues by myself.
Why? > because quite often I can.


all *I* did was make a comment about not killing ones computer by altering (flashing) the bios... Trying to talk sense into the guy (based on how his OS was acting).
I KNOW I'm not a programmer, nor am I experienced with linux! you dont see me acting like I am, or writing out scripts for people....  
BUT, I know hardware, from the pcb level, on up...
  Ive had fun bashing back and forth with our friend, but underneath it all, I was trying to answer his questions, at least the ones that made sense. .....I'm sorry If we didn't help the guy, but even when people did, he just attacked them, and me. 

yes sometimes I point out stupidity (like responding to a message that's the output of a lsusb command, and asking the op to try running lsusb command), but isn't that more of a "teach" than a "troll". The few poeple Ive dealt with on here, Ive had very pleasant experiences. and along comes this guy, I make a little giggle, and now I'm the bad guy?

---

### Post by 3rdalbum on 2011-08-21
> **Actonix said:**
> 
Yes, taken for granted - but it not completing does not explain why a getcwd() call is being issued on all tty's

A bug is the most likely explanation. For the life of me, I can't see why a "BIOS rootkit" would need a call to getcwd on all seven TTYs. Especially since rootkits modify system tools to NOT show their own activity. That's one very well-known behaviour of a rootkit - they modify the system libraries to stop the OS from reporting anything to do with it, and that's why a live CD helps in this case.

> neither does it explain the 7 new bash processes listed in System Monitor

Well there's seven ttys, each running Bash.

Also, this confirms that you don't have a rootkit, because a rootkit would have patched the 'ps', 'top', 'gnome-system-monitor' etc commands to NOT show the rootkit's activity.

> ... how to recover from it remains the question, any capable experts in the forum !?

You believe your computer has malware that you cannot get rid of, that exists even when you're running on a clean environment. People who know what they're talking about are telling you that the malware does not exist.

I've seen this kind of thing before across the internet. Sometimes it's a "virus" and sometimes it's a "hacker", but it's the same paranoia.

Soon you'll notice that the "rootkit" has spread to your router, smartphone, other computers or even to another device.

Unfortunately, it's all in your mind. As a fellow Ubuntu user and someone who generally cares about the welfare of others, I'd advise you to start seeing a psychologist; your problem is not in your BIOS but in your perception of your computer. I know shrinks aren't cheap :-)  But they should be able to give you some good, practical help.

Good luck! Best wishes, and get well soon.

---

### Post by asomad on 2011-08-21
> **Duncan Williams said:**
> 

A classic personal experience with bad forum advice: (my other dog is called mimi)
[http://peppermintos.net/viewtopic.php?f=9&t=3936](http://peppermintos.net/viewtopic.php?f=9&t=3936)


good luck, and yes it is an interesting thread

Lol, you and acto belong on a boat together. (and i mean that in a fun loving, friendly way) =P
Maybe when people barrate you saying "why are you doing that" maybe it's their way of offering advice and saving you trouble
(and don't say that's not advice.... it's the same thing as saying "you should not do that")

---

### Post by 3rdalbum on 2011-08-21
This thread reminds me of these:

[http://www.linuxquestions.org/questions/linux-newbie-8/help-me-shutdown-localhost-please-606409/](http://www.linuxquestions.org/questions/linux-newbie-8/help-me-shutdown-localhost-please-606409/)

[http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-machine-has-malware-and-spyware....need-help-692261/page2.html#post3384587](http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-machine-has-malware-and-spyware....need-help-692261/page2.html#post3384587)

[http://www.pubbs.net/ubuntu/201001/9722/](http://www.pubbs.net/ubuntu/201001/9722/)

[http://forums.cnet.com/7723-12545_102-531751.html](http://forums.cnet.com/7723-12545_102-531751.html)

---

### Post by asomad on 2011-08-21
it's priceless how people always refer to it as "they". They took over my system, they're watching me, they wont help me. they wont listen to me.. lol

---

### Post by Duncan Williams on 2011-08-21
wow, this thread has slowed down... 

@3rdalbum
wow, I'm in Kendenup (near Albany) so warm and sunny for a change...

---

### Post by hansdown on 2011-08-21
Today is a new day.

Let's continue the help portion of this thread.

Actonix,two possibillities are likely.

1-

  You received an email attachment from a friend,that had an incorrectly labelled attachment.

2-

  You received this from a misconfigured web server.

Both are not your fault, and all browsers will handle these the same way.It keeps malicious code from entering computer systems, mostly a concern to windows machines.

I'm not the most qualified member to answer this, so this will serve as a gentle bump for this thread.

---

### Post by Actonix on 2011-08-22
> **hansdown said:**
> Today is a new day.

Let's continue the help portion of this thread.

Actonix,two possibillities are likely.

1-

  You received an email attachment from a friend,that had an incorrectly labelled attachment.

2-

  You received this from a misconfigured web server.

Both are not your fault, and all browsers will handle these the same  way.It keeps malicious code from entering computer systems, mostly a  concern to windows machines.

I'm not the most qualified member to answer this, so this will serve as a gentle bump for this thread.

Thanks, not entirely sure how I got it but I at least can discount  the Flashrom utility now, there are however 3 areas of concern in that  regards, one is with FF's xul, the other Flash and the latest and most  wide open, ipv6, but that's btw and I'm not going to go into any of it.

Played around pretty exhaustively  with this and what my findings indicate is that my problem resides in  BIOS, is one of the first things loaded, has its own runtime environment  of sorts and pro-actively resists change, probably even has its own  flash utility with a name like flashdxe and flashplay and I cannot discount Mime as being an integral part, who knows for certain, I  could be partially wrong or even right the way through. ;)
... the same mechanism might  probably also be involved in retaining and reinstating Windows registry  settings some of which it maintains on HD and which can also get  carried over and stored on a brand spanking HD long after removal of a  prior - then again this might not even be related to it.

I'm sure many will try jumping down my throat at what they  could consider mere conjecture without trying to fact find so might as  well invite them along to do so now, please feel free to do so, it won't  change what is - but do try to remember down the line, when you find  out just what is, to come back and state your findings.

Anyhow,  If I am right, though I reckon it can be defeated it would be no small  feat as it requires a lot more insight and would be helped along if one  had some way of studying its mechanisms more openly or at least finding a  way of disabling it probably by locating and clearing it out of memory  but that requires identifying it first off, something I have thus far  been unable to do, most of what I have seen is effect and with that backing cause is known to exist - bar that, the only other way to bypass it and  replace ones bios would be with a soldering iron and an external  programmer unless you are fortunate enough to be able to simply pull out  and replace it with known good - and even then it is possible it might  also reside in other firmware so, if hot plug-able, I would say power up,  remove new and reinstate old bios to be safe - I unfortunately do not  have that choice.

Though I am and will continue to chase down the  soft approach I think this thread should die a death as no one with  appropriate knowledge appears willing to really make a contribution.

Never closed a thread before, how do I mark this as closed or even possibly get it deleted ?

---

### Post by hansdown on 2011-08-23
Well then, best of luck, Actonix.

If you wish to close, or delete a thread, this forum requires that staff do it for you.

Just press the report button on the bottom, left, and ask them .

---

### Post by Grenage on 2011-08-23
Never before have I seen so much text in a support thread, where neither the issue nor suggested resolution path was apparent.

This is without a doubt the poster-child of pseudo-computing.

---

### Post by howefield on 2011-08-23
> **Actonix said:**
> ...how do I mark this as closed or even possibly get it deleted ?

Closed at op request.

---

