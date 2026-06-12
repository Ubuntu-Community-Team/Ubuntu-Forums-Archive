---
title: "I can't shut down my computer"
date: 2012-06-22
forum: General Help
---

### Post by subjugater on 2012-06-22
After installing Ubuntu 12.04 on my new laptop with windows 7 kept, I found that I can not shut Ubuntu down now. Previously I can shut down normally right after installation, but now it never shut down. Each time it just keeps restarting the machine. 

I found the following threads and followed what suggested there by using boot-repair. But it helps nothing. The problem still persists! It has been so frustrated with the new Ubuntu this time. Big problems keep taking place since the first day after installation. :(

[http://askubuntu.com/questions/130160/ubuntu-12-04-does-a-restart-instead-of-a-shutdown](http://askubuntu.com/questions/130160/ubuntu-12-04-does-a-restart-instead-of-a-shutdown)

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Can anyone give some clue or suggestion? I appreciate in advance.

---

### Post by subjugater on 2012-06-22
I just tried these and they do not work too...

[http://www.sinarpelangi.com/ubuntu-can-not-shutdown/](http://www.sinarpelangi.com/ubuntu-can-not-shutdown/)

[http://www.sinarpelangi.com/ubuntu-can-not-shutdown-solution-2/](http://www.sinarpelangi.com/ubuntu-can-not-shutdown-solution-2/)

Hopeless~

---

### Post by subjugater on 2012-06-22
It doesn't shut down even I forced it brutally.

```
sudo shutdown -h now
```

---

### Post by sffvba[e0rt on 2012-06-22
Please edit previous posts to add more info and stop bumping the thread (once every 24 hours is acceptable).


404

---

### Post by subjugater on 2012-06-23
Sorry, FM.

Can anyone help?

---

### Post by rslater on 2012-06-23
does the following work? 

Sudo poweroff

---

### Post by subjugater on 2012-06-23
> **rslater said:**
> does the following work? 

Sudo poweroff

Thanks, my friend. It works, but only once. It only works the first time when I use this trick. Now the restart-problem still persists. Any other workaround?

BTW, is this a well-known bug in 12.04 LTS???

Again, thanks.

---

### Post by forestG on 2012-06-23
Try log out and when you are in the log-in screen try to shutdown.

Is there any difference in the behavior of "shutdown -P now" and "shutdown -r now"?

---

### Post by subjugater on 2012-06-23
> **forestG said:**
> Try log out and when you are in the log-in screen try to shutdown.


I tried many times to shutdown from the log-in screen and it never works. Same issue - computer restarts.

> **forestG said:**
> 
Is there any difference in the behavior of "shutdown -P now" and "shutdown -r now"?

No difference. Restart again for both. :(

But anyway, thanks, buddy.

---

### Post by ranger1021994 on 2012-06-23
Well 12.04 is buggy for now...
The Shutdown -P command normally does the job :)

---

### Post by subjugater on 2012-06-23
> **ranger1021994 said:**
> Well 12.04 is buggy for now...
The Shutdown -P command normally does the job :)

Thank you, my friend. But it doesn't work. 

Does anybody think that I should do something with my BIOS? Anything need to change in Setup?

BTW, the Windows 7 which co-exists with Ubuntu 12.04 can shutdown normally. So the problem may not be caused by the configuration of the machine.

---

### Post by forestG on 2012-06-24
@subjugater

Press Ctrl-Alt-F1 and write there "sudo shutdown -P now" when is shuts down does it say "preparing to restart" or "preparing to shutdown"?

---

### Post by subjugater on 2012-06-24
> **forestG said:**
> @subjugater

Press Ctrl-Alt-F1 and write there "sudo shutdown -P now" when is shuts down does it say "preparing to restart" or "preparing to shutdown"?

There are multiple lines showing up after doing this. They disappear at no time. I've never got a chance to see them.

Any other way to check this? Thanks!

---

