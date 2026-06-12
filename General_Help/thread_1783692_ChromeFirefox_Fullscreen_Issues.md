---
title: "Chrome/Firefox Fullscreen Issues"
date: 2011-06-16
forum: General Help
---

### Post by arukaddp on 2011-06-16
Hi guys,

Since this morning I noticed the following problem on my Natty install. 
When I hit F11 to go fullscreen in either Chrome or FF there is a top 'bar' left, that is empty and you can see through. I don't know if this is clear, probably why I could not find anything on Google. You can see in the attached screenshot. The height of the bar seems to be the same as the window decoration bar.

I use Compiz, Ubuntu Tweak and Compiz/Fusion, and if I select 'Metacity' Window Manager in Fusion, the problem seems to go away, but I lose all of Compiz' nice and shiny utilities. Reloading the Window manager has no effect whatsoever. 
Again this is a recent development as yesterday it was working fine!
EDIT: I don't use Unity, I am running Ubuntu Classic with AWN that replaces Gnome shell completely.
Thank you in advance guys!

---

### Post by wildmanne39 on 2011-06-16
> **arukaddp said:**
> Hi guys,

Since this morning I noticed the following problem on my Natty install. 
When I hit F11 to go fullscreen in either Chrome or FF there is a top 'bar' left, that is empty and you can see through. I don't know if this is clear, probably why I could not find anything on Google. You can see in the attached screenshot. The height of the bar seems to be the same as the window decoration bar.

I use Compiz, Ubuntu Tweak and Compiz/Fusion, and if I select 'Metacity' Window Manager in Fusion, the problem seems to go away, but I lose all of Compiz' nice and shiny utilities. Reloading the Window manager has no effect whatsoever. 
Again this is a recent development as yesterday it was working fine!
EDIT: I don't use Unity, I am running Ubuntu Classic with AWN that replaces Gnome shell completely.
Thank you in advance guys!
Hi, I believe it is because compiz had to be set up in a special way to work in natty as far as effects go. You can use this guide if you want to setup compiz with effects. Hi, To get the cube working in natty use this link.
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)
after you have finished with this guide and you change other settings it will mess up your windows again so just log out and back in and they will be fixed. I know you did not ask about the cube but the instruction in here are basically for any adjustments that you make to compiz.

---

### Post by arukaddp on 2011-06-16
> **wildmanne39 said:**
> Hi, I believe it is because compiz had to be set up in a special way to work in natty as far as effects go. You can use this guide if you want to setup compiz with effects. Hi, To get the cube working in natty use this link.
[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)
after you have finished with this guide and you change other settings it will mess up your windows again so just log out and back in and they will be fixed. I know you did not ask about the cube but the instruction in here are basically for any adjustments that you make to compiz.

Hi wildmanne39, thank you for your input!
I have tried the enabling/disabling of the plugins as suggested in your link, and after the gdm restart the problem seem to be gone. However after a reboot it was back, also I seem to be missing the 'Move to workspace right/left/etc' options from the alt+space menu. This though seems to repair itself when using the Desktop wall shortcuts ctrl+alt+shift+arrows to move the windows across the workspaces.

I suspect that I might have something, that overwrites something on boot... as a last resort do you think the compiz reset how-to in your sig could be an option?

---

### Post by wildmanne39 on 2011-06-16
> **arukaddp said:**
> Hi wildmanne39, thank you for your input!
I have tried the enabling/disabling of the plugins as suggested in your link, and after the gdm restart the problem seem to be gone. However after a reboot it was back, also I seem to be missing the 'Move to workspace right/left/etc' options from the alt+space menu. This though seems to repair itself when using the Desktop wall shortcuts ctrl+alt+shift+arrows to move the windows across the workspaces.

I suspect that I might have something, that overwrites something on boot... as a last resort do you think the compiz reset how-to in your sig could be an option?
HI, I am not sure if resetting compiz will help,but it might, are you still using the ubuntu classic? What video card do you have? metacity may be interfering with compiz, if it is not shutting down completely, I just have compiz and did not install metacity. Also a lot of people have had problems like your's and creating a new user account fixing the problem, the reason that works is because of some settings that have been changed are default again. It could not hurt to reset compiz and might reset unity too. If you update and updates intalled a new driver for your video card that is mostly the problem. Also when you see the top bar missing try f11 to see if it will come back.

---

### Post by arukaddp on 2011-06-16
Well F11 is not doing anything right, because when I hit F11 to go to fullscreen, that is when the bar disappears.

I have done the following:
reset compiz = no effect
unistalled compiz completely (including unity) + reinstalled compiz (w/o unity) = no effect

I have a K52F laptop with an Intel video card. 
lshw lists this:
```

  *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 12
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:41 memory:d0000000-d03fffff memory:c0000000-cfffffff
 ioport:e080(size=8)

```

---

### Post by arukaddp on 2011-06-16
Well, being the persistent and 'not afraid to break it all into pieces' SOB that I am, after I broke and fixed everything I found the problem, and for sure it was right in my face.

Apparently something is messing up the window decoration for Chrome and Firefox. I haven't found the what but I have found a solution for Chrome.

In Chrome > Preferences > Personal Stuff > Appearance there is a 'Hide system title bar and use compact borders' which actually kills the compiz window decorator for Chrome.

Now you are going to say that you can use Compiz Settings and modify window decorations to say 
```
(any) & !(name=google-chrome)
``` and exclude google-chrome from compiz, but that will also leave without any controls like close/max/min. 

The option in Chrome will actually put in its own replacing buttons. Actually this will also be useful for people that want to maximize the viewing area of Chrome as the tabs will be on the bar.

I could not find a similar option for Firefox though.

I also tried a new user, but the problem is persistent!

For now I will mark the thread solved!

---

### Post by Francewhoa on 2012-08-23
Easier fix at [http://ubuntuforums.org/showthread.php?p=12192047#post12192047](http://ubuntuforums.org/showthread.php?p=12192047#post12192047)

---

### Post by overdrank on 2012-08-23
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

