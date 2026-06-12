---
title: "Boot hangs, can't debug (but startx works)!"
date: 2011-08-30
forum: General Help
---

### Post by roastbeef on 2011-08-30
I can't seem to boot normally - I turned off 'quiet splash' in my grub config to see the boot process, and after "Starting CUPS printing spooler/server     [OK]" it just sits there indefinitely.   HOWEVER, if I start in recovery mode I can get to the command line, then run 'startx' and that works fine.

Any advice in where to look would be greatly appreciated.  I've been attempting to comb through log files but I'm not seeing anything.  I tried enabling boot logs but the boot logs are very small and not the output of what I'm seeing on screen during the boot process (I did a grep -r for cups in my /var/log directory and I don't get that 'Starting CUPS' line anywhere).

---

### Post by Wim Sturkenboom on 2011-08-31
I have a similar experience; my desktop hangs about every second boot ever since I replaced my video card. Most of the time (99% ?) at 'checking battery state' (this is a desktop so it must be checking the cmos battery :) ), I've seen it once or twice that it will be at 'cups'. It however always says that the starting of the process where it hangs is [OK].

I doubt very much that it is any of the 'processes' that you see being started. I think that that is only the case if there is no [OK] or [FAIL] at the end of the line.

Reason why I say this is that it's my understanding that the upstart process is more or less starting tasks in 'parallel'.

To solve / work around / debug the issue, I would prevent the system from starting gdm. Ubuntu seems to have made this about impossible in my opinion (it used to be so bloody easy by changing the default runlevel) but one way is to replace the *_quiet splash_* in the grub boot line by *_text_*. That should take you to a console where you can login.

If this works reliably (no hanging), it would indicate some kind of bug in the bootup in my opinion where starting gdm is waiting for something (that might even be waiting for something else again).

Once logged in, you can run *_sudo service gdm start_* or *_startx_* to start the gui environment. Some research on the web shows that startx might not be the way to go (see [http://ubuntuforums.org/showthread.php?t=1305659&page=3](http://ubuntuforums.org/showthread.php?t=1305659&page=3))

I'm not behind my faulty system at the moment (tested the above on another system) but I'm going to try it tonight.

If you can get reliably into the gui environment that way, I feel that the issue is in the combination of upstart / gdm; the latter might involve the driver that you use (I would include it in my scenario).

My (rough) specs
not sure about the motherboard at the moment
AMD 3000+ with 1GB memory
nVidia 8400 (GS?) based video card
ubuntu 10.04/64 bit
nvidia drive 260.something

I don't have the problem on a Dell Optiplex 780 (running 10.04/64 bit) nor on a laptop running 10.04/32 bit (both without additional drivers).

Note
thanks for posting; it made me finally start digging into the problem ;)

---

### Post by Wim Sturkenboom on 2011-09-01
Just a little update

I had a little time to test it a bit. Booted to a console by default and rebooted about 10 times. Did not hang once. Did try to start gdm from the console twice in those 10 attempts and that also does not give problems.

So the workaround works for me. [COLOR="Blue"]*Can you try it?*[/COLOR]

---

### Post by roastbeef on 2011-09-01
Well after I posted this things got worse - Grub stopped getting loaded and then I couldn't boot anything except a live CD.

I ended up re-installing but Grub still wasn't loading.  I reordered the drive order in my BIOS which fixed that, and since then everything has been good again. :/  Sorry I can't be of more help.

---

### Post by Wim Sturkenboom on 2011-09-01
No problem, your problem is solved. I'm going to study the boot process a bit more ;)

Please mark your thread as solved using the thread tools just above the first post.

---

### Post by xtremesupremacy3 on 2011-09-04
Firstly, do you have a Nvidia card by any chance?

If you go into Grub and delete 'quiet splash' and replace it with 'nomodeset', what happens then?

---

### Post by sevenmil on 2011-09-04
I can't get 11.04 to run I keep getting** input not support**, roving around the screen, or (initramsf) on screen. nothing happens?

---

