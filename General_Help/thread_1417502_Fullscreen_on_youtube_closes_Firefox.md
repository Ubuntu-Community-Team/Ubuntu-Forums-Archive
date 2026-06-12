---
title: "Fullscreen on youtube closes Firefox"
date: 2010-02-27
forum: General Help
---

### Post by pingu1 on 2010-02-27
Hi!
I've read all the posts concerning this subject, but haven't gotten a solution.
I did a system-update, and switched to gnome in "appearance"-settings, but I do not know exactly what caused this error.

Anyone know what to do?

---

### Post by Vaphell on 2010-02-27
run firefox from terminal and make it go down. Check terminal for error message.

---

### Post by pingu1 on 2010-02-27
I am a newbie... so please tell me exactly how to do that?

---

### Post by linuxman94 on 2010-02-27
Open a terminal window by going to Applications -> Accessories -> Terminal.  Type in firefox and hit enter.

Try starting firefox in safe mode by typing firefox -safe-mode and see if you still have the problem.

---

### Post by pingu1 on 2010-02-27
ok... embarassed

---

### Post by lovinglinux on 2010-02-27
Check if you have the latest Adobe plugin instead of swfdec or gnash.

For 32bit see [this](http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2).

For 64bit see [this](http://ubuntuforums.org/showthread.php?t=1358591).

You can also remove any conflicting plugins and install the appropriate version of flash with an [automated installer created by carlee](http://ubuntuforums.org/showthread.php?t=1414595).

For additional tips and instructions see the [COLOR="Sienna"]**Flash Optimization**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by pingu1 on 2010-02-27
I ran the command in the terminal, and then shut Firefox down (using the X) - no errormessages in terminal...

---

### Post by linuxman94 on 2010-02-27
Did you try safe mode?

---

### Post by pingu1 on 2010-02-27
I have not tried that yet, I just finished doing this one:
Code:
 sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get install flashplugin-nonfree


Hoping maybe that did the trick.... gonna test now...

---

### Post by pingu1 on 2010-02-27
Didn't work.... :(

---

### Post by pingu1 on 2010-02-27
I see a lot of people suffer from this error - and it seems it has something to do with the system-update I did earlier today... I didn't notice the error until about an hour after the update....
Is there something I can downgrade to the previous version to get rid of this problem?

I got a new kernel today also....
> home@home-laptop:~$ uname -a
Linux home-laptop 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux


---

### Post by lovinglinux on 2010-02-27
> **pingu1 said:**
> Didn't work.... :(

Did you restart Firefox before testing?

---

### Post by pingu1 on 2010-02-27
Could it be that the new kernelupdate screwed with the relation between the OS and my graphics-card? (ATI)

---

### Post by pingu1 on 2010-02-27
I restarted Firefox yes....

---

### Post by lovinglinux on 2010-02-27
> **pingu1 said:**
> Could it be that the new kernelupdate screwed with the relation between the OS and my graphics-card? (ATI)

I don't know, but you could try to reboot and use the older kernel. It should be available in the grub list.

---

### Post by pingu1 on 2010-02-27
how do I do that? Do I restart and choose a kernel after pressing some "magic" key during the restart?

---

### Post by warp99 on 2010-02-27
Then this is an issue with Adobe. If may be accelerated graphics that are giving you a problem. With a Flash video playing in a normal window right mouse click and un-check accelerated graphics.

---

### Post by linuxman94 on 2010-02-27
When it says "Grub loading..." press escape and select a different kernal.

---

### Post by pingu1 on 2010-02-27
Thank you. I unchecked "enable graphics acceleration", but then the fullscreenvideo sucks major....

It's lagging, and all scribbly.... not worth viewing in full screen now really....

But now we know what the problem was? Is it my graphics card, or the flashplugin?

---

### Post by pingu1 on 2010-02-27
I chose "copy debugging info" while on youtube:
> el=detailpage&fexp=901903&smoothing=1&w=483&nsiabbl=968&nsidf=14&debug%5FvideoId=N7IE%5FdXoicA&debug%5FsourceData=BADC20648HH&sd=BADC20648HH&nsivbbl=18155&debug%5FplaybackQuality=medium&nsiabl=2%2E02&nsivbl=2%2E636&debug%5FflashVersion=LNX%2010%2C0%2C45%2C2&md=1&h=360&debug%5Fdate=Sat%20Feb%2027%2020%3A20%3A18%20GMT%2B0100%202010&plid=AASAmedzzujDLcaQ&csipt=watch&hl=en%5FUS&cfps=0&cr=US&vh=240&scoville=1&vw=322&pd=0%2E39400000000000013&fmt=34&vid=SuNlKsk6JG7uNbVCUMWLWhOxVjrrx%5F5EC

---

### Post by pingu1 on 2010-02-27
I tried to switch to an older kernel by hitting ESC during restart (grub loading) - but nothing happened - it booted the OS as normal... no options came up, just normal start....

---

### Post by warp99 on 2010-02-27
> **pingu1 said:**
> But now we know what the problem was? Is it my graphics card, or the flashplugin?

It's the Flash plugin since it's trying to use the GPU instead of the CPU. You could try the Adobe beta which seems to work better. All you need to do is replace the file libflashplayer.so in the directory /usr/lib/adobe-flashplugin/ with the beta. Download the beta here:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)


It's pretty simple simple. First download the file, then start a nautilus session as root:

```
gksudo nautilus
```

Untar the download file with a right mouse click and choose "Open with Archive Manager", then copy the file to the directory above. If it isn't better just re-install the adobe-flash package to go back to same as before.

---

### Post by pingu1 on 2010-02-27
Could someone please hint to where the problem lies? Is it the Adobe flash - or my graphics card? Or the kernel? My updates? What's the deal?

---

### Post by _khAttAm_ on 2010-02-27
> **pingu1 said:**
> I tried to switch to an older kernel by hitting ESC during restart (grub loading) - but nothing happened - it booted the OS as normal... no options came up, just normal start....

Hold on <shift> to get the choices.

---

### Post by pingu1 on 2010-02-27
> **warp99 said:**
> It's the Flash plugin since it's trying to use the GPU instead of the CPU. You could try the Adobe beta which seems to work better. All you need to do is replace the file libflashplayer.so in the directory /usr/lib/adobe-flashplugin/ with the beta. Download the beta here:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)


It's pretty simple simple. First download the file, then start a nautilus session as root:

```
gksudo nautilus
```Untar the download file with a right mouse click and choose "Open with Archive Manger", then copy the file to the directory above. If it isn't better just re-install the adobe-flash package to go back to same as before.

I followed your instructions, and replaced the file with opening nautilus as root - but still the problem is there.... horrible graphics during fullscreen... I have not, however, reinstalled the adobe-flash plugin.... (i'm guessing in synaptics?)

---

### Post by warp99 on 2010-02-27
> **pingu1 said:**
> I followed your instructions, and replaced the file with opening nautilus as root - but still the problem is there.... horrible graphics during fullscreen... I have not, however, reinstalled the adobe-flash plugin.... (i'm guessing in synaptics?)

You have to turn the accelerated graphics back on to test it. :wink:

---

### Post by pingu1 on 2010-02-27
The adobe flash plugin just gave me the fullscreentrouble again.... :(

---

### Post by pingu1 on 2010-02-27
I turned on the acceleration again.... like you said - still bad.... (I did not forget)

---

### Post by warp99 on 2010-02-27
You could try switching to an older kernel. Let's set up your computer so the menu appears to make this easier:

Open a terminal and run the following:

```
gksudo gedit /etc/default/grub
```

and change this line:

```
GRUB_HIDDEN_TIMEOUT_QUIET=true
```

to this:

```
GRUB_HIDDEN_TIMEOUT_QUIET=false
```

If you like you can change the timeout on the next line from 5 seconds till you press any key to a higher number like 7 or 10 seconds. Save the file and run the following command:

```
sudo update-grub
```

Then reboot and you will be presented with a menu. Just choose a kernel that is one version older, which should be the third line.

---

### Post by pingu1 on 2010-02-27
I would like to know the "hard way" to change kernels during reboot, please...
I want to learn...

---

### Post by warp99 on 2010-02-27
I have all my machines setup with the menu showing because it's a lot easier than trying to hit the shift and escape key before the hidden menu times out. You can customize the menu with some graphics to make it look pretty spiffy at a later date.

---

### Post by pingu1 on 2010-02-27
But, if I have now returned to the previous version (the beta) - and that did not solve it - is the problem still the flash-player/codec/driver? I mean - would that not exclude flash as the culprit?

---

### Post by pingu1 on 2010-02-27
I'm back to where I was, I have removed everything in synaptics that relates to flash - and reinstalled the main (ubuntu-recommended version) version of flash, and now the problem _again_ of course is Firefox closing when trying to view fullscreen. Is this something that the programmers know about (fullscreenproblem)? Will this be solved at some point?

---

### Post by warp99 on 2010-02-27
No it's Adobe fault because trying to use the ATI GPU shouldn't cause a fatal exception. The plugin should fall over gracefully and use software rendering instead. This is how it's described in the Adobe Flashplayer Administration Guide:

[http://www.adobe.com/devnet/flashplayer/articles/flash_player_admin_guide.html](http://www.adobe.com/devnet/flashplayer/articles/flash_player_admin_guide.html)

Now there may be an issue with the proprietary drivers and Adobe's interaction, but Adobe does have the ATI specifications. Adobe treats Linux and even OS X as second class citizens with respect to Flash player.

---

### Post by pingu1 on 2010-02-27
okay... well I generally don't use flash at all, except youtube... so it's no crisis for me, but it still sucks... I dislike having an OS, with lack of functionality because they publish bad flash-versions and so on. I love Ubuntu. It's fast, very intuitive (when doing the basics), and great in every way. It's a shame the softwareprogrammers/hardwaremakers don't cooperate in making stuff work in Ubuntu/Linux as well as windows/mac. it's all about money...

---

### Post by warp99 on 2010-02-27
Best thing is to put in a bug report over at Adobe so at least they have knowledge of the problem. In the meantime if you want fullscreen use the Compiz zoom plugin. I did this for a while when Adobe had some serious issues with nVidia and fullscreen performance. The quality was no different since flash is pretty poor to begin with.

---

### Post by pingu1 on 2010-02-27
Is there no way I can revert to the old software? The old working version, now that I got the new, bad one? Is it the kernel-change that has narrowed down my choices?

---

### Post by warp99 on 2010-02-27
> **pingu1 said:**
> Is it the kernel-change that has narrowed down my choices?

At this point the answer is yes. Since both the drivers and the flash player are proprietary with no access to the source code we have to sit around and waiting for a solution from the vendors.

---

### Post by pingu1 on 2010-02-28
Thank you very much for very useful information and help.
Hope it gets solved in the near future....

---

### Post by warp99 on 2010-02-28
You could try to rebuild the modules for the kernel and see if this helps. Open a terminal and issue the following:

```
sudo dpkg-reconfigure fglrx-kernel-source
```

---

### Post by pingu1 on 2010-02-28
I have done it in the terminal now - hope it solves it...

---

### Post by pingu1 on 2010-02-28
Didn't help.... it was successful in rebuilding/reconfiguring - but still - didn't solve it...
Thanks anyway....

---

### Post by pingu1 on 2010-02-28
But could you explain me this:
Does the hw-drivers lie in the kernel? Is kernel synonymous with drivers?

I thought the kernel was the bridge between the OS and the hardware - does this in fact basically mean "drivers" for the hardware - so that the OS can communicate with the hardware?

---

### Post by warp99 on 2010-02-28
What you just build was the actual driver, in Linux it's known as a module. It may say fglrx-kernel-"source", but there are binary components included. 

Anyway to expand on your analogy if the kernel is the bridge then modules are the trusses. Some are included within the kernel itself while others are build outside of the kernel.

---

### Post by Monotoko on 2010-02-28
If all you use flash for is Youtube...you could try the HTML5 beta?
[http://www.youtube.com/html5](http://www.youtube.com/html5)

You'd need Google Chrome though

---

### Post by pingu1 on 2010-03-01
Okay, so some drivers lie outside the kernel, but the kernel is the layer using them to communicate with the hardware. In other words - the OS communicates with the HW via the kernel no matter where the drivers lie....?

---

### Post by warp99 on 2010-03-02
> **pingu1 said:**
> Okay, so some drivers lie outside the kernel, but the kernel is the layer using them to communicate with the hardware. In other words - the OS communicates with the HW via the kernel no matter where the drivers lie....?

Correct. ;)

---

### Post by pingu1 on 2010-03-06
I solved my fullscreen-problem by following an informative site 
> [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I guess it was just in need of the "open source" driver. I think I have been fiddling around too much with the drivers and OPENgl and so on that it made linux "dizzy".
I just followed the procedure as laid out in the link above - and then - NO closing Firefox _and_ I got compiz running.....

---

