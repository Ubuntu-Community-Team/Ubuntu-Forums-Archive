---
title: "Xscreensaver GLSLideshow Does Not See My Images"
date: 2012-05-12
forum: General Help
---

### Post by KestrellKestrell on 2012-05-12
I disabled gnome screensaver and installed xscreensaver as below:
sudo apt-get remove gnome-screensaver sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra

Then I launched the xscreensaver-demo by typing "screensaver" in the dash.  
I selected [FONT=Verdana]"ONly One Screen Saver Mode" and [/FONT]chose "GLSlideshow".

In the "Advanced" tabI checked "CHoose Random Image:" and pointed it a folder containing subfolders of all my pictures.

It will only display that yellow, blue, green and red bars default picture and does not see any of my pictures.

Please help.

---

### Post by egyres on 2012-05-13
Got the same problem. Not find the solution yet.

---

### Post by KestrellKestrell on 2012-05-13
Well at least we aren't alone.  What should we do about it?
I checked the permissions, it doesn't seem to be a permissions issue.  I've also tried other directories, even downloading new pictures to a brand new directory, and GLSlideshow still doesn't see them.

---

### Post by egyres on 2012-05-14
For the moment, I have no idea.
This problem affects any screensaver of Xscreensaver using pictures (GLslideshow, Photopile, etc).
I am working on a fresh 12.04 Ubuntu instalation (except "/home"). I tried also to change screensaver parameters, pictures folder, etc. It has no effects.
I deleted the previous Xscreensaver config file. It creates a new one, but it does not solve the problem.

I will continue to explore forums.

---

### Post by KestrellKestrell on 2012-05-14
I'm using 64bit Ubuntu.  You?
I haven't tried the other screensavers only GLSlideshow.

---

### Post by egyres on 2012-05-15
I am also using Ubuntu 64.
Xscreensaver worked with Ubuntu 11.10 64 bit on my PC. It bugs since I freshly installed 12.04.

---

### Post by KestrellKestrell on 2012-05-15
I wonder if it is related to 64 bit.
You know, one other thing that we have in common, I did a fresh install too, including the home directory, but before I installed Xscreensaver, I copied my old .xscreensaver file from Ubuntu 11.10 64 bit, that I had saved elsewhere to my home directory, naively thinking that would save me setup time...I have since deleted it and started over of course, to no avail.

Hey all you Ubuntu experts, what is going on here?

---

### Post by Megaptera on 2012-05-18
> **egyres said:**
> Got the same problem. Not find the solution yet.

Same here, 12.04 64bit as well - any help?
T I A

---

### Post by KestrellKestrell on 2012-05-18
> **Megaptera said:**
> Same here, 12.04 64bit as well - any help?
T I A

Nope, still have the issue.  WTF?

---

### Post by KestrellKestrell on 2012-05-20
I found a fix!  
```
sudo apt-get install libwww-perl 
```
Again, all you Ubuntu experts out there, WTF?

---

### Post by Megaptera on 2012-05-20
Thanks,
I'm on restricted download limit at the moment so I'll have to wait 'til Friday to try!

---

### Post by egyres on 2012-05-20
It works for me !
Thanks.

---

### Post by Wheel on 2012-05-23
Exact same problem here.
Your fix worked for me as well.
Thanks!

---

### Post by Megaptera on 2012-05-25
Worked for me too! Thanks!

---

### Post by gelie on 2012-05-26
Thanks the fix worked for me also. Ubuntu 12.04, 64-bit.

---

### Post by Wheel on 2012-05-27
A follow-up to my earlier post announcing success for the helpful suggestion offered by KestrellKestrell.

This has only *partially* fixed the problem.
Some pics show; some do not and I can't figure out why.
It seems to be about 50-50.

These are pics copied from various web pages, not taken from my camera, if that makes any difference.

All of the pics have the same .jpg format.  They all share identical ownership (that would be me) and permissions (owner,  r-w only)

Does anyone have an idea as to how I can include my other pics?

---

### Post by gmcorwin on 2012-06-02
> **KestrellKestrell said:**
> I wonder if it is related to 64 bit.
You know, one other thing that we have in common, I did a fresh install too, including the home directory, but before I installed Xscreensaver, I copied my old .xscreensaver file from Ubuntu 11.10 64 bit, that I had saved elsewhere to my home directory, naively thinking that would save me setup time...I have since deleted it and started over of course, to no avail.

Hey all you Ubuntu experts, what is going on here?
Thanks for solving GLSlideshow.   I installed XScreensaver but could not display my pictures in GLSlideshow.  I installed KDE Screensaver and it worked fine so I deleted KDE Screensaver and reinstalled XScreensaver and GLSlideshow worked but I did not know what fix it.  I thought it was something to do with Perl but could not figure out what it was.

I installed  "libwww-perl" , logged out and logged back in and it worked.  It now saw my pictures.  

Thanks for letting everyone know what was missing for XScreensaver.

---

### Post by ktkoma on 2012-07-25
I am also having the problem with a fresh build of 12.04 64bit.  The sudo apt-get install libwww.perl was already installed and it still is not working.

---

### Post by xycris on 2012-07-26
this fixed my problem. thank you for the fix. hopefully they will include this in the installation of xscreensaver in cases that there tons of us who experience the same.

btw, what is in the libwww-perl? just curious...

as for Wheel's case, it worked fine for me. all my images vary in sizes and all were taken by me. i have very wide shots (panoramic) to 4:3 stills.

have you checked your video card? maybe the culprit lies there. my unit has nvidia but things were shown awfully wrong not until i read on the problem with video card yesterday, it was the optimus feature of the nvidita card installed on my unit.

hope this helps.

---

### Post by Ter Rymon on 2012-09-28
I also having this issue with fresh install of 12.04 with all updates applied.  If I select /usr/share/backgrounds, they show; however, if I select ~/Pictures, they don't.

I think it might have to do with how folders were created?? Any suggestions?

---

### Post by weclark on 2012-10-21
This appears to have worked for me as well.

Ubuntu 12.04.1 LTS 64 bit.

---

### Post by tabinin on 2012-10-23
also worked in 12.10.

---

### Post by candtalan on 2012-10-27
> **KestrellKestrell said:**
> I found a fix!  
```
sudo apt-get install libwww-perl 
```
Again, all you Ubuntu experts out there, WTF?

Thanks! this worked for me. A new install of 12.04 (keep existing home folder).

---

### Post by eldiabolosk on 2012-12-13
Running sudo apt-get install libwww-perl did not help. 
Anybody got it working?

---

### Post by prabin-dahal on 2012-12-17
> **eldiabolosk said:**
> Running sudo apt-get install libwww-perl did not help. 
Anybody got it working?


I tried to run glslideshow from command line 

/usr/lib/xscreensaver/glslideshow

I found that LWP::Simple perl module was not installed. 
The following code will install the perl module.

$sudo cpan
cpan> install LWP::Simple
cpan> exit

Refer to this link for more details.
[http://stackoverflow.com/questions/10524840/cant-locate-lwp-simple-pm-in-inc](http://stackoverflow.com/questions/10524840/cant-locate-lwp-simple-pm-in-inc)

---

### Post by digitography on 2012-12-20
Thanks for this answer worked for me.
The annoying part is that I have installed xscreensaver on a whole bunch of computers, and they all worked fine, except this one!
The hardware of all the computers has been very similar, ie all HP and all fairly new.

Oh well it solved the problem which is the important thing.

---

### Post by dbaruzzini on 2013-10-26
Hello all, I'm sorry to bother you with this, but it seems none of the solutions found here working for me.
Uninstalling and reinstalling xscreensaver and perl din'd work either.
The only thing I can say is that GLslideshow used to work (picking up my set of photos) before I installed Eclipse and Node.js.
I don't know if it's related to it, maybe this can give a hint to someone.
Thank you for any idea.
D

---

### Post by dbaruzzini on 2013-10-27
Hi all, here another thing I discovered.
Running  xscreensaver-demo from command line
I get this:
unable to write /tmp/.xscreensaver-getimage.cache: Permession denied
Maybe it's related to the problem
David

---

### Post by Toz on 2013-10-27
> **dbaruzzini said:**
> Hi all, here another thing I discovered.
Running  xscreensaver-demo from command line
I get this:
unable to write /tmp/.xscreensaver-getimage.cache: Permession denied
Maybe it's related to the problem
David

What are the permissions/ownership of that file:
```
ls -al /tmp/.xscreensaver-getimage.cache
```
If it is not owned by your user account, you'll need to either delete the file or change the ownership.

What version of ubuntu are you using? In 13.10, that file sits in my home directory, not /tmp.

---

### Post by dbaruzzini on 2013-11-03
Hi Toz, thank you for replying and sorry for not coming back to you earlier, pretty busy week.
Sorry also for not putting any system specs.
I'm running 12.04 with gnome shell 3.4.1 and the version of Xscreensaver is the 5.15 (installed via apt-get install).
Back to the problem, the weird thing is that there is no /tmp/.xscreensaver-getimage.cache. 
In fact the message can be red as "I can't write this file I need".
The weird thing is, as you say, that Xscreensaver should try to write the file in my home directory...wait, let me check...in fact the file is right there.

So what have we got here is a script somewhere with a faulty address isn't it?
What do you think?
I mean, I've played around with some programming stuff, instaling thing I didn't understand. 
Maybe something has overwritten some system file telling some kind of script to point to /tmp instead of /home, I don't know it's a long shot.

Anyway I'v got my ".xscreensaver-getimage.cache" file right where it belongs (/home) and my /tmp seems to work fine (only root can do things there)

Thanks for any reply and sorry for my bad english and poor knowledge of anything.

D

---

### Post by Toz on 2013-11-03
Can you post back the results of these commands:
```
ps -ef | grep xscreen
```
```
ls -al | grep xscreen
```
```
ls -al /tmp | grep xscreen
```
> ...and my /tmp seems to work fine (only root can do things there)
Not necessarily true. Anyone can write to /tmp. Just keep in mind that the contents will be wiped on every reboot.

---

### Post by dbaruzzini on 2013-11-04
Hi Toz, thanks for replying so swiftly, here are the results of the commands you asked:

# ps -ef | grep xscreen
david     2357  2254  0 07:02 ?        00:00:02 /usr/bin/xscreensaver
david     9371  9317  0 21:13 pts/1    00:00:00 grep --color=auto xscreen

#ls -al | grep xscreen
-rw-r--r--  1 david david     7747 nov  3 11:53 .xscreensaver
-rw-r--r--  1 david david     7658 ott 27 13:09 .xscreensaver~
-rw-r--r--  1 david david      559 lug 27 16:01 .xscreensaver-getimage.cache
-rw-r--r--  1 root  root      7650 ott 27 11:59 .xscreensaver.old

#ls -al /tmp | grep xscreen
This one gives no result.

Thanks again for taking the trouble of thinking about this,

D

---

### Post by Toz on 2013-11-04
> **dbaruzzini said:**
> Hi Toz, thanks for replying so swiftly, here are the results of the commands you asked:

# ps -ef | grep xscreen
david     2357  2254  0 07:02 ?        00:00:02 /usr/bin/xscreensaver
david     9371  9317  0 21:13 pts/1    00:00:00 grep --color=auto xscreen

#ls -al | grep xscreen
-rw-r--r--  1 david david     7747 nov  3 11:53 .xscreensaver
-rw-r--r--  1 david david     7658 ott 27 13:09 .xscreensaver~
-rw-r--r--  1 david david      559 lug 27 16:01 .xscreensaver-getimage.cache
-rw-r--r--  1 root  root      7650 ott 27 11:59 .xscreensaver.old

#ls -al /tmp | grep xscreen
This one gives no result.

Thanks again for taking the trouble of thinking about this,

D

Everything looks good. Can you open a terminal and run:
```
xscreensaver-demo
```
...again and note if it works and what messages appear on the terminal window afterwards?

---

### Post by hunterrjh on 2013-11-09
Fantastic. Thank you very much.

---

### Post by dbaruzzini on 2013-11-09
Hi Toz,
here it is the xscreensaver-demo results

xscreensaver-getimage-file: unable to write /home/david/tmp/.xscreensaver-getimage.cache: Permission denied

Thanks again,
D

---

### Post by dbaruzzini on 2013-11-09
Ah, sorry, it's still showing only the XScreensaver logo

---

### Post by dbaruzzini on 2013-11-09
Ah, I just noticed it writes again this line (xscreensaver-getimage-file: unable to write /home/david/tmp/.xscreensaver-getimage.cache: Permission denied) about every 30 seconds.
D

---

### Post by Toz on 2013-11-09
> **dbaruzzini said:**
> Ah, I just noticed it writes again this line (xscreensaver-getimage-file: unable to write [COLOR="#FF0000"]**/home/david/tmp/.xscreensaver-getimage.cache**[/COLOR]: Permission denied) about every 30 seconds.
D
Interesting that it's pointing to a file in a tmp directory off of your home directory. Does that directory exist?
```
ls -al $HOME
```
...and if so:
```
ls -al $HOME/tmp
```

If it doesn't exist, what happens if you create one:
```
mkdir $HOME/tmp
```

---

### Post by dbaruzzini on 2013-11-10
Hi Toz, here is the result of #ls -al $HOME/tmp
[I]totale 8
drwxr-xr-x  2 root  root  4096 lug 28 12:32 .
drwxr-xr-x 93 david david 4096 nov 10 09:01 ..
[/I]
So yes, the directory exists and yes, it's odd that some script suddendly starts to point to /tmp instead of /Home as it should do (at least you told me you have your .xscreensaver-getimage.cache file there, so I suppose it's where it belongs to).
I mean Xscreensaver used to work just fine for me, then I installed some programming tools (Eclipse & Co.) and now it doesn't work.

Thanks again, 

D

P.S.
If you want the results to this command 
#ls -al $HOME
I can send them into a private message

---

### Post by Toz on 2013-11-10
Sorry, I wanted to see the permissions of tmp. Try:
```
ls -l $HOME | grep tmp
```
What happens if you link the file:
```
ln -s /home/david/.xscreensaver-getimage.cache /home/david/tmp
```

I don't know why it shifted from your home directory to the tmp directory. Maybe installing those apps created/changed an environment variable that xscreensaver also uses.

---

### Post by dbaruzzini on 2013-11-11
>>*Maybe installing those apps created/changed an environment variable that xscreensaver also uses.*
Hi Toz,
that's my idea, perhaps I should have asked [Jamie Zawinski]("http://www.jwz.org/") first, instead of pestering this forum with my machine configuration issues.
So thanks for your help and kindness.

I'm on another machine now, I'll try the "linking" tweak tonight.

Have a nice day,
D

---

### Post by dbaruzzini on 2013-11-11
Hi Toz, you did it, your tweak works!

Here's the results of your command:
#david@zaphod:~$ ls -l $HOME | grep tmp
drwxr-xr-x  2 root  root  4096 lug 28 12:32 tmp

Then I tried the symbolic linking but I I couldn't (permission denied), so I sudoed it and ...bingooo, I can see my son's pictures again in my screensaver.

Thank you very much for your help,

David

---

### Post by Toz on 2013-11-11
I'm glad it worked, but tmp in your home directory shouldn't be owned by root. Something is not right there. Did you ever run xscreensaver as root? Perhaps that is when the ownership to that folder changed. You might also try changing the ownership of that folder:
```
sudo chown david:david $HOME/tmp
```
...or if you're adventurous, try deleting the folder and see if it gets recreated or ends up using your home directory again.

---

### Post by dbaruzzini on 2013-11-12
mmmh, I'm very adventurous, but I think I'm going to stick to this tweak, unless it stops working just fine as is keeps doing even after a restart, eheh.

I always try to abide a rule (I suppose it's universal among the people who fix things) that is: "is it working? don't touch it!...if you can stop yourself".

Anyway, if my fingers will get bored and start craving for some hot keyboarding, I may try the other tweaks, I only need to know how to put the things as they were before i.e. how to remove the command "ln -s".

Thank you very much again,

David

---

### Post by Jonathan_of_Cincinnati on 2014-07-30
I have the same problem and was reading the thread.  What was the final answer?  I was (still not sure how) able to get the preview window to see my PICTURE folder.  But the screensaver did not.  Any chance, "Jamie Zawinski, based on an earlier version that was Copyright © 2002 by Mike Oliphant." could update the software to get it to work instead of us tweaking it.

---

### Post by Wheel on 2014-07-31
Hi J_of_C,

Did you see post #10?
That's what I used to fix the problem.
No idea if this fix works on any system other than 12.04, 64 bits.

Good luck

---

### Post by Marco_Bagliacca on 2014-08-27
perfect, solved the problem in my computer with ubuntu 12.04lts 32bits

---

