---
title: "Music folder keeps disappearing"
date: 2011-03-10
forum: General Help
---

### Post by cs567 on 2011-03-10
Hey

A few weeks ago my Music folder vanished, I started athread but didnt get any response.

So today I created a new music folder and used rhythmbox to copy my music from my ipod to the new folder. Everything was working fine but I have now gone to open the music folder and it is gone again!

Any Ideas as to why this is happening?

---

### Post by Hedgehog1 on 2011-03-10
cs567,

Where did you create the music directory?  Do you log in as different users?

Here is why I ask:

If I log in as '**hedgehog**', I am presented with a 'home' directory in nautilus (the GUI).  But it is written to disk as **/home/hedgehog/music**.

If I later log in as '**hamster**', I see what appears to be the same 'home' directory, but it is really **/home/hamster/music**

If you are not logging in with different logins, where are you creating the music directory?  Please give the '**/abc/def/music**' style path text.

***The Hedge***

:KS

---

### Post by cs567 on 2011-03-10
I created it in /home/craig/  

I am the only user if that helps

---

### Post by Hedgehog1 on 2011-03-10
Is the directory you created: **/home/craig/[COLOR="YellowGreen"]m[/COLOR]usic** or **/home/craig/[COLOR="YellowGreen"]M[/COLOR]usic**?

Note the Upper/Lower case of the first letter.  

***The Hedge***

:KS

---

### Post by cs567 on 2011-03-10
I spelt it with a capital M, just like the original

---

### Post by Hedgehog1 on 2011-03-10
One last thing, then:

In the terminal, if you would:

```
sudo ls /home/craig
```

Then cut and paste the output into your next post.

Also, the drive that your **/home** directory is on.  Is it formatted **ext3**, **ext4** or (possibly) **ntfs**?

***The Hedge***

:KS

---

### Post by cs567 on 2011-03-11
The disk is formatted as ext4. I checked the hidden files aswell and it is not there.

```
craig@craig-laptop:~$ ls /home/craig
Audiobooks        install-flash.sh                 Pictures   train.pdf
Desktop           jonesy.txt                       Podcasts   Videos
Documents         luktdkyf.pdf                     Public     VirtualDJ
Downloads         native-64bit-flash-installer.sh  run.pdf    Webcam
earthwallpaper    octave-core                      SimBin     xmas.pdf
examples.desktop  output.pdf                       Templates
```

---

### Post by tredegar on 2011-03-11
I expect you deleted it by accident.
Have you looked in the Rubbish Bin?

---

### Post by securitymeddler on 2011-03-11
Hey dude,

I am brand new to Linux. But I'd like to try and help. One thing I noticed since using Ubuntu on my laptop is sometimes it lags and things I click on "lag" so icons get dragged where I don't expect. I suspect that happened to you. 

You can do a quick search of your computer like this, 
find / -name FoLdeRnaMe

But you mentioned "keeps" in your subject line. This happened before? Perhaps a setting in your music player? 

If you are 100% sure you didn't do it, and the the music player's settings are fine. Then you might want to run a fsck against your drive. Check it for errors. 

This is a good read - 
[http://www.debianhelp.co.uk/fsck.htm](http://www.debianhelp.co.uk/fsck.htm)

Please share the results here so we can all learn. Thanks!

---

### Post by cs567 on 2011-03-11
So, I was using disk the usage analyser to check how full my hard drive was and if the files had been deleted or were still there.

While messing around with that I noticed a folder that was larger than it should have been - I checked and found the missing music folder in it.

It was in a hidden folder that is to do with some Uni stuff and it has nothing to do with music so I am unsure as to why it got moved to there. Although I may have been using that program at the time my music folder vanished.

Anyway thanks for your help, now I just have to figure out why it happened and to stop it happening again.

---

### Post by Hedgehog1 on 2011-03-12
Well, it took a village to figure it out (I think I played the part of the village idiot), but it is solved.

Great work everyone!

**The Hedge**

:KS

---

