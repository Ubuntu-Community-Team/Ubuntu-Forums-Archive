---
title: "Slow DVD Writing?"
date: 2005-02-25
forum: General Help
---

### Post by bobmitch on 2005-02-25
I have a pioneer A08 16x dvd writer.

Using k3b and Graveman, using auto for most settings, the software reports that it is attempting to write at 16x, as expected, but at most manages something akin to 2x, or about 2MB/s - taking up to 25 minutes to write a dvd.

This also seems to take a huge amount of cpu power. (Running on an xp2800+)

Are there known issues with these apps - or rather the command line tools they wrap around for dvd writing?

Whilst I can`t test it right now, I believe that creating an iso manually, and the burning that with nautilus disk writer, it writes at an acceptable rate.

Any help or pointers appreciated,
Rgds,
mitch

---

### Post by jdodson on 2005-02-25
[QUOTE=bobmitch]I have a pioneer A08 16x dvd writer.

Using k3b and Graveman, using auto for most settings, the software reports that it is attempting to write at 16x, as expected, but at most manages something akin to 2x, or about 2MB/s - taking up to 25 minutes to write a dvd.

This also seems to take a huge amount of cpu power. (Running on an xp2800+)

Are there known issues with these apps - or rather the command line tools they wrap around for dvd writing?

Whilst I can`t test it right now, I believe that creating an iso manually, and the burning that with nautilus disk writer, it writes at an acceptable rate.

Any help or pointers appreciated,
Rgds,
mitch[/QUOTE]

this doesnt help, but i have the same problem.  havent created an iso manually though to try it.  i figured i would wait for a better driver or program to fix the problem.  16x dvds are still pretty new, though that shouldnt matter.

---

### Post by bobmitch on 2005-02-25
[QUOTE=jdodson]this doesnt help, but i have the same problem.  havent created an iso manually though to try it.  i figured i would wait for a better driver or program to fix the problem.  16x dvds are still pretty new, though that shouldnt matter.[/QUOTE]

Well, I do feel better knowing I`m not alone. :)

I only discovered the problem because I`m running on a measly 10gig linux test partition and needed to burn using on-the-fly type method, as I didn`t have room to create the iso first.

I`ve a hunch the problem is related to how the 'growisofs' application is being used - but I am not experienced enough with linux yet to figure out what is going wrong.

If you find out any more info, post here or pm me.  (I will do likewise)

Cheers,
mitch

---

### Post by KLineD on 2005-03-01
It is indeed slower to write DVDs (and CDs I think also) using Linux. I say this because I'm running a dual boot machine and in XP one DVD writes in something like 10 minutes and in Linux it takes as long as 25-30 minutes.

Also ripping with DVDShrink in linux takes longer than in windows.

But I dont know the reason...

---

### Post by KLineD on 2005-03-02
I figured it out, it involves using hdparm to tweak the drives. Now I can burn at the same speed as in Windows, yet another reason not to boot that OS.

Anyway, the directions I followed where from [a Gentoo Wiki page](http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance) but it applies to any distro as long as you have hdparm installed. My Hoary installation came with hdparm installed so it should be there, just add sudo to any command you do with hdparm.

To make the changes permanent, that guide doesn't apply to ubuntu. First, the hdparm config file is located in /etc/hdparm.conf

That file is well documented and with a little reading anyone should be able to add the needed lines. As an example, my hdparm.conf file looks like this:

> /dev/hdb {
        write_cache = on
        dma = on
        transfer_mode = 68
        interrupt_unmask = on
        io32_support = 3
}

/dev/hdc {
        write_cache = on
        dma = on
        transfer_mode = 68
        interrupt_unmask = on
        io32_support = 3
}

These commands should be taken just as an example since all hardware is different. Once you get it right, save the changes and it's time to make another change. When booting, the hdparm file gets executed too early and only the parameters for the hard disks suceeded (at least in my installation) so I read somewhere in this forum the following solution:

First, go to /etc/rcS.d and do a 'ls'
In the listing, you should see S##hdparm where ## are some numbers I dont remember right now, I think the numer starts with 0
Now, remove the file with 'sudo rm S##hdparm' again substitute the ## with the correct numbers.
To finalize, do a 'ln -s /etc/init.d/hdparm S29hdparm' and that recreates the symbolic link but it sets to an apropiate execution time in the boot process.

And that's it, reboot to see if the new parameters for your drives are correct using hdparm.

As a sidenote, using the benchmark command 'hdparm -tT /dev/hdb' didn't show a significant improvement in my drives, in fact sometimes is was even slower, but burning with K3B, ripping with DVDShrink or burning with Nautilus CD/DVD burner improved a lot, I mean from 25-30 minutes to 5-7 minutes.

I hope this helps someone with the same problems I had, if this has been posted in the wiki I'm sorry but I couldn't find anything and if it hasn't well someone should!

---

### Post by bobmitch on 2005-03-02
[QUOTE=KLineD]I figured it out, it involves using hdparm to tweak the drives. Now I can burn at the same speed as in Windows, yet another reason not to boot that OS.
<snip>
I hope this helps someone with the same problems I had, if this has been posted in the wiki I'm sorry but I couldn't find anything and if it hasn't well someone should![/QUOTE]

Thanks for the heads up.  Looks like DMA wasn`t set on the dvd rom.

Will work on setting this up in my conf file and hopefully things will speed up.  (My conf file will match yours, only just for hdc)

Cheers!

---

### Post by vassalle on 2005-03-16
hi, ive tried changing my hdparm.conf using the tip from KlineD, but somehow it didnt work.. i know he said that all hardware are different but how could i find out what to put in my hdparm? anyway, tried this command. and got the resulting error.. 
vassalle@vassalle:~$ hdparm -d1 /dev/hdd

/dev/hdd:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Permission denied
 using_dma    =  0 (off)

after following all the steps mentioned.. Note that, ive changed hdb/hdc to hdc/hdd since mine is the latter.. hope someone could help me here.. thanks in advance!

---

### Post by bobmitch on 2005-03-16
Have you tried running the command with **sudo**?

ie.  sudo hdparm blahblahablah

---

### Post by vassalle on 2005-03-16
[QUOTE=bobmitch]Have you tried running the command with **sudo**?

ie.  sudo hdparm blahblahablah[/QUOTE]
 yeah.. i did that.. got the same error.. :( im using hoary btw..

---

### Post by IdoMcFly on 2005-03-16
[QUOTE=vassalle]yeah.. i did that.. got the same error.. :( im using hoary btw..[/QUOTE]
 see this : [http://www.ubuntuforums.org/showthread.php?t=19519&highlight=hdparm](http://www.ubuntuforums.org/showthread.php?t=19519&highlight=hdparm)

---

### Post by vassalle on 2005-03-16
[QUOTE=IdoMcFly]see this : [http://www.ubuntuforums.org/showthread.php?t=19519&highlight=hdparm](http://www.ubuntuforums.org/showthread.php?t=19519&highlight=hdparm)[/QUOTE]
 wooottt.. that worked!! thanks!

---

### Post by IdoMcFly on 2005-03-16
[QUOTE=vassalle]wooottt.. that worked!! thanks![/QUOTE]
 you're welcome ;)

---

### Post by kuleali on 2005-03-27
hear is my hdparm.conf

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}
#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}


i have a 16x dvd writer

---

### Post by kagou on 2005-04-01
[QUOTE=kuleali]hear is my hdparm.conf

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}
#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}


i have a 16x dvd writer[/QUOTE]

All parameters are commented so they are not applied

---

