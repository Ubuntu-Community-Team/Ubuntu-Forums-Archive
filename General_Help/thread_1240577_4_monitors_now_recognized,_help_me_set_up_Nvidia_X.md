---
title: "4 monitors now recognized, help me set up Nvidia X Server Settings"
date: 2009-08-14
forum: General Help
---

### Post by PsychedelicWonders on 2009-08-14
Ok after having a vide card go bad on me and swapping the PCI slots around when I got the new one, I finally now have all 4 monitors recognized under Nvidia X Server settings.

I tried to activate them, it seems I have, but they still arent turning on?

Thanks.

---

### Post by scouser73 on 2009-08-15
For multiple monitors you need to run the nVidia settings as root: **gksudo nvidia-settings**

I found that out yesterday as I had bought another monitor and some kind people told me what to do, so I'm "paying it forward".

---

### Post by wojox on 2009-08-15
Wow, I remember getting all puffy chested when I got my dual monitors a couple years back. I'd probably pass out and go into a coma with four. :lolflag:

---

### Post by scouser73 on 2009-08-15
I'd definitely like to see that set-up, perhaps PsychedelicWonders could post a pic once he's got it sorted.

---

### Post by PsychedelicWonders on 2009-08-15
> **scouser73 said:**
> For multiple monitors you need to run the nVidia settings as root: **gksudo nvidia-settings**

I found that out yesterday as I had bought another monitor and some kind people told me what to do, so I'm "paying it forward".

Ok and what does this do?

I thought I was able to adjust everything needed in Nvidia X Server Settings?

Are you familar with that program?

My setup consists of three 19" monitors all next to each other to create sort of a space station window and then I have a 46" Samsung right next to those...

Here is a picture of it in windows.  Obviously this thread is to get it going in Ubuntu, which I've been trying for about 6 months and havent been able to do.  But now I can.

The background is the logo for my upcoming website:

PunkRockPrincess.com

---

### Post by Johnny B on 2009-08-15
thats freakin awesome.

(nvidia-settings and Nvidia X Server Settings, same thing)

---

### Post by PsychedelicWonders on 2009-08-15
Thanks, I love the setup too.

Ok so how do I save the changes in Server X config?

---

### Post by fooman on 2009-08-15
> **PsychedelicWonders said:**
> Thanks, I love the setup too.

Ok so how do I save the changes in Server X config?

thats why you need to run it as root (mentioned above by scouser73). run it as:

```
gksudo nvidia-settings
```after making the changes,  click apply,  then "save to x configuration file".

you can only save changes made to system files as root (sudo when using command line or *gk*sudo if using a gui app)....hope that helps.

---

### Post by PsychedelicWonders on 2009-08-15
Ok before you replied with that, I followed this walkthru:

[https://help.ubuntu.com/community/NvidiaMultiMonitors](https://help.ubuntu.com/community/NvidiaMultiMonitors)

now I wish I woulda ran your suggestion.  

But I got all 4 monitors active now! wow!  after 6 months, I've finally got it to work.

But now I need to tweak it.

I want all 4 monitors to act as one large entire desktop so I can easily drag anything across all monitors as simply as it works in XP Pro.

Right now everything as as 2 different sets of monitors.  

I can scroll the mouse over all monitors as one, (even though they arent in the right order) but I cant drag programs over to the 2 new monitors with out the original 2 twisting the desktop to a new workspace.

Now I should say I am running compiz fusion, so I think maybe I know have to get the newest 2 monitors on that also?

---

### Post by fooman on 2009-08-15
> **PsychedelicWonders said:**
> 

I can scroll the mouse over all monitors as one, (even though they arent in the right order) but I cant drag programs over to the 2 new monitors with out the original 2 twisting the desktop to a new workspace.


good luck with that.  i have not been able to drag anything from one screen to the other since hardy,  it has been a no-go with intrepid and jaunty.

i can only open apps on screen 2 if i first open a terminal there,  then type the command to start it.  if i try to open an app on screen 2 using the menus...it always opens on screen 1.  :(

i have installed "nautilus-open-terminal" so that i can right-click on screen 2 and choose "open in terminal" from the context menu.  then when the terminal opens,  type the command to start the app there....it was much easier when i could just drags things back and forth.  :confused:

---

### Post by Johnny B on 2009-08-15
you guys are using 'twinview' and not 'seperate X screen' right?

---

### Post by fooman on 2009-08-15
> **Johnny B said:**
> you guys are using 'twinview' and not 'seperate X screen' right?

...i was referring to separate x-screen myself.

---

### Post by PsychedelicWonders on 2009-08-15
Yes I have everything on twinview right now.

Does anyone have any suggestions or a direction they can point me in?

Is what I want to do even possible?

I am running 8.XX not 9.XX. I know you have to run 8.XX in order to get Compiz Fusion to work properly.  It wont on 9.XX.

---

### Post by fooman on 2009-08-15
compiz-fusion works great for me running jauny 9.04.

its just the dragging things from one screen to another and opening apps from the menus on screen 2 which do not work.

they used to work fine in hardy (8.04),  but both intrepid (8.10) and jaunty refuse to do it for me.

doesn't matter as far as compiz goes....even if i turn off/disable compiz,  i still cannot drag from screen to screen or open anything via the menus on #2 (they will always open on #1).

---

### Post by PsychedelicWonders on 2009-08-16
[http://ubuntuforums.org/showthread.php?t=884161](http://ubuntuforums.org/showthread.php?t=884161)

Watch the video in the first post of that thread.

Its possible to do.  I'm hopping in that thread...

---

### Post by scouser73 on 2009-08-16
I think that you need to set the position to **Absolute** in order to have one desktop spread over the four monitors. I am using Twinview and the position is set to Absolute, with this, I am able to drag across both screens, acting as one large desktop.

I really like your set up, absolutely brilliant.

---

### Post by PsychedelicWonders on 2009-08-16
> **scouser73 said:**
> I think that you need to set the position to **Absolute** in order to have one desktop spread over the four monitors. I am using Twinview and the position is set to Absolute, with this, I am able to drag across both screens, acting as one large desktop.

I really like your set up, absolutely brilliant.

Youre saying they all need to be set to absolute?

Thanks, the setup really works well.  I'm able to use the main three 19" dell monitors for whatever kind of weird stuff/work I'm doing.  Then I keep the 46" Samsung 750 for presentations when people come over, or to let my kid watch movies off the internet while I work.  I dont even have cable.

The Dell's arent anything special and was able to pick up all 3 over a period of time for $275 used, but in perfect shape.  Once budget allows, I will upgrade the 3 to something really impressive.  The 750 doesnt get much better.

This is the stand I want to use for my main 3:

[http://www.9xmedia.com/products/x-top/X-Top-multi-screen.php](http://www.9xmedia.com/products/x-top/X-Top-multi-screen.php)

I was about a month away from buying it for $950 from them, but I got fired a couple of weeks ago.

---

### Post by scouser73 on 2009-08-16
I'm pleased that you managed to sort it, and what a picture you posted. I'd love a set up like that, sorry to hear about the job front too, hope something turns up for you soon mate.

---

### Post by PsychedelicWonders on 2009-08-16
Well I only got the cards activated, I dont have everything worked out.

They arent in the right position & doesnt act as one giant desktop, but 2 when in Ubuntu.

You're seeing a picture from Windows.

---

### Post by PsychedelicWonders on 2009-08-16
Ok making some serious progress.

Now all screens are in alignment and I can drag a program from one end to the other no problem.

But I dont think compiz fusion is active because I cant flip workspace.  I went into system>preferences>compizconfig settings manager

Everything is still checked, but it doesnt seem active?  How do I activate it?

Also programs & tool bars seem to share screens, making it very awkward.  How do I make stuff like that work on 1 screen vs splitting itself between 2?

I dont know if it matter, but I got this error message:

Also what is pretty cool now is that screen saver Helios finally plays on all 4 monitors, something it CANT do in windows.

---

### Post by scouser73 on 2009-08-16
What I did was to apply the settings in the X server settings, and see how it looked, there was a problem where my dock would be on one monitor and a panel on the other. To rectify it, I canceled that setup before the timer ended, and I tried again and it worked.

Also, I checked to see whether **Allow Flipping**, under the **OpenGL Settings** was checked.

---

### Post by PsychedelicWonders on 2009-08-16
> **scouser73 said:**
> What I did was to apply the settings in the X server settings, and see how it looked, there was a problem where my dock would be on one monitor and a panel on the other. To rectify it, I canceled that setup before the timer ended, and I tried again and it worked.

Also, I checked to see whether **Allow Flipping**, under the **OpenGL Settings** was checked.

Hmm.  I dont know if that will fix it for me.  I've restarted a few times.

See in windows, even though its one large desktop, each monitor acts as its own.  Its nice so I can easily maximize programs to certain monitors & can also have the background show up on each monitor instead of trying to do all 4.  (And I dont have it on stretch either)

What/where is OpenGL Settings?

---

### Post by lessgov2007 on 2009-08-16
4 monitors? No problem. Just get three mirrors angle them correctly, add a little imagination, and no need to make any configuration changes! I'm the Ubuntu expert! hahahahaa 

No really, 4 panels would kick blank blankity blank blank blank.

---

### Post by scouser73 on 2009-08-16
> **lessgov2007 said:**
> 4 monitors? No problem. Just get three mirrors angle them correctly, add a little imagination, and no need to make any configuration changes! I'm the Ubuntu expert! hahahahaa 

No really, 4 panels would kick blank blankity blank blank blank.

That's not really helpful.

---

### Post by Rrasyrogenees on 2009-08-16
i only have two monitors (both 24" widescreen) set up in twinview but they do have that flip to another work station.  i remember that when i set it up they are in absolute and the second one i gave "to the left" of my main.  and i remember also that i had to do it all from terminal in root or at least sudo to open the nvidia-settings or it wouldn't save it.  i can't imagine that you can't do to your setup what you want... i just not sure how yet...

   that is an interesting setup and hadn't gotten past thinking about a third but i don't really have use for more than one but i did two anyway and having fun making panoramic wallpapers for it too... gives me a 3840x1080 resolution to work with (since they are 1920x1080 screens to start with).  these pix are of a background i put together (dragons) and one i found online that was already 3840x1080 (scenic view).

  i also can make panoramic views of pictures i take using Hugin panorama creator which i got from "applications".  that is what i have on the third picture... i used about five photos and Hugin put it together for me.

i'll wait to see what you can do with yours... :P

---

### Post by PsychedelicWonders on 2009-08-17
> **Rrasyrogenees said:**
> i only have two monitors (both 24" widescreen) set up in twinview but they do have that flip to another work station.  i remember that when i set it up they are in absolute and the second one i gave "to the left" of my main.  and i remember also that i had to do it all from terminal in root or at least sudo to open the nvidia-settings or it wouldn't save it.  i can't imagine that you can't do to your setup what you want... i just not sure how yet...

   that is an interesting setup and hadn't gotten past thinking about a third but i don't really have use for more than one but i did two anyway and having fun making panoramic wallpapers for it too... gives me a 3840x1080 resolution to work with (since they are 1920x1080 screens to start with).  these pix are of a background i put together (dragons) and one i found online that was already 3840x1080 (scenic view).

  i also can make panoramic views of pictures i take using Hugin panorama creator which i got from "applications".  that is what i have on the third picture... i used about five photos and Hugin put it together for me.

i'll wait to see what you can do with yours... :P

Youre right, now that I think about it, it wont give me the 3D cube with out designating the monitors left or right, it wont know which way to turn?

Any other suggestions?

How do I re-activate Compiz/Fusion to get my 3D cube effects back?

---

### Post by scouser73 on 2009-08-18
Hi, visit this tutorial for setting CompizConfick back up: [[COLOR="Red"]**Compiz Config Tutorial**[/COLOR]]("http://www.ghacks.net/2009/07/30/configuring-the-appearance-of-the-compiz-cube/comment-page-1/#comment-859972/")

---

### Post by PsychedelicWonders on 2009-08-19
Ok so I took everything off of twin view & put it into Separatae X screen with Xinerama enabled & I am able to drag all programs from one monitor to the next.

Now when I maximize a particular program, it will only expand to the particular monitor it is on, not stretch to both of them like it did with twinview.

But for some reason, I still cant get my background on all 4 monitors.

Right now I just have it centered & it is only on 2 monitors and broken up...  I want the logo to be a background on every single monitor, centered on that monitor. 

How do I do that?  It happens in windows easily.

---

### Post by scouser73 on 2009-08-19
Look under **System > Preferences > Appearance > Background** tab and check that **Style** is set to **Fill Screen**.

---

