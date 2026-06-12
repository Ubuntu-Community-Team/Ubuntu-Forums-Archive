---
title: "CPU Frequency Scaling Applet; can't set to remember authentication"
date: 2009-10-24
forum: General Help
---

### Post by HiatusLucari on 2009-10-24
In 9.04 you could set the frequency scaling applet (or just about any other program) to remember authentication. Since I'm using a laptop, I like to jump between power saving, performance and on demand depending on what I'm doing.. I.e. If I'm playing music and doing word processing, power saving, if I'm running an N64 emulator or watching HD Youtube videos, I obviously have to be in performance... Well, it's more of a nuisance than a problem, but I don't like typing in my password every time.. Any way around it? Preferably just for that one program.

Forgot to mention I'm currently running 9.10

---

### Post by mfdc1969 on 2009-10-30
Just installed 9.10 tonight and I'm having same problem on my Acer 5610Z ... I have to authenticate every change to the CPU Frequency Scaling applet.

Looks like it's being mentioned in LaunchPad:
[https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/455694](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/455694)

Does anyone have suggestions for a work around to reduce the need to authenticate?

---

### Post by teward on 2009-10-30
Can you use the kpowersave program?

It works on 9.04 Jaunty, and if you guys can get it, it allows you to limit your computer's CPU usage to:  Performance, Dynamic, or Powersave.

Performance runs your CPU at max speed.
Dynamic runs your CPU at the minimum speed, but increases the speed as its needed.
Powersave runs your CPU at the minimum speed period.  never higher.

it also provides other power-saving features as well (at least on 9.04).

---

### Post by mfdc1969 on 2009-10-31
The CPU Frequency Scaling applet worked flawlessly on 9.04 but since tonight's clean install of 9.10 the applet 'needs' authorization constantly. 

I like the applet and am hesitant change right now ... I guess I'll just track the bug on LaunchPad and hope for a quick solution.

---

### Post by mc4man on 2009-10-31
A temp workaround for cpu applet and in my case mounting, unmounting internal drives (partitions

note the edits

cpu post 5, partitions 3

If you edit to yes some of the other available settings you may get unexpected results with certain combos.....

[http://ubuntuforums.org/showthread.php?t=1299820](http://ubuntuforums.org/showthread.php?t=1299820)

---

### Post by mfdc1969 on 2009-10-31
Thank you ! That little work around is exactly what I need - it saves me the hassle of begging permission to change CPU freq.

Thanks.

---

### Post by chezzo on 2009-12-13
Thanks so much! This has been driving me mad!

---

### Post by tgeer43 on 2009-12-29
> **mc4man said:**
> A temp workaround for cpu applet and in my case mounting, unmounting internal drives (partitions

note the edits

cpu post 5, partitions 3

If you edit to yes some of the other available settings you may get unexpected results with certain combos.....

[http://ubuntuforums.org/showthread.php?t=1299820](http://ubuntuforums.org/showthread.php?t=1299820)
Unfortunately this 'workaround' does not work on my installation (9.10 64-bit). :(
After editing to 'yes' I'm still prompted for a password when attempting to change the cpu frequency scaling under Karmic.
I had made a change to Jaunty which bypassed the authentication and it worked fine. It wasn't the same workaround as this and I can't for the life of me remember what file I had edited. It was a long time ago.

Has anyone else had this 'fix' fail to work for them?

tgeer

---

