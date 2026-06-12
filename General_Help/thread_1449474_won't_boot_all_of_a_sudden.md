---
title: "won't boot all of a sudden"
date: 2010-04-07
forum: General Help
---

### Post by 6SPEED on 2010-04-07
I installed Ubuntu about 2 months ago on a partition with win7 and was using it off and on. I would get on Ubuntu about every other day and have had no real problems. It's been about a month now since I got on Ubuntu and when I tried to boot into with grub I just get a little white underscore at the top left corner and it just sits there. I let it go for 15 mins and my HDD light isn't even blinking. It's like it's mad at me for not using it, LOL. I've done no changes to the computer minus a new monitor. I've tried recovery mode in grub and get the same thing. Also grub used to time out after 5 seconds and auto load win for me but even grub just sits there now and I have to hit enter to get win7 to load. I'm very new to Linux and really don't know where to start.

---

### Post by Rasa1111 on 2010-04-07
I think its just upset because you chose window$7 over it.  lol

I really have no idea what would cause it (other than window$) . :p
I can give you a bump though. 

 bump. 

good luck

---

### Post by 2hot6ft2 on 2010-04-07
> **6SPEED said:**
> I installed Ubuntu about 2 months ago on a partition with win7 and was using it off and on.
Does that mean it's installed on it's OWN partition?
Or is it installed inside windows on a partition aka WUBI?
> **6SPEED said:**
> I would get on Ubuntu about every other day and have had no real problems. It's been about a month now since I got on Ubuntu and when I tried to boot into with grub I just get a little white underscore at the top left corner and it just sits there. I let it go for 15 mins and my HDD light isn't even blinking. It's like it's mad at me for not using it, LOL.
Oh no you p'd it off, now you're in for it.:P
But seriously we need to know how it was installed first.

---

### Post by oldfred on 2010-04-08
If you have wubi in a NTFS partition:
Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

If it is not wubi, you may have rogue windows software
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)

---

### Post by 6SPEED on 2010-04-08
I installed it on it's own partition. I had Win7 on first and then made a 60gb partition which I installed Ubuntu on. Sorry it took so long to respond, I've been working 14 hour days at work.

---

### Post by 6SPEED on 2010-04-11
Anyone have any ideas before I format and have to start all over?

---

### Post by Rasa1111 on 2010-04-11
> **6SPEED said:**
> Anyone have any ideas before I format and have to start all over?


a fresh new install might be better/easier anyway. 
it really doesn't take that long. 
specially not if you've backed up your apps/programs. 
but even then, its pretty quick. 

thats all i got man. lol
g'luck

---

### Post by Rasa1111 on 2010-04-12
could this be your problem?
[http://ubuntuforums.org/showthread.php?t=1449431](http://ubuntuforums.org/showthread.php?t=1449431)

not the first ive heard about window$ 7 messing up Ubuntu. 

seriously, best bet would be to kill it and just learn Ubuntu.

---

### Post by evenso on 2010-04-12
> **6SPEED said:**
> Anyone have any ideas before I format and have to start all over?

Sure. 

Download the SuperGrub live CD, burn the iso from Win7 (don't copy and iso, it is a compressed image. If you don't have an iso burning feature, install XPCD--I think.) Boot SuperGrub and reinstall grub to the MBR. 

If that doesn't work, download the Knoppix live iso and burn a cd from Win7. Boot from it and run efsck on the *unmounted* Ubuntu partition. And/or mount it and run install grub from Knoppix. 

Similarly for the Ubuntu CD. You Ubuntu guys must have a rescue facility on there someplace. 

Now you have tools and practice at self-rescue, and maybe a bootable Ubuntu partition.

-- 
Kind Regards,
Freeman

---

### Post by 6SPEED on 2010-04-13
Thanks everyone for your responses. I'll will be trying some of these things out. My grub2 seems to work just fine though. I can boot into 7 everytime. Even when I pick ubuntu it looks like it's going to load normally, it always put the little blinking underscore in the corner but it used to blink about 5 times then load, not it just for every blinks. I'll have to make a new ubuntu cd and go from there. I just gotta get my GF off eBay for a little so I can get some face time with my computer. There may be a netbook in my future, ubuntu is the first thing that's gong on it.

---

### Post by 6SPEED on 2010-04-14
well I am on Ubuntu at the moment, finally. I used the supergrub live cd during boot it showed an error saying something about my splash theme and my res being 1280x1024. I didn't read it all it went quick. Do you think this has something to do with when I bought a new monitor I booted into Ubuntu and changed my res to 1600x1200?

---

### Post by 6SPEED on 2010-04-14
Well just restarted a couple times without the cd and all seems well. Only weird thing is my grub menu res changed and is it's so small you can barely read it, no biggie though, I can live with that. Thanks everyone very much for all your help.

---

### Post by drs305 on 2010-04-14
> **6SPEED said:**
> Well just restarted a couple times without the cd and all seems well. Only weird thing is my grub menu res changed and is it's so small you can barely read it, no biggie though, I can live with that. Thanks everyone very much for all your help.

The grub screen resolution is set by this line in /etc/default/grub. You may have larger values in an uncommented line similar to this one:
> #GRUB_GFXMODE=640x480

If you want to check, you can put a # symbol at the start of your line, if it is different, and then uncomment the line above to have a larger font size for the Grub menu only.

If you want to know what resolutions Grub 2 can use, at the Grub menu type "c" to get to a grub terminal and then type "vbeinfo" to see the supported resolutions.

If you make any changes, run "sudo update-grub" to update the Grub configuration file.

---

