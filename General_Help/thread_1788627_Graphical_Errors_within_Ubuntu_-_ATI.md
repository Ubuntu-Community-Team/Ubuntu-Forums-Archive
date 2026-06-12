---
title: "Graphical Errors within Ubuntu - ATI"
date: 2011-06-22
forum: General Help
---

### Post by AtomicAMD on 2011-06-22
Hi,
This is my first post and my second day using Ubuntu and I have got to say I am liking it for school and for work. I am having some graphical errors though. First off let me give you my system spec so you know what I am working with. 

AMD x6 3.8Ghz
8GB Ram
HD Radeon 6950 
ASUS M4A79XTD EVO mobo
1920x1080 display 
x32 Ubuntu

I have the most recent ATI Drivers installed. 
Whenever I minimize a program, it leaves little graphic traces of the program for about a second before disappearing. 
Whenever moving a window around with the mouse it is very slow like a lag, same when moving to the edge to re-size. (But speed is normal when clicking the minimize or re-size button, besides the graphical errors when minimizing) 
Also, whenever I change a graphic setting in Compiz, the top menu bar tweaks out and distorts so you can't read anything (but can still guess and click and the menu drop-downs will still appear) and have to log out and in for it to fix its self. 

Any help would be appreciated. I apologize in advance if this has already been covered and answered. I am still very new :)

Thanks.

---

### Post by wildmanne39 on 2011-06-23
> **AtomicAMD said:**
> Hi,
This is my first post and my second day using Ubuntu and I have got to say I am liking it for school and for work. I am having some graphical errors though. First off let me give you my system spec so you know what I am working with. 

AMD x6 3.8Ghz
8GB Ram
HD Radeon 6950 
ASUS M4A79XTD EVO mobo
1920x1080 display 
x32 Ubuntu

I have the most recent ATI Drivers installed. 
Whenever I minimize a program, it leaves little graphic traces of the program for about a second before disappearing. 
Whenever moving a window around with the mouse it is very slow like a lag, same when moving to the edge to re-size. (But speed is normal when clicking the minimize or re-size button, besides the graphical errors when minimizing) 
Also, whenever I change a graphic setting in Compiz, the top menu bar tweaks out and distorts so you can't read anything (but can still guess and click and the menu drop-downs will still appear) and have to log out and in for it to fix its self. 

Any help would be appreciated. I apologize in advance if this has already been covered and answered. I am still very new :)

Thanks.Hi first lets fix what is broke from changing settings in compiz, click on reset unity and compiz and reset unity then, if you are still having lag post back and I have a fix for that, also I can tell you how to change effects in compiz without messing things up, but lets do this one step at a time.

---

### Post by AtomicAMD on 2011-06-23
Hi, 

I hit reset to default under the preferences tab in Compiz. Doing that resulted in my top menu bar tweaking out again but this time resulting in not letting my click on anything and the unity search doesnt pull up when hitting the windows button. Still having window lag.

---

### Post by wildmanne39 on 2011-06-23
> **AtomicAMD said:**
> Hi, 

I hit reset to default under the preferences tab in Compiz. Doing that resulted in my top menu bar tweaking out again but this time resulting in not letting my click on anything and the unity search doesnt pull up when hitting the windows button. Still having window lag.
Hi, did you go to the link by clicking on reset unity and compiz in my signature? Then did you follow the directions? You do not go into compiz and reset there.

---

### Post by AtomicAMD on 2011-06-23
Ah, no I didn't see your link in your sig. Well after hitting that restore to default in Compiz and it messing up my menu bar, I restarted the comp and came back to Ubuntu and my entire UI was gone. No menu bar, no taskbar, and no Unity search coming up when hitting the super/windows key. Ha what did I do?!
EDIT: I am writing this within my Windows partition.

---

### Post by wildmanne39 on 2011-06-23
> **AtomicAMD said:**
> Ah, no I didn't see your link in your sig. Well after hitting that restore to default in Compiz and it messing up my menu bar, I restarted the comp and came back to Ubuntu and my entire UI was gone. No menu bar, no taskbar, and no Unity search coming up when hitting the super/windows key. Ha what did I do?!
EDIT: I am writing this within my Windows partition.Hi, if you can get a terminal do what that links says and if that does not work post back here. Think you just disabled the plugin in compiz the say unity plugin, that is what the unity desktop is just a plugin.

---

### Post by AtomicAMD on 2011-06-23
Still nothing. Only terminal I could get was safemode from GRUB and when I typed in the code for the resets it just gave me errors like "No monitor presets" or stuff like that. 

Random question. In the event I need to erase this ubuntu partition, is there a way to restore this partition space back to my windows partition without losing data? Or do I have to repartition the drive as one partition and start over. (I do not want to boot to Grub each time so I may purchase a separate drive for Ubuntu if I can get it to run smoothly. )

---

### Post by wildmanne39 on 2011-06-23
> **AtomicAMD said:**
> Still nothing. Only terminal I could get was safemode from GRUB and when I typed in the code for the resets it just gave me errors like "No monitor presets" or stuff like that. 

Random question. In the event I need to erase this ubuntu partition, is there a way to restore this partition space back to my windows partition without losing data? Or do I have to repartition the drive as one partition and start over. (I do not want to boot to Grub each time so I may purchase a separate drive for Ubuntu if I can get it to run smoothly. )
Hi, if you follow the directions on the link, you would have got a lot of errors, but you do not need to worry about the errors that is normal, if you let it run for about three minutes and then restart you should be fixed up. If it is not fixed and it loads to the desktop , hit cltr+alt+t to open a terminal then type.
```
unity --reset
```that is what the link tells you to do, let it run about three minutes the restart.

---

### Post by AtomicAMD on 2011-06-23
Okay! We are back to where I started finally lol. "unity --reset" worked this time. 

Still have the tearing while minimizing/laggy window movements with mouse. 

Thanks for all the help so far though! x64 Ubuntu wouldn't help with any of these issues would it?

---

### Post by wildmanne39 on 2011-06-23
> **AtomicAMD said:**
> Okay! We are back to where I started finally lol. "unity --reset" worked this time. 

Still have the tearing while minimizing/laggy window movements with mouse. 

Thanks for all the help so far though! x64 Ubuntu wouldn't help with any of these issues would it?Hi, this should fix your last problem.
    Install CompizConfig Settings Manager from either the Software Center, or Synaptic.
    Click on the Composite tab, and un-check Detect refresh rate.
    Back to main menu.
    Click on the OpenGL tab.
    Uncheck Sync to Vblank.

---

### Post by AtomicAMD on 2011-06-23
> **wildmanne39 said:**
> Hi, this should fix your last problem.
    Install CompizConfig Settings Manager from either the Software Center, or Synaptic.
    Click on the Composite tab, and un-check Detect refresh rate.
    Back to main menu.
    Click on the OpenGL tab.
    Uncheck Sync to Vblank.

I have double checked the settings and restarted my computer but both problems still persist. Any other ideas?

---

### Post by wildmanne39 on 2011-06-23
> **AtomicAMD said:**
> I have double checked the settings and restarted my computer but both problems still persist. Any other ideas?Hi, To get the cube working or to change other settings in natty use this link.
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)
after you have finished with this guide and you change other settings it will mess up your windows again so just log out and back in and they will be fixed.
If you are logged in as classic and you are having these issues you need to follow this link.
[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

---

### Post by AtomicAMD on 2011-06-23
> **wildmanne39 said:**
> Hi, To get the cube working or to change other settings in natty use this link.
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)
after you have finished with this guide and you change other settings it will mess up your windows again so just log out and back in and they will be fixed.
If you are logged in as classic and you are having these issues you need to follow this link.
[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

I will go ahead and do this a little later tonight when I have some more time. If you would, could you explain what the "cube" is and what it does? 

As you can see, I am a Ubuntu noob, been stuck with Windows/OSX's GUI's ha. I'm trying to break free so thank you again for your help!

---

### Post by wildmanne39 on 2011-06-23
> **AtomicAMD said:**
> I will go ahead and do this a little later tonight when I have some more time. If you would, could you explain what the "cube" is and what it does? 

As you can see, I am a Ubuntu noob, been stuck with Windows/OSX's GUI's ha. I'm trying to break free so thank you again for your help!Hi, I am going to give you a link for the cube on youtube check it out. To help more with your problem are you logging into ubuntu or ubuntu classic?
[http://www.youtube.com/watch?v=Y772Zrjwgws](http://www.youtube.com/watch?v=Y772Zrjwgws)

---

### Post by AtomicAMD on 2011-06-23
> **wildmanne39 said:**
> Hi, I am going to give you a link for the cube on youtube check it out. To help more with your problem are you logging into ubuntu or ubuntu classic?
[http://www.youtube.com/watch?v=Y772Zrjwgws](http://www.youtube.com/watch?v=Y772Zrjwgws)

I am logging into Ubuntu. I can log into classic I believe if needed. I will check that link out, thanks. 

Another random question, does memtest come with the Ubuntu installation? It is showing in the GRUB menu when I boot, which is fine, I am just curious as to how it got there. I am familiar with the program from Overclocking.

---

### Post by wildmanne39 on 2011-06-23
> **AtomicAMD said:**
> I am logging into Ubuntu. I can log into classic I believe if needed. I will check that link out, thanks. 

Another random question, does memtest come with the Ubuntu installation? It is showing in the GRUB menu when I boot, which is fine, I am just curious as to how it got there. I am familiar with the program from Overclocking.
Hi, yes memory test comes with ubuntu.

---

### Post by AtomicAMD on 2011-06-23
> **wildmanne39 said:**
> Hi, yes memory test comes with ubuntu.

Thank you. And will this cube effect help with my graphical errors? Or am I missing something.

---

### Post by wildmanne39 on 2011-06-24
Hi, not the cube its self but you can see how changing some settings effects unity, basically most things you change in unity disables the unity plugin, and that is the problem, but after you make your changes in compiz then you reactivate the plugin and  log out and the windows are back to normal. I am not sure what is causing your problem with lagging if you already did my other suggestion in post #10? If you did my other suggestion then run this command in a terminal 
```
sudo lshw
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

