---
title: "video acceleration/drivers?"
date: 2009-12-09
forum: General Help
---

### Post by osmorphyus on 2009-12-09
hi,

i have an ATI 9600SE 128MB video card.

i installed the pro. driver, and it says "no prop. drivers installed".

i want to know if ubuntu is taking full advantage of my video card, but unlike windows we dont have a way to see which hardware is installed (device manager) or which driver is running it.

how can i find out if my system is taking full advantage of my video card?  i have to shut off visual effects because it slows down so much with them on, leading me to think that the card is not fully being utilized.  

hoep someone can help.

-regards.

---

### Post by darkksyde. on 2009-12-09
Which ubuntu are you using?

---

### Post by osmorphyus on 2009-12-09
the newest release, 9.10

"You are using Ubuntu 9.10 - the Karmic Koala - released in October 2009 and supported until April 2011."
from "about ubuntu"


-regards

---

### Post by darkksyde. on 2009-12-09
Any version of *buntu since 9.04 has to use the open source ati driver which is pretty crappy. If you want to use the official driver you have to go back to 8.04 or 8.10.

---

### Post by osmorphyus on 2009-12-09
oh wow, thats lame.

is this going to be worked on eventually, that you know of?  that anybody knows of?

is there a list of old school cards that will work to their full potential on this current version?


man, was the 8.x version the "hardy heron" release?  because if it is, i had horrible video driver support back then...  i was stuck in an over-scanned 640 x 480 display mode.  imagine the horror.

-regards.

---

### Post by darkksyde. on 2009-12-09
> **osmorphyus said:**
> oh wow, thats lame.

is this going to be worked on eventually, that you know of?  that anybody knows of?

is there a list of old school cards that will work to their full potential on this current version?


man, was the 8.x version the "hardy heron" release?  because if it is, i had horrible video driver support back then...  i was stuck in an over-scanned 640 x 480 display mode.  imagine the horror.

-regards.


I dont have a card that old so im not sure. The open drivers are ok, they just need more work. Nvidia cards apparently work great, so maybe you should upgrade. Ati dont support that card on windows anymore anyway.

---

### Post by osmorphyus on 2009-12-09
thanks for the tip.  ive never been an ati guy myself, this is my old ladys box, her brother built it a few years ago now.

if the nvidia drivers work, ill just ebay an old-school PCI card then.  im sure i can find one for a couple bucks and have it before xmas.  damn, what a bummer tho.  i guess i understand why the cards driver wasnt developed, but i swore i had read that it worked for ubu.  i suppose they meant an older version of ubu!

theres no reason to invest any real amount of money into this box.  after the new year ill start building a new system, but that wont be until tax time, here.

-regards.

---

### Post by darkksyde. on 2009-12-09
You can probably get a pci gforce 5200 for about $5-10

---

### Post by tcchris on 2009-12-09
With that card , you will be using the opensource Radeon driver .
You can edit /etc/X11/xorg.conf to gain better performance . 
there is documentation on the web .
I have a 9600xt that works pretty well for what it is .

---

### Post by osmorphyus on 2009-12-09
> With that card , you will be using the opensource Radeon driver .
You can edit /etc/X11/xorg.conf to gain better performance . 
there is documentation on the web .
I have a 9600xt that works pretty well for what it is .

hmm, sounds very interesting.  thanks for the tip!  ill start googling around about this!  if you have any other info, id appreciate it!  :popcorn:

---

### Post by darkksyde. on 2009-12-09
> **tcchris said:**
> With that card , you will be using the opensource Radeon driver .
You can edit /etc/X11/xorg.conf to gain better performance . 
there is documentation on the web .
I have a 9600xt that works pretty well for what it is .

How do you gain performance?

---

### Post by 3rdalbum on 2009-12-09
The open-source driver continues to be developed (lots of people with Radeon 9200s) but they won't get the old driver to work with the new Xorg.

---

### Post by tcchris on 2009-12-09
Read "http://linux.die.net/man/4/radeon"
I don't know your card but agp defaults to one , so agp=8 or agp=4 , will increase performance if your card is 4 or 8 speed .
I attached my xorg.conf , part of which I got from looking at someone elses . hope it helps :

# Xorg configuration created by system-config-display

Section "ServerLayout"
	Identifier     "single head configuration"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"

# keyboard added by system-config-display
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105+inet"
	Option	    "XkbLayout" "us"
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "radeon"
        Option	    "AccelMethod" "XAA"
	Option	    "AGPMode" "8"
	Option	    "GARTSize" "64"
	Option	    "EnablePageFlip" "on"
	Option	    "ColorTiling" "on"
	Option	    "DPMS" "on"

EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

### Post by osmorphyus on 2009-12-09
hmm, check this out:

i found a site that had instructions on how to roll back xorg (or something) to an older version so that the ati drivers would work on a 9.04 installation of ubuntu.  after reading it thru, and seeing that he had some more recent updates, i decided it would be alright to try this out.

it wound up breaking my desktop.  my system now only boots into text mode, and i have no idea how to do anything in text-mode ubuntu.

my computer will not connect to the internet in this state, and i do not know how to configure the network adapter from there, either.  so now, i am oline from a Live CD 9.10.

i dont mind having to reinstall, but id really  rather not have to, especially if this problem can be fixed and i can learn how to fix it.  

i bookmarked the site i was using for a guide, but since i am booting from a live cd, i cannot access my bookmarks.  i cant remember what i googled to find it, either.  it was a nice looking page, with a black bkg and a colourful left-to-right image spanning the top of it.  the page was set with a fixed bkg, just incase anybody may know the site i am talkig about.


alright, so can someone help me to unbreak my system or should i just reinstall?  i dont have anything to lose on the disk, really, but again, id rather not have to if i dont haver to.  i have full access to my FS thru the Live CD.

note that the site had me uninstall all ATI drivers, so im kinda thinking that had something to do with breaking my desktop, but i dont know.  it also had me change all entries from "karmic" to "intrepid" in the sources file, but it did at the end revert back what was changed.


edit:
here is the site link i used: [http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

which came from here:  [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)


oooooh, ouch, look what i found:
> [i]
The instructions posted in this article do not work in Ubuntu Karmic, however I am working on getting a new tutorial for Karmic up some time next week.
 (Refer to the latest post on this site)[/i]


if anyone can at least help me fix my system, cool.

---

### Post by tcchris on 2009-12-09
Os , I hope you get your system fixed .
I am by no means an expert ,but normally you can hit escape when booting to enter grub menu ,then select the previous kernal version or the repair but it sounds like you may have removed the original version so you may be better to reinstall unless some one else knows more to do .
The open source drivers do fine for me , 3d and all .
I am not sure that the fgrlx will really be worth the effort you are going through . Perhaps focus more on tweaking the xorg.conf to suit your card .
Always be careful and backup xorg.conf before editing

---

### Post by osmorphyus on 2009-12-09
yeah, i just reinstalled ubu.

now, can you please tell me, by default, on a fresh ubu install with this card, i am using the open-source driver, correct?

if this is true, then you are suggesting that all i should have to do is tweak my xorg file, correct?

---

### Post by tcchris on 2009-12-09
yes , in terminal type lspci -v
then look for your vga card and under kernel modules it will say radeon 
for the open source radeon driver .
If you were using the ati I think it would say fgrlx
Check this page "http://manpages.ubuntu.com/manpages/karmic/man4/radeon.4.html" for info on settings in the xorg.conf .
Make sure you backup xorg first . That way if it won't restart you just restore xorg restart and you are back where you started .
Also , on a fresh install you may not even have /etc/X11/xorg.conf . You may have to create one .

---

### Post by osmorphyus on 2009-12-09
hmm, i dont seem to have a xorg.conf file?

i have browsed to etc/x11 and its not in there.

as well, here is the return of the data when i run lspci -v:

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AQ [Radeon 9600]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 5
    Memory at b0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at a800 [size=256]
    Memory at cfef0000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at cfec0000 [disabled] [size=128K]
    Capabilities: [58] AGP version 2.0
    Capabilities: [50] Power Management version 2
    Kernel modules: radeon, radeonfb

01:00.1 Display controller: ATI Technologies Inc RV350 AQ [Radeon 9600] (Secondary)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Memory at a0000000 (32-bit, prefetchable) [size=256M]
    Memory at cfee0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [50] Power Management version 2

---

### Post by tcchris on 2009-12-09
Os :
You have a card similar to mine , probably a little older .
You can try my xorg , which is posted earlier .
copy and paste it to a file called xorg.conf
copy that file to /etc/X11/xorg.conf
you have to have elevated priveleges to write to /etc so type in terminal
 " sudo cp xorg.conf /etc/X11/xorg.conf " 
sudo gives you permissions 
cp is copy 
if it doesn't help , just delete /etc/X11/xorg.conf 
if it wont boot just get to command line and type 
" sudo rm /etc/X11/xorg.conf "
this will delete the file so you can reboot back where you started .
It most likely will boot , just will it help is the question.
Also is your card agp and is it 8 speed ? set file accordingly

---

### Post by osmorphyus on 2009-12-10
tcc, good lookin out on the help man.  im not sure yet, but so far i think your xorg configuration may be improving my cards performance.

visual effects are on and so far much more smooth, youtube video is not chopping as much as it was before i setup this file.  just before i created this xorg file of yours, youtube was skipping visually like crazy, at all times, not just before needign a reboot.  so far, so good.  ill keep a close watch on everything overall and post any questions about it.

thanks again, man!  :popcorn:

---

