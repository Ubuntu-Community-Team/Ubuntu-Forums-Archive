---
title: "Ubuntu 9.10 Unable to save nvidia-settings like resolution or twinview"
date: 2009-11-10
forum: General Help
---

### Post by Enav on 2009-11-10
I have a GForce 9800 GTX
This was the problem and how to solve it

The problem
-------------------
1- After run: gksudo nvidia-settings
2- I setup some video parameters like resolution or activate twinview
3- After click on [Save to X configuration file] buttom the program show me this error:

Windows message: 
"Failed to parse existing X config file '/etc/X11/xorg.conf'!", 

Terminal output:   
VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
                 Undefined Device "(null)" referenced by Screen "Default Screen".

The Solution
-------------------
1- Run: cd /etc/X11 && sudo mv xorg.conf xorg.conf.backup && sudo nvidia-xconfig
2- Run: gksu nvidia-settings
3- Setup some video parameters like resolution or activate twinview 
4-  click on [Save to X configuration file] buttom
5- Enjoy :D

Details
-------------------
Apparently Ubuntu 9.10 has no longer Xconf file by default and we must create a new one for the nvidia program can write setting on it

Thanks to Billiard of #ubuntu channel support (Xchat)

---

### Post by Breetai on 2009-11-21
Sweet!  Not enough people say it so THANKS!!!  You rock!

---

### Post by synapse13 on 2009-11-22
Thanks for this!  I had some trouble with this also and this did the trick.

---

### Post by manoriax on 2009-11-22
Thanks.

---

### Post by jslowery on 2009-11-23
Thank you very much for posting this!

---

### Post by altered.ego on 2009-11-24
Unfortunately, it doesn't work for me. I still have to change the resolution every single time i log in. :mad:

---

### Post by silverwood99 on 2009-11-28
I still get the message:

Failed to parse existing X config file '/etc/X11/xorg.conf'!

and

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Configured Screen Device".

in a dialogue box with a rather cute warning triangle!! please help

Edit: nevermind :)

---

### Post by theverant on 2009-12-07
Big thanks!

---

### Post by ashwinrao on 2009-12-07
Hello everybody, I came across same issue. I am using Geforce 6100 on board display. Also, using AMD 64 processor. I have used the above all methods but it was unsuccessful. Any body guide me. I have to set resolution each time when I restart the machine.

---

### Post by vesaliuz on 2010-01-28
Works great for me, thx!!

---

### Post by scifisam on 2010-01-28
> **Enav said:**
> I have a GForce 9800 GTX
This was the problem and how to solve it

The problem
-------------------
1- After run: gksudo nvidia-settings
2- I setup some video parameters like resolution or activate twinview
3- After click on [Save to X configuration file] buttom the program show me this error:

Windows message: 
"Failed to parse existing X config file '/etc/X11/xorg.conf'!", 

Terminal output:   
VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
                 Undefined Device "(null)" referenced by Screen "Default Screen".

The Solution
-------------------
1- Run: cd /etc/X11 && sudo mv xorg.conf xorg.conf.backup && sudo nvidia-xconfig
2- Run: gksu nvidia-settings
3- Setup some video parameters like resolution or activate twinview 
4-  click on [Save to X configuration file] buttom
5- Enjoy :D

Details
-------------------
Apparently Ubuntu 9.10 has no longer Xconf file by default and we must create a new one for the nvidia program can write setting on it

Thanks to Billiard of #ubuntu channel support (Xchat)
Hi,
I tried your solution but must not have done something right because I got a message in the terminal that no such file/directory existed.Could you possibly be more specific as to the exact commands needed to create the folder to save the configuration in so that it does exist so that what you describe as the solution works?
Thanks Scifisam

---

### Post by scouser73 on 2010-01-28
Sam do you mean the creating of the xorg.conf file? If so, then please follow my instructions.

Paste these commands into Terminal to create a new Xorg.conf, that should now have created a new xconfig file.

The first step creates a backup of your currently working xorg.conf file.
**> sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak**

Step 2 runs the NVIDIA utility to generate a new xorg.conf file that the utility can actually read.
**> sudo nvidia-xconfig**

Step 3 runs the graphical NVIDIA setup tool as root, so you can actually save your changes.
**> sudo nvidia-settings**

If this does not work then after step 1, do **sudo rm /etc/X11/xorg.conf** to delete your current xorg.conf file. Then run **sudo nvidia-xconfig** and **sudo nvidia-settings**.

---

### Post by scifisam on 2010-01-28
> **scifisam said:**
> Hi,
I tried your solution but must not have done something right because I got a message in the terminal that no such file/directory existed.Could you possibly be more specific as to the exact commands needed to create the folder to save the configuration in so that it does exist so that what you describe as the solution works?
Thanks Scifisam
Ido appreciate your help but without knowing at all what I'm really doing such as creating a folder and files tha t do not exist and making them . Is that what the commandsa you recommend are doing?And if so I wonder about the exclamation points and quotes and such.Which are just literary punctuation and which do stuf ?I am such a pain in the well you know but I stlill want to know these things so that I know the "truth"
The absolute truth and won't pass on something I really don't understand.So If you could/would you edit the commands to show exactly what I should type in the terminal window?

---

### Post by nerdtron on 2010-01-29
> **Enav said:**
> I have a GForce 9800 GTX
This was the problem and how to solve it

The problem
-------------------
1- After run: gksudo nvidia-settings
2- I setup some video parameters like resolution or activate twinview
3- After click on [Save to X configuration file] buttom the program show me this error:

Windows message: 
"Failed to parse existing X config file '/etc/X11/xorg.conf'!", 

Terminal output:   
VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
                 Undefined Device "(null)" referenced by Screen "Default Screen".

The Solution
-------------------
1- Run: cd /etc/X11 && sudo mv xorg.conf xorg.conf.backup && sudo nvidia-xconfig
2- Run: gksu nvidia-settings
3- Setup some video parameters like resolution or activate twinview 
4-  click on [Save to X configuration file] buttom
5- Enjoy :D

Details
-------------------
Apparently Ubuntu 9.10 has no longer Xconf file by default and we must create a new one for the nvidia program can write setting on it

Thanks to Billiard of #ubuntu channel support (Xchat)


Great! Thanks a lot!:popcorn:

---

### Post by lobodks on 2010-01-30
For people that still having trouble with this fix call nautilus as root and then look for xorg.conf~ on /etc/X11/ delete this file and try again, it happened to me and was really frustrating.

---

### Post by c_senthilkumar on 2010-02-17
@Enav : Thanks for the info. Helped me solve the problem :)

---

### Post by Jonners59 on 2010-02-17
Sadly this did not work for my GeForce FX 5200...  As soon as Ubuntu gets going I losse the primary screen and everything ends up on the second.

Shame.

---

### Post by Jonners59 on 2010-02-19
This is still not working for me.

I followed a couple of other links and installed their suggested terminal inputs and managed to get the second screen working after a reboot.  However, it ONLY showed the same image.

Then I followed another bit of advise which lost the screen again.  Now after following these alterations I can not load or make changes....  The second screen just flashes at me.

Tried below again but get rejections - command not found

See latest screen shot[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

---

### Post by Enav on 2010-02-19
Guys calm down and do not use the terminal like a mad  ](*,)...

Try this:
----------
1- Login as root --->   run: sudo su
2- run: sudo nvidia-xconfig
3- run: gksu nvidia-settings

Tell me what happen after those codes or send me another screenshoot

---

### Post by Jackzor on 2010-02-19
gksudo nvidia-settings


Just use that command to open the nvidia stuff. That.. I thought was well known.

---

### Post by Jonners59 on 2010-02-19
> **Enav said:**
> Guys calm down and do not use the terminal like a mad  ](*,)...

Try this:
----------
1- Login as root --->   run: sudo su
2- run: sudo nvidia-xconfig
3- run: gksu nvidia-settings

Tell me what happen after those codes or send me another screenshoot

Sorry, but new to all this...  How do I login as root?

---

### Post by Jonners59 on 2010-02-19
> **Jackzor said:**
> gksudo nvidia-settings


Just use that command to open the nvidia stuff. That.. I thought was well known.

Not to most people, especially those new to Ubuntu and non techies.

That did nothing....  Came up with the same messages.

---

### Post by Jackzor on 2010-02-19
> **Jonners59 said:**
> This is still not working for me.

I followed a couple of other links and installed their suggested terminal inputs and managed to get the second screen working after a reboot.  However, it ONLY showed the same image.

Then I followed another bit of advise which lost the screen again.  Now after following these alterations I can not load or make changes....  The second screen just flashes at me.

Tried below again but get rejections - command not found

See latest screen shot[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

You don't have the driver installed?
You need the driver installed.

---

### Post by Jonners59 on 2010-02-19
> **Jackzor said:**
> You don't have the driver installed?
You need the driver installed.

I know, I have tried to reinstall several times.:sad:

The "Solution" that I followed in the other threads deleted the original driver and created a new.  That worked to a point in so much as I got the other screen up, but it only showed the same image and would not change.  So I followed the rest of the Thread and hence the screen went again.  Then i tried to reinstall the driver, but it would not let me, os I deleted the drivers and tried to reinstall, but again it will not let me - see the screen shots.  I also got this from the Download Manager:

187200 files and directories currently installed.) 
Unpacking nvidia-glx-173 (from .../nvidia-glx-173_173.14.20-0ubuntu5_i386.deb) ... 
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead. 
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-173' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-185' 
dpkg: error processing /var/cache/apt/archives/nvidia-glx-173_173.14.20-0ubuntu5_i386.deb (--unpack): 
 subprocess new pre-installation script returned error exit status 2 
Errors were encountered while processing: 
 /var/cache/apt/archives/nvidiglx-173_173.14.20-0ubuntu5_i386.deb

CAN YOU HELP???](*,)

---

### Post by Jonners59 on 2010-02-21
**Jackzor and **Enav
Someone told me last night to remove everything that was nvidia related.  So I went in to Synaptic Manager, searched on nvidia and then selected each item installed with "Mark for Complete Removal"

I the "Applied".  After the removal I did a reboot and I now have both screens back up and running.

Both, however show the same image - not very useful and the resolution (1280x1024) is not as good as it should be either.

Now to fix these items, before I do ANYTHING I would like your advise.  What should I download?  How should I configure it/them?

---

### Post by Enav on 2010-02-21
People need to understand that new realeases of ubuntu normally have bugs....   if this is to complicated for you guys  just Downlaod and install  Ubuntu 8 LTS... is almost the same stuff
Check this:
Download Ubuntu 8.04 LTS
Released in April 2008 and maintained until April 2011 - ideal  for large deployments

Good Luck mates

---

### Post by Jonners59 on 2010-02-21
?
It's not unique.  There are many articles with this problem...  I now have two screens up, just need to be shown how to get them working in Twin mode.

PS.  What is the command line to stop X Server?

Seems that stops installs of drivers from nVidia

---

### Post by Enav on 2010-02-21
download and install drivers from nVidia is a big mistake....  do it using the Synaptic Package Manager

---

### Post by Jackzor on 2010-02-22
> **Enav said:**
> download and install drivers from nVidia is a big mistake....  do it using the Synaptic Package Manager

I run the beta drivers from the website. It wasn't a mistake for me.

Now to the OP

What exact have you got now? Do have drivers now? If so, what version. Have you got the nvidia settings working or no? Whats your problem now and what do you want done?

---

### Post by Jackzor on 2010-02-22
The 185 driver is available from the Hardware Drivers program in Ubuntu. If you don't see it, then either your Nvidia card is a little too new or you need to Reload your package list.

If your card is so new that it requires the 190 driver, or you do absolutely need this new driver for some reason, there is a PPA (Personal Package Archive repository) containing the driver. Follow this link:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

After adding the PPA, you can install the "nvidia-graphics-drivers-190" package, or even the "nvidia-graphics-drivers-195" package if you like living on the bleeding edge.

The advantages of this are:

1. Your system will keep the Nvidia driver up-to-date
2. You won't need to keep reinstalling the driver every time there's a kernel update
3. It's much easier to install, and you don't need to turn off X to install it.

---

### Post by Jonners59 on 2010-02-22
> **Enav said:**
> download and install drivers from nVidia is a big mistake....  do it using the Synaptic Package Manager

I did this first time and tried several times.  The particular package will not install as it has errors - see below.

[INDENT]***187200 files and directories currently installed.) ***
*** Unpacking nvidia-glx-173 (from .../nvidia-glx-173_173.14.20-0ubuntu5_i386.deb) ... ***
*** dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead. ***
*** dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-173' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-185' ***
*** dpkg: error processing /var/cache/apt/archives/nvidia-glx-173_173.14.20-0ubuntu5_i386.deb (--unpack): ***
***  subprocess new pre-installation script returned error exit status 2 ***
*** Errors were encountered while processing: ***
***  /var/cache/apt/archives/nvidiglx-173_173.14.20-0ubuntu5_i386.deb***
[/INDENT]
Mine is NOT a new card, it is the FX 5200 which uses the 173 driver.

Jaczor
In answer to your questions:

What exact have you got now?   I have cleaned out everything and re-installed the X Server, but have left the PC empty to follow instructions.  Did try to install drivers but get the errors as above.  And when I try the nVidia direct it will not load because another error message comes up saying the X-Server is running and needs to be turned off.  I do not know how too.

Do have drivers now? No, see above statement

If so, what version. I have downloaded waiting to be installed, the 173, which is correct - interesting I am running an AMD 64-bit, but that is always rejected as not my OS, so I use the 32-bit - very odd!!!!

Have you got the nvidia settings working or no?  No, see above, and previous comments below.

Whats your problem now and what do you want done?  I need to get drivers installed, and set up for twinscreen.  I have both working, but they use the defaultdrivers and both screens show the same image


I'll take a look at both of your suggestions and get back.

---

### Post by Jackzor on 2010-02-22
you should be able to install the old drivers from the ppa as well.

---

### Post by Jonners59 on 2010-02-22
I am on the machine now, and just about to start looking at all the ideas you have sent...  Very pleased you are about!!!!!!

---

### Post by Jonners59 on 2010-02-22
> **Jackzor said:**
> you should be able to install the old drivers from the ppa as well.
The drivers are listed, as expected.  I marked for install in Package Manager (I also added the PPA to the list of sources before hand), however, on install it failed again.  Same message:
See enclosed screen shot.

I then tried to go into the X Server again.  It did not show the full version and had an error message.  I followed the instructions.  See second screen shot of X Server, error and the Terminal entries messages.

---

### Post by Jonners59 on 2010-02-22
I copied the synaptic entries (bar 173 drivers) for this PC against a laptop I have using nVidia that works, and then also did your advise too.
 
 However, it still failed to load.  It's the driver and I am certain it is faulty.  It fails during install and the terminal states that the install failed because of using old processes something to do with "print-architecture" v print-installation-architecture"
 
 Enclosed screen shots show:
 Synaptics post install still showing the driver outstanding
 The install terminal comments that I get EVERY time I try and install this driver.

Bar the Ubuntu community fixing it - assuming I am correct, the only alternative is to load the nVidia version, but for this I need to know how to turn X Server off
 
 Any ideas, please.

---

### Post by Jonners59 on 2010-02-22
Any help, PLEASE?

---

### Post by RT236 on 2010-04-19
Thank you, Thank you, Thank you!!!  This worked extremely well.  I was really getting into circles trying to get the new config. saved.

---

### Post by MidiJake on 2010-04-20
Worked great, thank you. :)

---

### Post by john.quinn on 2010-05-12
> **silverwood99 said:**
> I still get the message:

Failed to parse existing X config file '/etc/X11/xorg.conf'!

and

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Configured Screen Device".

in a dialogue box with a rather cute warning triangle!! please help

Edit: nevermind :)
Why did you say "Never mind"? This is the exact error I'm getting. How did you fix it?
Thanks.

---

### Post by gsparky2004 on 2010-10-31
Enav started this thread, what, two years ago?  Still works today.  I just installed 10.10 Mav Meerkat 64-bit on a Dell XPS 8100 with a nVidia GeForce GT 220.  Enav's how-to worked perfectly for me.

Two words: Suh-WEEET!

---

