---
title: "Trying to set up dual monitors"
date: 2010-05-28
forum: General Help
---

### Post by geo909 on 2010-05-28
Hello all,

I have a Dell inspiron 1525 laptop with a 1280x800 display and 
an external 1280x1024 monitor. I'm using 9.04 with openbox.

I've done a loooot of online reading about how to get a dual
monitor setup using xrandr, and I really don't know what I'm 
missing here. Any advice that will get me out of this 
frustration will be so appreciated..

So here's the deal: I want to have my external monitor on the 
left of the laptop's display, and of course I want each of 
them to display different parts of the desktop.

First I set up the right resolution to each one of them (I do 
it using lxrandr). Typing xrandr -q in a terminal, I get the 
following:
```

jorge@flamingo:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1280
VGA connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0     60.0* 
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        75.0     72.8     59.9  
   720x400        70.1  
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TMDS-1 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)

```

My xorg.conf looks like this:
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Depth 16
		Modes "1280x1024" "1280x800"
		**Virtual 2560 1024**
	EndSubSection
EndSection

```

Although I have my virtual desktop line as you can see above, I get the following error when I try to adjust my dual monitors:

```

jorge@flamingo:~$xrandr --output VGA --mode 1280x1024 --left-of LVDS
xrandr: screen cannot be larger than 1280x1280 (desired size 2560x1024)

```

```
jorge@flamingo:~$ xrandr --output LVDS --mode 1280x800 --right-of VGA
xrandr: screen cannot be larger than 1280x1280 (desired size 2560x1024)

```

Could somebody please tell me what I am doing wrong here? I would be really grateful. Thanks a lot in advance for your time..

---

### Post by dino99 on 2010-05-28
which card is used ?

---

### Post by geo909 on 2010-05-28
> **dino99 said:**
> which card is used ?

Hi,

it's an *Intel Graphics Media Accelerator X3100*

---

### Post by dino99 on 2010-05-28
> **geo909 said:**
> Hi,

it's an *Intel Graphics Media Accelerator X3100*

[http://ubuntuforums.org/showthread.php?t=884203](http://ubuntuforums.org/showthread.php?t=884203)

[http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_X3100](http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_X3100)

[http://pr.zoinks.org/home/technology/tech-wiki/howto-ubuntu-dual-screen-intel-gma-x3100](http://pr.zoinks.org/home/technology/tech-wiki/howto-ubuntu-dual-screen-intel-gma-x3100)

---

### Post by dustinmarlowe56 on 2010-05-28
I have a dell inspiron 1501 with a amd turion 64 x2 processor. I am running dual monitors, primary one on my laptop, and a portrait orientated 19 inch dell monitor on my right for reading. I got them set up well just by using the set-up box located under system > preferences > monitors.


I am using 64 bit Ubuntu 10.04 LTS

---

### Post by marcottebj on 2010-05-28
That's built into Ubuntu 10.04, but not 9.04 (which he's using)

---

### Post by geo909 on 2010-05-28
> **dustinmarlowe56 said:**
> I have a dell inspiron 1501 with a amd turion 64 x2 processor. I am running dual monitors, primary one on my laptop, and a portrait orientated 19 inch dell monitor on my right for reading. I got them set up well just by using the set-up box located under system > preferences > monitors.


I am using 64 bit Ubuntu 10.04 LTS

Hi,

I guess I'm paying the price of minimalism here. I don't have gnome so I can't use this menu.. 
Could you please tell me if the set-up box you're mentioning is called "grandr"? You should be 
able to find out easily, there should be some "about" button or "help->about" menu item..

@dino99 I've already checked the first two pages, and I'm doing *exactly* what is advised 
in the third one. I still don't understand what is the difference to what I'm doing.. According 
to the error message, it seems that I haven't set the virtual display resolution correctly, but 
I do have this line in xorg..

Any ideas?

EDIT: I saw marcottebj's reply after I wrote mine

---

### Post by dustinmarlowe56 on 2010-05-28
its just monitor-preferences as far as i can see

[IMG]http://ubuntuforums.org/picture.php?albumid=1867&pictureid=6257[/IMG]

---

### Post by dougalkerr on 2010-05-28
I was having a similar problem but, using the GUI program grandr in 10.04 and even in Crunchbang 9.04.
I couldn't get the monitor set-up quite right.
I installed Ultimate Edition last night and set-up my dual monitors about 20 minutes ago and with a little moving around on the simple interface program I now have my monitors working exactly how I want - brilliant.
Maybe you don't want to change systems though - oh well, good luck, I am sure help is just around the corner.

---

### Post by geo909 on 2010-05-28
I see.. Yeah, I used grandr too and it wouldn't let me drag
my monitor left from the display or anywhere else. So, the
simple interface dialog you're mentioning is the same as the
one dustinmarlowe56 used, I guess?

Though I really don't understand why my way with xrand 
doesn't work and why I get this error message.. I'm 
following exactly what I found in a dozen different 
pages..

---

### Post by geo909 on 2010-05-28
Bump..

Any ideas?

---

### Post by dougalkerr on 2010-05-29
I'm not sure why you are having the problems you are having with what you have been doing.
I am not technically minded in Linux. A lot of my success has been pure luck and help from the forums people. Persevere and you will succeed.
I have had similar problems when trying to install the odd program from a web page somewhere and the text just wouldn't work.
I copy and paste and what do you know... it works.
I think there is some small part of the text format/syntax that gets missed if simply retyping instructions so, nowadays I try to copy and paste lines as much as possible.

Going back to grandr - I thought one of the monitors in the little program window was not going to move but, I moved the other one out of the way and then I could move it.
Go back to the program and try every silly little thing that comes to mind no matter how stupid it seems, you never know. Good Luck!!!

---

### Post by geo909 on 2010-05-30
> **dougalkerr said:**
> I'm not sure why you are having the problems you are having with what you have been doing.
I am not technically minded in Linux. A lot of my success has been pure luck and help from the forums people. Persevere and you will succeed.
I have had similar problems when trying to install the odd program from a web page somewhere and the text just wouldn't work.
I copy and paste and what do you know... it works.
I think there is some small part of the text format/syntax that gets missed if simply retyping instructions so, nowadays I try to copy and paste lines as much as possible.

Going back to grandr - I thought one of the monitors in the little program window was not going to move but, I moved the other one out of the way and then I could move it.
Go back to the program and try every silly little thing that comes to mind no matter how stupid it seems, you never know. Good Luck!!!

Yeah, I know, I've tried silly things but it's kind of disappointing.. Maybe an upgrade will do the job but I'm not sure If I have the time for it now.. Oh well, on the positive side, maybe I found a bug! :)

---

