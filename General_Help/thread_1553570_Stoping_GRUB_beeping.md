---
title: "Stoping GRUB beeping"
date: 2010-08-15
forum: General Help
---

### Post by AndrejaKo on 2010-08-15
I don't know if I'm using good prefix, so please advise if I'm mistaken.

Anyway, I'm using default GRUB version which shipped with ubuntu 10.04 4bit  and I have several items listed in grub.cfg.

My problems is that when I use arrows to move selected list item, sometimes it happens that more arrow key presses are detected than there are items in the list. Once the selection comes to then end of the list, I get one pc-speaker beep for every extra keypress. The beep lasts about one second and while it is beeping, computer is unresponsive.  It also seems to remember any key presses registered while GRUB was loading and beep for them too. I want to somehow eliminate this behavior. 

Please note that I don't want to disable pc speaker in general and this happens before kernel is loaded, so I don't think that disabling kernel modules is going to help.

Any ideas on what I should do?

grub.cfg attached.

---

### Post by mike555 on 2010-08-15
to disable the beeps you can try these two commands (one after the other):

Code:

sudo rmmod pcspkr

and then this:

Code:

echo 'blacklist pcspkr' | sudo tee -a /etc/modprobe.d/blacklist

Hopefully you will now be beep-free! If your system fails to shutdown, another way to shut down is to run this command:

Code:

sudo shutdown -h now

---

### Post by AndrejaKo on 2010-08-15
Thank you for taking time to open this thread and write your reply, but it seems you didn't entirely read my post or I wasn't clear enough.

**I don't want to be beep free and I am in fact a great fan of pc speaker.** I also do not have any problems shutting down the computer. It's just **this one specific case** which irritates me.

My problem occurs **during boot** at **GRUB stage 2** when **menu appears,** **before** kernel is loaded.

I'll provide an example which will illustrate my problem. Let's say that I have 4 options in GRUB menu. If I want to select option number 4 I have to press down arrow 3 times and press enter. If I press down arrow 4 times, I'll get one beep. If I press down arrow 5 times, I'll get 2 beeps. While the computer is emitting a beep, it does not respond to keyboard input. I have to wait until it stops beeping. So if I press enter when the beeping starts, only when it stops beeping will the selected option be loaded.

What makes this issue for me is that my windows option is on the bottom of the list and I usually keep down arrow pressed until selection box moves to windows option. Unfortunately, by the time it reaches windows selection option, two or three additional key presses are usually detected and I get two or three beeps.

---

### Post by mike555 on 2010-08-15
guess I misunderstood, mine doesn't do that beeping at grub , I have never heard of it before ...

---

### Post by Cavsfan on 2010-08-15
My PC speaker has never beeped either... I even tried the setting to make it beep and it still did not.

On a side note, if you would like a maintenance free grub screen, look into the tutorial in my signature.

---

### Post by AndrejaKo on 2010-08-15
Yeah it is pretty strange. Only this one computer beeps for me. Others don't.
@[Cavsfan]("http://ubuntuforums.org/member.php?u=889820") I'll take a look at your tutorial and see if it helps me.

---

### Post by Cavsfan on 2010-08-15
The GRUB2 file that you can edit controls default line, timeout and resolution also has something about beeping at the bottom:

**gksu gedit /etc/default/grub**

```
# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```You might check that.

---

### Post by linux18 on 2010-08-15
could be a BIOS beep

---

### Post by AndrejaKo on 2010-08-15
@Cavsfan 

I just tired that option and I get one expected beep once GRUB menu shows. After that I was unable to produce more beeps.

@linux18  
When my computer boots I first get black screen, then BIOS screen, then black screen again, then black screen with white flashing _ on it then GRUB menu. If I press a button while second black screen or white flashing _ are visible, I still get beeps, so this could be somehow related to my BIOS. 

On the other hand, I do not get classic single beep which is emitted on some computers after BIOS completes POST, so these beeps are not it.

---

