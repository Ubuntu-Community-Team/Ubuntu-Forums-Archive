---
title: "Ubuntu10.04: trouble with ccsm and cube function"
date: 2010-06-07
forum: General Help
---

### Post by eidasadie on 2010-06-07
Hi all,

I tried using ccsm to get the cube desktop working on ubuntu 10.04. After reading through many of the forums here on how to get the cube working I still could not find an answer for 10.04. Changed my settings with gconf-editor to disable Nautilus show desktop and a few other recommended setting and nothing worked. Also, for some reason, ccsm did not have the Wallpaper option (its supposed to be under utility), and I think it was necessary for the cube in some way. Does anyone know how to get the cube working on ubuntu 10.04, or can anyone recommend an earlier release of ubuntu that is compatible with compiz? Thanks for any advice you can give, much appreciated.

-eidasadie

---

### Post by _khAttAm_ on 2010-06-07
Install compiz-fusion-plugins-extra via synaptic package manager or by typing in the following in the terminal:
```
sudo apt-get install compiz-fusion-plugins-extra
```
Now open up ccsm and enable "Cube Reflection and Deformation" and "Rotate Cube". You should also find Wallpaper option, but that is not required.

---

### Post by eidasadie on 2010-06-07
Thanks for the fast reply _khAttAm_,

I have ccsm and fusion plugins. I went into ccsm and changed settings also changed Nautilus back so it doesnt display the desktop, but i still dont have the cube. do i need to use compiz --replace command or something for the settings to change (after i changed the settings and closed ccsm manager nothing changed)?

---

### Post by _khAttAm_ on 2010-06-07
Try this and let us know what happens:
Right Click On Desktop>**Change Background**>**Appearance** Tab>Select **Extra**

Now, if that is successful, can you see the woobly effect when you move the windows around (by dragging the Title Bar)?

---

### Post by morrcahn on 2010-06-07
Did you ever use the cube in karmic? You checked out all the keybindings and settings of the cube?

---

### Post by eidasadie on 2010-06-07
I had changed to Extra earlier, and when i went back in just now to check and make sure, the setting had reverted back to normal for some reason. I changed to Extra and made sure that wobbly and all other settings were correct. still no effects for some reason.

---

### Post by eidasadie on 2010-06-07
morrcahn, 

I have never used Karmic, but i will look into it. All the keybindings should be default since i have just installed ccsm and all the cube settings are per _khAttAm_ 's instructions and other setting adjustments i picked up in other threads.

---

### Post by morrcahn on 2010-06-07
Ah yes. When you upgraded to 10.04 did you keep everything in your home folder?

---

### Post by morrcahn on 2010-06-07
Wait, so is this a completely new system for you?

---

### Post by _khAttAm_ on 2010-06-07
Check your keybindings of Rotate cube:
[http://yfrog.com/6fselection003jp](http://yfrog.com/6fselection003jp)

Show your screenshot.

---

### Post by eidasadie on 2010-06-07
I did not upgrade. did a straight install of 10.04 with a partition.

---

### Post by eidasadie on 2010-06-07
> **_khAttAm_ said:**
> Check your keybindings of Rotate cube:
[http://yfrog.com/6fselection003jp](http://yfrog.com/6fselection003jp)

Show your screenshot.
ok so i just realized that everytime i go in and click the Extra setting, after i accept the changes and close the window it reverts back to normal. I will post a screen shot next

---

### Post by _khAttAm_ on 2010-06-07
> **eidasadie said:**
> ok so i just realized that everytime i go in and click the Extra setting, after i accept the changes and close the window it reverts back to normal. I will post a screen shot next

In that case, you might not be getting Woobly windows as well. This is how it looks like: [http://www.youtube.com/watch?v=icm7GGCPOt8](http://www.youtube.com/watch?v=icm7GGCPOt8)

---

### Post by eidasadie on 2010-06-07
> **eidasadie said:**
> ok so i just realized that everytime i go in and click the Extra setting, after i accept the changes and close the window it reverts back to normal. I will post a screen shot next
Here is my screen shot with all settings enabled and correct

[http://img175.imageshack.us/img175/7726/screenshotcf.png](http://img175.imageshack.us/img175/7726/screenshotcf.png)

---

### Post by morrcahn on 2010-06-07
This happened on some machines here. We had to change the graphics driver. There should be two choices. Try the one you aren't using.

---

### Post by eidasadie on 2010-06-07
> **_khAttAm_ said:**
> In that case, you might not be getting Woobly windows as well. This is how it looks like: [http://www.youtube.com/watch?v=icm7GGCPOt8](http://www.youtube.com/watch?v=icm7GGCPOt8)
im def not getting any of those effects

---

### Post by eidasadie on 2010-06-07
> **morrcahn said:**
> This happened on some machines here. We had to change the graphics driver. There should be two choices. Try the one you aren't using.
how do i go about doing that? i think ATI driver runs my graphics right now. im not sure what the other driver is.

---

### Post by _khAttAm_ on 2010-06-07
> **eidasadie said:**
> Here is my screen shot with all settings enabled and correct

[http://img175.imageshack.us/img175/7726/screenshotcf.png](http://img175.imageshack.us/img175/7726/screenshotcf.png)

seems OK...

Now, once you have ccsm installed, just open the visual effects once (and only once) and tick extra. Close it and launch ccsm. Enable Rotate Cube and press Ctrl+Alt+Right Arrow.. If you open Visual Effects and change it to Extra (or Normal or None), then the effects will stop working. 

What happens when you press Ctrl+Alt+Right or Ctrl+Alt+Mouse Left Click + Drag??

---

### Post by _khAttAm_ on 2010-06-07
> **eidasadie said:**
> im def not getting any of those effects

really? then it might be some other issue..

You probably have not installed Binary ATI Driver... 

Here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by morrcahn on 2010-06-07
System > Administration > Hardware Drivers

Can you screen shot what the window shows?

---

### Post by eidasadie on 2010-06-07
> **_khAttAm_ said:**
> seems OK...

Now, once you have ccsm installed, just open the visual effects once (and only once) and tick extra. Close it and launch ccsm. Enable Rotate Cube and press Ctrl+Alt+Right Arrow.. If you open Visual Effects and change it to Extra (or Normal or None), then the effects will stop working. 

What happens when you press Ctrl+Alt+Right or Ctrl+Alt+Mouse Left Click + Drag??
when i use  CTRL+ALT+RIGHT i switch desktops (panels). the effects dont work because it just keeps reverting automatically to normal. i am going to try to get the binary ATI Driver and see if that fixes the problem

---

### Post by eidasadie on 2010-06-07
> **morrcahn said:**
> System > Administration > Hardware Drivers

Can you screen shot what the window shows?
[http://img444.imageshack.us/img444/7494/screenshot1s.png](http://img444.imageshack.us/img444/7494/screenshot1s.png)

---

### Post by morrcahn on 2010-06-07
It looks like you were installing the binary driver in terminal in the background? If that gives you another driver to choose from in that hardware drivers window, try it out.

---

### Post by eidasadie on 2010-06-07
> **morrcahn said:**
> It looks like you were installing the binary driver in terminal in the background? If that gives you another driver to choose from in that hardware drivers window, try it out.
i did install the driver but there is only 1 ATI driver listed in hardware manager. and now i just noticed my windows have no headers now.. so i think the problem is compounding, but i wanna figure it out regardless. thanks for all your replys so far, learning a lot.

---

### Post by morrcahn on 2010-06-07
Exactly which graphics card do you have? 

Also, if you plan on working with ubuntu/linux long term, next graphics card upgrade I would go with NVidia. Easier to work with.

---

### Post by eidasadie on 2010-06-07
> **morrcahn said:**
> Exactly which graphics card do you have? 

Also, if you plan on working with ubuntu/linux long term, next graphics card upgrade I would go with NVidia. Easier to work with.
i have the Radeon HD 4350 RV710. i also have a Nvidia card but for some reason the sound would not work. its a GeForce 9400GT 1GB DDR2. if you know anything about fixing a sound issue then maybe i could switch over to the Nvidia card? maybe having a Nvidia would fix the other issues too?

---

### Post by morrcahn on 2010-06-07
Navigate to your xorg.conf file in terminal.
```
vim /etc/X11/xorg.conf
```If you don't have vim installed
```
sudo aptitude install vim
```Then try again. Find within the file the "Device" section where it has:

Option      "EnableRandR12" "false"

If it is set to true, change it to false. See if that works.

Also, are you saying that you NVidia video card messes your sound up?

---

### Post by eidasadie on 2010-06-07
> **morrcahn said:**
> Navigate to your xorg.conf file in terminal.
```
vim /etc/X11/xorg.conf
```If you don't have vim installed
```
sudo aptitude install vim
```Then try again. Find within the file the "Device" section where it has:

Option      "EnableRandR12" "false"

If it is set to true, change it to false. See if that works.

Also, are you saying that you NVidia video card messes your sound up?
yes, when i had the Nvidia in before it ran much smoother but i couldnt get the sound to work. But i have not tried it with ubuntu yet (just assuming it wouldnt work). I used vim /etc/X11/xorg.conf and there was a Device section but no option for EnableRandR12

---

### Post by morrcahn on 2010-06-07
> Device section but no option for EnableRandR12
Go ahead and put that line in there then. If you don't know how to use vim: hit insert to type and then esc. then :wq to exit vim. 

>  But i have not tried it with ubuntu yetIf this doesn't work I would most definitely give it a try.

---

### Post by eidasadie on 2010-06-08
> **morrcahn said:**
> Go ahead and put that line in there then. If you don't know how to use vim: hit insert to type and then esc. then :wq to exit vim. 

If this doesn't work I would most definitely give it a try.
Set "EnableRandR12" to "false" but still not able to get the cube or any effects work. im thinking a reinstallation with 9.10 or maybe switching to the Nvidia might be easier than trying to fix 10.04.. seems like 10.04 still has some things that need to be worked out..

---

### Post by morrcahn on 2010-06-08
> seems like 10.04 still has some things that need to be worked outThis is very possible. I would switch to Nvidia before giving up on lucid. When you get that switched use envyng in terminal to get updated drivers, and also [http://www.nvidia.com/object/linux-display-ia32-195.36.24.html.]("http://www.nvidia.com/object/linux-display-ia32-195.36.24.html")
That should give you the correct one. After both of those you should have two choices in the hardware drivers program. Test which one fixes the problem. If this all fails, I am sorry. :smile: Oh, and you will also probably need to make a new xorg.conf file.

---

### Post by eidasadie on 2010-06-08
> **morrcahn said:**
> This is very possible. I would switch to Nvidia before giving up on lucid. When you get that switched use envyng in terminal to get updated drivers, and also [http://www.nvidia.com/object/linux-display-ia32-195.36.24.html.]("http://www.nvidia.com/object/linux-display-ia32-195.36.24.html")
That should give you the correct one. After both of those you should have two choices in the hardware drivers program. Test which one fixes the problem. If this all fails, I am sorry. :smile: Oh, and you will also probably need to make a new xorg.conf file.
Ya so i spent all last night trying to get Nvidia to work on Lucid but failed. Deleted Lucid and installed Karmic in its place on /dev/sda. Everything works great now. Thanks for all your guys help! I have another question now tho. When I installed Karmic I manually partitioned my hard drive which worked out fine, except I made the linux-swap space larger than i intended (1.8 GB). Is there a way i can check how much space the kernel is using and resize the partition just for the kernel, and add the unallocated space into the Ext3 partition that ubuntu is installed on? thanks again

eidasadie

---

### Post by eidasadie on 2010-06-08
or should i just leave it as is and live with it? if i ever wanted to install another OS do you think i could do a manual partition again to use up the extra swap space?

---

### Post by morrcahn on 2010-06-08
1.8 GB is not actually bad for the swap. If you want to ever hibernate your computer the swap should be as big as how much RAM you have. So, I would just keep the 1.8 there. Also, you can't 'add' space to an already allocated partition. You would have to just recreate the whole partition. I am unsure if there is a way to check how much the kernel is using.

---

### Post by eidasadie on 2010-06-09
> **morrcahn said:**
> 1.8 GB is not actually bad for the swap. If you want to ever hibernate your computer the swap should be as big as how much RAM you have. So, I would just keep the 1.8 there. Also, you can't 'add' space to an already allocated partition. You would have to just recreate the whole partition. I am unsure if there is a way to check how much the kernel is using.
thanks morrcahn. ill just leave it be then. you wouldn't happen to know how to fix an error with .ICEauthority by chance? I looked thru all the forums regarding this issue and nothing worked (except i have not tried to delete the .ICEauthority). Any thoughts on this would be appreciated even though its completely off topic for this thread

---

### Post by morrcahn on 2010-06-11
What exactly is going wrong with your .ICEauthority file? 
So, the graphics and everything working with the Nvidia? You also said that you went down to karmic. There isn't too much of a difference between the two. The only major thing that makes it for me is the option to have a second pane in your file browser.

---

### Post by eidasadie on 2010-06-17
> **morrcahn said:**
> What exactly is going wrong with your .ICEauthority file? 
So, the graphics and everything working with the Nvidia? You also said that you went down to karmic. There isn't too much of a difference between the two. The only major thing that makes it for me is the option to have a second pane in your file browser.
Alright so all i had to do to fix the .ICEauthority was create a new user, so thats fine.  Still havent had time to try the Nvidia, just too busy, but i will eventually and if i have any problems i'll start a new thread here in the forums.  As for switching to karmic, i just felt i would have less issues with it, and as you were sayin, its pretty much the same as Lucid. thanks again for all the assistance

eidasadie

---

