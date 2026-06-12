---
title: "Quick Nooblet Questions (Post-Search Phase)"
date: 2010-03-12
forum: General Help
---

### Post by Maggew on 2010-03-12
[SIZE=1]Hello Community!

It's a pleasure to be apart of something exciting as Ubuntu!
This is not my first venture into the LINUX gateway, however I plan to make this my final....

I installed Kubuntu 9.10 on my 64-bit AMD PC.
[/SIZE]   
[LIST]
[*][SIZE=1]9600 Phenom Quad-Core Chip[/SIZE]
[*][SIZE=1]4 GB+ Ram w/500GB HDD[/SIZE]
[*][SIZE=1]HD 2600 Radeon (nothing fancy, but it's stable)[/SIZE]
[/LIST]
=-=-=-=-=-=-=-=-=-=-=-=-
Quick Nooblet Questions
=-=-=-=-=-=-=-=-=-=-=-=-

Web Broswer **_Konqueror_** is defualt browser.

[LIST]
[*]How do I change defualt browser? The options in FF & Opera settings don't function as smoothly as they do in Windows
[/LIST]
I particularly favored _CuteFTP_ and _Daemon Tools_

[LIST]
[*]Your Mounting TOOL? (img's, iso's, .daa's, etc..) Will D.T. work in 9.10?
[/LIST]
I goto complete the form and I have ZERO, Zilch, Nadda, No luck....
[http://kubuntuforums.net/forums/index.php?action=register](http://kubuntuforums.net/forums/index.php?action=register)

[LIST]
[*]How the FRIK do I register an account with _Xubuntu_ forums?
[/LIST]
so far the answers I've put in are as follows:  [SIZE=2][B]2010, 20, Bangalore, Canada, No
([/B][/SIZE]Perhaps I need not to capitalize the words, or my math is wrong?!)

[FONT=Arial]=-=-=-=-=-=-=-=-=-=-=-=-
Quick Nooblet Questions Pt.2
=-=-=-=-=-=-=-=-=-=-=-=-[/FONT]

My Audio works "outside" of the browser, I just got done jamming out to Jimmy Morrison.

[LIST]
[*] Why does it not work in FF, Opera, or Konqeror?
[/LIST]
[CENTER] [FONT=Verdana][SIZE=1]**How come I didn't need to my Drivers for mobo, audio, etc, during install?** [/SIZE][/FONT][/CENTER]

[LIST=1]
[*]Why can't a "DRAG a BOX" around my icons on desktop but I can in sub-folders?
[*] What is the purpose of Desktop Folder?
[*] I've read that people install'd CS4 Photoshop?  Any luck/advice?
[*] What advice could you share with me (good or bad)?
[/LIST]

I've snag'd a solid domain name, I hope to gather a good amount of data and publish some blog-content for other new-linux users in the future. Any help/flame war would be great advice for me. Thanks.

---

### Post by adam814 on 2010-03-12
As for mounting images probably the closest I've found to Daemon Tools for Ubuntu is gmountiso.  It's in the repos and is pretty decent.  Of course it's just a GNOME front end to mount (recently I've just stuck to using mount directly and I know it works for .iso and .img files).

FileZilla is a pretty good graphical FTP program.  I've never used CuteFTP.

If your sound isn't working in your browser most likely you're missing a plugin.  Most audio would be covered with the Adobe Flash plugin or any of the media player plugins (I prefer VLC, but MPlayer has one and I think even Totem has one).

As for why you didn't need to install separate drivers it's just a difference of how Linux handles drivers vs. the way Windows does.  Ubuntu stock kernels come with all the supported drivers built as modules and only load the ones your particular machine needs at boot.

---

### Post by Maggew on 2010-03-12
> **adam814 said:**
> .....

If your sound isn't working in your browser most likely you're missing a plugin.....

You've made some good solid points, well noted :)

Thanks for your input, appreciate it much, can't wait to try the mounting software. 
Would the audio plug-in be included in my system updates? Or even perhaps the java 64 or Flash audio player update?

Any idea how to change system defualt programs?

---

### Post by uRock on 2010-03-12
Go to the preferred applications applet and change it.

---

### Post by adam814 on 2010-03-12
Most of the plugins are available from the repos.  You can get the flash plugin from the "flashplugin-nonfree" package.  I also installed the "mozilla-plugin-vlc" package.  Note that this will also install VLC and about 150MB or so of related libraries.  It wasn't an issue for me as I also wanted VLC player.

---

### Post by Maggew on 2010-03-13
BUMP

> **adam814 said:**
> Most of the plugins are available from the repos.  You can get the flash plugin from the "flashplugin-nonfree" package.  I also installed the "mozilla-plugin-vlc" package.  Note that this will also install VLC and about 150MB or so of related libraries.  It wasn't an issue for me as I also wanted VLC player.

i've installed both packages and still no luck with SOUND in my browser.

i'm currently attempting to install the flash 64-bit beta player.
[http://ubuntuforums.org/showthread.php?t=1414595](http://ubuntuforums.org/showthread.php?t=1414595)

check out the link, i'll keep you updated.  Thanks for the advice!

---

### Post by adam814 on 2010-03-13
I use the 64-bit Flash 10 prerelease myself.  I've found it to be much more functional and stable than the 32-bit version using nspluginwrapper except for hulu.com, which seems to have issues with it.

The instructions in that thread seem a little more confusing than necessary.  Download it from here:
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

Install it by going to the directory where you saved it in the terminal and typing this:
```
tar -xzvf libflash*.gz && sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
```After restarting Firefox you should have working flash.

---

### Post by uRock on 2010-03-13
What is hard about downloading a little app then clicking the button to uninstall one flash then clicking the other button to install the 64 bit flash?

---

### Post by adam814 on 2010-03-13
Upon further review it doesn't look as hard as I originally thought.  I'd still rather run the two shell commands than have to compile and run a graphical app to do the same thing.  Not to mention I usually prefer to at least look over source code I find in a forum post before I actually run it (although I'm guessing it's safe as no one has posted otherwise).

---

### Post by uRock on 2010-03-13
I did it the hard way a few days before I found Carlee's program. Either way wasn't too bad for me. Hopefully they can implement the 64bit into the repos soon.

---

