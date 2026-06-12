---
title: "major upgrade bugs"
date: 2009-11-13
forum: General Help
---

### Post by elishac on 2009-11-13
hello,
i'm starting with linux.
i'm using ubuntu.
the computer offered me to install the last version (9.10, is it), which i did.
then i rebooted.
after this, the touchpad didn't work anymore.
i rebooted, and now, i can't even log in (it says the password is incorrect).
 
i need a FAST answer please, because i'm using a neighboor's computer, as mine is blocked at the login page (i don't even know how to make it stop without unpluging the plug).
 
i hope this forum will be able to help me, it's the second one i'm trying.

---

### Post by metalf8801 on 2009-11-13
try pressing 
ctrl Alt F6 
this will turn off the gui 
Then type 
         sudo shutdown -P now 
make sure to use an upper case P oh also make sure capes lock is not on 
also after you enter that your going to need to enter your password 

If this doesn't work don't unplug your computer just press and hold the power button for at least 5 seconds that should turn it off

---

### Post by elishac on 2009-11-13
When I press alt f6, I don't get a command line, but the login windows is not activated anymore : what's activated is a small icon in the bottom screen, and if i press enter then it opens a window asking me if i want some options to help blind people and such.

---

### Post by fluffman86 on 2009-11-13
No, that's CTRL + ALT + F6

If you want to keep troubleshooting this, then hopefully someone will have an answer for you.  My advice, however, is to get a Karmic Live CD, boot from it, back up your /home/username/ directory, and reinstall.

---

### Post by metalf8801 on 2009-11-13
> **fluffman86 said:**
> No, that's CTRL + ALT + F6

yeah thats what I meant I just don't like using the + sign because lol the fist time I saw that I thought I should press the + key

---

### Post by elishac on 2009-11-13
oh, sorry about that, i misread you.
ok, i pressed ctrl+alt+f6 then, and now the screen is black, and it gets white for a fraction of a second, which makes it flashy. there seems to be parts of line codes in the upper screen, but they can't be read.
i tried to type your command nonetheless (although what i type doesn't appear on the screen), and nothing happened.

---

### Post by elishac on 2009-11-13
i pressed ctrl alt del then ctrl alt echap then ctrl maj echap and one of them made the computer restart.

ok, so it has restarted then. what do i do now?

---

### Post by elishac on 2009-11-13
my problem is not nearly fixed, i just managed to stop the computer.
i still don't know how to get my mouse to work, and to fix all the other bugs.

---

### Post by elishac on 2009-11-13
please? :(

---

### Post by elishac on 2009-11-13
...

---

### Post by elishac on 2009-11-13
Maybe you can at least forward me to another forum where i have a better chance of getting answered?

---

### Post by elishac on 2009-11-13
:(

---

### Post by seanj on 2009-11-13
I wasn't able to use the new Ubuntu for various reasons, but you might want to check out [http://www.linuxquestions.org](http://www.linuxquestions.org) it's kind of sad no one actually using Ubuntu has any idea how to help you. Good luck.

---

### Post by elishac on 2009-11-13
What's weird is that, when i start the computer, it says "boot on ubuntu 9.04".
Do you think this has anything to do with my problem?
if yes, how to solve it?

---

### Post by 23dornot23d on 2009-11-13
If you choose boot 9.04 ..... does it start to boot ..... ?

You said your touchpad is not working ,,,, have you got a usb mouse ... 
it just might make things easier for now ...... 
for navigating on the screen .... 

I am thinking that you get as far as entering the username and password

as you said it does not accept a password ..... is CAPS lock off .....when you get to this point .........

---

### Post by elishac on 2009-11-13
yes, it boots, it's just that there are some features that don't work, such as the touchpad.

(i couldn't enter the password, but i rebooted and now it's ok, i'm in ubuntu)


can this have anything to do with the bios or something like that?
(like: the bios still thinks it's 9.04, and tries to load some files that don't exist anymore?)

---

### Post by elishac on 2009-11-13
what do you think?

---

### Post by elishac on 2009-11-13
please?

---

### Post by elishac on 2009-11-13
...

---

### Post by klemes on 2009-11-13
No its not the BIOS.
Why dont you try some of the suggestions the others already gave you?
Like plugging a USB mouse in the laptop and see if its working.
An other thing that come in mind is to boot in recovery mode and then boot into a root prompt and try to give this command:

```
passwd <your_username_here>
```

then hopefully it will prompt you for a new password.Give it two times as it asks you to and then try to login with your new password and see what happens....
That's all I can think for the moment.
Keep us informed how it goes although most likely backing up your home directory and making a clean install from scratch is the best practise assuming you know how to do this.;)

---

### Post by elishac on 2009-11-13
But why would the bios propose me to boot on the wrong version then?

i don't have a usb mouse.

I don't know how to install from cratch, and i'd rather not to anyway. (edit: i thought linux was the best os, that i wouldnt need to reinstall it, that it could stay on for years and such, and now i need to reinstall it all after 1 day only??? )

and I've already said I managed to enter my password now.

the only problem that remains, as far as i know, is that i can't use my mouse.

---

### Post by klemes on 2009-11-13
Thats not the BIOS.This is the grub menu.You can edit /boot/grub/menu.lst
accordingly to set it to boot 9.10 automatically by default.
Try to give the following command in the console:

```
less /var/log/messages |grep udev
```

And tell us the output.

---

### Post by mixmaster on 2009-11-13
I'm a little confused here.  On the first post you say that you upgraded to 9.10 (or at least tried to) and now when you boot you are being offered 9.04.  That sounds to me as though the upgrade has been screwed up in some way.

How did you do the upgrade? Via the upgrade option from Upgrade Manager or in some other way?  What happened when you did this - did it run to completion or did you interrupt it? 

If you start the upgrade manager what does it offer you (you can get to the menus via Alt-F1 even if you can't use the touchpad).

Do you have a Karmic live cd? If you boot that does your touchpad work?  If you haveb't got one, maybe you neighbour can make one for you.

---

### Post by elishac on 2009-11-13
i've been told that the version issue when the computer starts has nothing to do with the bios, but it's rather the file */boot/grub/menu.lst *that hasn't been updated.
i did try to install the new version.
i'm not sure if it was a window that appeared and asked me to do it, or if i opened the window myself.
it was the upgrade manager, yes.
it had to download quite a lot of things, and actually the first time around my connection didn't last that long, so it stopped. but i restarted it, and afterwards it seemed to go to completion.
when i start the upgrade manager it says "the system is up to date. the package informations have been updates 22h ago".

i don't have an internet connection though, maybe it's part of the problem?

no, i don't have a Karmic live cd.

i think it would be best to just go back to the previous version, but the problem is that :
- i don't know how to do it.
- it wasn't me who installed linux the first time around
- there's another os on the computer, with personal data.
- i don't have money to buy storage devices (and i don't have any available) to make backups if they are needed to reinstall it.

---

### Post by 23dornot23d on 2009-11-13
[i've been told that the version issue when the computer starts has nothing to do with the bios, but it's rather the file */boot/grub/menu.lst *that hasn't been updated.]

This is correct ...... for 9.04 in  [I]/boot/grub/menu.lst ....... this is the file that gives you your first MENU screen for options to boot your various Operating Systems ......

but for 9.10 its different ......... [/I][http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
but I think this is only for a clean install as this statement says
Grub 2 *will* be the default in Ubuntu 9.10, Karmic Koala but the plan is *not* to convert over previous Grub legacy installations to Grub 2.

_________________________________________________________________

[i don't have an internet connection though, maybe it's part of the problem?]

( A USB mouse would help you ..... but you are obviously managing so ....... )

Ok lets start here ...... because once you regain your internet connection ....... it gives
us a lot more options ........

______________________________________

So as Mixmaster says how did you do the upgrade ...... if you have no CD then you must have

  had a internet connection to do the upgrade ...... 

so first ........ how did your internet connect before ...... the upgrade

was it a wireless 
or 
a cable connection (USB or Ethernet)

once we re-establish an internet connection we need to re-check the system
is up-todate ......

as this is what I did and 9.10 is now running very well indeed ........ 

So ...... onward and lets find a solution .....

It sounds like its booting up ok ........ and you can enter a valid password and get into
the desktop ...... 

I can see now the problems are touchpad ...... 

( this can be sorted with a USB mouse for a start till we get the touchpad working )

 and once we regain the internet connection ...... then we can add any additional

packages you may need to get the touchpad working .... as long as its compatible ......

so then we need to ensure which version that you are running 9.04 or 9.10

(The Live CD would be very helpful as it allows us to check that 9.10 runs
ok on your system ... and would check if the touchpad works ok from it ...
thats if you can get a CD .....)



hope we can carry on from here ......

---

### Post by elishac on 2009-11-13
i had wireless.
(that was your only question, wasn't it?)

what shall i do now?

---

### Post by 23dornot23d on 2009-11-13
Ok I had the same problem ..... 

so I linked it up direct from the modem using USB

if you can do this or use a ethernet cable ......... guess it depends on your modem here though

as mine picked this up quickly ,,,, and as I keep reading ,,,, there seem to have been a lot of issues
with wireless connections ........

**Question** ......... What modem do you use and what computer is it by the way ?

once you have a cable connection you might then be able to get the updates ..... 

as I did ............. and .........

then I got my wireless connection back .....

for me it was plain sailing after that ...... 

I hope this helps ..........

---

### Post by elishac on 2009-11-13
i'm not from usa so i guess we don't have the same modems.
my computer is a hp laptop.

---

### Post by 23dornot23d on 2009-11-13
> **elishac said:**
> i'm not from usa so i guess we don't have the same modems.
my computer is a hp laptop.


I am not from USA either I am from France ..... 

but I use a Livebox ,,,

which has three types of connections ,,,, 

USB ETHERNET and WIRELESS ....

Model types help here a lot ............ 

Your Computer is HP ..... what model

Your Modem is ?

I can help if I have more info ..... 

as I can look on the net for more information on your particular setup and try to find a solution for you ,,,,,,

( I am finding this very difficult as all the things I have said so far ...... have got me to think I am wasting my time ) 

 so I will leave it here  ...... maybe some one else can help you  .......... 

_______________________________________________________________

Information Received to help me help you .........

The info gained so far ..... its a HP laptop .... 
the touchpad does not work
the wireless connection does not work
It appears to be booting from grub as 9.04 ......
It connects to a modem of some description ..... we do not know the type .....

My Recomendations .....

USB mouse ..... to make life easy for you
LIVE 9.04 CD ..... to check that the system works with and on the setup
USB or ETHERNET ..... wired connection to the modem if possible to get the updates

---

### Post by elishac on 2009-11-13
well we can speak in french then i guess :D

j'ai une freebox.
hp 6730b

---

### Post by 23dornot23d on 2009-11-13
There is a link here all to do with freebox ....

If you speak french ...... :D

 ( if you do not - it can be translated using google translate .... )


[http://www.commentcamarche.net/forum/affich-13317744-freebox-en-usb-avec-ubuntu-9](http://www.commentcamarche.net/forum/affich-13317744-freebox-en-usb-avec-ubuntu-9)



hope this helps a little for the freebox connection ........ using cable ......

Freebox ...... It still could be any device ...... a link to a picture ....

is it the same as in there advert ..... here ?

[http://www.free.fr/adsl/index.html](http://www.free.fr/adsl/index.html)

if so does it have the connections for Ethernet and USB

A grey cable with red ends on usually ..... comes supplied with this .......

( it could be a case of just plugging this into the freebox and the computer 
in the correct sockets ........ to get the internet working ........ again ...... )

Then we can see about sorting the wireless connection out ........
 
______________________________________________

will have a look now for the touchpad problem ...........

I can only find a couple of things that might be useful - this is a link to some useful information

on that particular model ....... 

[http://en.gentoo-wiki.com/wiki/HP_6730B](http://en.gentoo-wiki.com/wiki/HP_6730B)

the xorg.conf file ..... might be the next thing to look at ........ to see how yours has been set up .....

as this is the file that sets things up like keyboard screen graphics and mice etc ....
________________________________________________

All for now ......

---

### Post by elishac on 2009-11-13
i managed to restore the wireless connection
what shall i do now?

---

### Post by 23dornot23d on 2009-11-13
> **elishac said:**
> i managed to restore the wireless connection
what shall i do now?


The next thing is to check the xorg.conf file .......

can you open it in a editor and cut and paste it here ........ 


use this command in a terminal window .........


gedit /etc/X11/xorg.conf



there should be a backup file here too ......... which may help us to get the touchpad back
if it worked ok before ....... we will see ..........



then select all the text and copy and paste it here so I can see it ......... ty



I would rather you did this before doing any more updates or upgrades ..... as they may overwrite
the backup file xorg.conf ...... 


this obviously will not matter if it fixes the problem updating ..... but we may lose any valuable info
in the xorg.conf.backup file .............

gedit /etc/X11/xorg.conf.backup ............ and save it to your Desktop ...... for reference ......

before updating anything ........


If I do not hear anything back ...... here ...... I will presume that you are ok and have fixed it ........ ty

Interesting .... more info here ..... LinuxQuestions.org .... which I am a member of ....

[http://www.linuxquestions.org/questions/linux-newbie-8/update-problem-768835/#post3755176](http://www.linuxquestions.org/questions/linux-newbie-8/update-problem-768835/#post3755176)

You have posted to four forums .... what are the other two ........
Quote from LinuxQuestions.org
[ i hope this forum will be able to help me, it's the fourth one i'm trying. ]

How many people are trying to help on this one problem ?

I do not mind helping anybody .... but we all appear to be saying the same things ....

I really hope you have sorted your problem out .......

---

### Post by elishac on 2009-11-13
yes, i'm trying everywhere i can to get some help lol.
the best one is linuxquestions, followed by this one, then commentcamarche.net, and the last one is not even worth mentionning, i didn't get any answers.

only 2 people are really trying to help, actually.
you and a guy from linux.

---

### Post by 23dornot23d on 2009-11-13
> **elishac said:**
> yes, i'm trying everywhere i can to get some help lol.
the best one is linuxquestions, followed by this one, then commentcamarche.net, and the last one is not even worth mentionning, i didn't get any answers.

only 2 people are really trying to help, actually.
you and a guy from linux.


Ok see what you have done ..... its in the LinuxQuestions thread ......

[http://www.linuxquestions.org/questions/linux-newbie-8/update-problem-768835/page8.html](http://www.linuxquestions.org/questions/linux-newbie-8/update-problem-768835/page8.html)

[http://www.linuxquestions.org/questions/linux-newbie-8/update-problem-768835/page11.html](http://www.linuxquestions.org/questions/linux-newbie-8/update-problem-768835/page11.html)

The Full help ...... is amazing ..... 13 pages ..... 

and your problems - Grub ..... Password ...... the Wireless, Network and the touchpad ......

[http://www.linuxquestions.org/questions/linux-newbie-8/update-problem-768835/#post3755176](http://www.linuxquestions.org/questions/linux-newbie-8/update-problem-768835/#post3755176)

The problems ........ 

checking first with the Live CD to make sure everything was compatible  before upgrading ....

(Why the password problem and the menu link ,,,, stayed at 9.04 ..... is interesting though)


1. USB mouse would have been a temp ...........                  while sorting the touchpad problem ...
2. Cable to the Freeview                  ..................                would have got the internet back up for updates

so then you could update .... all of the software packages that needed updating to get wireless back

The touchpad ..... could probably have been fixed with restoring the xorg.conf.backup .......

but that may be too late now ........ as there are many more things going on ,,,,, 

____________________________________________________________________

WOW nice answers and lots of patience at the LinuxQuestions.Org forum though ..... well done

it looks like you are sorted now .........

[http://www.linuxquestions.org/questions/linux-newbie-8/update-problem-768835/page12.html](http://www.linuxquestions.org/questions/linux-newbie-8/update-problem-768835/page12.html)

........ touchpad .... works ok ...... in last message ,,,,

So how do you do a full system check to make sure its all ok ,,,,,, thats a hard one ,,,,,

Try it out and see what works ......... I guess ,,,,, 

as I do not know of a full System Checking Tool ...... other than use it and find out what

Works and What does not work ...........

as said at LinuxQuestions.org
(Apparently known problem is the wireless, so check if you have internet access. 
Play around with it, check if all applications work, webcam, printer, scanner, whatever.)

and mark it as complete ,,,, if its working ....

Best of Luck ..... in the Future with 9,10 .....

I am quite enjoying it now ......

;) ..... well done everyone ...

---

### Post by 23dornot23d on 2009-11-14
I am adding this because it is the CONCLUSION to the problems one user had ...... and could be one

of the main problems others may be having ...........


The answer was found after a long process and both the USER and The person that fixed it had a lot of patience ........

Here is what Eric .... 

The person at LinuxQuestions concluded ......... and I too agree that it all stemmed from this ......... one thing ....... 

Booting from the correct .......... Kernel ....... 

I can relate to this ..... too as my GRUB was created by ELIVE ,,,, and I too found that 

The UBUNTU installation did not change my GRUB ,,,,,, 


_______________________________________________________________________

Hi elishac,

What's up? Checked everything and found it working again as it should? I hope so. 

What happened, in short and simple words, is that your [[COLOR=blue][FONT=Verdana][FONT=Verdana]upgrade[/FONT][/FONT][/COLOR]]("http://www.linuxquestions.org/questions/#") didn't change the boot manager configuration correctly. As a result of this you were booting with the kernel of Jaunty instead of the one that comes with Karmic. 

Apparently a lot of things changed in Karmic, resulting in the fact that various things didn't work anymore after your upgrade. This just because packages and modules and such were upgraded correctly but since you booted into the 'old' kernel were not compatible or recognized by that one.

What you have done yesterday is install the correct version of Grub, the boot manager, then do an upgrade from legacy to change from using menu.lst to grub.cfg. Then you checked what devices could be found by Grub and install the boot manager correctly.

So after doing all that, when you rebooted the correct kernel was loaded, and with that you got all modules, packages, [[COLOR=blue][FONT=Verdana][FONT=Verdana]drivers[/FONT][/FONT][/COLOR]]("http://www.linuxquestions.org/questions/#") and such recognized and working again.

Kind regards,

Eric

_________________________________________________________________________

If this is totally correct ............ then maybe a lot of the problems being seen arise from this one thing

if so can it be made any better to check the GRUB ...... has been updated and show the menu you will get

after the installation ...........


Then at least the user can see if what they should get ..... as a boot menu ....... is actually the same as
what appears after the re-boot .............

__________________________________________________________________________

Ok All For Now ..... hope this helps someone ........

---

### Post by Monotoko on 2009-11-14
My advice would be the same, get a Karmic liveCD, bott from it, backup your home dir, then reinstall.

---

