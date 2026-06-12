---
title: "Maximize, Minimize, and Close Buttons Not Showing At All"
date: 2010-05-16
forum: General Help
---

### Post by TheRainbowBitMe on 2010-05-16
After I completed the upgrade to Lucid, my maximize, minimize, and close buttons disappeared. I looked around on the forums and i didn't see any other posts about this problem. I'm sorry if i might have over looked one though. Anyways, the buttons are not on the left or the right, they just don't show up. I tried messing with the theme settings and I also tried some of the things that were recommended on the main sticky about bugs with Lucid, and i still don't have them. Dose anyone know how to fix this or will it fix itself with updates?

(I attached a screenshot to better show what I mean by they are missing.)

---

### Post by Ginsu543 on 2010-05-16
Give this a try. If you haven't already, download and install _[Ubuntu Tweak](http://ubuntu-tweak.com/)_. Open the program, then go to the "Window Manager Settings" tab under "Desktop." There, you should see options to change Window Titlebar Button Layout. See if Maximize, Minimize, and Close buttons are checked. If not, check them. You can then move them around (left side or right) by drag-n-drop.

---

### Post by scouser73 on 2010-05-16
I think this can be sorted by going to **System, Preferences, Appearance** click on the **Visual Effects** tab and select **Normal**.

By rights, it should now be sorted for you.

---

### Post by wilee-nilee on 2010-05-16
Post this from the terminal.
```
lspci | grep VGA
```

---

### Post by WorMzy on 2010-05-16
Your window manager has either failed to load, or has crashed. Run
```
metacity --replace
```
to bring it back.

---

### Post by 3rdalbum on 2010-05-16
It looks like there isn't a window manager running.

> I think this can be sorted by going to System, Preferences, Appearance click on the Visual Effects tab and select Normal.

That should do the trick. Otherwise you can create a launcher on your panel that has the command 'metacity --replace', and then click the launcher.

You could even try 'compiz --replace', assuming that you have some 3D acceleration.

---

### Post by TheRainbowBitMe on 2010-05-16
So as I was going down the posts and trying things, WorMzy's answer worked until i closed to terminal. After it was closed it went back to how it was. Do i just have to do this every time I get on my computer and leave the terminal open?

---

### Post by TheRainbowBitMe on 2010-05-16
> **wilee-nilee said:**
> Post this from the terminal.
```
lspci | grep VGA
```

kaylaface@Lappy-Chan:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

---

### Post by wilee-nilee on 2010-05-16
> **TheRainbowBitMe said:**
> kaylaface@Lappy-Chan:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

I think what you have is a graphic card that isn't well supported. So did you open the backports in software sources or add any ppa's like xswat or any others. You can when your computer boots hit e=edit then put nomodset in the kernel line between the end which is quiet splash and the end of the kernel information to see if the buttons return just as a test.

So your not the only one having problems with this card.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/416073](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/416073)

---

### Post by seanelly on 2010-05-16
Add metacity to the startup list?

---

### Post by wilee-nilee on 2010-05-16
> **seanelly said:**
> Add metacity to the startup list?

Why?

---

### Post by seanelly on 2010-05-16
...'cause it isn't starting normally? I thought I remembered doing this as a work-around when xfwm4 wasn't starting on an install I did. Normally when I encounter this I just alt+f2 [wm] --replace and it's all dandy from there...

---

### Post by wilee-nilee on 2010-05-16
> **seanelly said:**
> ...'cause it isn't starting normally? I thought I remembered doing this as a work-around when xfwm4 wasn't starting on an install I did. Normally when I encounter this I just alt+f2 [wm] --replace and it's all dandy from there...

It us a bug for this card, it can be dealt with in several ways. I am trying to see what the OP has done so far. I have a similar problem with a graphics card on another computer.

---

### Post by TheRainbowBitMe on 2010-05-17
> **wilee-nilee said:**
> I think what you have is a graphic card that isn't well supported. So did you open the backports in software sources or add any ppa's like xswat or any others. You can when your computer boots hit e=edit then put nomodset in the kernel line between the end which is quiet splash and the end of the kernel information to see if the buttons return just as a test.

So your not the only one having problems with this card.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/416073](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/416073)

When I hit e nothing happened, maybe I didn't do something right? If there another way to do that?

---

### Post by wilee-nilee on 2010-05-17
> **TheRainbowBitMe said:**
> When I hit e nothing happened, maybe I didn't do something right? If there another way to do that?

When grub comes up you might have to hold down the shift key when you start to get it to show there are instruction there.

---

### Post by TheRainbowBitMe on 2010-05-17
> **wilee-nilee said:**
> When grub comes up you might have to hold down the shift key when you start to get it to show there are instruction there.

This is going to sound really stupid, but what is grub? Is that when it says "starting up....." and stuff? Sorry I'm not the best with Linux.

---

### Post by wilee-nilee on 2010-05-17
> **TheRainbowBitMe said:**
> This is going to sound really stupid, but what is grub? Is that when it says "starting up....." and stuff? Sorry I'm not the best with Linux.

Grub is the screen that comes up when you hold down the shift key it lists the kernels, and a recovery and memory test.

---

### Post by wilee-nilee on 2010-05-17
So it is important that you read the instructions and answer whether you have tried them, such as turning off all the visual effects in preferences>appearance. A non supported or weakly supported card is not my specialty. Also I asked you if you have the backports open and whether you added like the xswat ppa. It is okay if you don't know what this means just ask.;)

My only specialty anyway is making some great coffee in my French press. ;)

---

### Post by TheRainbowBitMe on 2010-05-17
> **wilee-nilee said:**
> So it is important that you read the instructions and answer whether you have tried them, such as turning off all the visual effects in preferences>appearance. A non supported a weakly supported card is not my specialty. Also I asked you if you have the backports open and whether you added like the xswat ppa.

I have tired all of the answers that have been posted and the only one that seems to work was putting "metacity --replace" into the terminal, but only worked if I didn't close the terminal. 

And I don't know if i have the backports open or not. And I truthfully don't know what xswat ppa is.

Also, i just tried booting and getting to the grub screen again. All that happens is what normaly happens when i boot up.

---

### Post by wilee-nilee on 2010-05-17
Since you have limited knowledge, I am hesitant to offer any real solutions, as it could leave the computer worse then it is, but would be able to be fixed by removing any fixes. It might just be best to back everything up off the computer you can't lose the reinstall a fresh Ubuntu. IT seems that you are probably dual booting but I don't see any information about this.

Have you turned off all the visual effects? in system>preferences>appearance>visual effects.

You also don't mention whether you upgraded from hardy, or Karmic.

---

### Post by TheRainbowBitMe on 2010-05-17
> **wilee-nilee said:**
> Since you have limited knowledge, I am hesitant to offer any real solutions, as it could leave the computer worse then it is, but would be able to be fixed by removing any fixes. It might just be best to back everything up off the computer you can't lose the reinstall a fresh Ubuntu. IT seems that you are probably dual booting but I don't see any information about this.

Have you turned off all the visual effects? in system>preferences>appearance>visual effects.

You also don't mention whether you upgraded from hardy, or Karmic.

I'm not dual booting.

And I have tried turning off all the visual effects, but I don't think that having them off should make a difforence since i had them on before and everything was fine.

And I upgraded from Karmic. And when I had Karmic everything worked fine. I usually don't have any problems with Linux at all, but when I upgraded I had this problem.

When I use to have a problem I just ask my sister for help since she has had Linux for several years, but she is currently unavailable and I want to learn to fix these things by myself.

---

### Post by wilee-nilee on 2010-05-17
I understand the want to fix this yourself and learn from it.

You might install ubuntu tweak as another person suggested with  ```
sudo add-apt-repository ppa:tualatrix/ppa
```
in the terminal.
 
Then go to the section the person who suggested this and make sure the right buttons are clicked on (windows manager settings). If this does not work then go to software sources and go to the bottom of the list and tick the x updates hit refresh and install what it adds. This is a additional PPA that will load relevant drivers to your card. But this may not fix things but it's worth a try. You will have top reboot or restart the desk top to get the full results. 

Now I suggest this without you knowing how to stop the computer at the grub bootloader, which is where you would put the nomodset if this doesn't work and makes the computer usable by not using the newer drivers.

I know you want to learn but this is not the best area to start at, but we all learn in different ways so do what seems appropriate.

So the ubuntu tweak ppa is here so you can see what a ppa is.
[https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)

---

### Post by WorMzy on 2010-05-17
Does pressing Alt+F2 not bring up the run command? If it does, then running 'metacity --replace' there is a permanent solution for your current session.

Can you run gconf-editor, browse to /desktop/gnome/applications/window_manager, and check that the default key is set to 'metacity' (no quotes), then browse to /desktop/gnome/session/required_components, and check that the windowmanager key is also set to 'metacity' (again, no quotes).

---

### Post by Warren North on 2010-06-30
I read the some of the previous post and I am glad.
I have a similar problems but mine only occurs occasionally or at some point I lose the bar that minimize, maximize and close. I am using 10.04 but I seen this when I was using hardy. I usually log out and log back in and it will get fixed. But may not have to do that with some of the info I recently read. So thanks for asking and others for helping in that matter.
I think I be ok. Any additional info on why would be good if anyone wants to add.

---

