---
title: "Newbie trying linux.  Problem with video card... I think."
date: 2010-02-17
forum: General Help
---

### Post by BewilderedStranger on 2010-02-17
Howdy folks,
I have been thinking that I wanted to try out [[COLOR=#0000ff][COLOR=#0000FF ! important][FONT=Arial][COLOR=#0000FF ! important][FONT=Arial]linux[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxnewbieguide.org/content/video-card-driver-problemi-think#") for quite some time now. Well I finally initiated the first steps of the operation and have run into a problem before even getting a glimpse of the [[COLOR=#0000ff][COLOR=#0000FF ! important][FONT=Arial][COLOR=#0000FF ! important][FONT=Arial]desktop[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxnewbieguide.org/content/video-card-driver-problemi-think#"). Haha typical. I donloaded the iso and burned it and started looking at partitioning everything and I have a question about that as well but I'll get to that in a moment. I decided before I went through all the hassle of installing it and partitioning drives I'd check it out on the live cd. So I restart and boot from the cd and it works up to the black loading screen with the little symbol in the middle then my monitor switches to blue and gives me the no signal message. It never returns. I would assume my video card is not supported or something along those lines. Also I am currently running vista x64 and when I go to shrink my partition I notice that if I shrink my partition it doesn't get very small at all. I think this may be because I have all kinds of files on the partition. When I do set this all up I wanna be able to access all of my files from either os. The best option I could think of was to create a new partition and shift everything to it that was important then reload [[COLOR=#0000ff][COLOR=#0000FF ! important][FONT=Arial][COLOR=#0000FF ! important][FONT=Arial]vista[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxnewbieguide.org/content/video-card-driver-problemi-think#") Which doesn't sound fun because it is a very messy and buggy oem copy. Anyhow What do you all think are my best options? Or where can I turn for support on such a matter?
 System Specs:
I7 920
X58 [[COLOR=#0000ff][COLOR=#0000FF ! important][FONT=Arial][COLOR=#0000FF ! important][FONT=Arial]chipset[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxnewbieguide.org/content/video-card-driver-problemi-think#")
9gb  Ram 1066 mhz
Visiontek ATI Radeon HD4850

---

### Post by BewilderedStranger on 2010-02-17
What the deuce is all of this epic failure weasel code that has weaseled any kind of legibility out of my post?  ](*,)      Basically when i try to run without installing it loads up but after the splash screen I get no video output to monitor leading me to believe the live cd doesn't include the drivers for my video card.  Being new to this os I don't know how to resolve this.  Also when I figure out how to deal with this how do I shift all of the stuff the media and just stored stuff on my windows partition to the new shared partition?  I hope you all can help me out.  I am really looking forward to trying out linux.  Hoping to regain the functionality we lost when everyone left dos in the dirt.  :cry:

---

### Post by RasterBurn on 2010-02-17
well, i could be a smart *** and ask for your lspci output for the info but even though you can use the command "ALT+CTRL+F#" to switch your screen from any of the cmd outputs to the GUI (though it may help to find out what is going on (i had a similar problem earlier today), my first tip would be to load the live cd and where it asks you for the boot options, select "check disk for errors" if the disk is fine then it would be a hardware related problem with the OS which brings me to the problem i encountered earlier today

I booted my pc as normal, it got to a black screen (as it usually seems to do) but wouldnt go any further.... i used ALT+CTRL+F1 to switch over to the first instance of the command line the system was having some troubles with the automatic disk cleanup prog it does every so often, i hit "ALT+CTRL+DEL" it stopped the problem and continued to boot into the GUI...

Other then that, if the disk has no errors and you have the login prompt then login as root and try the command: dpkg-reconfigure xserver-xorg

[FONT=Verdana]I dont remember exactly but this command will either bring up an interface to let you select the drivers or else otherwise try and redetect your video card.[/FONT]

---

### Post by BewilderedStranger on 2010-02-17
I may have missed what you were saying as this is 100% first time i've touched a linux os, but I never made it to any kind of login prompt after the black loading screen with the ubuntu symbol in the middle there was no output to my monitor at all (monitor goes blue and says no signal).  Same thing youd get if the computer were turned off.  Sorry if you explained it and I didn't get it.  haha  But could you elaborate a little more?  LSPCI may as well be greek.  Feels kinda strange asking someone to talk to me like a dummy about computers as I've been around them all my life but linux is all new to me.

---

### Post by Jackzor on 2010-02-17
First thing you need to do is boot to the Live CD and right after you press enter on the language you need to use the arrow keys to "check disc for errors" Or something along those lines. It will tell you if the disc was downloaded and burned with no errors. This may be the end of all your problems. If it comes back with errors then re-download the disk and re-burn it and try again. Just let us know what happens.

---

### Post by Jackzor on 2010-02-17
If you can try to get this done ASAP. I have class in 20 minutes. So I will be gone for two hours.

Well I'm off to class. I will check up on this after my next two classes.

---

### Post by RasterBurn on 2010-02-17
thank you jackzor for the quick explination on the check disk while i was asleep, if there is no errors, during bootup of the quick cd do you see a flash of giberish text before the screen goes black?

---

### Post by Jackzor on 2010-02-17
did you check the disc for errors?

Should be the selection that I have highlighted in the screenshot.

"Check disc for defects"

---

### Post by BewilderedStranger on 2010-02-17
Yes I checked for errors it says it good.  I did figure out that if I hit ctrl + alt + f# I can get into a terminal.  But I tried typing in that cmd you gave me and got no where.the dpkg - reconfigure xserver-xorg.  Or @ least I don't think it got me anywhere.  By the way guys I really appreciate your help.  I'm really @ a loss here without some support.  I was trying to get some pictures with my camera phone to post for you but apparently my bluetooth capabilities on my phone decided they would just drop a deuce on my face and quit working.  Go figure right.

---

### Post by golusweet on 2010-02-17
What video card do you have?

---

### Post by BewilderedStranger on 2010-02-17
Yeah after the black screen with the whitish ubuntu loading symbol i get a bunch of karmic kaola I/O buffer error business then i lose the video output.  I have a...I think its a visiontek ATI Radeon HD 4850 i know its a 4850 just not 100% on the maker.  It brings me to som kind of terminal after it loses signal if i hit ctrl + Alt + f1 and a different one if i hit f2 instead.  seems like a little piece of it is off the screen though and its kinda difficult to pick up what its saying.

---

### Post by BewilderedStranger on 2010-02-17
Guess I lost ya?

---

### Post by RasterBurn on 2010-02-17
the command i gave you to type is an admin command, from the sounds of it you will need to put the word "sudo" in front of it and it should allow you to use that command, keep in mind "sudo" is for doing admin related tasks from a normal user account in a terminal, to log in completly as admin from a normal user account use "sudo -s"

---

### Post by BewilderedStranger on 2010-02-17
So I need to go to the point where i lose the signal and press ctrl alt f2 and type sudo -s <dpkg - reconfigure xserver-xorg>  just like that?  Also what is the difference between pressing ctrl alt f1 vs pressing ctrl alt f2 they seem to give me different terminals.  And is that exactly character for character what I need to punch in? it said something about enclosing the cmd in the <> but i don't even know which part is actually the command.  haha i'm gonna need a book to get all this stuff figured out. Is there a space before and after the hyphen between dpkg and reconfigure?

---

### Post by BewilderedStranger on 2010-02-17
Also am I gonna have to go through all this again when I decide to actually install the os? will it be pretty much the same or a whole different ballgame?

---

### Post by BewilderedStranger on 2010-02-17
](*,)](*,)](*,)](*,)Okay here's the list of stuff I tried:

sudo dpkg-reconfigure xserver-xorg
sudo -s dpkg-reconfigure xserver-xorg
sudo <dpkg-reconfigure xserver-xorg>
"sudo... ahh heck with it you get the picture I tried everything I could think of.
then I just punched in sudo -s... or maybe just -s which did something then tried it all again.  Any idea where I'm blowing it?

---

### Post by RasterBurn on 2010-02-17
well, the first part being the individual cmd prompts, i believe there is about 5 of them in total (F1 - F5) the rest being reserved for GUIs, i could be wrong with that, but there is pretty much nothing different about each one (or atleast there isnt supposed to be any difference as for the command it would be as follows, character for character

"sudo dpkg-reconfigure xserver-xorg"

exactly as it shows with no quotation marks :) right now i am using UBUNTU 8.10 64bit with dual ATI Sapphire HD 3870 vid cards (1280x720 res + audio via HDMI) with absolutely no problems, the problem you are having could be simply a lack of video drivers in that version of UBUNTU, you could try downloading a previous version such as the one i have, or maybe 9.04 (i think you said you have version 9.10) if you can get a previous version to work properly with your setup you can install that, update it fully and then try upgrading to the newest release before transfering your files over to the new partition :)

---

### Post by BewilderedStranger on 2010-02-18
alright I'll try a different version that command didn't do anything for me.

---

### Post by RasterBurn on 2010-02-21
if the problem still persists, you could try turning off your screen and then turning it back on to see if that fixes it (I have just upgrade from 8.10 to 9.04 and encountered a similar problem then got irritated and reformated to 9.10 and still the problem) the suggested fix is more of a work around to the problem but so far for me, verson 8.10 works the best GUI wise

---

### Post by BewilderedStranger on 2010-11-28
Okay i gave up on it all together for a long time but now i'm trying again and i still have the same results. well... almost. now i can't even get to the command prompt in version 10.10. i'm wondering if it could be my tv that i use for the moniter it seems like it was tricky to get it working right with windows when i first got it. its a polaroid tlx-04240b running on an ati radeon 4850 hd. but i'm lost if anyone can help out it would be awesome.

---

