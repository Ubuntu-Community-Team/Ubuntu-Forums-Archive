---
title: "im going crazy here!"
date: 2010-09-26
forum: General Help
---

### Post by Ballbrekr on 2010-09-26
**excessive lag** 			
 			 			 		   		 		 		Let me start this off by saying I love Linux.


I have some troubles here and not sure where to turn.  I will describe them best i can.

[B]_description:_
Lucid Lynx has become slow and laggy and sometimes unresponsive to  commands.  World of Warcraft is getting about 9 frames per second in  Dalaran (for those who know that place).  To initialize the game takes a  considerable amount of time (15-30 seconds).  [/B]

Knowing that, I do want to say, please help.  I do not like windows.  HELP ME PLEASE!

Here are some solutions I have tried to correct the issue.  This has  been going on for a little over four weeks now.  Going on so long now I  have WoW on usb stick to help get files transferred.

_**Solutions tried:**_
[B]All versions of Wine have been installed and tried.  Play on Linux  has been tried and removed.  CrossOver trial version is currently  installed and working (still same old lag  issue).  My ATI radeon HD 5770 card has been replaced with an Nvidia  GT240, and then swapped back after that failed ( oh and those drivers  also very difficult to install i.e. kill all this  then install and then  restart something else then you can configure it after the reboot if it  reboots to gui).  Then went back to my original ATI card.  ATI drivers  are even worse, download latest driver and install them ( ok fine but  after that you cant make any adjustements because the config app wont  work).  Finally figured out (after 7 fresh installs) that fglrx-modalias  update is garbage.  So in short more than 4 weeks have gone by, ive  used 3 different video cards( onboard video also), all versions of wine,  and have used the downloaded and the recommended drivers for all of  those.

[/B]Nothing in 4 weeks has brought me closer to my goal.  My goal is to  have Linux as an Operating system and be able to play World of Warcraft  at a decent frame rate (more than 9 frames per second).

[B][U]This is what I am working with:
[/U]Release version Ubuntu 10.04
Kernel 2.6.32-24 generic
Gnome 2.30.2

hardware:
ATI radeon hd5770
AMD phenom 9150e Quad core
8 gig mem

$top =
with 1 program running I have 2 gig of memory being used that seems odd to me.

glxinfo | grep rendering  = yes
this is the result of Unigine tropic:

[/B]**Tropics Demo v1.3**

  FPS:**47.9**
 Scores:**1207**
 Min FPS:**13.0**
 Max FPS:**100.4**
  **Hardware**

  Binary:Linux 32bit GCC 4.3.2 Release May 20 2010
 Operating system:Linux 2.6.32-24-generic x86_64
 CPU model:AMD Phenom(tm) 9150e Quad-Core Processor
 CPU flags:1800MHz MMX+ 3DNow!+ SSE SSE2 SSE3 SSE4A HTT
 GPU model:ATI Radeon HD 5700 Series 3.2.9756 Compatibility Profile Context 1024Mb
  **Settings**

  Render:eek:pengl
 Mode:1920x1080 fullscreen
 Shaders:high
 Textures:high
 Filter:trilinear
 Anisotropy:4x
 Occlusion:disabled Reflection:enabled
 Refraction:enabled
 Volumetric:enabled

So if this tells me anything, I think it  says that my video card and drivers are pretty good.  Oh also I have  done all the WTF.conf file tweaks and the registry tweaks as well.  I am  at wicks end there is no more information to look up on the internet  that i have not tried.  Maybe im just doing something wrong or maybe  this guppy needs to go back the kiddy pool.  Any information or  something new to try would be great any new directions to move toward  would be great.  Also others that i know using linux have no problems  with closely similar hardware.  Thank you for your time.

Very respectfully and sincerely,
Ballbrekr

---

### Post by harrismh777 on 2010-09-26
There are several tools available that will help you figure out what is using your system's resources. 

There are several versions of "top" that will give you the data you need. There are also several "System Monitors" that will give you the same information with a graphical interface. 

Open up a terminal and enter the command:

   top

The "top" processes that are using the system (cpu, memory, cache, etc) will be at the "top" giving virtual, actual, and percentages.

It is not unusual for linux to appear to use most or all of memory. Reason being that linux balances memory usuage for buffers, cache, system and user processes in a way that maximizes memory utilization. This is normal. What is important to take note of is which processes are hogging (if any) your system resources; either cpu or memory.

:confused:

---

### Post by Ballbrekr on 2010-09-26
Thank you for the response.

this is what I have the processes change quickly and the only info I could copy is this.

top - 22:37:33 up  6:42,  2 users,  load average: 0.32, 0.77, 0.74
Tasks: 209 total,   1 running, 208 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.1%us,  0.6%sy,  0.0%ni, 98.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8195084k total,  2057676k used,  6137408k free,    39496k buffers
Swap: 24008696k total,        0k used, 24008696k free,  1023532k cached

I do not think this is enough info.  The highest value of memory resources being currently used is about 2.4% from Xorg.  At this point I am not even certain its a memory issue.  These seems to be decent results while running the benchmark.  If my interpretation is correct.  Thank you again for your response.

Very Respectfully,
Ball

---

### Post by harrismh777 on 2010-09-26
208 processes !  :confused:


Basically, your system is quiesced. You have more than enough resources, and there is no problem... xorg is using 2.4 % and I presume is the *only* process not sleeping?   Where is wine?  Where is warcraft? 

What are those 208 processes... that is a rather large number of sleeping processes.  Is this machine also a server?  

Start warcraft and leave it running, then press ctrl-alt-F1 and login to the black screen terminal... run top... what is going on?

---

### Post by Ballbrekr on 2010-09-27
Very sorry for not responding promptly.  The system is not a server and I have no idea why there is 200+ processes sleeping.  The information you requested or as much as I could copy and paste is here.

  	 	 	 	p { margin-bottom: 0.08in; }   2 users,  load average: 1.42, 1.04, 0.59 
 Tasks: 214 total,   4 running, 210 sleeping,   0 stopped,   0 zombie 
 Cpu(s): 25.8%us,  7.6%sy,  0.0%ni, 65.8%id,  0.7%wa,  0.0%hi,  0.1%si,  0.0%st 
 Mem:   8195084k total,  3100848k used,  5094236k free,    83000k buffers 
 Swap: 24008696k total,        0k used, 24008696k free,  1540016k cached 
  
 

 

 14580 ball      20   0 2786m 615m  30m R  115  7.7   2:17.02 WoW.exe             
 14532 ball      20   0  5420 2772  692 S    8  0.0   0:09.49 wineserver          
  1249 root      20   0  331m 184m  41m S    6  2.3  19:19.65 Xorg                
 14627 ball      20   0  201m  15m  10m S    1  0.2   0:00.85 gnome-terminal      
  1629 ball      20   0  243m  33m 7788 S    1  0.4   0:56.83 compiz              
  3906 ball      20   0  624m  74m  36m S    1  0.9   1:10.15 cairo-dock          
  1921 ball      20   0 2599m  13m 8356 S    0  0.2   2:37.83 BackgroundDownl     
 14646 ball      20   0 19328 1448 1028 R    0  0.0   0:00.49 top                 
     1 root      20   0 23712 1920 1244 S    0  0.0   0:00.92 init                
     2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd            
     3 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/0         
     4 root      20   0     0    0    0 S    0  0.0   0:01.94 ksoftirqd/0         
     5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0          
     6 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/1         
     7 root      20   0     0    0    0 S    0  0.0   0:05.96 ksoftirqd/1         
     8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1 



Having another look at this info.  I am curious if its displaying all four processors as one.  Oh one more thing here.  I know I have compiz and cairo running also.  Please know that those apps. have no difference in the game what so ever.  Already tried getting rid of those guys (no difference).  I hope this information helps you out because it has pretty much confused the heck out of me.  Do you think this should be normal?


Thank you for your time.


Very Respectfully,
Ball

---

### Post by Ballbrekr on 2010-09-29
8th reinstall.  I screwed something up
 
Ball

---

### Post by goodolandy on 2010-09-29
Any idea on the cache size on your processor?  I ask because when I replaced my old Intel E2600 1MB cache with a E8400 8MB cache, my FPS in Warcrack did a tremendous jump from an average of 10 FPS to an average 40 FPS with some times hitting as high as 60FPS.

My next upgrade is to replace my MB and RAM to take advantage of the 1333 FSB that my new processor is capable of.

---

### Post by Ballbrekr on 2010-09-29
AMD Phenom™ X4 9100e 64-bit Quad-Core Processor.  Looks like 2MB = 512k eaach processor from what internet says.  Do you think I need to update it along with motherboard?
 
Very Respectfully,
Ball

---

### Post by Ballbrekr on 2010-09-29
is there anything that will help manage my cache better.  I could always give that a try and of course post the result.

Very Respectfully,
Ball

---

### Post by goodolandy on 2010-09-30
> **Ballbrekr said:**
> AMD Phenom™ X4 9100e 64-bit Quad-Core Processor.  Looks like 2MB = 512k eaach processor from what internet says.  Do you think I need to update it along with motherboard?
 
Very Respectfully,
Ball

Updating your CPU and MB is your call, all I can say is when I moved from a 1MB cache dual core to a 8MB cache dual core my games started running much better under wine.  Warcrack jumped by around 30fps, L4D 1 & 2 no longer locks up my system as soon as a campaign starts and I am hoping they will improve further when I upgrade my MB and RAM from a 800 FSB to 1333 FSB which the new CPU supports.

---

### Post by Ballbrekr on 2010-09-30
I do have to be skeptical (a little).  As much as I would like upgrade unfortunately its not in my immediate future.  But still how is it possible that windows runs it just fine and linux lags behind?  Does this have to do cpu or with video?  It seems to me that the cpu is not loading down while the game is running.  Then there is also the case of the benchmark scoring pretty high.  Like I said I have no idea what's going on here.
 
Thank you,
Ball

---

