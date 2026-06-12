---
title: "Computer hangs at boot splash"
date: 2010-10-17
forum: General Help
---

### Post by kotaro535 on 2010-10-17
Hey guyz I have a problem on my computer.

When I  login to my account using KDM login screen after that instead of loading my desktop environment it opens a terminal since IDK what the hell is happening I simply configure it back using GDM 
"sudo dpkg-reconfigure gdm" and then after the process completed IDK what is the command for restart so I simply closed the terminal and it turned black after that I force to restart my computer using restart button and then after the boot screen animation(since I used plymouth) it freezes though I doesn't continue to login screen I wait for how many minutes and IDK what to do....

and BTW I don't want to reinstall and format  my Ubuntu anymore I have done many changes on it and I don't want to lose them...

and if can someone help how to return my Ubuntu back to normal using liveCD please reply...T_T

:(waiting for someone to help.

BTW I am using Ubuntu Lucid 10.04.

---

### Post by MooPi on 2010-10-17
Lets try to enter recovery console and get your computer squared away. Just after the bois prompt tap the shift key to enter grub. Scroll down to recovery mode and enter. If you haven't removed kdm it may be interfering with your boot sequence. So your going to want to ```
apt-get remove kdm
``` while in recovery. You should reboot to check if this corrected the issue.

---

### Post by kotaro535 on 2010-10-17
> **MooPi said:**
> Lets try to enter recovery console and get your computer squared away. Just after the bois prompt tap the shift key to enter grub. Scroll down to recovery mode and enter. If you haven't removed kdm it may be interfering with your boot sequence. So your going to want to ```
apt-get remove kdm
``` while in recovery

Ok let me try...xD

---

### Post by kotaro535 on 2010-10-17
> **MooPi said:**
> Lets try to enter recovery console and get your computer squared away. Just after the bois prompt tap the shift key to enter grub. Scroll down to recovery mode and enter. If you haven't removed kdm it may be interfering with your boot sequence. So your going to want to ```
apt-get remove kdm
``` while in recovery. You should reboot to check if this corrected the issue.


weird...
after the boot prompt when I tapped shift key it says...
"GRUB loading"

but after that it goes to boot splash...
IDK what happened...it should show me a menu...

any ideas?...:confused:

---

### Post by MooPi on 2010-10-17
You missed grub try again plz hold the key instead don't tap

---

### Post by kotaro535 on 2010-10-17
> **MooPi said:**
> You missed grub try again plz hold the key instead don't tap
oh..
sry I just follow the instruction(peace).xD


ima ask...
just after going to enter recovery mode....

there are many options to be choose from...
which of them will I choose??...

sry I really don't know much in recovery mode...

---

### Post by MooPi on 2010-10-17
No problem , scroll down to root shell

---

### Post by kotaro535 on 2010-10-17
> **MooPi said:**
> No problem , scroll down to root shell

Hmm...
weird...

when I choose root it says something about enter/assign root password for maintenance...
or control+D to continue...

but I can't even type a single letter because every time I type a letter it says "Login Failure"...
I didn't press enter yet...
>,<

---

### Post by MooPi on 2010-10-17
That is not normal and it has me stumped temporarily. Go ahead and try your password and hit enter.Have you activated the root password on your computer?

---

### Post by kotaro535 on 2010-10-17
> **MooPi said:**
> That is not normal and it has me stumped temporarily. Go ahead and try your password and hit enter.

uh oh!...
>,<
It didn't work...
like I said...

every time I type a letter it automatically entered the key w/out pressing enter yet...T_T

---

### Post by MooPi on 2010-10-17
Lets back out and re-enter recovery console. This time choose instead ```
dpkg repair packages
``` . Hopefully you won't be prompted for a password.

---

### Post by kotaro535 on 2010-10-17
> **MooPi said:**
> That is not normal and it has me stumped temporarily. Go ahead and try your password and hit enter.Have you activated the root password on your computer?

BTW I didn't activate my root account...>,<

---

### Post by kotaro535 on 2010-10-17
> **MooPi said:**
> Lets back out and re-enter recovery console. This time choose instead ```
dpkg repair packages
``` . Hopefully you won't be prompted for a password.

It worked but...
after that it will update some programs used by the computer 
and it prompts me whether yes or no/ Y/n...

But now I can't even type a key...
>,<

---

### Post by MooPi on 2010-10-17
Wow more hoops to jump through Ughhhhh. Okay on a hunch do you use a wireless keyboard ? If so can you switch to a wired temporarily. I'm grabbing @ ideas now and drawing a blank. Another option would be to use the Live CD and choose the repair broken system option on the splash screen. I'm unfamiliar with this and if you hit a problem I can't help with maybe you should start a new thread for help.

---

### Post by kotaro535 on 2010-10-17
> **MooPi said:**
> Wow more hoops to jump through Ughhhhh. Okay on a hunch do you use a wireless keyboard ? If so can you switch to a wired temporarily. I'm grabbing @ ideas now and drawing a blank. Another option would be to use the Live CD and choose the repair broken system option on the splash screen. I'm unfamiliar with this and if you hit a problem I can't help with maybe you should start a new thread for help.

No I am using a USB keyboard...
but glady I have a PS/2 reserved here but still the same...
no changes
>,<

Ok let's see I'm also doing my part but never found one...
but I will back to you when I solve this additional problems...

---

