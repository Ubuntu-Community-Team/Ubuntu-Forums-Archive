---
title: "Why does 10.04 crash?"
date: 2010-05-23
forum: General Help
---

### Post by lakelovers on 2010-05-23
10.04 runs perfectly most of the time, then every once-in-awhile it crashes. The screen goes black and I have to restart. Hopefully, somebody can solve this problem. I had a similar problem with 9.10, so I reverted back to 8.04 which never crashed. I did a fresh install of 10.04. Any ideas?

---

### Post by Souris on 2010-05-23
Same thing here!!!

New install.

---

### Post by j7%&lt;RmUg on 2010-05-23
uuuummmm, not if you dont provide any additional information so we can help you out.

---

### Post by houseworkshy on 2010-05-23
Not a fix but a handy way of posting more detail about your system easily is to install sysinfo.  Save a file with it and post the contents.  Looking through the system logs could also provide some clues.

---

### Post by Souris on 2010-05-23
Sorry,

my hard drive is failing, nothing ubuntu related

cheers

---

### Post by sgosnell on 2010-05-23
It has something to do with your system.  No idea what, since you didn't provide any information.  That's like asking "Why does my car stop running?".  It could be lots of things, but I wouldn't know where to start.

---

### Post by lakelovers on 2010-05-24
I don't know what part of the system log is pertinent. This screen shot, if you can read it, suggests that the system shut down because of inactivity. However, the screen goes black when I'm actively using the computer. I've looked at the power management options and have them set to "never" shut down and never put the display to "sleep." Can you guide me to what I should be looking for in the system log.

That didn't work. I tried to post a screen shot. How do I get the log displayed in this post?

---

### Post by houseworkshy on 2010-05-24
When in a system log you can right click and select all, then right click again and copy.  Make a new document ( right click again is fastest ) and paste.  You may wish to edit out details which are not relevant and focus on reported errors.  This may still be quite large so use the paperclip icon in the forum editor to attach rather than just paste to keep things tidy.  If you don't have a paper clip icon, go to the user CP and choose an alternative editor.  You can choose this by clicking "options and settings" then scroll to the bottom of the page, it is under the "Miscellaneous Options" title.  Also if using no-script or something similar allow ubuntuforums.org and yahooapis.com so it all works.

---

### Post by lakelovers on 2010-05-24
This error shows repeatedly in the syslog. Rather than pasting them all I figured this may give somebody a clue to correcting my problem. Let me know whether I should post more of the syslog.

May 24 13:14:02 jerry-desktop kernel: [96260.043393] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
May 24 13:14:02 jerry-desktop kernel: [96260.388016] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
May 24 13:14:02 jerry-desktop kernel: [96260.388032] render error detected, EIR: 0x00000000
May 24 13:14:02 jerry-desktop kernel: [96260.390027] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 154261 at 108373)
May 24 13:14:04 jerry-desktop kernel: [96262.460026] [drm:i915_gem_idle] *ERROR* hardware wedged
May 24 13:14:05 jerry-desktop acpid: client 23648[0:0] has disconnected

---

### Post by houseworkshy on 2010-05-25
This is deeper than I know about.  Searching for "drm:i915" and "Reenabling wedged hardware, good luck" pulls a lot of bug reports from google so it may be one and taking a look at those may help.  When it hasn't actually crashed yet installing and using htop and sysinfo ( both available in the repositories ) would help you to dig out and post info which would help people with more expertese than me diagnose the problem.  The system moniter would help too.  If any non-fatal errors happen you should get the chance to post on launchpad, when you do this you will also be taken to the page you have posted on and may find out if others are affected too.  It is certainly worth finding out if you have a bug which is unresolved or a setup problem which you can easily fix for yourself before getting frustrated attempting what may be difficult or impossible for you.

Ahhhh yes 8.04lts ...was it the end of the golden age of Ubuntu stability and trouble free setups?  That one almost always "just works" perhaps 10.04.something may return Ubuntu to the haydays, I hope so,  as according to many on this forum the .0 doesn't.  It seems, at least so far, less difficult than 9.10 was only a month after its' stable release.  Well if all else fails the previous lts still has support untill 4/11 so one can afford to wait and hope one of the revisions makes 10.04 an easy stable install before 8.04 dies.
I wish I could help more, as it happens I've just thrown the night at Lucid trying to install it too. Without success, though I'm getting a glimmer of what needs to be researched further and a vauge idea of how it might be done when I next have enough time. 
I'll probably just stick with 9.04, which is ok now, untill 10.04 gets the next .1 
Failing that, the original "debian" is rock solid, simpler and quicker to install than post 8.04 Ubuntu's if one includes the post install research and messing around. Please forgive the tone I'm getting a bit frustrated and tired though to be fair I'm duel booting and have old onboard nvidia.  I may have found leads to answers for both Lucid disabilities on this forum but don't have time and just can't face any more just now.
Good luck with it.

---

### Post by Dayofswords on 2010-05-25
i've had one crash on  10.04 on my school hdd

i had my arm on the enter key and it open a program like 100x, i could recover from it, hard restart

---

### Post by lakelovers on 2010-05-25
Thanks for your time and effort. I guess I'll just have to live with it for now. Hopefully, and update someday with fix it.

---

### Post by dino99 on 2010-05-25
> **lakelovers said:**
> Thanks for your time and effort. I guess I'll just have to live with it for now. Hopefully, and update someday with fix it.

sudo gedit /etc/default/grub

add [COLOR="Blue"]i915.modeset=0 [/COLOR]before [COLOR="Blue"]quiet splash[/COLOR], save and close

sudo update-grub

for better video driver, add this ppa:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by lakelovers on 2010-05-25
I added "i915.modeset=0" before "quiet splash" and when I run sudo update-grub, it said that "i915.modeset=0" could not be found. Maybe I did a wrong edit. The way I put it in was: "GRUB_i915.modeset=0" on a line immediate before the line with "quiet splash." is that correct? Or how should write the new line?

GRUB_i915.modeset=0
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

---

### Post by super.niels on 2010-05-27
I think it's supposed to be 

```
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash i915.modeset=0&#8243;
```

---

### Post by lakelovers on 2010-05-27
Thanks. I'll give it a try.

---

### Post by lakelovers on 2010-05-29
I'm back. I thought the advice above had solved by problem but I just had my computer crash again. This time, however, rather than blanking the screen, the screen alternated between blanking and the cursor reappearing. I had to do a restart to get my splash screen back.

---

### Post by lakelovers on 2010-06-04
I think I solved this problem. After a process of elimination I figured it must be Firefox or one of it's extensions that was the culprit. So, I stopped using Firefox and installed Chromium and I haven't had my computer crash since. Plus, I think Chromium is pretty cool.

**Edit**I thought I had it solved; not so. It crashed on me again. It's still a puzzle to me and very annoying. I can deal with it if it goes down occasionally but not if it happens often. I'm still hope'n a fix will come along.

---

