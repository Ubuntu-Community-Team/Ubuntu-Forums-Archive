---
title: "My Entire Ubuntu is Breaking Down As I Speak!! Help with everything going wrong??"
date: 2010-02-10
forum: General Help
---

### Post by person9 on 2010-02-10
Hi everyone, I am currently browsing a horribly disfigured and aggravating version of the internet because Im using the Fennec browser - apparently I cant type apostrophes in it?? Nothing will install, because of this crazy irritating issue that started a few days ago and no one was able to help me with it. I will try again since now things are actually degrading to the point that Im going to literally scrap my entire Ubuntu install and go back to depressing Windows Vista because I have school work to do and I cant have a nonfunctional system! 

Here is the deal, I simply installed updates as usual the other day. Apparently there was some issue with Firefox and I got some annoying messages which I didnt understand and I just continued using my computer as usual since everything else was fine. The next time I restarted my computer, the Firefox icon was a little blank puzzle piece and ceased to function properly. Several restarts later, every trace of firefox is apparently gone now. I have deleted a few folders at peoples suggestions, I have tried synaptic, terminal, sudo this and sudo that, reinstalling, manually pasting folders, everything is out of control.


I am constantly getting messages when I try to install ANYTHING that i have, now, missing dependencies, skype needs this and firefox needs that, and almost every time, "google-desktop-linux" is having some issue  too. I literally am going to just delete this entire install if I cannot find some viable solutions within a few hours, it almost would  be easier to just attempt backing up my important files and use dumb Windows until I get something figured out.  :oops:

*** I will gladly provide any information needed, please just ask. I can do screen shots, I can do outputs of terminals or messages in synaptic, I can give you any info about my system. 

*** I have Jaunty 9.04  and an Amd 64 processor, I installed this ubuntu through Wubi on my original- &saddening - windows Vista OS. 

Thank you hugely!! I will do anything necessary because I am totally on board with ubuntu, so any suggestions are welcome

---

### Post by Lee3155 on 2010-02-10
Try restart your OS and boot back into Ubuntu. If it doesnt work there is probably nothing you can do since you used wubi but you can use the recovery option

I agree with below, what messages are you getting?

_____________
Lee

---

### Post by oldos2er on 2010-02-10
What were the "annoying messages"?

---

### Post by person9 on 2010-02-10
In Add/Remove programs, firefox is still checked off even though it's essentially dead. However, when I uncheck its box, it says:
> Cannot remove 'firefox-3.0-branding'
One or more applications depend on firefox-3.0-branding. To remove firefox-3.0-branding and the dependent applications, use the Synaptic package manager.

---

### Post by person9 on 2010-02-10
This is what happens when I do ```
sudo apt-get update
```
> [shortened to just the end ......]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Fetched 308B in 0s (408B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9BDB3D89CE49EC21
W: You may want to run apt-get update to correct these problems


This is pretty funny because apt-get update is GIVING "these problems". I am not a fan. Any insights at least to *this* problem so maybe I can start solving it piece by piece?

---

Oh, and here is the message that I get EVERY time I do anything on Add/Remove Programs.
> E: google-desktop-linux: subprocess post-installation script returned error exit status 1 

I just found and unchecked the box next to **Ubufox extension for firefox** because I want to UNINSTALL anything that has to do with firefox, I guess. And the "details" pane said: > Removing ubufox ....
Setting up google-desktop-linux (1.2.0.0088) ...
File /opt/google/desktop/ .gdl_installed_files is missing!
dpkg: error processing google-desktop-linux (--configure): 
  subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
   google-desktop-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)
 A package failed to install.   Trying to recover:

That was it. Thats what I keep getting on ANY activity, be in install or uninstall, from Add/Remove programs and I believe Synaptic is giving the same type of messages.

---

### Post by suncoup on 2010-02-10
I'm definitely no expert, although I'm proud to say I was able to get my lexmark printer and intel embedded graphics cards working with ubuntu less than four days after installing!

I think you should take the advice some others have given and reinstall. And I WHOLEHEARTEDLY recommend installing ubuntu as a regular install, instead of from within Windows. It's pretty easy to set up a partition and just make your computer a dual boot. That way, when things get out of hand, you can just boot into that OTHER o.s., take care of business, and then return to the joy of creatively tackling a problem.

Good Luck, 

Ricky

---

### Post by person9 on 2010-02-10
I would kind of just like to reinstall as well, but I kind of am avoiding it since I just recently got my ubuntu set up exactly the way I like it - the dock down the bottom with all the links in the order I'm used to, the theme I like, all the programs I like to use,even my IM histories, all my passwords and schoolwork saved and all my settings for all these programs.. 

So, is there any way to preserve my settings and files and stuff? If it's easy enough to do, I might just reinstall because it's literally plagued with problems right now.

And sorry if this is like a super basic question but how do I install the latest ubuntu if this is the only computer I have access to? Must it be from the CD? I don't have any CD's large enough to hold the data, BUT I do have a disc that contains Ubuntu 9.04 I think.. or 8.10... not sure, but if I install from that, is it easy to quickly upgrade it to the most recent 9.10 --- or is it just a waste of my time to have done it that way?

LOL sorry for being way too in depth with this , THANKS For suggestions!!

---

### Post by drewsus on 2010-02-10
next time you install ubuntu you should do it so you have three partitions
they are:
/
/home/
swap

/ is your system
/home/ is your home directory
swap (From Ubuntu.com) "Swap space is the area on a hard disk which temporarily holds memory pages that are inactive. Swap space is used when physical memory, or RAM, is full." Swap space should also be just over double the size of your RAM for Suspending and Hibernation

the benefit to this is that you can reinstall ubuntu formatting the / partition and NOT formatting your home partition thus saving all your files and settings (you just have to reinstall apps)

NOW, you said you tried using Add/Remove Programs to remove Firefox and it told you to remove it from Synaptic Package Manager so... why have you not done that? 
Open Synaptic Package Manager (System -> Administration -> Synaptic Package Manager) search for firefox right-click on it and say remove. It will tell you many more packages that it has to remove say yes, then click apply. 
After its removed, do the same in reverse... (reinstall firefox)

alternatively, you can do this in terminal: 
```
sudo apt-get purge firefox
```
and then:
```
sudo apt-get install firefox
```

---

### Post by drewsus on 2010-02-10
and if you have a USB stick with enough free space we can use that to install Ubuntu instead of from a CD (its the environmentally friendly way too ;))

---

### Post by colobix on 2010-02-10
why would u install it via windows? ok too late now but you should have thought bout that. Ok uninstall ubuntu and reinstall it from scratch on its own partition and first then you'll be able to fix problems like this.

---

### Post by person9 on 2010-02-13
Hi thank you for your replies!

* I installed it through Windows because, as Ubuntu/Canonical themselves suggest, if you have never used Linux before and you'd like to get familiar with it, its an easy way to install it and try it out with the option to remove it later through Windows (and the LiveCD is way too slow/hassle and I actually wanted to *use* Ubuntu). This was when my computer was brand new last year: I'd never owned my own computer, needed it for school, never used Linux but liked the idea... why would I go ahead and do something I was unsure of? 
I don't agree that I "should have thought about it" if I hadn't the first idea of how Ubuntu even worked or what a partition was, sorry. Now I'm familiar with Ubuntu having learned about it this way, and decided I liked it enough to use it for like 1 - 2 years.... seems logical enough to me. I'm like 19, I wouldn't want to accidentally trash my own brand new laptop and be stuck without one.

* drewsus, thanks, but I did try Synaptic just like it said. Sorry, I had mentioned that in a completely different thread and already moved on since that didn't work either. If you are interested here is the thread:

[http://ubuntuforums.org/showthread.php?t=1401904](http://ubuntuforums.org/showthread.php?t=1401904)

> And thanks for the suggestions about making those different partitions, I don't actually know how to do that but I'll research it before I go ahead and install 9.10. As for the sudo apt-get purge firefox, I had read that a lot of stuff in Ubuntu was super-dependent on firefox, and that you could break a LOT of packages by removing stuff like that, so I never went ahead and ran that particular command. BUT, if I just back up my files that I want to save, I suppose I have nothing to lose and I will try it. I'll post results in a few days, maybe tomorrow morning. I've been on Windows today because of my music program and because I just don't feel like looking at Ubuntu right now :)

I really appreciate these suggestions, and I'll give them a try. If it's still not working, I think I'll probably just go to someone's house who has fast internet, make myself a 9.10 install CD, and install it on an actual partition after uninstalling the Wubi fake partition thing outta Windows. I just don't want to lose files (by simply *forgetting* about some files I wanted that were stranded in an obscure folder..) or render my nice computer useless by messing something up- but I don't want to use it with just Windows.

Thanks again everyone, have great days!

---

### Post by robertneville777 on 2010-02-13
Yeah, I feel your pain, hehehe. I'm 18, in college, and currently have a shnieke-load of homework. ](*,)

I did that Wubi installer a few months back, just to see what the fuss over it was all about, and I just had problems everywhere with it.

So I installed it natively like my other Ubuntu machine, and bam, everything worked! 

But getting back to your point, I would do what you said and download ubuntu 9.10. Then use drews' instructions so you save all your personal stuff, i.e. your home folder.

Good luck!:guitar:

---

### Post by person9 on 2010-02-13
Lol thank you, thats most certainly what I was intending when I first did the Wubi thing and then discovered I liked it, buuuut then by the time I was like "hey I should install this the proper way!" I already had it filled with files, customizations, programs, etc. 

I have installed 9.10 to my mom's laptop for her, but there was no partitioning involved, it is only Ubuntu with nothing else. So I *kinda* know what I'm doing but not completely. And thats why I come on the awesome forums!

:)

---

### Post by 3rdalbum on 2010-02-13
The output of "apt-get update" suggests that you have a PPA enabled in your software sources. What is the nature of this? Have you tried to update Firefox from it?

If so, try removing the PPA from System > Administration > Software Sources and then use Synaptic to downgrade the Firefox packages to the regular "jaunty" or "jaunty-security" versions.

---

### Post by lenoirrichelieu on 2010-02-13
First you put an awesome title :D
"My Entire Ubuntu is Breaking Down As I Speak!! " I felt like in Tales from the Crypt or Alien. 
 
Now back on topic.
First is always useful to have a partition separately for backup. Even i that is not mounted as /home but a spare space where you can put some files when needed. 
 
As I understand you have Ubuntu installed under Windows via Wubi. Then you can use the Windows partition for backup. If you copy the entire /home folder on the NTFS you should not lose any customizations because you can recover them after a new installation of Ubuntu. Of course is about customizations and links not programs. Those you'll have to re-install after a fresh Ubuntu.
 
As for dependencies you can actually try to remove only firefox despite warnings and reinstalling again after.

---

### Post by squareff255 on 2010-02-13
Well, I started using Ubuntu about 6 months ago and I did the Wubi install. I, too had so many problems, so I reinstalled it using Wubi, and again, I had so many problems. So finally I just installed outside of windows, and I have been sailing problem free for quite some time. :) Now, my 2nd install (Wubi) I got set up very nicely and I was heartbroken when I decided to abandon it, but in the long run, I realized it was much better to just start fresh, so I would recommend backing up school files and stuff and then just installing 9.10 fresh. 
There's an excellent tool called EASEUS Partition Manager. Google it. It's the only way I've found to successfully shrink the NTFS (Windows) partition. 
lol I'm not trying to be rude but you said something in your first post about having school work and you may have to scrap your non-funtioning Ubuntu and just use Vista because you have to have a functioning system. It's funny because if you used Vista, you WOULDN'T have a functioning system. lol... sorry.
Well, good luck to you. Make sure that if you use EASEUS Partition Manager that you to a couple disk cleanups, disk defragments and disk checks on Vista before resizing your partition. TO RUN THE DISK CHECK, FIND THE COMMAND PROMPT IN THE START MENU, RIGHT CLICK AND GO TO "RUN AS ADMINISTRATOR..." OR WHATEVER. Then you can use the command:
```

chkdsk -R

```
and then restart the compy. Do this AFTER your disk cleanup and your disk defragments. THEN after it runs the disk check, you can successfully run the partition manager. :) any other questions, you can email me.
[email]mckenzie.warren@gmail.com[/email]
CHEERS! :)

---

### Post by person9 on 2010-02-13
* 3rdalbum: I have no idea what a PPA is, I just sometimes copy and paste stuff into the Software Sources box when I'm instructed to, lol! So, if I'm following your instructions right, I'll go and get rid of all those software-source addresses, and THEN try to use Synaptic to "reinstall" firefox or look for the right version of it? Would I need to first do apt-get update again? Thank you!!!

* lenoirrichelieu: Wow, just copying the entire home folder. That's so obvious that I never even thought to do that!! Last time, for some reason, I copied all my folders of documents **separately** into a folder called "Ubuntu Backup" on the Windows partition... no idea why I didn't think to copy the whole thing! Thanks!  And as for firefox having warnings/dependencies? I no longer care lol, I am just going to back up everything and go ahead and try everything on firefox because I have nothing to lose. Great advice!

* squareff255: I totally agree with your whole first paragraph. Ever since I became attached to my install with Wubi I wished I had just done a real install! As for Vista, lol, it's not my best friend but it *does* function - barely. I can't even upgrade it to SP1 so its like the most basic version of it and it gets the job done for *two* things: simple internet browsing, and my Windows music production software. :)
     Now, for EASEUS Partition Manager -- do you think that I really need this since I have no separate partitions yet? I may be wrong but I installed Ubuntu onto someone elses' laptop once and it asked me during installation how much space I wanted to / could allow the Ubuntu partition to take up. I have **not** uninstalled my Wubi thing yet, and then when I do all I will be left with is drive C: Vista OS and then drive D: HP's Backup partition. Will popping in and installing Ubuntu straight off the CD require any *further* tinkering with partition sizes or will it just make it easy for me to get both Vista and Ubuntu going by asking me to set the partition size? Will it still dualboot properly or do I need to do some kind of bootloader myself?

Thank you again, and sorry I have so many endless questions. You guys are all so helpful with everything!!

<3 the forums

---

### Post by junapp on 2010-02-13
> **person9 said:**
> I have no idea what a PPA is, I just sometimes copy and paste stuff into the Software Sources box when I'm instructed to
just a suggestion, but be sure to find out exactly what you are doing before following such instructions, or you may find yourself in a similar predicament in the future even with a typical install.

---

### Post by person9 on 2010-02-13
Haha I agree. I try to triple-check everything and Google and find out exactly what it does before following stuff like that - I guess I meant I know how to use the Software Source things to do what I need to, but I am not extremely knowledgeable on why/how it works. I also recommend to myself and everyone else, backing up! I'm sure everyone knows this but I cant say enough how many times going out of my way to back-up has totally saved me. :)

---

### Post by person9 on 2010-02-14
WHOAAAA the entire thing is fixed apparently! I have no idea yet if its true, I'm just waiting to run into another error, but it seriously looks like it's fixed. One of the main problems was, when I tried to install or uninstall ANYTHING, on the way to a fix, I was getting errors left and right involving "google-desktop-linux" which I did not ever even intend to HAVE. Anyway, after some googling just now (ha, google, go figure) and I came across this website:

> [http://odzangba.wordpress.com/2009/10/14/how-to-fix-&#8220;subprocess-pre-removal-script-returned-error-exit-status-2&#8243;-error/](http://odzangba.wordpress.com/2009/10/14/how-to-fix-&#8220;subprocess-pre-removal-script-returned-error-exit-status-2&#8243;-error/)

And I followed some of the directions there to go into the text file and delete the problematic entry. Well, I found google-desktop-linux and sure enough, it said it was 'half-configured'. I had no interest in having this anyway, so I deleted it and ..... firefox reinstalled properly, the broken packages went away, no more error messages!!

Therefore I can delay the 3-hour download of 9.10 a little more, haha! Thanks everyone for all your help!!

---

### Post by houseworkshy on 2010-02-14
As a lot of that seemed to be firefox going mad you could also install a backup browser.  I still like it's close relative seamonkey, nice editor too.  There is also a handy backup utility called aptoncd.  It's on the repositories and can be used not only for work but drivers and application too.  Saves downloading it all again.  One thing to be cautious of is adding repositories.  The default ones and the ones which are listed in a fresh install along with mediabuntu are ok, others are not checked by the Ubuntu team so may not be.  

It is worth having programs like sysinfo and htop on the system in case you need to post about problems in the future.  They are an easy and quick way of collecting info.  Also worth enableing the firewall "sudo ufw default deny" and  "sudo ufw enable".  The man pages are very helpful I guess you know typing "man" in front of a command will take you to it's manual.  Another I like is "apropos" which will list any referances to whatever word you type next, eg "apropos find" will bring up any command with find in its manual pages, good for trying to find the command you need when you don't know what it is.  

Another thing worth remembering is that when you use "sudo" it counts down from 15 minuets during which time a password is not needed for an admin action.  So a good habit is to finish with "sudo -k", before browsing around, "man sudo" will tell you all about it.  I think someday, perhaps not yet, browsing in the 15 minuets grace period following sudo may be risky.  A nice addon for firefox is noscript which does what it sounds like, not all add ons are good.  ClamAV told me that one, ghostery, was a virus.  It is worth putting clamtk on the machine as I guess you will share files with windows types and someday, as it gets more popular, even linux will get dirty.

---

### Post by person9 on 2010-02-14
Wow! That is a **ton** of helpful information! I have Opera installed now just as a back-up, since it was the only one I was able to get to work then. And I also tried "Fennec" which is the cell-phone version of Firefox -- *awful* on a computer screen. But, I had to do that when Opera broke. I also tried Conkeror - a strange little browser with no controls, all keyboard commands. It was interesting, lol. 
Well thank you for that info, I did not know about most of those things you mentioned. Thanks!

---

### Post by houseworkshy on 2010-02-14
You're welcome.  It's only stuff people told me when I was banging my head against the wall, just passing it on.  There are a lot of browsers, I prefer firefox myself but sometimes it does seem to go belly up.  One of the things about the man command is that it lets you check up on what you are being told to copy and paste into the terminal before doing it. I haven't seen any malicious things myself but have read the sticky warnings.

This is really good and the pdf is free ( got me started )

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

