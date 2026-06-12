---
title: "Temp Files???"
date: 2011-02-16
forum: General Help
---

### Post by ubunwhat on 2011-02-16
Ok, I admit to being a youtube addict.  I have always been able to save flash videos from youtube by simply pausing the video in the browser and letting the download finish, and then just grabbing the video from file system / temp /.  It was so easy!  And now, for whatever reason, I cannot.  The files are no longer there.  I wondered if it was just a youtube thing but the same holds true for dailymotion as well.  What gives?  Did the latest update move them somewhere else?

---

### Post by ankspo71 on 2011-02-16
Hi,
It appears the new flash player 10.2+ will be marking the cached flash files as deleted somehow. I'm guessing this might break some addons for *tube sites too.
> 
...but the latest Flash 10.2 breaks it because the cached files are deleted from /tmp (but are still there). [http://www.webupd8.org/2011/02/play-youtube-videos-without-flash-from.html](http://www.webupd8.org/2011/02/play-youtube-videos-without-flash-from.html)

---

### Post by ubunwhat on 2011-02-16
Suckage.  Looking through the link it appears that most of that is way over my head, but I will give it a shot.  Thanks for the response.

---

### Post by lisati on 2011-02-16
Remember: according to the [Youtube terms and conditions]("http://www.youtube.com/static?gl=US&template=terms"), you're *supposed* to use an approved player......

---

### Post by 3rdalbum on 2011-02-16
When I use Chromium, I still find the files inside my Chromium cache.

---

### Post by mcduck on 2011-02-16
> **3rdalbum said:**
> When I use Chromium, I still find the files inside my Chromium cache.

Same with Firefox, they were just moved into Firefox's own cache instead of /temp.

---

### Post by ubunwhat on 2011-02-16
Can you tell me where to find firefox's cache?  I'm still new enough to Linux that I get a bit lost with the file structure.

Also, I tried the workaround in the link posted about and got no love.  I am fairly certain that it was done correctly as the launcher installed correctly, but when I follow the directions to launch mplayer nothing at all happens.

---

### Post by quadproc on 2011-02-16
> **lisati said:**
> Remember: according to the [Youtube terms and conditions]("http://www.youtube.com/static?gl=US&template=terms"), you're *supposed* to use an approved player......
Here is another point to consider: in my case, I have a medium speed Internet connection.  This means that video usually comes in a little slower than it gets played.  That causes freezes of the video and dropouts of the audio, making the presentation essentially unwatchable.

I work around this by letting the item play itself out and then use the temp file to view it.  No freezes, no dropouts.  My player is irrelevant; the relevant factor is the bandwidth of my Internet connection.

quadproc

---

### Post by pavelexpertov on 2011-02-16
If u want to download videos and convert it into a different format, try clipgrab or something. follow this [link]("http://www.youtube.com/watch?v=HTA7smqOBUY")...

---

### Post by mcduck on 2011-02-16
> **ubunwhat said:**
> Can you tell me where to find firefox's cache?  I'm still new enough to Linux that I get a bit lost with the file structure.

Also, I tried the workaround in the link posted about and got no love.  I am fairly certain that it was done correctly as the launcher installed correctly, but when I follow the directions to launch mplayer nothing at all happens.

It's a hidden directory inside your home dir.

~/.mozilla/firefox/*profilename*/Cache/

Also note that the naming of cached flash stream was changed, it doesn't start with "flash" any more, instead being just a random string like all the other cached files are, so finding the flash video among all the other cached stuff might be a bit harder than before.

---

### Post by TeoBigusGeekus on 2011-02-16
1)Open flash video page (that you own of course) and let it load. Don't close the page.

2)Open terminal and give
```
lsof | grep Flash
```
lsof: list open files
In my case (opera user) it gives
```
operaplug 2840        teo    9u      REG        8,8  6962837     392986 /tmp/FlashXXFfe85s (deleted)
```
Notice the 2nd (process id) and 4rth (file descriptor - without the letter) columns.

3)
```
cp /proc/2840/fd/9 ~/Desktop/video
```

4)????????????

5)Profit.

---

### Post by ubunwhat on 2011-02-16
> **mcduck said:**
> It's a hidden directory inside your home dir.

~/.mozilla/firefox/*profilename*/Cache/

Also note that the naming of cached flash stream was changed, it doesn't start with "flash" any more, instead being just a random string like all the other cached files are, so finding the flash video among all the other cached stuff might be a bit harder than before.

This was almost what I was looking for.  The only issue is that it stops caching the file when the player stops.  Before I could pause a 2:00 video after 15 seconds and let the other 1:45 load in cache and then just open the full 2:00 video in a player.  Now, when I pause after 15 seconds the video stops being written to cache and all I have is the 15 seconds.  ( Of course I am giving it time to finish downloading.  It simply stops. )  Is this a difference in how the caches work or another kick to the crotch from Adobe?

---

### Post by Vaphell on 2011-02-16
it's not what i am experiencing. I pause the video, progress bar loads up and in opened cache folder file constantly grows in size until the whole bar is filled.

---

### Post by ubunwhat on 2011-02-16
> **TeoBigusGeekus said:**
> 1)Open youtube video (that you own of course) and let it load. Don't close the page.

2)Open terminal and give
```
lsof | grep Flash
```
lsof: list open files
In my case (opera user) it gives
```
operaplug 2840        teo    9u      REG        8,8  6962837     392986 /tmp/FlashXXFfe85s (deleted)
```
Notice the 2nd (process id) and 4rth (file descriptor - without the letter) columns.

3)
```
cp /proc/2840/fd/9 ~/Desktop/video
```

4)????????????

5)Profit.

LOL  Not for profit at all.  Anyway, I get something like this...

firefox-b 2586     steven  mem       REG        8,1 12110348   14942756 /usr/lib/adobe-flashplugin/libflashplayer.so

and when I type...

cp /proc/2586/fd/mem ~/Desktop/video

I get

cp: cannot stat `/proc/2586/fd/mem': No such file or directory

Am I staying in memory instead of writing to cache?

---

### Post by ubunwhat on 2011-02-16
> **Vaphell said:**
> it's not what i am experiencing. I pause the video, progress bar loads up and in opened cache folder file constantly grows in size until the whole bar is filled.

This is totally weird.  I switched over to DailyMotion that has some mp4 videos as well as flash.  When I pause an mp4 it continues to load just as before, but when I pause a flash video it stops loading.  WTF?

---

### Post by Vaphell on 2011-02-16
is your system 32 or 64bit and where did you get your flash from?

---

### Post by ubunwhat on 2011-02-16
32 bit and I am assuming it comes from Adobe and is updated via the                                                             automatic updates in Ubuntu.  I had to pick it up the first time from Adobe, but after that it's been updated automatically.

---

### Post by TeoBigusGeekus on 2011-02-16
> **ubunwhat said:**
> LOL  Not for profit at all.  Anyway, I get something like this...

firefox-b 2586     steven  mem       REG        8,1 12110348   14942756 /usr/lib/adobe-flashplugin/libflashplayer.so

and when I type...

cp /proc/2586/fd/mem ~/Desktop/video

I get

cp: cannot stat `/proc/2586/fd/mem': No such file or directory

Am I staying in memory instead of writing to cache?

Try with capital F in the grep pipe. I presume you inserted a lowercase f and therefore lsof returned the libflashplayer.so file as open, ie.

```
lsof |grep [COLOR="Red"]F[/COLOR]lash
```

---

### Post by ubunwhat on 2011-02-16
The capital F helped with the first part.  I now get...


plugin-co 1997     steven   16u      REG        8,1  7063607    6422540 /tmp/FlashXXI3gZKV (deleted)

So I type cp proc/1997/fd/16 ~/Desktop/video and I get...

cp: cannot stat `proc/1997/fd/16': No such file or directory

I just cannot buy some love at all.

---

### Post by lisati on 2011-02-16
> **quadproc said:**
> Here is another point to consider: in my case, I have a medium speed Internet connection.  This means that video usually comes in a little slower than it gets played.  That causes freezes of the video and dropouts of the audio, making the presentation essentially unwatchable.

I work around this by letting the item play itself out and then use the temp file to view it.  No freezes, no dropouts.  My player is irrelevant; the relevant factor is the bandwidth of my Internet connection.

quadproc

We feel your pain.

Another point to ponder: we don't want to get anyone in to trouble from advice given through these forums, no matter how well intentioned. Threads have been closed for less..... :D

---

### Post by Vaphell on 2011-02-16
i wonder how binding is that ToS. I don't remember ever seeing it (not to mention actual reading) so they could ask for the blood of my firstborn (not yet produced) and i wouldn't know any better. Game EULAs at least have to be accepted, yet they are still pretty much worthless and non-binding in majority of the world.

---

### Post by TeoBigusGeekus on 2011-02-17
> **ubunwhat said:**
> The capital F helped with the first part.  I now get...


plugin-co 1997     steven   16u      REG        8,1  7063607    6422540 /tmp/FlashXXI3gZKV (deleted)

So I type cp proc/1997/fd/16 ~/Desktop/video and I get...

cp: cannot stat `proc/1997/fd/16': No such file or directory

I just cannot buy some love at all.

It should have been

```
cp [COLOR="Red"]/[/COLOR]proc/1997/fd/16 ~/Desktop/video
```

---

### Post by frubblezuck on 2011-02-17
I was perplexed this morning. Couldn't view video on my usual sites(not XXX btw). I ran an apt-get upgrade for the first time since Jan just last night. Apparently the 10.2 Flashplugin was released(doh) and installed in the upgrade. I went site to site trying to figure out where my temp files went because I like to buffer them in with firefox and then watch them as they stream in via mplayer as Flash still runs like **** on my hardware. 10.2 does the delete thing from what's posted here and elsewhere since 2/08/11 or so when Adobe released 10.2 and it found its way into the respositories. I have since downgraded using KPackageKit to _10.0.22*_ and my Flash* temp files are back. So when/if that tricksy code in 10.2 becomes part of the de facto version that everyone requires...grrrrr. You find a way to make your crappy hardware do a headstand and someone throws a bowling ball at it.

---

### Post by Vaphell on 2011-02-17
you know, there is a good reason to store temporary files in browser's cache - consistency. Without it firefox (or any other browser) has no control over what flash does and can't apply cache policy to flash content. It's flash that is the plugin here, it should obey rules of its master, the browser. In fact i hope flash dies in a fire. 
Let's say your hdd free space is running low, you set small cache but that doesn't matter because you still can have few gigs of flash in /tmp. I know you can purge it, but the point stands - flash shouldn't be exempt from browser rules.

---

### Post by ADani on 2011-02-24
> **TeoBigusGeekus said:**
> 1)Open flash video page (that you own of course) and let it load. Don't close the page.

2)Open terminal and give
```
lsof | grep Flash
```
lsof: list open files
In my case (opera user) it gives
```
operaplug 2840        teo    9u      REG        8,8  6962837     392986 /tmp/FlashXXFfe85s (deleted)
```
Notice the 2nd (process id) and 4rth (file descriptor - without the letter) columns.

3)
```
cp /proc/2840/fd/9 ~/Desktop/video
```

4)????????????

5)Profit.
Thanks for this, even though I had found the elusive new temp cache location, my limited cache size on Chrome caused the file to disappear before the loading finished (and I don't know how to resize the cache on Chrome). Your workaround worked for me.
many thanks!

---

### Post by TeoBigusGeekus on 2011-02-24
> **ADani said:**
> Thanks for this, even though I had found the elusive new temp cache location, my limited cache size on Chrome caused the file to disappear before the loading finished (and I don't know how to resize the cache on Chrome). Your workaround worked for me.
many thanks!

And you'll also find that this is a rock solid method; whatever adobe will do with the temp folder, or the "elusive" cache folder, its flash player will still have to read a flash file in order to play it.

---

### Post by chetancrasta on 2011-02-25
The methods described by previous may work well, however if there is someone who wants the previous behavior of video caching in the /tmp directory, here is what you need to do:

To restore this 'feature', you will need to downgrade Flash to version 10.1.102.64

The download link for older versions of flash is [http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)

Download the (large) file named "Flash Player 10.1.102.64 and 9.0.289.0".
After downloading, extract the file named flashplayer10_1r102_64_linux.tar.gz

From this file extract libflashplayer.so and overwrite the file at /usr/lib/flashplugin-installer (you will need root privileges, try gksudo nautilus)

Restart Firefox and your flash videos will land up in the /tmp directory as before! This won't work for Google Chrome, it will continue to use the latest version of Flash.

Note: For the above steps to work, a version of Adobe Flash should have been previously installed.

---

### Post by ankspo71 on 2011-02-25
Hi,
Flash 10.1 is still available in the repositories too. It's just hidden away from plain site to see.

Open up Synaptic Package Manager, and search for flashplugin-installer.
When you find it, right click on it, select properties, then click on the versions tab. You will see 10.2 from the maverick-updates repository and 10.1 from the maverick repository.

To install version 10.1, you need to go to the menu > Package > Force Version, choose the version you want to install from the drop down menu, then click force version then click apply.

To protect version 10.1 from getting future updates, you have to lock that version by going to the menu > Package > Lock Version.

---

### Post by chetancrasta on 2011-02-25
@ankspo71: Thanks for the tip. It is much easier to downgrade flash that way.
However, the version available in the repository is 10.1.85.3 where as the previous Flash version is 10.1.102.64. The latter version fixes some critical vulnerabilites: [http://www.adobe.com/support/security/bulletins/apsb10-26.html](http://www.adobe.com/support/security/bulletins/apsb10-26.html)

Therefore, I think it is better to follow the procedure I described earlier.

Note: The latest 10.2 version also fixes some vulnerabilities, see below.

---

### Post by chetancrasta on 2011-02-25
Actually, Flash version 10.2.152.26 also fixes some security vulnerabilites: [http://www.adobe.com/support/security/bulletins/apsb11-02.html](http://www.adobe.com/support/security/bulletins/apsb11-02.html)

Therefore, if one has downgraded Flash in Firefox, one should use Firefox only to access the page containing the video (after determining that the site is trustworthy).

Since the downgrade procedure I described does not affect Google Chrome, one could use Chrome for regular surfing and Firefox for downloading videos.

---

### Post by chetancrasta on 2011-02-25
sorry, posted this by mistake

---

### Post by ron999 on 2011-02-25
> **TeoBigusGeekus said:**
> And you'll also find that this is a rock solid method; whatever adobe will do with the temp folder, or the "elusive" cache folder, its flash player will still have to read a flash file in order to play it.
As you say, it is indeed a rock solid method. :D
It would be more user-friendly though if it could be run as a script.
Just run the script to copy the file from cache onto desktop. :cool:

---

### Post by TeoBigusGeekus on 2011-02-26
An update on my system (arch) added a new column to lsof (TID).
So, in lsof 4.84-2, the output of 
```
lsof|grep Flash
```
gives
```
operaplug 4191 4202  teo    9u   REG        8,2    6096253    1052194 /tmp/FlashXXECqXK3 (deleted)
```
Columns of interest: 2nd and 5th
If you have a similar output, then
```
cp /proc/$(lsof|grep Flash|sort -nk 8|tail -n1|awk '{print $2}')/fd/$(lsof|grep Flash|sort -nk 8|tail -n1|awk '{print $5}'|sed 's/[A-Za-z]//g') ~/Desktop/Oh_Hi_Adobe.flv
```
will copy the largest flash file that flash player has in memory to your desktop. 
I made it so because there might be other, smaller flash files open (adds for example).


If you're still using the older version of lsof (which applies to all ubuntu users I assume) and your output is something like this,
```
operaplug 2840        teo    9u      REG        8,8  6962837     392986 /tmp/FlashXXFfe85s (deleted)
```
(Columns of interest: 2nd and 4th), then the command should be
```
cp /proc/$(lsof|grep Flash|sort -nk 8|tail -n1|awk '{print $2}')/fd/$(lsof|grep Flash|sort -nk 8|tail -n1|awk '{print $4}'|sed 's/[A-Za-z]//g') ~/Desktop/Oh_Hi_Adobe.flv
```
Just a tiny change in the last awk command (column of interest).

---

### Post by ron999 on 2011-02-26
Redacted.

---

### Post by TeoBigusGeekus on 2011-02-26
> **ron999 said:**
> ```
plugin-co 5781        ron   17w      REG        8,1   5479401   27291 /tmp/FlashXX0S8Pj2 (deleted)
```

```
ron@ubuntu:~$ cp /proc/$(lsof|grep Flash|sort -nk 8|tail -n1|awk '{print $2}')/fd/$(lsof|grep Flash|sort -nk 8|tail -n1|awk '{print $4}'|sed 's/u//') ~/Desktop/Oh_Hi_Adobe.flv
cp: cannot stat `/proc/5781/fd/17[COLOR="Red"]w[/COLOR]': No such file or directory
```

@TeoBigus, there's something wrong with the command.
It's trying to find file '17[COLOR="Red"]w[/COLOR]'.
The file is '17' without the '[COLOR="Red"]w[/COLOR]'.

I stand corrected... Sorry!!!
I replaced the commands with more general ones.
Try these.

---

### Post by ron999 on 2011-02-26
> **TeoBigusGeekus said:**
> 

I replaced the commands with more general ones.
Try these.

Yes, that's cured it.:guitar:

The command works properly for me now.:)
Thanks.

---

### Post by TeoBigusGeekus on 2011-02-26
That's my personal revenge on adobe, for having not corrected its cr@appy linux version of flash after all these years of complaints. :evil:

---

### Post by kiridude on 2011-03-05
> **TeoBigusGeekus said:**
> An update on my system (arch) added a new column to lsof (TID).
So, in lsof 4.84-2, the output of 
```
lsof|grep Flash
```
gives
```
operaplug 4191 4202  teo    9u   REG        8,2    6096253    1052194 /tmp/FlashXXECqXK3 (deleted)
```
Columns of interest: 2nd and 5th
If you have a similar output, then
```
cp /proc/$(lsof|grep Flash|sort -nk 8|tail -n1|awk '{print $2}')/fd/$(lsof|grep Flash|sort -nk 8|tail -n1|awk '{print $5}'|sed 's/[A-Za-z]//g') ~/Desktop/Oh_Hi_Adobe.flv
```
will copy the largest flash file that flash player has in memory to your desktop. 
I made it so because there might be other, smaller flash files open (adds for example).


If you're still using the older version of lsof (which applies to all ubuntu users I assume) and your output is something like this,
```
operaplug 2840        teo    9u      REG        8,8  6962837     392986 /tmp/FlashXXFfe85s (deleted)
```
(Columns of interest: 2nd and 4th), then the command should be
```
cp /proc/$(lsof|grep Flash|sort -nk 8|tail -n1|awk '{print $2}')/fd/$(lsof|grep Flash|sort -nk 8|tail -n1|awk '{print $4}'|sed 's/[A-Za-z]//g') ~/Desktop/Oh_Hi_Adobe.flv
```
Just a tiny change in the last awk command (column of interest).

Hi Teo. I used your script and it worked great - once. After that I kept getting 
```
cp: cannot stat `/proc//fd/': No such file or directory

```

Also, for some sites, once the video buffers completely, it disappears from the mozilla cache. I cant seem to find where it goes. It is obviously somewhere on my computer as the video plays again without re-buffering.

Also, I am using firefox.

Thanks.

---

### Post by TeoBigusGeekus on 2011-03-06
> **kiridude said:**
> Hi Teo. I used your script and it worked great - once. After that I kept getting 
```
cp: cannot stat `/proc//fd/': No such file or directory

```
Can you give more details about the situation?

> 
Also, for some sites, once the video buffers completely, it disappears from the mozilla cache. I cant seem to find where it goes. It is obviously somewhere on my computer as the video plays again without re-buffering.

Also, I am using firefox.

Browsers have a limited size cache. Once your video "fills" firefox's cache, it is deleted to free up space.

---

### Post by kiridude on 2011-03-07
> **TeoBigusGeekus said:**
> Can you give more details about the situation?



Browsers have a limited size cache. Once your video "fills" firefox's cache, it is deleted to free up space.

It seems that some sites have done something so that once the video finishes buffering, it disappears from the .mozilla cache. This is not due to space restrictions as videos from other sites stay there, and I have designated a large cache size. I opened the cache and watched the video downloading there, and the second it finished, it disappeared. ?

Any idea where the vid goes, or how to locate it. I tried locate and the file name but found nothing...

---

### Post by chetancrasta on 2011-03-07
> **kiridude said:**
> It seems that some sites have done something so that once the video finishes buffering, it disappears from the .mozilla cache.
Any idea where the vid goes, or how to locate it. I tried locate and the file name but found nothing...

These videos **are** buffered (probably in RAM or Swapfile). Once the video has disappeared from the cache, just play the video in the browser again, and the file magically reappears (usually).

---

### Post by TeoBigusGeekus on 2011-03-07
> **kiridude said:**
> It seems that some sites have done something so that once the video finishes buffering, it disappears from the .mozilla cache. This is not due to space restrictions as videos from other sites stay there, and I have designated a large cache size. I opened the cache and watched the video downloading there, and the second it finished, it disappeared. ?

Any idea where the vid goes, or how to locate it. I tried locate and the file name but found nothing...

Have you tried locating the file with lsof?

---

### Post by kiridude on 2011-03-10
> **TeoBigusGeekus said:**
> Have you tried locating the file with lsof?

I tried with lsof but I get the "no such file or directory" error.

Maybe I am not using the correct file name. I look at the name (numbers and letters) of the file while it is downloading into the cache (before it disappears). Is there another way to get the file name? 

Even when I use unplug there is still no file to download. The only options it offers are two little shockwave flash icons. But there is a video that downloads and plays...?

---

### Post by TeoBigusGeekus on 2011-03-10
Open the site with the video and let it load (remember to have only one video loaded for simplicity).
Then post us the output of
```
lsof|grep Flash
```

---

### Post by Rushyang on 2011-03-10
If you just want to have YouTube Video then let me tell you something *off the record* .."Clipgrab".

---

### Post by searchfgold6789 on 2011-03-10
Why not use the _**[Easy Youtube Video Downloader Plugin for Firefox]("http://https://addons.mozilla.org/en-us/firefox/addon/easy-youtube-video-downl-10137/")**_? It is an exceptional program that may be just what you are looking for if you run Firefox, and there is probably a similar plugin for Chromium.

---

### Post by chetancrasta on 2011-03-10
> **searchfgold6789 said:**
> Why not use the _**[Easy Youtube Video Downloader Plugin for Firefox]("http://https://addons.mozilla.org/en-us/firefox/addon/easy-youtube-video-downl-10137/")**_? It is an exceptional program that may be just what you are looking for if you run Firefox, and there is probably a similar plugin for Chromium.

Because if one fully viewed a long video and then tried to download it using one of those plugins, the plugin downloads the entire video again, though it had already been fully buffered!
What a waste of time!

---

### Post by Rushyang on 2011-03-10
> **chetancrasta said:**
> Because if one fully viewed a long video and then tried to download it using one of those plugins, the plugin downloads the entire video again, though it had already been fully buffered!
What a waste of time!

Don't give up on yourself man.. There are also many other plugins... one of them I have been using is **FlashGot**.

---

### Post by kiridude on 2011-03-10
> **TeoBigusGeekus said:**
> Open the site with the video and let it load (remember to have only one video loaded for simplicity).
Then post us the output of
```
lsof|grep Flash
```

Filaraki, please forgive my ignorance. I had recently re-installed firefox and had not readjusted the cache size - as you first suggested. That was the problem.

Thanks for you help.

---

### Post by dnguyen1963 on 2011-03-10
> **TeoBigusGeekus said:**
> Open the site with the video and let it load (remember to have only one video loaded for simplicity).
Then post us the output of
```
lsof|grep Flash
```

The newer Flash version does not use Flash* in the temp file name.  It is just some random letter and number.  Also, if you pause the video the temp file also pauses its download.  Adobe designs this feature to circumvent any copyright issue.  This hurts many valid users with slow internet speed, but really, nothing is "free".  I have seen advertisement of 30 Mbps for about $50/mo.

---

### Post by TeoBigusGeekus on 2011-03-10
> **dnguyen1963 said:**
> The newer Flash version does not use Flash* in the temp file name. 
Which version would this be?

---

### Post by dnguyen1963 on 2011-03-11
> **teobigusgeekus said:**
> which version would this be?

10.2

---

### Post by TeoBigusGeekus on 2011-03-11
> **dnguyen1963 said:**
> 10.2

I'm using flashplugin 10.2.152.27-2 and not witnessing the behaviour you described.

---

### Post by dnguyen1963 on 2011-03-14
> **TeoBigusGeekus said:**
> I'm using flashplugin 10.2.152.27-2 and not witnessing the behaviour you described.

Strange but not surprising because I have this behavior (disappearing of Temp Flash file) with Mint 10, but not with ArtistX.  I downgraded Flash down to 10.1 in Mint and the problem went away.

---

### Post by pottzie on 2011-04-09
Let me jump in and say that this thread is awesome! I'm using it to download videos for a church presentation-I have the author's permission. Several videos were downloaded using this method, and all went well. However there are several longer videos (lessons, seminars ) that lsof | grep Flash showed nothing, just a flashing cursor. My guess is that they were recorded/formated using something other than flash.
 Are there any other formats I can try besides Flash in the command to see if I can capture the video?

---

### Post by chetancrasta on 2011-04-10
Here is script that makes downloading flash videos even easier than copying it from /tmp: [http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html](http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html)
This technique is better than downgrading Flash because older versions of Flash have security vulnerabilities.

---

### Post by TeoBigusGeekus on 2011-04-10
> **pottzie said:**
> However there are several longer videos (lessons, seminars ) that lsof | grep Flash showed nothing, just a flashing cursor.

Can you give us a link?

---

### Post by tmy on 2011-04-22
> **TeoBigusGeekus said:**
> Can you give us a link?
  Hi this seems to be a great solution and I would love try this method. However I too could use the link and also how to make it executable thanks for the post take care 

tmy 

bye

---

### Post by Loevborg on 2011-04-26
> **chetancrasta said:**
> Here is script that makes downloading flash videos even easier than copying it from /tmp: [http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html](http://davesource.com/Solutions/20110313.Chrome-linux-hidden-flash-files.html)
This technique is better than downgrading Flash because older versions of Flash have security vulnerabilities.

This is useful, thanks (also to the script author).

---

### Post by G4tekeeper on 2011-06-02
> **TeoBigusGeekus said:**
> An update on my system (arch) added a new column to lsof (TID).
So, in lsof 4.84-2, the output of 
```
lsof|grep Flash
```
gives
```
operaplug 4191 4202  teo    9u   REG        8,2    6096253    1052194 /tmp/FlashXXECqXK3 (deleted)
```
Columns of interest: 2nd and 5th
If you have a similar output, then
```
cp /proc/$(lsof|grep Flash|sort -nk 8|tail -n1|awk '{print $2}')/fd/$(lsof|grep Flash|sort -nk 8|tail -n1|awk '{print $5}'|sed 's/[A-Za-z]//g') ~/Desktop/Oh_Hi_Adobe.flv
```
will copy the largest flash file that flash player has in memory to your desktop. 
I made it so because there might be other, smaller flash files open (adds for example).


If you're still using the older version of lsof (which applies to all ubuntu users I assume) and your output is something like this,
```
operaplug 2840        teo    9u      REG        8,8  6962837     392986 /tmp/FlashXXFfe85s (deleted)
```
(Columns of interest: 2nd and 4th), then the command should be
```
cp /proc/$(lsof|grep Flash|sort -nk 8|tail -n1|awk '{print $2}')/fd/$(lsof|grep Flash|sort -nk 8|tail -n1|awk '{print $4}'|sed 's/[A-Za-z]//g') ~/Desktop/Oh_Hi_Adobe.flv
```
Just a tiny change in the last awk command (column of interest).

Honor to those who deserve it! You saved me a lot of pain looking for that elusive cached flash file! :) I don't like Adobe that much because of its crappy support to Linux users but until then, we'll have to figure out ways around it. :roll:

---

### Post by tg3793 on 2011-06-10
I highly recommend Minitube (in the repositories) for those like myself who have problems with caching Youtube videos. The program looks a bit retro but it works great.

And you don't even have to wait until the video is completed downloaded. You can watch partial videos with VLC or any other player that will watch videos in packets (not quite the right way of putting but you get my drift).

---

### Post by honeybear on 2011-06-25
Using google on a gentoo board, I found this bash code:

```
#!/bin/sh
	# Beware this program shall be used with only a video you owns
	FLASH=`lsof |grep Flash`
	PS=`lsof |grep Flash | awk '{ print $2}'`
	FD=`lsof |grep Flash | awk '{ print $4}'`
	FDSMALL=`echo "$FD"  |sed s/.$//`
	LINKVID="Link: /proc/$PS/fd/$FDSMALL"
        LINKVID1=`echo "$LINKVID" | head -n 1`
	mplayer "$LINKVID1"
```



or you may simply do : 

> cd .mozilla/firefox/XXXXX.default/Cache$ for FILE in * ; do mplayer -noconsolecontrols  "$FILE" ; done

---

### Post by nec207 on 2011-07-08
> **ubunwhat said:**
> Ok, I admit to being a youtube addict. I have always been able to save flash videos from youtube by simply pausing the video in the browser and letting the download finish, and then just grabbing the video from file system / temp /. It was so easy! And now, for whatever reason, I cannot. The files are no longer there. I wondered if it was just a youtube thing but the same holds true for dailymotion as well. What gives? Did the latest update move them somewhere else?
 
 
On my old computer running windows 98 you could check your temp folder and copy and paste the file ( from the windows temp folder ) and re-name it as a flv and play it yes you could play it if you have a flv player.
 
Not sure if windows vista and windows 7 blocks this .Also youtube updated the flash and cannot be run on windows 8 any more may be do to people doing this.

---

### Post by masamunedark on 2011-08-31
Sorry to revive this solved thread, but I just wanted to share a perl script which uses the method of saving flash files mentioned here. 
As long as the script is running it keeps saving any video files you open with firefox ( even if they are still loading ). and when you're done send it an INT signal( CTRL+c ). 
The files are saved by default in ~/videos but you can change the $outdir variable as you wish.

I know the code looks crappy, cause I am a crappy programmer, but at least it works :)

```

#!/usr/bin/perl 

use File::Temp qw/ tempfile /;


my $outdir = $ENV{'HOME'} . '/Videos';
my @files;
my $int_count = 0;

sub my_int_handler { $int_count++ }

$SIG{'INT'} = 'my_int_handler';

{
  my @newfiles = map { my ($procid, $fd) = /\s+(\d+)\s+\S+\s+(\d+)/; "/proc/$procid/fd/$fd" } grep { /\/tmp\/Flash/ } map {`lsof -p $_`} 
                            map {my @blah = /^\s*(\d+).+plugin-containe/} `ps -e`;
  BIGLOOP: for ( @newfiles ) {
             my $shouldreplace;
             open my $tempfh, "< $_";
             my $tempstamp;
             until ((length $tempstamp) > 100000) {
               $tempstamp .= readline $tempfh;
             }
             $tempstamp = substr $tempstamp,0,100000;
             for ( @files ) {
               if ($_->{'stamp'} eq $tempstamp) {
          
                 if ( $_->{'isdone'} && ($_->{'size'} < -s $tempfh)  ) {
                   $shouldreplace = $_;
                   $_->{'stamp'} = undef;
                   last; 
                 }
                 else { next BIGLOOP };
               }
             }        
            
            open my $ifh, "< $_" 
              or die "can't open $_: $!\n";
 
            if ( $shouldreplace ) { 
              seek $shouldreplace->{'ofh'},0,0;
              $ofh = $shouldreplace->{'ofh'};
              undef $shouldreplace;
            }
            else { 
              $ofh  = File::Temp->new( TEMPLATE => 'Flash_XXXXX',
                                       DIR => $outdir);
              $ofh->unlink_on_destroy(0);  
            }
            my $filepath = "$outdir/" . $ofh->filename;
            push @files, { 'size' => undef, 'ifh' => $ifh, 'ofh' => $ofh, 'path' => $filepath, 'stamp' => undef, 'cache' => undef, 'isdone' => undef } ;                     
         }

  for ( @files ) {
    next if $_->{'isdone'};
    unless ( $_->{'stamp'} ) {
      until ( length $_->{'stamp'} > 100000) {
       $_->{'stamp'} .= readline $_->{'ifh'};
      }
      $_->{'cache'} = $_->{'stamp'};
      $_->{'stamp'} = substr $_->{'stamp'},0,100000;
    }
    unless ( defined $_->{'size'} ) { 
      $_->{'size'} = -s $_->{'ifh'} ;
      next;
    }    
    
       if ( $_->{'cache'} ) {
         print {$_->{'ofh'}} $_->{'cache'};
         undef $_->{'cache'};
       }
       print {$_->{'ofh'}} readline $_->{'ifh'};
       if ($_->{'size'} == -s $_->{'ifh'}) {
         $_->{'isdone'}++;
       } 
       else { $_->{'size'} = -s $_->{'ifh'} }   
  }
  if ( $int_count ) {
    print STDERR "\n";
    print STDERR "-" x 30;
    print STDERR "$0: Process was interrupted";
    print STDERR "-" x 30;
    print STDERR "\n";
    last;
  }
  sleep 5;
  
  redo;
}
```I like using this with firefox by using a shell script like this:

```

#!/bin/bash

saveflash.pl &
firefox
kill -INT  %+
exit
```

---

### Post by Laysan_A on 2012-12-01
I'd really like to thank masamunedark for his script. I copied it into a word processor and saved it, made it executable (though I don't know if I really needed to), and ran it. I changed the output folder to flashvids first, so there wouldn't be other stuff in there (I confuse easily). Then I held my breath and opened an mp4 in firefox. Low and behold, there appeared a flash video (actually mp4, not flv, but both are handled by the flash plugin) in my flashvids folder. I clicked on it and voila, it opened up and played in vlc.

If you watch a lot of video online, like I do, you know how frustrating it can be when the audio and video are out of synch. It ruins the whole experience. With this script I can always have a backup (vlc) if the embedded player on whichever site I'm on isn't doing what I need it to. My only concern is remembering to delete the vids after I watch them, so I don't fill up my drive or otherwise make a mess of my folder.

Thank You!!!

---

### Post by wildmanne39 on 2012-12-01
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

