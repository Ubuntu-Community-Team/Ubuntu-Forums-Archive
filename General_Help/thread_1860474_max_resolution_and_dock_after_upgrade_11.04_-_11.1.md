---
title: "max resolution and dock after upgrade 11.04 - 11.10"
date: 2011-10-14
forum: General Help
---

### Post by DeadlyChicken on 2011-10-14
I was running 11.04 on my desktop and liked it well enough but just could not get past that it felt a little less ... refined than Windows ( I have been using ubuntu for a while on laptops but wanted to see how it looked on a desktop ).

Anyway I figured it out after the upgrade.  I decided to check the display properties ( I have dual 24 inch screens ) and found they were both running at 1680 x 1050, they should be at 1900 x 1200 .. aaah I thought that's why it seems so dated compared to windows.

however when I set the resolution higher I get an error

> The selected configuration for displays could not be applied

requested position/size for CRTC 147 is outside the allowed limit: position=(1920, 0), size=(1920, 1200), maximum=(3360, 1920)


Using the ATI control panel does not throw up the error but does not change the displays either.  it did allow me to set one of them to max, but that's just silly.

So why can Ubuntu not display this resolution, it seems as though in this day and age its not unusual to have dual screens of a high resolution.


The other issue I am having is that the unity dock no longer shows up, its still turned on if I check using compiz, but it just will not open when I move my mouse to the edge of the screen.  If I press the windows key it will show up so I know its loaded and which screen its on, but it just refuses to come out and play.

Video card is a gigabyte ATI 5770

dual dell 24 inch ultra sharp lcd ( an older model and a current one ).

anyway I would be more appreciative on the resolution issue as I have cairo dock installed, but I wold like to try out the new unity dock as it already looked better than the first one.

---

### Post by DeadlyChicken on 2011-10-14
err ..  i made it worse by trying to upgrade the ati drivers, now I can only get max resolution of 1920 x 1920.  so only one display will activate.  I have been messing with ubuntu since v 6.04 I think, and this is the first time that it doesn't "just work" which is a bit disappointing.  Anyone got any ideas

---

### Post by DeadlyChicken on 2011-10-16
OK,

So it was b0rked and I figured I would do a fresh install of 11.10.  Downloaded a disk, ran, and told it to remove and replace the current 11.10 install.

then it wouldnt boot, had the grub rescue prompt.  I needed to insert a windows 7 disk and fixmbr and fixboot to get the old grub loader working.  Then I had much fun getting the burg loader installed ( that grub loader is soooo ugly  ) 
got that going, finally I attempted to resolve the resolution issue.

I had to 
sudo gedit
then browse to then xorg.conf file ( which was all but empty ) and add in a virtual desktop size that would allow both screens to work. The etc/x11/xorg.conf now shows


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1920x1200"
		Virtual 3840 1200
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

All I added was the subsection.

Now this seemed to work I could select my second screen and get it working at full resolution using either the catalyst control center or the ubuntu display app.  

The only issue is that now when I boot up.  The second screen is scrambled., like it is trying to display an image but failing miserably.  

By simply going into catalyst control center, clicking on one of my screens and then clicking Apply, the second screen displays correctly.

anyone got any pointers.

As a side not I am a bit disappointed to have lost the nice blue theme I had on 11.04.  Why so few themes ?

---

### Post by DeadlyChicken on 2011-10-17
ok so fixed the scrambled screen by adding a startup command

xrandr --output DFP4 --auto --left-of DFP3

---

