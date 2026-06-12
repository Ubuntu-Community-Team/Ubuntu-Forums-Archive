---
title: "Machine boots before video card can wake up"
date: 2010-06-22
forum: General Help
---

### Post by hwttdz on 2010-06-22
I have a feeling that my machine is booting before my video card can wake up and I'm wondering if there's some way I can put a sleep command in the bootup so that it stalls for a while.  I'm not quite sure where it would have to go, because it would have to be after the video card is awoken but before the video card needs to be ready.  The behavior I'm seeing is that:

1) gdm fails to start and I get a message about graphics errors, I can then boot to failsafe graphics, view logs or drop to terminal
2) if I drop to terminal and run "sudo service gdm start" I get functioning accelerated graphics

This is a minimal boot and startup time as recorded by bootchart is right around 4 seconds (3.99 last boot).  I'm totally ok with a 5 second boot, or 10 seconds, I just want it to work every time.  But I don't want to go to a full install.

---

### Post by hwttdz on 2010-06-22
Looks like what I'm going to want to do is put a script in /etc/rc#.d/ and then run "update-rc.d script defaults" of course the issue I'm going to run into is ordering.

---

### Post by cascade9 on 2010-06-22
I'm not convinced its the video card 'not waking up' causing the problem, but there is a way to delay booting without having to make scrpits, etc. On some motherboards anyway. 

Just go ito the BIOS and see if there is a 'delay IDE initialisation' or a setting like that. Add a few seconds there ;)

---

### Post by hwttdz on 2010-06-22
It is possible something else is causing the problem, but 
1) Graphics fail to start on boot, but start flawlessly from the command line after failing to start automatically
2) The system sometimes fails to find "/dev/nvidiactl" on boot but it exists later when I check for it, 
so it was the only plausible explanation I could come up with.  

Wouldn't putting the pause there not help as the system doesn't start to boot, and therefore doesn't try to "mount" the video card until after all the drives are mounted?

Oh and I should add, I have gotten the "failed to initialize the nvidia kernel module" error with the not found /dev/nvidiactl error.  (with this evidence I think it's almost certainly video card related, not saying it's necessarily my guess of not waking up in time, just that seemed consistent with the poor behavior on boot, but better behavior after boot from command line, also after installing a program, bootchart for instance, ureadahead is run at boot slowing down boot and graphics work)

---

