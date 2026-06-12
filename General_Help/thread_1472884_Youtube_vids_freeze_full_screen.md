---
title: "Youtube vids freeze full screen?"
date: 2010-05-04
forum: General Help
---

### Post by bigsmitty64 on 2010-05-04
If I watch a full screen video in youtube, it plays fine, UNLESS...I move my mouse at all, then it freezes. This only happens "fullscreen" at ANY setting (360, 480, 720, 1080).
I am running 64 bit Lucid, with the restricted extras. And an nVidia 9400gt graphics card. I'm thinking its got to be something to do with flash because other sites, (stage-vu.com) that don't use flash, I'm o.k. Any help is greatly appreciated. Thanks,
Smitty

P.S. Running Firefox 3.6.3 Have NOT tried other browsers yet.

---

### Post by cuberts on 2010-05-04
> **bigsmitty64 said:**
> If I watch a full screen video in youtube, it plays fine, UNLESS...I move my mouse at all, then it freezes. This only happens "fullscreen" at ANY setting (360, 480, 720, 1080).
I am running 64 bit Lucid, with the restricted extras. And an nVidia 9400gt graphics card. I'm thinking its got to be something to do with flash because other sites, (stage-vu.com) that don't use flash, I'm o.k. Any help is greatly appreciated. Thanks,
Smitty

P.S. Running Firefox 3.6.3 Have NOT tried other browsers yet.Yes, that has also happened to me in windows. Try getting the newest version of the adobe plugin from the ubuntu soft ware center:
Applications> Ubuntu software center

---

### Post by bigsmitty64 on 2010-05-04
I already tried that and it didn't help with my situation :(

---

### Post by bigsmitty64 on 2010-05-04
Just tried [THIS]("http://www.sucka.net/2010/04/proper-install-of-flash-for-x64-ubuntu/") with no success.

---

### Post by lovinglinux on 2010-05-05
See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Get the 64bit version with one of the tools liked there, so they remove previous versions correctly.

---

### Post by bigsmitty64 on 2010-05-16
So...nothing seems to fix this particular situation yet. One thing to add. 

I have learned that if I let the video load, then go to  /temp folder and view the video (it's still a flash video right?) and view it with vlc or mplayer it works fine. It only is happening in the browser (s) Firefox and Chromium.

Side note: I recently installed a 32 bit version of Lucid on another drive. Same problem.

---

### Post by lovinglinux on 2010-05-16
Disable compiz and check if the problem persists.

---

### Post by bigsmitty64 on 2010-05-16
> **lovinglinux said:**
> Disable compiz and check if the problem persists.

Nope, it didn't help, thanks for that suggestion though, I hadn't thought of that.

---

### Post by mordecai83 on 2010-05-16
I use the latest flash in lucid 64 and it happens to me too, i think its attributable to flash (still in beta). So nothing to do about it except wait till adobe fixes it i think.

---

### Post by gnik1 on 2010-05-16
For me, I couldn't hit the play button for flash video embedded in websites until I found a post that says I can hold down the right click and then left click on the play button.

That worked for me.

You could try these helpful links:

[http://ubuntuforums.org/showpost.php?p=8666948&postcount=72](http://ubuntuforums.org/showpost.php?p=8666948&postcount=72)

[http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

[http://ubuntuforums.org/showthread.php?t=1414595](http://ubuntuforums.org/showthread.php?t=1414595)

[http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

Good Luck

---

### Post by bigsmitty64 on 2010-05-16
> **gnik1 said:**
> 

[http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)



I found a great workaround at the very bottom of the page at this link, its a greasemonkey script that  allows viewing without flash, so thanks for that!  At least I can watch full screen vids now.

---

### Post by gnik1 on 2010-05-16
You're welcome I'm glad it worked.

For me, the one that worked fully were the directions from this link:

[http://ubuntuforums.org/showthread.php?t=1423423&highlight=64+bit+flash](http://ubuntuforums.org/showthread.php?t=1423423&highlight=64+bit+flash)

Flawless.

---

### Post by bigsmitty64 on 2010-06-01
UPDATE:
I had to remove that greasemonkey script because it caused it's own problems, now I went back to my original problem. SO, today I wiped my drive and did a fresh install of  **32 bit Lucid** and I have the same problem.

It seems to **ONLY** be youtube. **FULL SCREEN** is terribly choppy. I can watch hd vids on there no problem, as long as I don't go full screen.

Again, this is not a problem on any other sites, google vids, cnn vids, are all fine at full screen.


So to recap:
Full screen total lag/choppy/non responsive.
Only youtube @ full screen
32 AND 64 bit same problem
I'm using flashplugin-installer  from synaptic

Thanks in advance for any help/ideas

---

### Post by lovinglinux on 2010-06-01
> **bigsmitty64 said:**
> UPDATE:
I had to remove that greasemonkey script because it caused it's own problems, now I went back to my original problem. SO, today I wiped my drive and did a fresh install of  **32 bit Lucid** and I have the same problem.

It seems to **ONLY** be youtube. **FULL SCREEN** is terribly choppy. I can watch hd vids on there no problem, as long as I don't go full screen.

Again, this is not a problem on any other sites, google vids, cnn vids, are all fine at full screen.


So to recap:
Full screen total lag/choppy/non responsive.
Only youtube @ full screen
32 AND 64 bit same problem
I'm using flashplugin-installer  from synaptic

Thanks in advance for any help/ideas

Install [FlashVideoReplacer](http://flvideoreplacer-extension.blogspot.com). It is a Firefox extension that does the same job of that greasemonkey script, but support more sites. I'm currently working on adding more sites to the supported list, but YouTube already works (except for channels).

---

### Post by bigsmitty64 on 2010-06-01
> **lovinglinux said:**
> Install [FlashVideoReplacer]("http://flvideoreplacer-extension.blogspot.com"). It is a Firefox extension that does the same job of that greasemonkey script, but support more sites. I'm currently working on adding more sites to the supported list, but YouTube already works (except for channels).

Unfortunately, that didn't help. All I got after installing that was a white screen where the  vid should be. :)

This is happening in Chrome browser also by the way.

---

### Post by lovinglinux on 2010-06-02
> **bigsmitty64 said:**
> Unfortunately, that didn't help. All I got after installing that was a white screen where the  vid should be. :)

This is happening in Chrome browser also by the way.

Is not the extension fault, otherwise it wouldn't occur on Chrome. So you have a flash issue. Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by bigsmitty64 on 2010-06-02
@lovinglinux
First, I truly appreciate all your time and effort here. Unfortunately, that didn't help either. This is weird. 

I took the drastic route of reinstalling Lucid, this time going with 32 bit. I STILL have this problem. It's definately only on youtube, and ONLY in full screen. I installed that last plugin you suggested again in the new install too. So so frustrating ! 
Again, thank you for your help!

---

### Post by lovinglinux on 2010-06-02
> **bigsmitty64 said:**
> @lovinglinux
First, I truly appreciate all your time and effort here. Unfortunately, that didn't help either. This is weird. 

I took the drastic route of reinstalling Lucid, this time going with 32 bit. I STILL have this problem. It's definately only on youtube, and ONLY in full screen. I installed that last plugin you suggested again in the new install too. So so frustrating ! 
Again, thank you for your help!

Could you please post a screenshot of an YouTube video not in fullscreen?

---

### Post by bigsmitty64 on 2010-06-02
I also included a shot of my plugins (not many, as this is a brand new install)

---

### Post by lovinglinux on 2010-06-02
> **bigsmitty64 said:**
> I also included a shot of my plugins (not many, as this is a brand new install)

Have you tried FlashVideoReplacer after the clean install of Ubuntu?

---

### Post by bigsmitty64 on 2010-06-02
Hahaha, now I don't remember when I tried what! I BELIEVE I did, should I try again? And if so , should I remove the FLASH AID first?

---

### Post by bigsmitty64 on 2010-06-02
Actually, I know I did try it, because I removed it after I installed the latest one you gave me.

---

### Post by bigsmitty64 on 2010-06-02
Also, I have this in plugins, just thought I'd mention it :)

---

### Post by lovinglinux on 2010-06-02
> **bigsmitty64 said:**
> Hahaha, now I don't remember when I tried what! I BELIEVE I did, should I try again? And if so , should I remove the FLASH AID first?

No you can have both. FLASH-AID is just an installation tool, it doesn't interact with any web site.

---

### Post by bigsmitty64 on 2010-06-02
Nothing seems to be working here :(

---

### Post by lovinglinux on 2010-06-02
> **bigsmitty64 said:**
> Nothing seems to be working here :(

I out of ideas. It should be working, since your flash plugin is working.

Click the FlashVideoReplacer icon in the status bar while viewing an YouTube video and then untick the YouTube option from the extension dialog. It should reload the video using flash. Then tick again. It should reload the video again, but this time with totem plugin.

Tell me what happens when you do that. Does it reload the video but totem plugin doesn't show up or doesn't it reload the video at all?

---

### Post by bigsmitty64 on 2010-06-02
O.K. Step in the right direction. THAT gives me my full screen without freezes!  
BUT, I now have no controls in the video. As in volume/pause/length of video.  They are gone. *sigh*

**EDIT: Firefox keeps crashing now, as in,shuts down completely while in youtube :(  **

---

### Post by lovinglinux on 2010-06-02
> **bigsmitty64 said:**
> O.K. Step in the right direction. THAT gives me my full screen without freezes!  

THAT what? Please be more specific about what you are doing, otherwise is hard to keep track of things. I'm replying to several flash threads simultaneously and every time I need to go back and read a couple of posts to understand what is going on in each case.

---

### Post by lovinglinux on 2010-06-02
I guess I understand what happened. You are using a plugin which has no controls. I recommend using gecko-mediaplayer.

Do this:

```
sudo apt-get purge totem-mozilla
```

```
sudo apt-get purge mozilla-plugin-vlc
```

```
sudo apt-get install gecko-mediaplayer
```

Then restart Firefox and try again.

---

### Post by bigsmitty64 on 2010-06-02
> **lovinglinux said:**
> I out of ideas. It should be working, since your flash plugin is working.

Click the FlashVideoReplacer icon in the status bar while viewing an YouTube video and then untick the YouTube option from the extension dialog. It should reload the video using flash. Then tick again. It should reload the video again, but this time with totem plugin.


Sorry bout that, what you said here, worked but now I have no controls in youtube AND firefox keeps crashing every time I'm watching a video.

---

### Post by dodo3773 on 2010-06-02
O.K. here is what I did. I read this on this blog 

[http://blog.killtheradio.net/technology/slow-flash-in-ubuntu/](http://blog.killtheradio.net/technology/slow-flash-in-ubuntu/)

What I did was right click on any flash video, go down to settings, and uncheck the box that says enable hardware acceleration. Then open a terminal and type

 
sudo mkdir /etc/adobe

sudo su

sudo echo "OverrideGPUValidation = 1" >> /etc/adobe/mms.cfg


I added the sudo su as the second command because I was getting a permission denied error.

After that I re-enabled hardware acceleration, closed firefox, then opened it back up. I have not experienced that problem again.
I hope that helps you.

---

### Post by bigsmitty64 on 2010-06-02
@ lovinglinux
We are closer and closer to calling this one solved! Using the  gecko-mediaplayer as you suggested is great, the only thing I can see that isn't working is the ability to change the rez in youtube ya know? 360/480/720. Thats not showing up in a vid I know has the options. I can almost live with this though. We've come a long way and I thank you VERY much!

---

### Post by lovinglinux on 2010-06-02
> **bigsmitty64 said:**
> @ lovinglinux
We are closer and closer to calling this one solved! Using the  gecko-mediaplayer as you suggested is great, the only thing I can see that isn't working is the ability to change the rez in youtube ya know? 360/480/720. Thats not showing up in a vid I know has the options. I can almost live with this though. We've come a long way and I thank you VERY much!

There is no such option in the plugin, only in flash. What the extension does is determine the best available video source according to quality option selected by you. Click the FlashVideoReplacer icon again and change the option next to YouTube selection box, where it says HIGH. Since YouTube can have multiple resolutions and not all of them are available to all videos, I decided to make it simple and offer only HIGH, MEDIUM and LOW options. Depending on which option you choose, the extension will detect the best available video. So if you select HIGH and the video has a 720p version, that is the one that will be displayed. If you select the LOW quality option, it will use the lowest quality available video.

---

### Post by bigsmitty64 on 2010-06-02
Excellent. Thank you sir for sticking this one out with me. I very much appreciate it. I'm marking this one solved. Have a great day!

---

### Post by lovinglinux on 2010-06-02
> **bigsmitty64 said:**
> Excellent. Thank you sir for sticking this one out with me. I very much appreciate it. I'm marking this one solved. Have a great day!

You are welcome. Keep in mind that you still have issues  with flash in fullscreen that might appear in sites not supported by my extension. So would recommend taking a look at dodo3773 previous post.

---

### Post by bigsmitty64 on 2010-06-02
> **dodo3773 said:**
> O.K. here is what I did. I read this on this blog 

[http://blog.killtheradio.net/technology/slow-flash-in-ubuntu/](http://blog.killtheradio.net/technology/slow-flash-in-ubuntu/)

What I did was right click on any flash video, go down to settings, and uncheck the box that says enable hardware acceleration. Then open a terminal and type

 
sudo mkdir /etc/adobe

sudo su

sudo echo "OverrideGPUValidation = 1" >> /etc/adobe/mms.cfg


I added the sudo su as the second command because I was getting a permission denied error.

After that I re-enabled hardware acceleration, closed firefox, then opened it back up. I have not experienced that problem again.
I hope that helps you.

Thats great! worked like a dream. I disabled lovinglinux's plugin (to make sure there were no conficts) and did what you said , and presto, no ,more lag, and all controls. A big thanks to you both for all your help!

---

### Post by lovinglinux on 2010-06-02
> **bigsmitty64 said:**
> Thats great! worked like a dream. I disabled lovinglinux's plugin (to make sure there were no conficts) and did what you said , and presto, no ,more lag, and all controls. A big thanks to you both for all your help!

I'm glad you fixed it. The sad thing is that dodo3773's hack is in my tutorial linked from post #5, so I assumed you had already tried it. I didn't know the link was broken since I changed my web site host. ](*,) I need to stop moving my site :)

The correct link is [http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

---

