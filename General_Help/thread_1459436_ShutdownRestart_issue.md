---
title: "Shutdown/Restart issue"
date: 2010-04-21
forum: General Help
---

### Post by Aythadis on 2010-04-21
I'm having an issue with the Shutdown command. Going to Shutdown, restarts the pc. i've used 

"sudo shutdown -h now" 

and that even restarts. Tried (just to try) telinit command and still a restart. Booting into Windows does allow for shut down so i know its not something hard ware related. Any thoughts?

---

### Post by Aythadis on 2010-04-21
My bad on not adding this. 

Ubuntu 10.04 beta 2 

and shut down did work until I rebooted from updating.

edit:

I did try a previous kernel, finding out that 2.6.32-19 works over 2.6.32-21

I am lost for words.

---

### Post by _0R10N on 2010-04-21
I always use the ```
init
``` command...

```
sudo init 0
``` to shutdown the system
```
sudo init 6
``` to restart the system

Kind regards!

_0R10N >>

---

### Post by Aythadis on 2010-04-21
I've used telinit 6 and the system restarts with the "newer" kernel. I beleive off hand 2.6.32.21. Fresh update to that kernel caused this issue. I'm not overly worried since I can still access 2.6.32.19 ( there needs to be an easier numbering with this) its just that specific version is giving me problems with just shutting down. Shutdown whether its with GUI or with command prompt. ( not trying to get the Windows hatters out) but shut down is fine there. Obvious not some kinda obscure hardware issue.
 
 
I have used both 
 
"init 6" 
"inti 0"
 
also 
 
"telinit 6" 
 
and
 
"shutdown -h now"
 
All restart the system. I would like to note taking out the battery works faster then rebooting into Windows since the power button just looks at me like I'm smoking something. 
 
I do say thank you for your time.
 
As my dad says " I may not have an solution to your problems, but I do certainly admire it"

---

### Post by dannyboy79 on 2010-04-21
i have a similar problem. i issue the sudo shutdown -r now command when I am ssh'd into one of my computers and it hangs on shutdown, so obviously it never restarts since it never shutdown properly. 

I don't want to hijack your thread but thought I would mention this is happening for me also running kernel 2.6.32-21. It's an old motherboard and maybe bios needs updating. What would I put in the boot line within grub so that the shutdown -r now command works. noacpi or something liek that? or do I need to update the bios. i believe it's an old foxconn motherboard

---

### Post by Aythadis on 2010-04-23
Don't worry about it Danny. Kinda weird. I've seen many issues, just not one that makes my computer WANT to stay on ( not a problem if it was a Desktop). Who knows, I guess I'll continue using the previous kernel. Just weird that the "new" one failed like that. Prolly something with a call or what not.

---

### Post by Lampi on 2010-04-23
How about using 2.6.33? I recall tons of acpi error messages in "dmesg" using any sort of 2.6.32 kernel ... errors that never occurred in 2.6.30, and disappeared again in 2.6.33.

Mostly stuff with "AE_NOT_FOUND"

But then I again I was always able to poweroff the system.

---

### Post by Aythadis on 2010-04-24
I should give it a try but the laptop gave me a good thermal shut down. I'm sending it back to HP. (My fault) 

Won't get it back for at least 7 days. I'll try it when I get back. Who knows.

I just find it amusing that my pc is telling me " NO you WON'T turn me off....." 

kinda makes me think of Skynet or Hal.....

As always, thank you for your time. If the problem exists after their repair ( prolly a new mother board or a really hyper hamster) I'll be back once again. Thank you for the looks and responses.

---

