---
title: "No sound after Hardware change"
date: 2010-10-20
forum: General Help
---

### Post by satish_j on 2010-10-20
After changing the M/B from Intel to Gigabyte,Lucid stopped playing sound.System is using XP also and it(XP) plays the sound properly after installing its chipset drivers.
Are there any propriety drivers that needs to be installed in Lucid to get it working??
Thanxx..

---

### Post by mastablasta on 2010-10-20
Yes you can try to upgrade alsa.
 
Can you post output from a ```
lspci
``` command in terminal first to see what sound card you have?

---

### Post by satish_j on 2010-10-21
> **mastablasta said:**
> Yes you can try to upgrade alsa.
 
Can you post output from a ```
lspci
``` command in terminal first to see what sound card you have?

I can see the output of above command.It gives me a lot of output.Internet is not working at my home so i cannot forward the command output on office mailID.But,it does shows some Intel HDA ALC in output.
Will this info suffice or the output still required?:(

---

### Post by mastablasta on 2010-10-21
intel hda - hmm.... sitll can't say what exactly the card is. but you will probably need to upgrade your ALSA (these are basically sound drivers). i too have new intel chips and had a similar issue. note that this requires you to have internet connection and also "build essentials" are quite big (150MB).
 
There is an upgrade script available.
 
however, i followed this guide: [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
just copy pasted the command one by one in terminal.
 
works perfectly now. though surround sound works mic doesn't when using it. however isnce i have only two speakers and stereo is enough for me i just use stereo analog duplex. in this setting both mic and speakers work well.
 
a word of advice after upgrading alsa you will have to be carefull not to install any sound libraries (libsound wahtever...) as they overwrite the new files necessary for upgrade to work. i did this and i had to repeat the whole upgrade thing to get the sound back. :-)

---

### Post by satish_j on 2010-10-24
i downloaded build-essentials from synaptic,rebooted,but still NO SOUND IN LUCID

---

### Post by satish_j on 2010-10-25
Bump..pls help..goig crazy w/o sound..My audio codec ALC Realtek 887

---

### Post by satish_j on 2010-10-28
Solved.Thanks to below post..
[http://ubuntuforums.org/showpost.php?p=10014033&postcount=11]("http://ubuntuforums.org/showpost.php?p=10014033&postcount=11")

---

