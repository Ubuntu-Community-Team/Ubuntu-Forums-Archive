---
title: "Xrandr puzzle for Ubuntu wizards!"
date: 2011-02-26
forum: General Help
---

### Post by Dry Lips on 2011-02-26
Hey folks!  

I'm a newbie with Linux, and I've got an interesting
problem for you experienced guys to chew on! At the
Login Screen Ubuntu insists on setting the screen resolution
to 1600x1200, which is waaay to much for my trusty
old CRT-monitor. Once I log into my account it is possible
to change my resolution through the preferences, but this 
doesn't affect the login screen. I've searched the forum, 
and luckily came across a post with almost the same 
problem as my own:
[http://ubuntuforums.org/showthread.php?t=1679297&highlight=login+screen+resolution](http://ubuntuforums.org/showthread.php?t=1679297&highlight=login+screen+resolution)

I then tried to add this line:[B] 
xrandr --output VGA1 --mode 1024x768 --rate 85[/B]
to* /etc/gdm/Init/Default*                                                        
But after rebooting my computer, the resolution at the 
login screen was still 1600x1200. Ugh!


Here are my current xrandr values (if it makes any difference):

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 360mm x 270mm
   1792x1344      60.0  
   1920x1200      59.9  
   1600x1200      75.0     70.0     65.0     60.0  
   1680x1050      74.9     60.0  
   1400x1050      85.0     74.9     60.0  
   1280x1024      85.0     75.0     60.0  
   1440x900       84.8     75.0     59.9  
   1280x960       85.0     60.0  
   1360x768       60.0  
   1280x800       84.9     74.9     59.8  
   1152x864       75.0     70.0  
   1280x768       84.8     74.9     59.9  
   1024x768       85.0*    75.1     75.0     70.1     60.0     43.5     43.5  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        85.0     72.8     75.0     72.8     66.7     60.0     59.9  
   720x400        87.8     85.0     70.1  
   640x400        85.1  
   640x350        85.1  

Are there any Ubuntu wizards able to help me out on this one?

---

### Post by Dry Lips on 2011-02-27
Yo wizards! Reading up on the forums when you have a problem can
sometimes make things seem more difficult than they really are. 

At System>Preferences>Monitors you can just select &#8220;make default&#8221;,
which changed the resolution of the Login Screen perfectly. 
No need for Xrandr! 

Reading technical posts on the topic can certainly confuse an Ubuntu
Noob like me, and apparently there were no wizards out there bright
enough to notice that this was a problem that could be solved with 
a single click. ;)
[URL="http://ubuntuforums.org/showthread.php?t=1544285"]
[/URL]

---

