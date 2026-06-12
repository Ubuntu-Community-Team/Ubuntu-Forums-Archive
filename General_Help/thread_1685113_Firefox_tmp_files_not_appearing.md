---
title: "Firefox tmp files not appearing"
date: 2011-02-10
forum: General Help
---

### Post by Amused2Death on 2011-02-10
Thanx in advance to anyone who knows the solution....

Up until a couple of days ago, if i went to youtube and played any videos i would automatically see a tmp file appear. If i renamed it it would stay and i could save the clip off to somewhere else.

Now instead of getting a file called say xfsn135k5643.flv i get a folder called plugtmp-1 with nothing usable in it.

Is it youtube or firefox that has changed, and if it's my end, can i access the clips another way.

I dont recall changing anything and i'm fairly sure i've taken my medication today :)

---

### Post by kellemes on 2011-02-10
Don't know where Firefox stores it's tmp's but you could search the system for *.flv to find the location of these files..

---

### Post by Taijitu on 2011-02-10
The change lies in the new version of the flash player, that now saves the temporary flash video files to ~/.mozilla/firefox/??????.default/Cache/

Mind you, the Terms of Use for Youtube forbids you from keeping copies of the movies you "stream" from their site... Just thought i ought to mention that...

I have a keyboard shortcut to open the flash files in /tmp using smplayer, because that usually is silky smooth for any video, whereas the same can not be said for flash player. The change in flash player kinda screwed that up, as they are no longer called "Flash<gibberish>" anymore, but just all gibberish.

My solution: Kept the old flashplayer.

---

### Post by Amused2Death on 2011-02-11
Thanx, very informative..
now to confess
i cant find the cache for firefox now, tho a week of 12hour plus days and little sleep isnt helping, im not Linux savvy enough to work out how to turn the flash player back from the upgrade.

I failed the smplayer test as i told it the wrong version of mplayer :(

never mind, some sleep and i will try again.... as i only borrow the occasional clip, its not an urgency, more of a learning curve.

---

### Post by polardude1983 on 2011-02-11
in flash 10.2 it stores the files differently. i found out how to download them

read this article hopefully my comments make it easier to get

[http://n00bsys0p.wordpress.com/2011/...ux/#comment-92](http://n00bsys0p.wordpress.com/2011/...ux/#comment-92)

---

### Post by McGyver81 on 2011-02-11
Hi everyone.

I had the same problem and after a bit of headbanging it seems to me that the file /etc/alternatives/mozilla-flashplugin now points at /usr/lib/gnash/libgnashplugin.so

I modified this to point to the old flash plugin: /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
and the flash player was again running in the usual way.

Hope this helps
Mc

---

### Post by Hoopz on 2011-02-11
[http://ubuntuforums.org/showthread.php?t=1685710](http://ubuntuforums.org/showthread.php?t=1685710)

---

### Post by Amused2Death on 2011-02-11
Thanx to all, and once again i've learnt something new.

Now to work out how i mark the thread "solved"............. found it :)

---

### Post by chetancrasta on 2011-02-25
While you can get the flash videos from firefox's cache, it is not as convenient and reliable as getting it from the /tmp directory.

Therefore, if you want to restore this 'feature', you will need to downgrade Flash to version 10.1.102.64

The download link for older versions of flash is [http://kb2.adobe.com/cps/142/tn_14266.html](http://kb2.adobe.com/cps/142/tn_14266.html)

Download the (large) file named "Flash Player 10.1.102.64 and 9.0.289.0".
After downloading, extract the file named flashplayer10_1r102_64_linux.tar.gz

From this file extract libflashplayer.so and overwrite the file at /usr/lib/flashplugin-installer (you will need root privileges, try gksudo nautilus)

Restart Firefox and your flash videos will land up in the /tmp directory as before! This won't work for Google Chrome, it will continue to use the latest version of Flash.

Note: For the above steps to work, a version of Adobe Flash should have been previously installed.

---

