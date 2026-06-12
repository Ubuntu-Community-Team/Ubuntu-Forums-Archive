---
title: "Two problems I have with ubuntu 11.10"
date: 2011-10-18
forum: General Help
---

### Post by qunungnauraq on 2011-10-18
The two Problems I am having with ubuntu 11.10 64 bit are:
1. Alien arena 7.51 is not working at all in either unity or gnome shell. I am using a Thinkpad T510 with nvidia NVS 3100 discrete  graphics. When I press the icon nothing happens. Alien arena worked in ubuntu 11.04 64 bit on the same laptop. 
2. When I enable initiate window picker for all windows in scale-bindings using mouse button 2 it disables reveal mode for the unity dash launcher and I have to press the ubuntu button to access it.
Solutions anyone?

---

### Post by ECPCLINUX on 2011-10-19
Hi, I'm having the same issue with Alien Arena on 11.10.  I would love to find an answer, so far my Google searches have not produced any help.  :(  As a matter of fact I ended up here because I've been looking for this answer for the pass 3 days.  Hopefully someone knows a fix.  My system is an AMD 235e, integrated Nvidia 8200.

---

### Post by alexvy13 on 2011-10-24
It wont work for me either, and its outdated too.  It isn't 7.52
and i downloaded the tarball from the homesite but it seems kind of complicated and like there tons of dependencies needed before even using the tarball.
Can anyone just make a simple deb for it?

---

### Post by _XeNoS_ on 2011-11-01
The list of dependencies for building the tar ball can be found _[here]("http://corent.proboards.com/index.cgi?board=aatech&action=display&thread=4422")_ 

Go to a terminal, type crx and post the output from the terminal.[URL="http://corent.proboards.com/index.cgi?board=aatech&action=display&thread=4422%22"]
[/URL]

---

### Post by ECPCLINUX on 2011-11-07
H, thank you for your help.  Here are the result for crx:

No command 'crx' found, did you mean:
 Command 'cyrx' from package 'keyboards-rg' (universe)
 Command 'crm' from package 'crm114' (universe)
 Command 'crm' from package 'pacemaker' (main)
 Command 'rx' from package 'lrzsz' (universe)
 Command 'cr' from package 'seesat5' (universe)
crx: command not found

Did I do that correctly?

I also tried installing 7.52 from here, after removing 7.51:

[http://askubuntu.com/questions/72637/how-to-install-alien-arena-7-52](http://askubuntu.com/questions/72637/how-to-install-alien-arena-7-52)

It installed but nothing happened.

I removed 7.52 and reinstalled 7.51, still the same results. :(
I double checked Alien Arena in the Ubuntu Software Center and it does show as installed.

---

### Post by _XeNoS_ on 2011-11-08
Try a search to see if crx exists on your system:

cmd: sudo find / -name *crx*

If it exists go to the directory where it is found and type ./crx

Are you installing via software center or via terminal, doing it in terminal will give us a better idea of what is going wrong on installation.

edit: cmd: sudo apt-get install alien-arena

---

### Post by ECPCLINUX on 2011-11-09
Hi, once more thank you for your help. I turned on my computer a while ago. Before I could run the command you suggested I noticed I had an update.  Looked at what was being updated and I notice AlienArena among the updates. I proceeded to update my Desktop and rebooted as needed.  Once I booted up I decided to try AlienArena once more before I would run the command. Low and behold AlienArena started up and it's working well.  Seems that the update fixed it! :)  Thank you for your help.

---

### Post by _XeNoS_ on 2011-11-10
I actually did nothing, obviously whoever maintains the alien-arena packages has fixed the issue, awesome! See you in the arena :-)

---

### Post by Perfect Storm on 2011-11-10
Easiest way:  [http://www.playdeb.net/updates/Ubuntu/11.10/](http://www.playdeb.net/updates/Ubuntu/11.10/)

---

### Post by qunungnauraq on 2011-11-12
I was able to install alien arena 7.51 from playdeb and start it from terminal entering sudo su alien-arena twice in a row. Now the problems I am having are that I can't save custom resolution settings and the other aliens don't appear.

---

### Post by Perfect Storm on 2011-11-12
Why are you running Alien Arena with sudo? First it's very insecure to do that, second you're are ruining the permission of the game so you can't edit/change options in the game.


**>>> ONLY use sudo when you change/edit in the system itself!!! <<<**

---

### Post by qunungnauraq on 2011-11-12
I only ran sudo two consecutive times once and now alien arena will open using the icon without sudo but still wont save settings. It was just an experiment and sudo was the only way I could get alien arena to run. Afterwards I replaced my linux partition with a clean backup image.

---

### Post by qunungnauraq on 2011-12-06
I still have not been able to play alien arena in ubuntu 11.10 unity,ubuntu 11.10 gnome shell,or in any version of mint 12. Has anyone figured out how and done it on there own computer yet?

---

### Post by Philip Farrugia on 2011-12-26
Same problem here.
Anyone got a solution?

---

### Post by Perfect Storm on 2011-12-26
See if the Alien Arena in Desura works for you: [http://www.desura.com/](http://www.desura.com/)

---

### Post by qunungnauraq on 2012-01-05
Desura works with my 2008 Mac Pro but With my ThinkPad T510 with nvidia nvs 3100 discrete graphics AA will play but with no sound.

---

### Post by K-Ghidorah on 2012-01-19
In the Software Center, a user called motionride put up an effective fix.

> 
sudo chown [user name]:[user name] /home/[user name]/.config/alien-arena/

Then run Alien Arena normally.

---

### Post by qunungnauraq on 2012-01-20
Here is what i get when I try to run alien-arena:

qunungnauraq@qunungnauraq-ThinkPad-T510:~$ alien-arena
ln: creating symbolic link `/home/qunungnauraq/.config/alien-arena/data1': Permission denied
using /home/qunungnauraq/.config/alien-arena/arena for writing
Could not exec default.cfg
Could not exec config.cfg
Console initialized.
--------- [Loading Renderer] ---------
Master server at 69.136.224.226:27900
Sending shutdown to 69.136.224.226:27900
recursive shutdown
Error: Couldn't load pics/colormap.pcx
qunungnauraq@qunungnauraq-ThinkPad-T510:~$

---

