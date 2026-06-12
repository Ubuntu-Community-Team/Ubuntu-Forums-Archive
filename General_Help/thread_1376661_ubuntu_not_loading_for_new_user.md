---
title: "ubuntu not loading for new user"
date: 2010-01-09
forum: General Help
---

### Post by the_egg_man on 2010-01-09
i was on here earlier with some questions about moving my media to the Ubuntu desktop. i got the problem resolved, but i restarted my computer, and now Ubuntu won't load for me. I Have the option at startup to use Vista or ubuntu, but when i select Ubuntu, it gives me a black screen prompting a command. when i type "load" it says no kernel available or something similar... any ideas? 

i just got Ubuntu and spent all morning getting it just right, and now i can't get it back...:(

---

### Post by the_egg_man on 2010-01-09
Here's what i see when i select Ubuntu at start-up...

"GNU GRUB 1.97 beta 4


[Minimal Bash-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else, TAB  lists possible device/file completions]

sh:grub>" 

now, if i type boot and press enter, it says "No loaded kernel"

i've been using it all morning, not sure what happened... any help?

---

### Post by mk1w86 on 2010-01-09
What exactly did you do before having this problem? :-s

---

### Post by the_egg_man on 2010-01-09
i was just modifying the desktop, playing some videos. then i restarted and it went down. could it be because i was playing videos that were saved in my Vista documents? i'm brand new to this and am totally clueless...

---

### Post by warfacegod on 2010-01-09
On the black screen try typing startx. It sounds like you may have to reinstall gdm.

---

### Post by the_egg_man on 2010-01-09
i still have the iso disc i used, should i reinstall the whole "Wubi" thing?

again, forgive my ignorance. i'm not really tech-savvy...

---

### Post by warfacegod on 2010-01-09
Did you change any start up applications?

---

### Post by the_egg_man on 2010-01-09
honestly, i wouldn't even know how to do that... but i guess it's possible i did without knowing.

---

### Post by warfacegod on 2010-01-09
> i still have the iso disc i used, should i reinstall the whole "Wubi" thing?

You're running ubuntu inside Windows?

---

### Post by SecretCode on 2010-01-09
Not absolutely sure how you recover from this with a "wubi" installation.

At the sh:grub> line type *ls* and *ls /* and post the results.

---

### Post by the_egg_man on 2010-01-09
i didn't think i was. when i turn my pc on, i have the option to run windows vista or Ubuntu. but, now i'm running into this problem. but i just put the disc in, and windows asked if i wanted to run Wubi.exe.

but i thought i had actually downloaded/installed on my pc. not just running through windows.

---

### Post by the_egg_man on 2010-01-09
is that IS or LS?

---

### Post by warfacegod on 2010-01-09
Ls

---

### Post by normandstm on 2010-01-09
I have the same problem I have ubuntu 9.10 on sda1 and I intalled ubuntustudio 9.10 and he ask me to install grub.  what I did but my system wont start anymore.  it said grub loading. and after that rescue:grub> I did tab to get the command but went I do any command it said does not exist.  ???????  I tried with live cd to reinstall grub but still the same.

---

### Post by warfacegod on 2010-01-09
I think both of you need to try typing *startx* on the black screen.

---

### Post by SecretCode on 2010-01-09
lower case L, lowercase S

warfacegod ... egg_man is stuck in a grub prompt. Do you think startx is a good option there? :wink:

egg_man ... the wubi install uses a file within your windows file system, but it boots directly into ubuntu (via the boot loader screen that you've seen); windows isn't running at the same time. It's what you have, I'm sure!

---

### Post by warfacegod on 2010-01-09
> warfacegod ... egg_man is stuck in a grub prompt. Do you think startx is a good option there?

No. I'd forgotten that aspect, I was thinking a shell command prompt. My apologies egg_man.

---

### Post by warfacegod on 2010-01-09
Credit for this goes to meierfra. 

Type this at "grub sh>" prompt:

Code:

set Path=/ubuntu/disks/root.disk
search -f --set=Root ${Path} 
probe -u (${Root})  --set=UUID   
linux /vmlinuz root=UUID=${UUID} loop=${Path}  ro
initrd /initrd.img
boot

Once booted in Wubi, open a terminal and type

Code:

sudo update-grub

---

### Post by the_egg_man on 2010-01-09
i type all that code in one line? does spacing matter? 
i just downloaded the ISO file from their website again. burned it, installed it. it did everything. it determined how much space ubuntu should take (i did not delete vista, and am having to use it now.) everything seemed fine. then i had to restart for some installations i did (trying to get compizconfig) and when i restarted, i had the same problem all over again... it's been a stressful day trying to get ubuntu running and then actually stay anytime i restart my pc. 

i'm starting to wonder if i should stick to Windows... i'm a novice in every sense of the word, but was hoping to teach myself...

---

### Post by warfacegod on 2010-01-09
> i type all that code in one line? does spacing matter?

No. One line at a time hit enter. Yes. Spacing does matter.


> everything seemed fine. then i had to restart for some installations i did (trying to get compizconfig) and when i restarted, i had the same problem all over again...

I think that virtually all of the problem is that your doing a wubi install as opposed to a true dual boot.


It's much easier to teach yourself linux than windows. I've learned 5 times as much in the last three years with linux than I learned the previous six years in windows. Don't give up hope!

---

### Post by michy99 on 2010-01-09
Eggman, I think you would do best to make a real dual boot system and forget about Wubi. This is what you would need to do:

1. In Vista, uninstall Ubuntu.
2. Still in Vista, defragment your drive and then resize the partition to make room for Ubuntu.
3. Boot from the Ubuntu disk. (Don't open it in Windows. Boot from it.)
4. Choose to install side-by-side with Windows.

---

### Post by the_egg_man on 2010-01-09
thanks. i really want to learn it... i've been watching youtube tutorials and reading about it for a while. 

so, how would i go about doing a dual boot? would that be easier? i'm just terrified of anything that will cause me to lose my music/pics/vids...

---

### Post by the_egg_man on 2010-01-09
michy, i tried that. i didn't uninstall ubuntu (can't find it in programs) but i did boot from disc, and it went through that whole process and gave me the option to run side-by-side, but when i restarted, i had this same issue.

---

### Post by the_egg_man on 2010-01-09
michy, sorry. i should have tried again before replying. okay, i DID uninstall Ubuntu just now. defragging now... how do i go about resizing partition? and how much room should i set aside for ubuntu?

---

### Post by warfacegod on 2010-01-09
Put the disc into the cd drive and reboot eventually you'll see something that says try ubuntu without installing pick that. If you are that concerned about your files then make a backup in Windows. Copy them to another drive, a few dvds, a dozen cds, or 40,000 floppy disks.

---

### Post by michy99 on 2010-01-09
Here's a page I found about resizing partitions in Vista. 20 Gigs for Ubuntu is probably enough to start out with. The system itself only needs about 8 gigs.

[http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)

---

### Post by warfacegod on 2010-01-09
michy99:

> Here's a page I found about resizing partitions in Vista. 20 Gigs for Ubuntu is probably enough to start out with. The system itself only needs about 8 gigs.

I agree that 20 GB is probably more than enough but wouldn't using gparted in a livecd be safer? I've seen some bad results from resizing in Windows (I've seen good too though).


the_egg_man:

If you don't want to make two partitions for ubuntu (one for the OS the other for your pictures and stuff) I would suggest going much bigger than 20 GB. Remember, Make a backup!

---

### Post by michy99 on 2010-01-09
> **warfacegod said:**
> michy99:



I agree that 20 GB is probably more than enough but wouldn't using gparted in a livecd be safer? I've seen some bad results from resizing in Windows (I've seen good too though).

I've heard exactly the opposite, that Vista does not like its partition to be resized by other partitioners.

---

### Post by warfacegod on 2010-01-09
> I've heard exactly the opposite, that Vista does not like its partition to be resized by other partitioners. 

Yeah, you're right now that you mention it, I recall seeing bunches of threads about Vista going haywire because of that.

---

### Post by the_egg_man on 2010-01-09
hey guys. well, it looks like it's worked. (fingers crossed.) thanks for the help... i guess now it's time to start customising! 

thanks again!!!

---

### Post by warfacegod on 2010-01-10
If you're still using a wubi install and this comes up again, see post #8.

[http://ubuntuforums.org/showthread.php?t=1377175]("http://ubuntuforums.org/showthread.php?t=1377175")

---

