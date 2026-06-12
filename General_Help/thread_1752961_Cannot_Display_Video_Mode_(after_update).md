---
title: "Cannot Display Video Mode (after update)"
date: 2011-05-08
forum: General Help
---

### Post by adambond on 2011-05-08
Hello all, I apologize if this is in the wrong section. 

I am running a dual boot system. I have XP on one HD and Ubuntu 10.04 on  the other. No problems. I boot back and forth all the time. Then came  along Natty. :sad:   Now I tried to boot over, and I get "Cannot display this video mode".   I have it set up that when I restart, if im away from the computer,  Ubuntu starts by default. So it eventually starts in ubuntu. But the  screen where I used to be able to choose which operating system to boot  into is now replaced with "Cannot display this video mode".  

I am not wireless, and nothing has changed as far as hard wear. The  monitor is some old Dell that worked perfectly fine with 10.04. 
I tried changing my resolution and settings to every different one, and restart, and still no dice. 

_To sum it up, after my update to Natty, when I reboot, my OS  selection screen is no longer visible. Its now replaced by "Cannot  display this video mode". _

So now it seems, what ever setting this screen is running on, XP dont like it..... because of Natty? 

Any help would tickle me pink, cause I gotta get some work done in XP,  so right now im screwed. My CRT is currently sitting outside in the  rain. :sad: Or I would try it.

---

### Post by parajulik on 2011-05-08
I think I am having the [same problem]("http://ubuntuforums.org/showthread.php?t=1752969") too. You could boot into XP by pressing down a lot of times when your computer starts and press enter.

---

### Post by adambond on 2011-05-08
lol. I actually considered that. But im afraid xp wont display (even if I happen to blindly select it)?  

If I can be sure I can get into windows and it wont be a blank screen, I will give it a go.

---

### Post by adambond on 2011-05-09
Is anyone else having this exact problem? Is it Nvidia related? 

If I acquire an old CRT monitor, can I fix this problem? If so, how would I do that?

---

### Post by adambond on 2011-05-09
Im guess a grub problem? Is there a way to determine what grub I need to load the operating system select screen during post?

---

### Post by Blasphemist on 2011-05-09
The current kernel uses kernel mode settings for video where earlier versions didn't. I can't fully explain that but I can point you in the right direction to fix this. It's not a grub problem but is related to grub.

You first need to know what your gpu you have. Do you know that already? Is it Nvidia since you mentioned that? If it is nvidia, you likely now have the nouveau drivers and need to install the proprietary nvidia drivers. You'll likely need to use kernel mode settings to boot enough to do that.

See this thread for more information on what to do and how. Please do post back questions and results.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by adambond on 2011-05-09
Thank yuh buddy. Yup. Nvidia. I will look into it after work. Thanks again. :)

---

### Post by adambond on 2011-05-10
Holy cow! Thats scary as hell! I understand the problem I think. And that sounds exactly like it. 
How do I install these 'proprietary nvidia drivers'? 

 Im assuming GPU means Graphics PRocessing Unit?  I think mine is Nvidia. 

Do I type this code into the terminal, or into bios? 
acpi_osi=

---

### Post by Blasphemist on 2011-05-10
So lets backup a minute. Let me know if this is all a correct understanding. Ubuntu runs fine when it comes up? You can't see grub so you haven't proven whether or not windows works?

I think windows would still be working fine if you were able to boot to it. I wouldn't be installing drivers if Ubuntu is working. Don't get ahead of yourself with the acpi-osi=. The first part of the post where you see that is not saying start right there. It is describing the mode setting options.

This instruction is where you should start. It will allow you to try options temporarily to see what works.
> How to temporarily set kernel boot options on an installed OS (not wubi)

To set kernel boot options, you must edit your grub configuration. You can do this temporarily for a single boot by entering the grub menu. If you do not get to see the grub boot menu after the bios automatically, you may have to press SHIFT key after the bios logo to get in to grub:



Select the default ubuntu kernel (usually the top one), and rather than pressing enter, press E to edit.

Press DOWN ARROW until you get to the line that starts with

Code:
linux /boot
and press END keys to position your cursor at the end of the that line usually ending with “quiet splash”. 

Now you can type in additional kernel options like nomodeset (please dont make the same typing error I made for this screenshot  ):



press control+X to boot the modified grub entry.

Important: setting boot options this way only applies to a single boot. If you reboot the machine, those settings will be lost, unless you make them permanent (see below)

I recommend that you start with trying the nomodeset option. If that doesn't work, I'd try acpi_osi="Linux" next. Once you find an option that works, you can go to his next instructions to make the change permanent.
> How to permanently set kernel boot options on an installed OS (not wubi)

To permanently change the default kernel boot options, press ALT+F2 or open a terminal from system > accessories > terminal. Type in the following command:

Code:
gksudo gedit /etc/default/grub
a text editor will open with the grub configuration file. Near the top of that file you will see something very similar to this:
Code:
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
add your custom boot options to the GRUB_CMDLINE_LINUX_DEFAULT line, so for instance:

Code:
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
GRUB_CMDLINE_LINUX=""
Save the file and exit gedit. If you have to add kernel options that contain quotation marks, add them as such:

Code:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi=\"Linux\""
Now in the terminal, run the following command to update your grub configuration with the new default settings:
Code:
sudo update-grub
Thats all. 


---

### Post by adambond on 2011-05-11
Alrighty. Here is a video of what is happening (or not happening rather). [http://www.youtube.com/watch?v=Ds_ZJT5R5EY](http://www.youtube.com/watch?v=Ds_ZJT5R5EY)  
My camera focus is fubar, but I think you will get the jist. The white text on the screen all by itself is the "cannot display video mode". 

I agree with you on trying the nomodeset first. My questions are, what is the 'grub menu', what is the bios logo? 

I ask because I restarted computer, and hit shift key several times at different points, and no response. Still booted up Ubuntu. I also noticed im in 'safe mode'. Since this computer was built (about a year) ive never put it in safe mode. 

I will give it another shot. But its tough not knowing all this terminology.
Thanks again for taking the time to help out. 
If you are a die hard Natty fan, we might as well get this figured out to help future folks. Cause from reading around, alot of people are getting effed in the a with this Natty.
Why do people have to fix what aint broken? Isnt the spirit of linux to NOT be like the corporate wart hogs that constantly shove new (barely functional) stuff down our throats?

---

### Post by adambond on 2011-05-12
Ok. I cannot get into the Grub. After the bios screen, I have pressed, and held down the shift key. And no response. The boot up proceeds as normal. Ubuntu loads. 

I think your method will work.... if I can get into the grub. :(

---

### Post by Blasphemist on 2011-05-12
I do wish I could read the screen in your video prior to the cannot display this video mode message. The video is a good try though. Can you describe what the screen says before the cannot display message? Usually BIOS just displays very little, how to get into it, and then passes the boot process to the hard drive. Just as that hand off is happening is when to press the space bar to get into the grub menu and kernel mode settings. 

At the start of the restart in the video, were you accessing something? I think you said you were exiting it but I couldn't understand for sure. On my computer, a toshiba, it gives me a prompt where I can access bios or a boot menu. Were you in a boot menu or bios? If you haven't been in bios, try going into it. You should get a simple graphic screen. Look for anything related to operating systems or video. Usually navigation instruction is shown at the bottom of the screen and menu's at the top. If you see anything that lets you tell the system about the operating system, look for a Linux or Unix option. If you see a video option look for options more like the resolution you need.

Don't give up on getting into the grub menu via the space bar but I'm just hoping for a way to attack this from a bios change. After all what we are trying to do is get the operating system to understand what it is getting from bios better, or at least use what it gets appropriately. The time for the space bar is before that cannot display message. Please do try that some more. If you keep getting the same results, try to type in here the text I couldn't read in the video.

---

### Post by adambond on 2011-05-12
Waaaait a minute. ..... I been pressing the shift key. And you say its the spacebar I need to press....? lol  Alright. I will give that a go tonight. 

At the beginning of the vid, i went to top right to access 'restart'. Thats all. 
At :49 i press f1 ' to continue'. Other options are f9 to select booting device. And DEL to enter setup. 

   When bios is up, it does give me the f9 option, which lets me select booting device. I go there and it says 'removable, hard drive, cd rom'. Those are the options in that order. I dont figure thats the path to the grub. 

I will go into bios menu also and look around. Pretty sure I already have, and didnt find anything I thought would relate to the problem. But worth another look. Thanks again. I will get back tonight. :)

---

### Post by Blasphemist on 2011-05-12
OK, I'm an idiot. I had read the information on making this change but didn't understand at all it seems. First, I was having a brain cramp. I should have said shift and not space bar. But, you are getting the cannot display message when it is trying to display the grub menu already, now that I finally understand. You can get into Ubuntu and the make the change in the method described for permanent changes. See this from the other thread.

> **How to permanently set kernel boot options on an installed OS **(not wubi)

To permanently change the default kernel boot options, press ALT+F2 or open a terminal from system > accessories > terminal. Type in the following command:

Code:
```
gksudo gedit /etc/default/grub
```
a text editor will open with the grub configuration file. Near the top of that file you will see something very similar to this:
Code:
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```
add your custom boot options to the GRUB_CMDLINE_LINUX_DEFAULT line, so for instance:

Code:
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
GRUB_CMDLINE_LINUX=""
```
Save the file and exit gedit. If you have to add kernel options that contain quotation marks, add them as such:

Code:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_osi=\"Linux\""
```
Now in the terminal, run the following command to update your grub configuration with the new default settings:
Code:
```
sudo update-grub
```


I think the nomodeset change will work for you. Here is it's description again.
> nomodeset
The newest kernels have moved the video mode setting into the kernel. So all the programming of the hardware specific clock rates and registers on the video card happen in the kernel rather than in the X driver when the X server starts.. This makes it possible to have high resolution nice looking splash (boot) screens and flicker free transitions from boot splash to login screen. Unfortunately, on some cards this doesnt work properly and you end up with a black screen. Adding the nomodeset parameter instructs the kernel to not load video drivers and use BIOS modes instead until X is loaded. 

Should that not work for some reason, you'll notice when editing the grub file that you can uncomment the following line to set a resolution.
[HTML]GRUB_GFXMODE=640x480[/HTML]
I believe the grub menu is trying to come up at the same resolution you are using for your monitor in natty. It is giving you a message that it can't display grub at that resolution but I bet it can at 640x480.
Do be sure to remember the update of grub
```
sudo update-grub
```

---

### Post by adambond on 2011-05-12
Alrighty. I got into grub. Edited the 'quit splash' and made it now 'quit splash nomodeset'. 
I saved it. Restarted, and no change. 
I reopened grub to confirm that I saved the change, and it is still changed.

---

### Post by adambond on 2011-05-13
So now im gonna look at the resolution as you suggest. It is already set at 640x in grub. 
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

So I think I will try '1024x768'. 

Just for fun. I opened up my laptop with the same XP on it and its running 1024x.

---

### Post by adambond on 2011-05-13
Ok. Heres the things ive tried, with no change in the problem. 

First: [FONT=monospace]I changed 'quiet splash' to "quiet splash nomodeset"

2nd: I changed [/FONT]640x480 to '1024x768'.

So far, it has had no affect. 

I did notice some other grub commands that look interesting.  Like, 
(# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo')

So is it saying that if I use the command (dont know where to enter it) 'vbeinfo' that it will show me the modes which my g card will support? 

Also, the grub file mentions 'uncomment'. How does one 'uncomment' in the grub? 

Thanks for the help so far. Im excited that im actually learning more about linux (atleast). 

Im not gonna touch anything else for now. Except probably try some other resolutions just for fun. If you dont hear from me, ..... I probably shot my computer.

---

### Post by Blasphemist on 2011-05-13
The # sign needs removed for your changes on that line to take effect as it disables the line. Try that since your changes to that line haven't been in affect. I'd try the 640x480 first. I'll look more into vbeinfo.

---

### Post by Blasphemist on 2011-05-13
From the Grub 2 documentation. Look at what I have highlighted in red and do that starting with your desired resolution and backing down as it shows. This will tell us what is the highest that works.
> #GRUB_GFXMODE=640x480
You can remove the # symbol to make this line active. The entry sets the resolution of the graphical menu (the menu text size). It provides resolutions supported by the user's graphics card (e.g. 640x480, 800x600, 1280x1024, etc). The setting applies only to the boot menu display, not the resolution of the operating system that boots.
Tip: Setting the same resolution in GRUB 2 and the operating system will decrease boot times slightly.
Although not required, the user can also specify the color bitdepth by appending it to the resolution setting. An example would be 1280x1024x24 or 640x480x32.
[COLOR="Red"]The user can also add multiple resolutions. If GRUB 2 cannot use the first entry, it will try the next setting. Settings are separated by a comma. Example: 1280x1024x16,800x600x24,640x480.[/COLOR]
If using a splash image, make sure the resolution setting and the splash image size are compatible.
If using an entry that produces a "not found" message when running update-grub, try adding or changing the color bitdepth.
Resolutions available to GRUB 2 can be displayed by typing vbeinfo in the GRUB 2 command line. The command line is accessed by typing "c" when the main GRUB 2 menu screen is displayed.
If this line is commented (#) or the resolution is unavailable GRUB 2 uses the default setting determined by /etc/grub.d/00_header.
For a guide to changing resolutions when using a splash image see the Splash Images and Theming section.

---

### Post by adambond on 2011-05-13
In all the lines I made changes to, there is no # sign. There is 
#GRUB_HIDDEN_TIMEOUT=0 Area you saying to remove that #? 



[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html)

Heres a link I found on vbeinfo.

---

### Post by Blasphemist on 2011-05-13
yes, remove the #

---

### Post by adambond on 2011-05-13
We have success!  Heres what I did (well... you did really). 

I went to Applications, Terminal, and typed in 

gksudo gedit /etc/default/grub
That opened the grub editor, and I first changed [FONT=monospace]"quiet splash" to "quiet splash nomodeset"

This had no effect. So I left it as is throughout the later changes. 
[/FONT]Then I went to line #GRUB_GFXMODE=640x480  and simply deleted the # sign. 

I then saved the document, closed the grub editor. Then in the terminal I typed
sudo update-grub.. to save the grub changes. 

I restarted the computer, and the problem was solved. I could then see the GNU GRUB screen after Bios. The GNU GRUB screen is where I am able to select the different operating systems I have on my HD's. 
XP and Ubuntu in this case. 


So, to summarize. Im gonna guess, that deleting that # at the GRUB GFXMODE was the only thing I needed to do in the first place. Not the 'quiet splash nomodeset'. ??

I hope this helps someone. Many thanks to Blasphemist for hangin in there. :guitar:

---

### Post by Blasphemist on 2011-05-13
Glad to hear! I'll remember this solution. Yes, apparently nomodeset didn't change it. If you want to make that grub screen look a little better, you could try 800x600 by just changing that one line. I think you use 1024x768 in Ubuntu if I remember right and it tries to use that same thing in grub.

---

### Post by rksii on 2012-08-31
See, this is the kind of stuff that makes it nearly impossible to convince other people to try linux. If I install or upgrade windows it just works. If I plug in a different monitor with windows, it just works. But, I setup a brand new 12.04 Ubuntu box for my sister, send it to her and she plugs it into her monitor and she gets "cannot display video mode" and there is not even a command-line utility anymore to reconfigure X11? WTH?

---

