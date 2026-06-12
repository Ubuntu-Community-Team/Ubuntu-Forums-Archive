---
title: "Low graphics mode after upgrade; solved, but reset on every reboot"
date: 2010-05-12
forum: General Help
---

### Post by eternalthinker on 2010-05-12
Hi,
       I'm using Ubuntu 9.10. Recently after an upgrade my Ubuntu started running in low graphics mode. After searching through forums, I could finally fix it.
I'm not sure what exactly fixed it. I first changed the window manager to metacity. Run the following command:
```
sudo nvidia-xconfig --composite --render-accel --add-argb-glx-visuals
```And then changed window manager to compiz and desktop effects could be enabled.

The problem is, everytime I reboot, its again running in low graphics mode, desktop effects cannot be enabled, and I have to do all the troubleshooting again! Any idea how to permanently fix this?

EDIT: I found that the graphics is reset even without  typing the command everytime. But I still have to switch back and forth from compiz window manager to set it all right! :(

---

### Post by niite on 2010-05-13
Yeah, nvidia is pretty much hosed with 10.04.  I've been following the forums since it's release looking for some kind of permanent fix, but nothing so far.  i'm reseting my graphics after every boot - it's a pain.   Hopefully it will be resolved soon - it's starting to feel like the hulu 64bit problem -- it goes on and on and on with no word.

---

### Post by MSPdwalt on 2010-05-13
Is your user a member of the video group?

---

### Post by niite on 2010-05-13
well i finally found a fix -- i had  to change the grub config at /etc/default/grub   i changed "quiet splash" to "nomodeset" and it starts up without choking.

---

### Post by niite on 2010-05-13
> **niite said:**
> well i finally found a fix -- i had  to change the grub config at /etc/default/grub   i changed "quiet splash" to "nomodeset" and it starts up without choking.

Well that was a bust -- when i shut down, and let it sit.. upon boot up i get the same nvidia loading kernal error..  anyone have a solution for this yet?

---

### Post by itsols on 2010-07-24
Hi, have you found a solution to your problem? Even I'm having issues with my Dell Inspiron 1150.

Honestly I don't think it's your problem. Rather, it's everybody's... I have not heard of anyone so far on 10.4 'happily using' their systems.

Please update the forum when/if you solve the problem.

Thanks and all the best with the fix.

---

### Post by eternalthinker on 2010-07-24
> **itsols said:**
> Hi, have you found a solution to your problem? Even I'm having issues with my Dell Inspiron 1150.

Honestly I don't think it's your problem. Rather, it's everybody's... I have not heard of anyone so far on 10.4 'happily using' their systems.

Please update the forum when/if you solve the problem.

Thanks and all the best with the fix.

I've figured out a fix, but I'm not quite sure whether it will work with everyone else. My problem was that i had to switch back and forth through the window managers everytime. And, I'm using 9.10, and only an update caused the problem, it wasn't an upgrade to 10.04.
Anyways,** I put the compiz fusion icon in start up**, and then the graphics was all right from next boot onwards! I hope this helps.;)

---

### Post by itsols on 2010-07-24
Thank you for your prompt response. I mistook you to be a 10.4 user. Anyway, I've not heard of anyone moving from 9.10 successfully.

So it's best that you stick to your version until we (at least most of us) figure out how to get out of this mess or until we get some decent fixes.

Cheers!

---

