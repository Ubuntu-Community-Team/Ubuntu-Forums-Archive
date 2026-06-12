---
title: "installation failed failed to create bootloader"
date: 2011-06-26
forum: General Help
---

### Post by p3aul on 2011-06-26
I don't know why I can't seem to install Ubuntu on any computer I have! I tried this before when WindowsXp crashed on my old computer and I tried to install Ubuntu 9. Grub or something like that failed to install on the last one and now this bootloader failed on this go around.( I should mention that Win 7 crashed on me, which is the reason for this go-a-round). I was presented with a dialog box and asked to choose a different folder. I looked at thew list and saw that it was trying to install it on an SD card that I had left in. I then chose my harddrive, as the place to install the bootloader but now clicking the OK button did nothing. As a matter of fact the whole installation had ground to a halt and I had to reboot from the cd. I had selected a small partition for Ubuntu(about 60 GB) could this have been the problem? Also, am I at risk here, I had Microsoft Security Essential running when I had Win 7 running?
Any Help would certainly be appreciated!
Thanx,
Paul

---

### Post by nzjethro on 2011-06-26
Hi Paul. Grub is the bootloader - if it didn't install properly, you're gonna run into some issues. If this is a new install, I'd recommend reinstalling, with the main HDD as the install destination for Grub.

And, 60GB is more than enough, you should be fine in that respect.
And what do you mean by
> Also, am I at risk here, I had Microsoft Security Essential running when I had Win 7 running?

---

### Post by varunendra on 2011-06-26
> **nzjethro said:**
> Hi Paul. Grub is the bootloader - if it didn't install properly, you're gonna run into some issues. If this is a new install, I'd recommend reinstalling, with the main HDD as the install destination for Grub.
+1
Just reinstall ubuntu in the same partition, and choose to 'format' the partition in the step where you are asked to choose 'where to install ubuntu' (manual selection option). In all other prompts, just go with defaults. Installation should be fine!

---

### Post by p3aul on 2011-06-26
Thanks for the replies. Actually I did finally(whew!) get it installed. the difficulty was that I saw windows(restore) in my list of options when I booted up and tried that. The process overwrote grub(i learned) . I reinstalled Ubuntu from the live disk and now everthing works fine, or would, if:

I checked and I can view flash and avi files but[COLOR=Red] **there Is No Sound!**[/COLOR]

[COLOR=Green]How can I fix this?[/COLOR] I am using a realtek sound card. I am a complete newbie to Linux(Ubuntu) and I would have to held by the hand and walked thru it. Please tell me it's something simple like a script i can type into the terminal!
Thanx,
Paul

---

### Post by nzjethro on 2011-06-26
Hi Paul. Glad you got it installed. Could you mark this thread as solved?
And as for your sound issue, please post this problem as a new thread. It is likely to be a soundcard or config issue (I haven't had much experience dealing with these problems) but as this problem is unrelated to your original post, please post it as a new thread. :)

---

### Post by p3aul on 2011-06-26
OK Thanks nzjethro, I will comply! Thanks again for your replies they were very helpful. It's nice to know that there are people here who jump right in to help a newbie!

As for the speaker problem, after much deliberation and searhing for an answer, I found the problem. The speakers were unplugged! :redface:

Sorry, I was unable to figure out how to mark the post as [SOLVED] If someone can clue me in I will do so in the future.
Paul

---

### Post by nzjethro on 2011-06-26
> **p3aul said:**
> 
As for the speaker problem, after much deliberation and searhing for an answer, I found the problem. The speakers were unplugged! :redface:

Sorry, I was unable to figure out how to mark the post as [SOLVED] If someone can clue me in I will do so in the future.


D'oh! Mind you, that's probably an easier fix than having to trawl through sound configuration files. To mark a thread as solved, scroll to the top, and click on the arrow next to "Thread Tools" (in red, on the right hand side of the page). It will come up with an option to "Mark this thread as solved". :)

---

### Post by varunendra on 2011-06-26
> **nzjethro said:**
> To mark a thread as solved, scroll to the top, and click on the arrow next to "Thread Tools" (in red, on the right hand side of the page). It will come up with an option to "Mark this thread as solved". :)
^ this, or just follow the (see how) in my signature. Good luck with Ubuntu!

---

