---
title: "Can't even start in 'low graphics mode'"
date: 2010-05-06
forum: General Help
---

### Post by broken sword on 2010-05-06
I'm not sure where this goes, so I'm starting off here since I'm using the 64 bit version of 9.10

I've had a few issues with this install, but haven't really had time to fix them because I work with my laptop.

One thing that's constantly been happening is that for some reason, the video drivers fail. Normally, I just re-install the NVIDIA drivers after logging into the console, and everything works fine. Not so recently, now I'm getting the following error:

Ubuntu is running in low-graphics mode

> Your screen, graphics card and input device settings could not be detected correctly. You will need to configure these yourself.

The following screen give me the option to 'run ubuntu in low graphics mode for just one session', 'reconfigure graphics', 'troubleshoot the error' and 'exit to console login'

I can't even run it in low graphics mode, it exits right to the console. I've checked the log files, but I can't seem to find a clue as to what's going on. I'm also getting the following message:

> (EE) xf86OpenSerial cannot open device /dev/input11

This isn't the exact error message, it only appeared twice but I didn't catch all of it.

Any help would be appreciated, I'm typing on another computer. Can't include any log files just yet.

Also getting the following error:

>  (ee) --failed to initialize glx extension ( compatible nvidia x driver nout found ) 

---

### Post by ma3ahmed on 2010-06-05
i am facing the same problem. i tried to upgrade to ubuntu 10.04 and still no use... my keyboard and mouse arn't working either... i upgraded it from recovery mode...

---

### Post by rantingmoose on 2010-09-18
I'm in the same boat.  Well, my dad is, anyway.  I'm using his computer at the moment from the live CD, as his machine doesn't appear to want to start X properly.  Each time I try to fire it up I get:

(EE) [drm] KMS not enabled
(EE) Failed to initialize GLX extension (Compatible Nvidia X driver not found)

In looking in the log of errors I see a line:

Error setting MTRR, inappropriate ioctl for device (25)

When I'm asked what I want to do, I can try running in Low Grpahics Mode for this time only, but that just hangs.  Asking it to reconfigure graphics and then restarting X does the same.  I can drop out to a command line, but that's the only step that seems to go anywhere.  Obviously, though, it doesn't get me where I want to go.

I'm no expert, though I am the one who recommended he try Ubuntu about 18 months ago, and he's been pretty happy with it.  I tried it for a while, but after it failed to resolve the problem I had hoped was a Windows thing (turned out to be my laptop), and causing all sorts of others, I went back to the dark side.  I don't want to go down that road here if it can be avoided.

Thanks for any assistance!

---

