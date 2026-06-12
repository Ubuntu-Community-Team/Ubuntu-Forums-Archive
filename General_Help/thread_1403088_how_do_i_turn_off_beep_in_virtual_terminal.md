---
title: "how do i turn off beep in virtual terminal?"
date: 2010-02-09
forum: General Help
---

### Post by btnz on 2010-02-09
hi there,
I'm running ubuntu 9.10 on a Dell XPS M1530. Sometimes i get a _VERY_ loud beep-sound, eg when i run out of battery or, the case that has me coming here when i'm working in a virtual terminal (tty1-6) and hit backspace once too often, that is, when the command line is actually empty.
Not that big of a deal you might think, but, especially when you're wearing good (read: possibly loud) headphones the experience is that god damn unpleasant that i'd like to make sure it won't happen again.
Oh and well, just hitting mute (in gnome, which doesn't have a lot to do with tty1 anyways) won't do the job.
So, how deep into the guts do i have to dig?

thx + greez

---

### Post by mohaakilla51 on 2010-02-09
edit /etc/modprobe.d/blacklist to contain the line:
blacklist pcspkr

and then reboot. AFAIK, this should work

---

### Post by btnz on 2010-02-09
sounds like a good idea to me, well, guess what - i just had a quick look into /etc/modprobe.d/blacklist.conf and found this little snippet there:

# ugly and loud noise, getting on everyone's nerves; this should be done by a   
# nice pulseaudio bing (Ubuntu: #77010)                                         
blacklist pcspkr   

i guess this means that pcspkr.ko should actually *not* get loaded, yet 

# modprobe -l | grep spkr
kernel/drivers/input/misc/pcspkr.ko

and

# modprobe -v pcspkr
insmod /lib/modules/2.6.31-19-generic/kernel/drivers/input/misc/pcspkr.ko

confusing, i find at least. after i run

# modprobe -r pcspkr

the output of # modprobe -l | grep spkr stays the same while # modprobe -v pcspkr returns nothing anymore.

Shouldn't /etc/modprobe.d/blacklist.conf actually prevent modules listed in there from getting loaded?
Other modules like de4x5 or eth1394 which are also listed in blacklist.conf also appear to be loaded (just to make sure, when 'modprobe -v [module name]' yields 'insmod [module path]', that means that it *is* loaded, right?).

Guess I'll do a reboot now and see what happens..

Edit:

So, rebooted a bunch of times, still have blacklist pcspkr in blacklist.conf, and things now start to really look weird:
right after reboot pcspkr is defenitely loaded, beeps like hell when i'm at tty1.
when i then run modprobe -v pcspkr once i get insmod ....spkr, but after that it is unloaded: no more beeps and any further
modprobe -v pcspkr doesnt return anything anymore.

Any explanations for this behaviour? Why isn't /etc/modprobe.d/blacklist.conf taken account of at startup?

---

