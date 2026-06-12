---
title: "[Thinkpad T430s] System freezes randomly"
date: 2012-10-02
forum: General Help
---

### Post by monnand on 2012-10-02
Hi all,

On my lenovo thinkpad T430s, the latest ubuntu freezes randomly roughly once a day. I also tried other distros, including Arch, Fedora, Mint... none of them works perfectly --- they all freeze randomly.

Right now, I didn't see anything useful from the log. When the system freezes, I can do nothing bot hard reboot --- Alt-Ctrl-F1 does not work, Ctrl-Alt-Backspace neither.

The only (possible) useful piece of information from the log during boot is:

```
kernel: [    5.767141] [drm] MTRR allocation failed.  Graphics performance may suffer.
```Does anyone have similar problem with me?

Regards,
-Monnand

P.S., I tried 3.4.11 kernel as well, it does not work for me.

---

### Post by m303 on 2012-10-11
Hey there,

I'm having the same problem with my T430s.

I found this:
[http://askubuntu.com/questions/190058/hp-notebook-pavilion-g6-2101sl-freeze](http://askubuntu.com/questions/190058/hp-notebook-pavilion-g6-2101sl-freeze)

and this:
[http://partiallysanedeveloper.blogspot.it/2012/05/ivy-bridge-hd4000-linux-freeze.html](http://partiallysanedeveloper.blogspot.it/2012/05/ivy-bridge-hd4000-linux-freeze.html)

I have just installed the 3.3.6 Kernel and now testing.

Best Regards

PS: just saw, you already tried kernel 3.4... Please update this post when you find a solution.

---

### Post by monnand on 2012-10-15
1. I upgraded to kernel 3.4.11, and still have same problem
2. I disabled the security chip from bios and still have same problem.

Right now, I found this: [http://partiallysanedeveloper.blogspot.it/2012/05/ivy-bridge-hd4000-linux-freeze.html](http://partiallysanedeveloper.blogspot.it/2012/05/ivy-bridge-hd4000-linux-freeze.html)

it might be useful and I will try it later (and report my status after one week test.)

---

### Post by m303 on 2012-10-16
I wondered if the freezes and kernel panics are a Linux-only problem.

I installed Windows 7 on my machine (plain Windows, with all updates and drivers, not the pre-installed windows version) and I experienced random blue screens with code 124.

This is may be a hardware issue with the T430s:

[http://forums.lenovo.com/t5/T400-T500-and-newer-T-series/T430s-2352-Blue-Screen-and-Stop-Code-101-Issue/td-p/824467/page/4](http://forums.lenovo.com/t5/T400-T500-and-newer-T-series/T430s-2352-Blue-Screen-and-Stop-Code-101-Issue/td-p/824467/page/4)

---

### Post by monnand on 2012-10-19
Thank you, m303.

By following your link, I found more evidence about it: 
[http://help.wfu.edu/thinkpads/t430s/status](http://help.wfu.edu/thinkpads/t430s/status)

It seems like the problem of the hardware itself.

I updated to kernel 3.6.2. It randomly panic (yes, kernel panic) with error messages (I will upload the error message soon.)

Here is my solution: call lenovo tech support and tell them about the problem. They first said that the problem is because of the GNU/Linux itself and they are not responsible for it. I showed them some evidence I found online saying it is the hardware's problem. And fortunately, they said they will send me a box and let me send the laptop back and they will repair it.

I am not sure if they can fix it. (It is possible that they start my computer, and decide not to fix it simply because of seeing a Linux on it.) I will keep reporting my status on this topic.

---

### Post by monnand on 2012-10-21
As I mentioned, here is the screenshot on kernel panic.

---

### Post by monnand on 2012-11-08
Quick update:

Right now, my laptop is hold by lenovo for more than two weeks and still  on "part hold" status.  What's worse, their web-site always return an  error with "StringIndexOutofBoundException". That means I cannot check  status online and have to call them everyday, which also means I have to  be put on hold on the telephone for *more than* 20 mins. In conclusion:  Lenovo service sucks.

---

### Post by m303 on 2012-11-08
That's really sad. My service experience was also not the best:

Our IT people sent the notebook to Lenovo service (which is operated by Teleplan in Europe). They sent it back with a note not being able to reproduce the error. 

The system still kept freezing/bluescreening.

Tomorrow someone from Lenovo (or Teleplan, don't know yet) will come in and have a look at it again, and hopefully replace the main board.

---

### Post by monnand on 2012-11-08
m303,

Here is what I did: I printed the web page from wfu ( [http://help.wfu.edu/thinkpads/t430s/status](http://help.wfu.edu/thinkpads/t430s/status) ) and printed another sheet of paper saying: replace the motherboard!

Fortunately, they decided to replace the mother board for me. But simply replacing the board takes two weeks and I am still waiting. I was told it may be back on next week, that is, 3 weeks in total. And they claim that they can fix it with 6 business days.

EasyServ is the one that fixed my laptop.

---

### Post by monnand on 2012-11-15
Now I finally get my t430s back from lenovo. A summary on this problem:

- Lenove replaced the motherboard. The problem of freezing is not because of software, it is because of the defective hardware.
- I have been watching youtube for about an hour and there is not freeze until now. I will test more applications later
- I sent my laptop on Oct 25 and get it back on Nov 15, which is more than 3 weeks. What's worse, their website always return HTTP 500 error making me impossible to check the repair status online. I have to call them everyday.

In short, if you have same problem on your Thinkpad T430s, don't hesitate, it's not your fault, not GNU/Linux's fault, it's their defective hardware. Call lenovo, send your laptop back and let them to repair it. Remember: the repair may take longer than you expect. If you don't want to wait, you can return it for refund and buy a new one --- that will take less time.

---

### Post by instantmove on 2013-01-08
I also thought about hardware problems, but eventually I've found a way to get non freezing system. Go to BIOS and disable "CPU power management", with kernel 3.7.1 it worked.
More about it in thread  [http://ubuntuforums.org/showthread.php?t=2102787]("http://ubuntuforums.org/showthread.php?t=2102787")

---

### Post by m303 on 2013-01-08
After a long time waiting I got the mainboard replaced.

Now Windows 7 and Ubuntu run without freezing. I cannot tell the manufacturing date of the laptop.

---

