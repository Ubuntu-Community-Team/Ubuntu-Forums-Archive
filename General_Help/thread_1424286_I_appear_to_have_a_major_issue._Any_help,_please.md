---
title: "I appear to have a major issue. Any help, please?"
date: 2010-03-07
forum: General Help
---

### Post by rcayea on 2010-03-07
I really don't know how this issue started but here I go.

When I turn on my computer, Ubuntu gets just passed the splash screen and I get a little notice that says, "Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself."

I click OK (which is one option and the other is cancel). After clicking ok, I am sent to the screen that gives me the option to run Ubuntu in low graphics mode and so on. However, none of those options work and I can never even load Ubuntu in failsafe mode.


I did just use a wireless mouse for about all of 5 minutes and then it froze computer and I stopped using it. That is all I can think of that might have caused this message.  


I would greatly appreciate any attention you can give me tonight. 

thanks,
Randy

---

### Post by pastalavista on 2010-03-07
At the first boot screen (manufacturer motherboard), press and hold the 'shift' key to access the grub menu... select the 2nd option (recovery mode) where you'll get more options to repair your system.

---

### Post by rcayea on 2010-03-07
Thanks. I'll go give the "Shift Key" option a try. 

Randy

---

### Post by rcayea on 2010-03-07
I apologize if I mis-typed my issue. I do get to the kernel screen. I select my recent kernel or even my failsafe kernel and then my issue happens, as described above.

Any other ideas?

Thanks,
Randy

---

### Post by pastalavista on 2010-03-07
Ah, sorry I misunderstood. Only option I know is booting up the live CD and running a terminal from there. I would try
```
sudo fsck -C /dev/sda*
```
Replace the 'sda*' with the drive# (sda/hda) of your installed root partition.

---

### Post by rcayea on 2010-03-07
ok, thanks. since I am on livecd now, I will give this a try. thanks again.

---

### Post by rcayea on 2010-03-07
The information I get back is, "Need terminal for interactive repairs"

I don't know what to make of this comment.

---

### Post by rcayea on 2010-03-07
Thanks for the help. I have compressed and saved my info onto an external drive so I can do a fresh install. 

Thanks again,
Randy

---

### Post by pastalavista on 2010-03-07
> The information I get back is, "Need terminal for interactive repairs"That means run it again without the -C tag

```
sudo fsck /dev/sda1
```

---

