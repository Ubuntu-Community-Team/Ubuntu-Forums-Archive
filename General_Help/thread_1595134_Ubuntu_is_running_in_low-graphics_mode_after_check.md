---
title: "Ubuntu is running in low-graphics mode after checking drive for errors"
date: 2010-10-12
forum: General Help
---

### Post by unknownjason on 2010-10-12
I have been running 10.4 with no problems for some time now. Today when I booted up it started checking the drive for errors, and I just left it to do its thing. I came back to this warning screen:

Ubuntu is running in low-graphics mode
Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.
OK

I press OK and am given the following options:
Run Ubuntu in low-graphics mode for just one session
Reconfigure graphics
Troubleshoot the error
Exit to console login
Restart X

I've tried all of these with no luck. 
When I select to run to low graphics mode, it says "Stand by one minute while the display restarts...OK"
I select OK and then it gets stuck checking for battery state.
I try to reconfigure the graphics, and nothing happens when I select any of the options on the next screen.

I'm newish to Linux, and could use some help...
Thanks.

---

### Post by 23dornot23d on 2010-10-12
What graphics card do you have and what computer is it please .......

---

### Post by unknownjason on 2010-10-12
The computer is a custom thing I bought for cheap on ebay a few years ago. I have no idea what the graphics card is. Am I screwed?

---

### Post by 23dornot23d on 2010-10-12
Looking at your previous posts ..... is it still this one .... ?

 was looking at your old posts 9.10

lspci | grep VGA :
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)

lshw -C display :
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: 82G33/G31 Express Integrated Graphics Controller

do this in a terminal just to check ........ again .... 
was looking at your old posts about 9.10 ...... if its the same card I will do a quick check to see if there are any problems and solutions

[B]lspci -v


[/B]

---

### Post by unknownjason on 2010-10-12
Yup its still the same!

---

### Post by 23dornot23d on 2010-10-12
You got it going last time here ..... it should be the same ..... or similar to get it going 
again ......

[Link]("http://ubuntuforums.org/showthread.php?t=1319491&page=4")


Type 

  more /etc/X11/xorg.conf



just see if the file exists and looks the same as you had before .... it maybe needs doing again .....

Is it this monitor sitll ? ...... [LINK]("http://reviews.cnet.com/lcd-monitors/viewsonic-vx2025wm/4505-3174_7-31747549.html")

---

### Post by unknownjason on 2010-10-12
I am unable to open a terminal to do this, because I cant get anything past that warning..

---

### Post by unknownjason on 2010-10-13
Yea. Same monitor, same computer. No changes.

I just rebooted (again) to try something new, and the:
Your disk drives are being checked for errors, this may take some time.

This what caused the problem, perhaps it will fix it...

---

### Post by 23dornot23d on 2010-10-13
Ctrl + Alt + F1

will get you to a console once it finishes checking .....

Why its checking the disk so much is a worry ..... maybe the drive is on its way out > !!!

What sort of errors does it report if any on the disk checking  ?

If it was my computer ..... 

I would just make sure everything is uptodate first - but you need to do

 **Ctrl + Alt + F1**

It will ask you to

login as normal .....  on a plain black screen .....

then do the following ..... just to make sure that the system is all uptodate .......

[B]sudo apt-get update

sudo apt-get install aptitude[/B] [B]

sudo aptitude update[/B] [B]

sudo aptitude safe-upgrade


and then 


sort out the xorg.conf (by adding a new one - the option to [/B]Reconfigure graphics then[B] create new xorg.conf)

and reboot should work 
[/B]

---

### Post by unknownjason on 2010-10-13
It finished, and went right back to the warning screen.
I then ran all the updates that you recommended, and everything is still the same. I dunno what to do.
it won't let me select anything past the reconfigure graphics option. I press ok but nothing happens.

---

### Post by sendblink23 on 2010-10-13
> **unknownjason said:**
> It finished, and went right back to the warning screen.
I then ran all the updates that you recommended, and everything is still the same. I dunno what to do.
it won't let me select anything past the reconfigure graphics option. I press ok but nothing happens.

I think maybe some of your hardware... is going bye bye soon :(
Would you.. give a try and installing an older Ubuntu version.. maybe your machine would be happier there

---

### Post by 23dornot23d on 2010-10-13
Ok if you managed to do the updates ok .... you can get work with the terminal and you have a internet connection .... too .....

so things are not all bad ..... 

and you got it to work before .... [here is the output you posted ]("http://ubuntuforums.org/showthread.php?t=1319491&page=5")

[COLOR=Red]only thing is that you did not post the final xorg.conf[/COLOR]

There so 

lets look at the xorg.conf ............. do you have any backups in there too ,,,, it may still be there

[B]cd /etc/X11/

ls[/B]

List the files and see how many **xorg.conf**.xxxxxx ........... there are ..... *(the xxxxxx may be **backup** or a date ...... **10012010 **or similar )

[B]more /etc/X11/xorg.conf

see if these are the same .... or different .... !!! .... or are there any other backups in there too ?

more /etc/X11/xorg.conf
[/B]
see if its similar to what your original was that worked ok ........ it should be in the other thread you had .... print it off ...... you may need to type it in again .....
if you can remember what you did last time ..... as the full xorg.conf is not there ........

Can you type out what the latest one created for you ..... and post it please .........

---

### Post by unknownjason on 2010-10-13
I have 4 xorg.conf files. When I type in:
[B]cd /etc/X11/

ls
[/B]
This is what I get:
app-defaults                       rgb.txt                   xorg.conf-backup-101012221853                 xorg.conf.failsafe       Xresounces        XvMCConfig
cursors                                     X                       xorg.conf.dist-upgrade-200905070201       xorg.conf.old               Xsession             Xwrapper.config
default-display-manager xinit                   xorg.conf.dist-upgrade-200911060851       Xreset                         Xsession.d
fonts                                           xorg.conf~          xorg.conf.dist-upgrade-20100714755         Xreset.d                    Xsession.options

---

### Post by 23dornot23d on 2010-10-13
Ok now we have to work out which was the one that worked ok

so first we should copy them or archive them so that we do not loose the good one - (that could be there).

So first do this ..... just to be safe

**cd /etc/X11/**

[B]sudo apt-get install zip
[/B]
**sudo zip  xorg  *.***

Then we can start by using one at a time and see if one will work ok ......

[COLOR=Red][B]Let me know when you have a successful backup
[/B][/COLOR] 

These look old but - may be promising ... 

xorg.conf.dist-upgrade-200905070201

xorg.conf.dist-upgrade-200911060851

xorg.conf.dist-upgrade-20100714755


To look at these files .... you can do .... more lists the full contents of the file

[B]more xorg.conf.dist-upgrade-20100714755

or 

less [/B][B]xorg.conf.dist-upgrade-20100714755

[/B]displays it little by little .... 

**ctrl + z**

to exit

You may be able to recognize the one that worked for you last time ..... 
in which case we will just use that one as the proper xorg.conf

possibly the last one is the one ..... so its probably ..... this you need to do once you have the zip backup file.

**sudo mv**   [B]xorg.conf.dist-upgrade-20100714755   xorg.conf

Then reboot


[/B]

---

### Post by unknownjason on 2010-10-13
I'm not sure what should happen when I do the backup, and if what I did was successful. 
I'm doing this on my phone, so here is a picture of what the output was after I hit [B]sudo zip  xorg  *.*:

[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-ash2/hs004.ash2/33542_568273648354_46303541_32933281_6159232_n.jpg[/IMG]
[/B]

---

### Post by 23dornot23d on 2010-10-13
Yep that worked .. now you have a zip file with all the files in that directory in it .. there will be a new file [COLOR=Blue]**xorg.zip**[/COLOR] in that directory now .....

just do 

**ls**

to check ....

then continue with the command below ... this will create the new xorg.conf 

**sudo mv**   [B]xorg.conf.dist-upgrade-20100714755   xorg.conf

Then reboot[/B]

---

### Post by unknownjason on 2010-10-13
Just ran **ls** and there isn't another one added. Just the same that were there before..

---

### Post by 23dornot23d on 2010-10-13
Bizarre ,,, I did it to check and your output looks ok ....... adding the files to it ... [COLOR=Red]**xorg.zip**[/COLOR]

[IMG]http://img706.imageshack.us/img706/2162/zipm.png[/IMG]

Show me a screenshot of the directory like you did last time .......

[B]cd /etc/X11
ls[/B]

---

### Post by unknownjason on 2010-10-13
AH! The number stayed the same, but that name -did- change. its xorg.zip now.

So I'm cool to proceed..?

---

### Post by 23dornot23d on 2010-10-13
Yep .... you have a copy now .... of all the files in there ....  so we can continue ....

I just play safe because we are now going to overwrite the file that sets the graphics up for you ......

with a old one from a previous setup you had before .... and hopefully that should work ok

I chose the most recent , it should be the one used before the upgrade ....

did you manage to look at it to check it looked ok ....

**sudo mv**   [B]xorg.conf.dist-upgrade-20100714755   xorg.conf

Then reboot[/B]

---

### Post by unknownjason on 2010-10-13
It's saying:
mv: cannot stat 'xorg.conf.dist-upgrade-20100714755': No such file or directory

---

### Post by 23dornot23d on 2010-10-13
Its a simple move command ..... it moves one file to replace the other.

Why its not working is hard to say ...... 

[B]I can just see the error on the screen ..... before the backup ....... that you posted ..... did you get to see
the contents of this file ok ...... previous to doing this ?[/B]

I have just had a quick check around for errors on mv .... and they seem to point to
a faulty file .... !!!

what happens if you do this

sudo mv xorg.conf-backup-101012221853 xorg.conf

---

### Post by unknownjason on 2010-10-13
I get the same message....

---

### Post by 23dornot23d on 2010-10-13
Can you post a photo of the full screen showing what you have tried upto now please .....

I might be able to get a better idea from that ........ if not ......

Try this ... it may not like the fact a file is already there .... CP for copy in lowercase

sudo cp xorg.conf xorg.conforiginal
sudo rm xorg.conf
sudo cp xorg.conf-backup-101012221853 xorg.conf

If none of the above works .... 
I do not know what is happening ....

---

### Post by unknownjason on 2010-10-13
[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-snc4/hs786.snc4/66671_568284441724_46303541_32933457_601094_n.jpg[/IMG]

This isn't everything, because after I tried the first time I rebooted to see if anything had worked.

---

### Post by 23dornot23d on 2010-10-13
ok one thing I spot is ...... 

**cd**   /etc/X11

This needs doing **first** and make sure that there is space ..... in between **cd**    and the** /etc/X11**

then [COLOR=Red]that makes sure you are in the right directory[/COLOR] then it should work ok

**sudo mv**   [B]xorg.conf.dist-upgrade-20100714755   xorg.conf

Then reboot[/B]

---

### Post by unknownjason on 2010-10-13
What do you mean by make sure I'm in the right directory?

I tried it again after doing cd /etc/X11 correctly, and I got the same no such file or directory message..

---

### Post by 23dornot23d on 2010-10-13
When you do a 

ls

the file names should be there ... for the files we are moving .... in the screenshot you
showed there was a error ..... after cd /etc/X11

There is something else wrong then ....

Some one else might be able to see whats wrong ...... 

I thought the easy way was to restore one of your backup files ..... but its proving not to be that easy .....

If it was mine ..... 

I would be tempted to re-install it again takes 30 mins ...... just to ensure everything is as it should be .... the install process
should set everything up ..... if it does not .... then there may be something else wrong.


**What we tried is to ..... copy the backup into place and then reboot it - it should then boot up with the correct old settings ..... but that is not happening .....**

---

### Post by unknownjason on 2010-10-13
The error was because the first time I forgot to put the space.
This is what I get after putting in** ls**:

[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-snc4/hs834.snc4/69433_568286402794_46303541_32933481_5223997_n.jpg[/IMG]

---

### Post by 23dornot23d on 2010-10-13
Ok that worked .... other than for the move command ..... the copy is working so the files are ok

You have the old xorg.conf there now ..... so we can try one at a time .... 

You have 4 chances .... with the old backups you have there ...... hopefully you have one from before that still works ok

do a

reboot now

---

### Post by unknownjason on 2010-10-13
Rebooted. Back to the original 'Ubuntu is running in low-graphics mode' screen

---

### Post by 23dornot23d on 2010-10-13
Ok do the same again

[B]cd /etc/X11

sudo cp xorg.conf.dist-upgrade-200911060851 xorg.conf[/B] [B]

reboot

[/B]Try this it may give us more of a clue [B]

startx

[/B]

---

### Post by unknownjason on 2010-10-13
Again, no such file or directory...

---

### Post by 23dornot23d on 2010-10-13
Ok its upto you .... the time it will take to load another OS up that detects the monitor properly will take possibly 30 mins .....

Thats what I would try ..... unless someone else watching this thread can help you out.

I usually set up Nvidia graphics cards and they work most of the time with new drivers

I looked at what you went through before to set this monitor up ...... the thread that you
used ...... [maybe the answer is in there somewhere]("http://ubuntuforums.org/showthread.php?t=1319491&page=5") ..... or if you contact the user that sorted it for you the last time around ......

I am out of ideas ..... on this ..... as nothing seems to be changing ...... sorry :confused:

you could remove the xorg.conf completely and see if it goes into graphics mode .....

or failing that reinstall gdm (this is the gnome desktop manager)

[B]sudo aptitude install gdm
[/B]
one thing that used to work if gdm was giving me a problem at booting up was to load kdm the kde Desktop Manager

[B]sudo aptitude install kdm

but these are last ditch attempts before a full re-install as you said previously this started from some possible errors on the filesystem

[/B]> 
Today when I booted up it started checking the drive for errors, and I  just left it to do its thing. I came back to this warning screen:


---

### Post by unknownjason on 2010-10-14
I did both:[B]

sudo aptitude install gdm
[/B]
[B]sudo aptitude install kdm

[/B]And after rebooting I was brought to this screen:
[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-ash2/hs391.ash2/66991_568357046224_46303541_32934553_5605468_n.jpg[/IMG]

After I click on my name and put in my password, it reloads right back to this screen... Progress?
THEN after a restart it went back to the old low graphics mode warning screen, but this time it has these reasons listed on it:
(EE) failed to load module "i915" (module does not exist, 0)
(EE) No drivers available.


hmmm.....

---

### Post by 23dornot23d on 2010-10-14
You may be missing xserver-xorg-video-intel

You could try this .... its the intel display driver ..... 

(there may be a problem with gnome  desktop too but we may be getting closer now)

[B]sudo aptitude install xserver-xorg-video-intel

try this first .....

[/B]But it probably needs the desktop loading in again .... which is just one more command ..... once the graphics are ok

---

### Post by unknownjason on 2010-10-14
ran :sudo aptitude install xserver-xorg-video-intel
and restarted. No improvement.

---

### Post by 23dornot23d on 2010-10-14
There are log files created for the screen driver in .....** /var/log/xorg.0.log**

type this below in - just to see what kernel is running .

**uname -a**

---

### Post by unknownjason on 2010-10-14
Linux Jason 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686 GNU/Linux

when I type in /var... I get no such file or directory.

---

### Post by watupgroupie on 2010-10-14
I was having pretty much the same problem you were. Try booting up in recovery and just continue and you should eventually get a terminal like screen just like you do now. Then I typed in startx and it worked. I'm still trying to figure out how to fix the normal startup.

---

### Post by 23dornot23d on 2010-10-14
To view the log file .....

**cd /var/log**

capital X and zero .... in the middle .... Xorg . 'zero' . log as below ....

**less Xorg.0.log**

**ctrl z**

to exit

you may be able to find out more information here ....

Have a look for this ........  X.Org X Server 1.9.0

is it 1.9 or 1.8 ........

Some reports that I have been reading point towards reverting back to a older xorg version ...... 1.7 .......

____________________________________________________________________________________

What gets me is why it suddenly stopped working ......... unless something got updated at the time it stopped.

The module needs loading with the kernel as far as I know ........ someone earlier mentioned going back to 

a version that worked for you ....... possibly that may still be the easiest option .....

**startx**

will start the x-server if everything is set up ok ..... but if its not .... it will just return a error .... 
but there is no harm in trying it, in safe mode .... the second option down in the grub boot 
menu ...... usually .... if linux is all you have,

The other thing is ..... are there still the options to boot into your older kernel .....

[B]maybe the third down in your boot menu .... !!!

The other question is ..... does it run and display ok from using a live CD .... if so which version ?

I really do hope that you get this going .....

( If I was there I would be trying as many different linux CDs as I had available ....
  to see which one picks up the graphics the best ....... then use that one ...... or try 
  to work out what the differences are ...... in drivers ..... )

If you look in my menu down below in the footer ..... there are loads that I use and they all work
slightly different ..... with different computers .... but the only way to find out is to try them.

Just a thought as we seem to be stuck at the moment ..........
[/B]

---

### Post by Slincher on 2010-10-15
I had the same problem. I want to say a few things about it for people who ever have this problem.

The reason that I REMOVED (sudo apt-get remove gdm) was because it ran upto 100% cpu. This was probable due to the VNC server. **The VNC servers of GDM and the X11VNC server did not startup anymore after the upgrade from ubuntu 10.04 to 10.10**. Notice that there might be a bug in the upgrade installation of ubuntu 10.10.

In the final I also fixed it by:

sudo apt-get purge gdm
sudo apt-get install gdm

now I lost my config of my VNC server(s) but that's worth it. My computer starts up again :]

---

### Post by unknownjason on 2010-10-15
@Slincher - I tried those codes, but no improvement. Thanks tho..

@23dornot23d - 

Here is what I get when I run startx:
[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-snc4/hs794.snc4/67424_568478862104_46303541_32936870_221928_n.jpg[/IMG]

I am unable to get to the grub menu for boot options, and for safe mode. I hold down tab (thats what you are supposed to do, correct?) and it looks like its going to go to it for a second, but then it goes to the warning screen instead. I then have to cancel out of that to get to a terminal.


The only CD I could find is 8.10, and its running off the disk perfectly! If going backwards and installing an older version is my last hope, there isn't any chance that files from my old system that I had yet to back up will still be there, is there?

---

### Post by 23dornot23d on 2010-10-16
Your files are still all on the drive ..... and safe ..... and you can boot from a CD ok ...... 

so you can get them off the machine and back them up .... 

I also notice that you have run out of space on the drive ..... the top messages are saying that the disk is full ......

Basically saying that there is no space left on the drive ....... now this could be part of the problem .....

so first things first ...... clean it up .. .[B]sudo apt-get clean
[/B].. it just gets rid of old archives used to put the gdm etc onto the drive .....

also you are running the 1.7.6 Xserver ..... which may be good ..... 
 
so ...... 

Once we get some space back we will see what we can do ..... so to clean it up .....
That is to remove old archives that are no longer needed.
[B]
sudo apt-get autoclean

[/B]Then do a ....... DF .... disk filesystem ....... will tell us what space you have on the devices that you have setup ....... can you do a screenshot of the results or cut and paste them to the thread ..... whichever is easiest for you .....[B]
  
df


[/B]Do you have a lot of DATA on there photos films music etc ... and how can you back it up ...... do you have a external USB drive ...........[B]

If you have an external USB drive ...... you can copy your files to it .........

Booting from the CD ...... you should be able to drag and drop the files you need onto an external device .....
depends how much you have ...... and what sort of devices you have to backup to .....

If not we will work something out somehow ...... depending on how the drive is partitioned .....

[/B]

---

### Post by unknownjason on 2010-10-16
After running the cleaning, and df:

[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-snc4/hs789.snc4/66945_568546202154_46303541_32938529_4372455_n.jpg[/IMG]

Currently backing up my files to an external HD..

---

### Post by 23dornot23d on 2010-10-16
Ok good to hear .... you seem to have a 300 Gig Hard Drive and the root partition is Full to the brim .... [B]
300 Gig is that the full size of it > ?[/B]
Let me know when you have backed up the Data ...... unless you are ok now .... a fresh install should sort it all out
if its running ok from the CD .....

 If you run **Gparted** from the CD ..... just get to where it displays the disk layout 
and post a screen shot if you would please ......... ty ....... it may help me or others have a better idea of what the drive layout is like .....

How much of the 300 Gig is your useful Data ........ ? 
( knowing this might determine how its best to partition the new install .... I made some guesses down below though ...... as to how it might work out ok )

I have a feeling that what happened was .... the computer ran out of space doing a upgrade.
The thing is you only appear to have one partition .... do you use this with an external USB normally ?

We have to work out how best to lay out the drive ..... but once you have all your DATA off of it ....

Then you could do a complete clean install ..... and lay the drive out something like this ..... 
as an example of what I would maybe do with it ........ your choice here .... 
as regards what is best for what you use the computer for ........

If its just Linux ..... 

[B]30 Gig for root [COLOR=Red]/
[/COLOR][/B]**30 Gig unnallocated (leave this available - so you can try another OS later on .... will make for a easy way to upgrade and test things) **
and if you do not use it .... you can always re-size your root system to use it later on ..... if needed ......
[B] 4 Gig for [COLOR=Red]swap[/COLOR]
236 Gig for [COLOR=Red]/home [/COLOR][/B][B](set this to accommodate your Data .... I just gave this figure as what is left on the drive after setting the main part up)
[/B]This can be smaller ..balance the drive partitions the way you feel you would need them  .. this is just an example .....

I rarely use more than 100 Gig though ....... on any of mine .

**Hope you get it sorted ..... seems like the problems may stem from running out of space though** .....

[COLOR=Blue]You could run your operating system from the External USB and leave the DATA where it is ..... depends if you are going to
be attaching and detaching it all the time though ..... 
I have 3 external USBs ..... and always have one plugged in.
But the computer boots with its own internal .... or with any of the 3 external USB drives that I have ..... they are slightly slower
than the internal ..... but for most things they are fine .....[/COLOR]

---

### Post by unknownjason on 2010-10-18
I backed everything up, and went ahead and did the clean install.
The monitor was again f-ed up, but I fixed it as per this post:
[http://ubuntuforums.org/showthread.php?p=8302145#post8302145](http://ubuntuforums.org/showthread.php?p=8302145#post8302145)

Thank you so much for all of your help!!

---

### Post by 23dornot23d on 2010-10-18
Ok glad you got it working ......

[COLOR=Blue]**Post the xorg.conf ..... onto here ...... then it will always be available for you should you ever need it again ......**[/COLOR]

Best of luck in the future with your setup ..... 

keep the /etc/X11/xorg.conf safe useful  for upgrades too by posting it somewhere you can retrieve it ...... 

specially with monitors that do not pick up automatically ....... ( this is advisable to others too )

[COLOR=Red]It takes a minute or two to post it somewhere ... but a lot longer to work it all out again.[/COLOR]

ok all for now and good luck in the future.

---

