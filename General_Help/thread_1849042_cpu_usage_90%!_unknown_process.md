---
title: "cpu usage 90%! unknown process"
date: 2011-09-23
forum: General Help
---

### Post by sdowney717 on 2011-09-23
something running but what, when I open system monitor there is nothing I can see gobbling up the cpu.

---

### Post by sdowney717 on 2011-09-23
ok running top shows a root process eating the cpu
what to do?

udevd cpu brings up this notice for massive cpu usage on gutsy, but I running latest ubuntu 
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/130818](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/130818)

---

### Post by sdowney717 on 2011-09-23
dmesg giving constant message!

```
[510547.865263] VFS: busy inodes on changed media or resized disk sr1
[510547.887924] VFS: busy inodes on changed media or resized disk sr1
[510547.915164] VFS: busy inodes on changed media or resized disk sr1
[510547.925264] VFS: busy inodes on changed media or resized disk sr1
[510547.947798] VFS: busy inodes on changed media or resized disk sr1
[510547.975291] VFS: busy inodes on changed media or resized disk sr1
[510547.995638] VFS: busy inodes on changed media or resized disk sr1
[510548.018178] VFS: busy inodes on changed media or resized disk sr1
[510548.090050] VFS: busy inodes on changed media or resized disk sr1
[510548.100262] VFS: busy inodes on changed media or resized disk sr1
[510548.122923] VFS: busy inodes on changed media or resized disk sr1
[510548.150165] VFS: busy inodes on changed media or resized disk sr1
[510548.160138] VFS: busy inodes on changed media or resized disk sr1
[510548.182923] VFS: busy inodes on changed media or resized disk sr1
[510548.210414] VFS: busy inodes on changed media or resized disk sr1
[510548.220387] VFS: busy inodes on changed media or resized disk sr1
[510548.242924] VFS: busy inodes on changed media or resized disk sr1
[510548.271136] VFS: busy inodes on changed media or resized disk sr1
[510548.286012] VFS: busy inodes on changed media or resized disk sr1
[510548.308422] VFS: busy inodes on changed media or resized disk sr1
[510548.385801] VFS: busy inodes on changed media or resized disk sr1
[510548.395763] VFS: busy inodes on changed media or resized disk sr1
[510548.418549] VFS: busy inodes on changed media or resized disk sr1
[510548.446164] VFS: busy inodes on changed media or resized disk sr1
[510548.456262] VFS: busy inodes on changed media or resized disk sr1
[510548.478928] VFS: busy inodes on changed media or resized disk sr1
[510548.506790] VFS: busy inodes on changed media or resized disk sr1
[510548.516888] VFS: busy inodes on changed media or resized disk sr1
[510548.539424] VFS: busy inodes on changed media or resized disk sr1
[510548.566790] VFS: busy inodes on changed media or resized disk sr1
[510548.577013] VFS: busy inodes on changed media or resized disk sr1
[510548.599425] VFS: busy inodes on changed media or resized disk sr1
[510548.627040] VFS: busy inodes on changed media or resized disk sr1
[510548.637262] VFS: busy inodes on changed media or resized disk sr1
[510548.660095] VFS: busy inodes on changed media or resized disk sr1
[510548.687039] VFS: busy inodes on changed media or resized disk sr1
[510548.698263] VFS: busy inodes on changed media or resized disk sr1
[510548.721049] VFS: busy inodes on changed media or resized disk sr1
[510548.748791] VFS: busy inodes on changed media or resized disk sr1
[510548.759643] VFS: busy inodes on changed media or resized disk sr1
[510548.783300] VFS: busy inodes on changed media or resized disk sr1
[510548.809165] VFS: busy inodes on changed media or resized disk sr1
[510548.819389] VFS: busy inodes on changed media or resized disk sr1
[510548.842303] VFS: busy inodes on changed media or resized disk sr1
[510548.869289] VFS: busy inodes on changed media or resized disk sr1
[510548.883263] VFS: busy inodes on changed media or resized disk sr1
[510548.905926] VFS: busy inodes on changed media or resized disk sr1
[510548.984161] VFS: busy inodes on changed media or resized disk sr1
[510548.994514] VFS: busy inodes on changed media or resized disk sr1
[510549.006448] VFS: busy inodes on changed media or resized disk sr1
[510549.033062] VFS: busy inodes on changed media or resized disk sr1
[510549.099802] VFS: busy inodes on changed media or resized disk sr1
[510549.110013] VFS: busy inodes on changed media or resized disk sr1
[510549.132422] VFS: busy inodes on changed media or resized disk sr1
[510549.159912] VFS: busy inodes on changed media or resized disk sr1
[510549.179763] VFS: busy inodes on changed media or resized disk sr1
[510549.202430] VFS: busy inodes on changed media or resized disk sr1
[510549.275038] VFS: busy inodes on changed media or resized disk sr1
[510549.292532] VFS: busy inodes on changed media or resized disk sr1
[510549.315925] VFS: busy inodes on changed media or resized disk sr1
[510549.398339] VFS: busy inodes on changed media or resized disk sr1
[510549.415513] VFS: busy inodes on changed media or resized disk sr1
[510549.438178] VFS: busy inodes on changed media or resized disk sr1
[510549.511539] VFS: busy inodes on changed media or resized disk sr1
[510549.524639] VFS: busy inodes on changed media or resized disk sr1
[510549.547424] VFS: busy inodes on changed media or resized disk sr1
[510549.622551] VFS: busy inodes on changed media or resized disk sr1
[510549.632512] VFS: busy inodes on changed media or resized disk sr1
[510549.656125] VFS: busy inodes on changed media or resized disk sr1
[510549.683417] VFS: busy inodes on changed media or resized disk sr1
[510549.693514] VFS: busy inodes on changed media or resized disk sr1
[510549.717173] VFS: busy inodes on changed media or resized disk sr1
[510549.743164] VFS: busy inodes on changed media or resized disk sr1
[510549.753263] VFS: busy inodes on changed media or resized disk sr1
[510549.777424] VFS: busy inodes on changed media or resized disk sr1
[510549.803290] VFS: busy inodes on changed media or resized disk sr1
[510549.823639] VFS: busy inodes on changed media or resized disk sr1
[510549.846054] VFS: busy inodes on changed media or resized disk sr1
[510549.917913] VFS: busy inodes on changed media or resized disk sr1
[510549.928023] VFS: busy inodes on changed media or resized disk sr1
[510549.950424] VFS: busy inodes on changed media or resized disk sr1
[510549.978041] VFS: busy inodes on changed media or resized disk sr1
[510549.988140] VFS: busy inodes on changed media or resized disk sr1
[510550.013552] VFS: busy inodes on changed media or resized disk sr1
[510550.038038] VFS: busy inodes on changed media or resized disk sr1
[510550.049140] VFS: busy inodes on changed media or resized disk sr1
[510550.071675] VFS: busy inodes on changed media or resized disk sr1
[510550.098164] VFS: busy inodes on changed media or resized disk sr1
[510550.108263] VFS: busy inodes on changed media or resized disk sr1
[510550.131174] VFS: busy inodes on changed media or resized disk sr1
[510550.156288] VFS: busy inodes on changed media or resized disk sr1
[510550.166389] VFS: busy inodes on changed media or resized disk sr1
[510550.189300] VFS: busy inodes on changed media or resized disk sr1
[510550.215786] VFS: busy inodes on changed media or resized disk sr1
[510550.226014] VFS: busy inodes on changed media or resized disk sr1
[510550.248800] VFS: busy inodes on changed media or resized disk sr1
[510550.277418] VFS: busy inodes on changed media or resized disk sr1
[510550.287642] VFS: busy inodes on changed media or resized disk sr1
[510550.310309] VFS: busy inodes on changed media or resized disk sr1
[510550.341558] VFS: busy inodes on changed media or resized disk sr1
[510550.351640] VFS: busy inodes on changed media or resized disk sr1
[510550.374312] VFS: busy inodes on changed media or resized disk sr1
[510550.447060] VFS: busy inodes on changed media or resized disk sr1
[510550.457142] VFS: busy inodes on changed media or resized disk sr1
[510550.480064] VFS: busy inodes on changed media or resized disk sr1
[510550.560168] VFS: busy inodes on changed media or resized disk sr1
[510550.570392] VFS: busy inodes on changed media or resized disk sr1
[510550.593178] VFS: busy inodes on changed media or resized disk sr1
[510550.671932] VFS: busy inodes on changed media or resized disk sr1
[510550.682017] VFS: busy inodes on changed media or resized disk sr1
scott@scott-P5QC:~$ 

```

---

### Post by sdowney717 on 2011-09-23
I unplugged a usb thumb drive I had left plugged in overnight and rebooted and the problem went away. So dont leave flash drives plugged in too long or the CPU will cook. Or perhaps just reboot after you finish using a flash drive.):P

glad it is solved now. HAHA. sure it is.

FWIW, this particular flash drive 4gb with 32,000 files brought my wifes work PC with vista to its knees and eventually caused it to crash so she had to reboot. Virus anyone has thoughts? Her computer slowed got slower and slower then it would not repond anymore and the thing then crashed. I dont know why, we used that flash drive to copy oddles of pictures from my daughters xp laptop. So she brings it home to me to look at and there is nothing odd that I see, so I just left it plugged into my ubuntu pc. Then a few minutes ago I noticed the cpu going crazy. But maybe the cpu was going crazy all night long.

---

### Post by Frogs Hair on 2011-09-23
UDEVD [http://www.linuxmanpages.com/man8/udevd.8.php](http://www.linuxmanpages.com/man8/udevd.8.php)

---

### Post by sdowney717 on 2011-09-23
yes, as soon as I saw udevd and hotplug I remembered the flash drive I left plugged into the PC. Simply unplugging did not help so I rebooted and problem is gone away. 

SO what is going on with the flash drive??

---

### Post by WorMzy on 2011-09-23
Are you sure it was the flash stick? As far as I know, sr# refers to an optical drive (e.g. CD or DVD).

Flash sticks should be sd[a-z].

---

### Post by sdowney717 on 2011-09-24
there was no disc in the drive and I have not used the drive for days and days. Why would the dvd drive do anything when it is empty?

a mystery
[http://thebigbyte.blogspot.com/2010/02/vfs-busy-inodes-on-changed-media-or.html](http://thebigbyte.blogspot.com/2010/02/vfs-busy-inodes-on-changed-media-or.html)

---

### Post by dino99 on 2011-09-24
so the "zombie" process are gone now ?

---

### Post by sdowney717 on 2011-09-24
yes, no more cpu activity.
I plugged in the flash drive again and after an hour got this message

trying to load the drive shows this, so is it ruined?
just saw that, so maybe the flash drive is broken now.

---

### Post by sdowney717 on 2011-09-24
weird, ok put usb flash drive back in, open places, and get this 
'SR1' message when I click the U3 drive, which is flash drive USB.

there is no disc in the dvd drive!

---

### Post by WorMzy on 2011-09-24
Yeah, if your USB stick is claiming to be an optical drive, there's probably something *very* wrong with it.

Either that, or there's something wrong with udev (it's unlikely, but still possible).

If the USB stick is malfunctioning on Windows too, then I'd say that it's definitely the cause. Bin it.

---

