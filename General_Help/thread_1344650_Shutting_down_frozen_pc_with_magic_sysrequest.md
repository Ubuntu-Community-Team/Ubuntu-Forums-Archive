---
title: "Shutting down frozen pc with magic sysrequest"
date: 2009-12-03
forum: General Help
---

### Post by andypearce on 2009-12-03
Hi
I have a persistent problem with my pc freezing after about five minutes from switch on. I have been crashing it by holding the power button in and really upset it. I have, with great help from the forum, fixed the crashing damage. Now I have been advised to perform a magic sysrequest if my pc freezes again. I am using ubuntu 9.10.

Having looked about (on the forum) for the commands I am told that I should hold down the Alt and printscreen keys and while doing so slowly type R then E then I then S then U then B leaving a couple of seconds for the pc to understand each command to reboot the pc.

Can anyone confirm that this is still the case with 9.10. I have become wary of mucking about with my pc. I have no idea why it freezes... one thing at a time.

If magic sysrequest does not work any suggestions?

Thanks
Andy

---

### Post by John Bean on 2009-12-03
Not the "print screen" key but the one marked "sys req", which may or may not be the same. For example, on my keyboard "sys req" is marked on the delete key rather than prtscr.

---

### Post by hansdown on 2009-12-03
Hi andypearce.

It should work, unless it is a kernel freeze.

NOTE:- This keystroke does not work in the event of a kernel freeze as the keystroke sequence depends on the kernel in order to unmount and make the required steps before the shutdown.

My keyboard uses the print screen button.

[http://www.ubuntugeek.com/how-to-use-magic-system-request-keys-in-ubuntu-linux.html](http://www.ubuntugeek.com/how-to-use-magic-system-request-keys-in-ubuntu-linux.html)

---

### Post by andypearce on 2009-12-04
Thanks for the advice... my keyboard (an over complicated one) does not even have the key on printscreen, del or anywhere!!! My daughter's boyfriend has a keyboard on his pc that does though so I will pinch his!

I suspect (but do not know) that it may be a hardware problem but will investigate once I get the keyboard. Pity there is not a programme or function of ubuntu (that I have found..) that will scan the drive, identify the problem and then fix it.. with one command from the terminal!

Thanks
Andy

---

### Post by andypearce on 2009-12-06
Hi.... got a new key board (£5 from Tescos) with all the bits in the right place. The PC froze and I thought ah ha!... magic sysrequest. No luck. Also Ctrl Alt F1....nothing. Downloaded a new kernel (recommended on another thread) but could not get it in the right place....this is really hard. Why is it all so difficult?

I am back to holding in the on/off button

---

### Post by hansdown on 2009-12-06
Will CTRL+ALT+BACKSPACE work?

---

### Post by andypearce on 2009-12-07
Hi, will give it a go. PC froze again a minute ago and had to do a hard shut down, what it is doing to the OS I shudder to think. Good news is that I managed to upgrade the Kernel and have it working.... got a read out from uname -a and it is there so that rules that out. So far new kernel, compiz removed and screen saver sorted but still freezing. I have tried to follow some of the other freezing threads and can pick out bits but frankly as a new user of linux I am really struggling with the language.

Will try to do a normal shut down now before the pc freezes again.
Thanks for your suggestion,
Andy

---

### Post by andypearce on 2009-12-07
Hi Hansdown

unfortunately CTRL+ALT+BACKSPACE will not work. I have had to hard shut down the pc about five times this morning. It is starting to be reluctant to boot up. I am starting to think it may be a hardware problem.....who knows, is there any way to scan the computer to tell?
Anyone know what will happen if I bung my 8.10 disc in?

Thanks all
Andy

---

### Post by John Bean on 2009-12-07
Do a long memory scan with memtest from boot. Faulty memory is the most common cause of this kind of thing and when I was still using FreeBSD a few years back I had this exact same problem, which eventually wrecked the installation. A quick memory test (several in fact) revealed nothing but an overnight run certainly did - five separate bit faults on obscure bit patterns in the same memory bank. I swapped out the bad DIMM and the problems disappeared with it.

---

### Post by andypearce on 2009-12-09
Hi John Bean, 
I will have a look at running the long memtest, I originally downloaded ubuntu 8.10 onto a cd and installed on my laptop (which I use mostly) and installed it later on my pc when I got sick of microsoft problems, trojans viruses etc; will it be on that? I am also having a look at smartmontools as well but have not been able to download it as yet... seems to be another problem there. Oddly though, the last two times I have used the pc it has not crashed at all.... I am using the new kernel but it did crash with that a couple of times, very strange. Thanks for your help
Andy

---

