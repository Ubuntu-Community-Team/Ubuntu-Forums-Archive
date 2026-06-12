---
title: "Blank screen after GRUB"
date: 2012-02-16
forum: General Help
---

### Post by Odexios on 2012-02-16
Hello everyone!

Seemingly out of the blue, my Asus EeePc started to give me a completely blank screen at startup. I am (was?) using lubuntu 11.10.

After a bit of research I was able to get to a root console via grub; I tried to run "sudo startx" (is that what I had to do?), but I got this messages:

```
 Fatal server error:
Could not create lock file in /tmp/.tX0-lock

Please consult
[...]
for help.

ddxSigGiveUp: Closing log
xinit: giving up
xinit: unable to connect to X server: Network is unreachable
xinit: server error
xauth: error in locking authority file /root/.Xauthority
```

So, after further researching the subject, I found out I might have some /tmp attributes issue; I tried to check permission with lsattr -d /tmp, and this is what I got:

```
-----------------e- /tmp
```

From what I understand, this isn't what it should be. But if I try to change permissions with a chmod, I get this message:

```
chmod: changing permissions of '/tmp': Read-only file system
```

I kind of ran out of options, and I couldn't find anything useful by searching the web. Considering I was a Windows user until two years ago, and I was kind of used to the idea of reinstalling everything every once in a while, I decided the easiest thing would have been to install everything again.

So, I got a pen drive with ubuntu and... I got the same black screen when the system tried to start from the pen drive. I'm kind of stuck, right now; is there anyone who can help me?

---

### Post by Odexios on 2012-02-16
Ok, I made some progress.

The system successfully starts if I disable acpi; if I try to start via recovery mode (l)ubuntu without disabling acpi, I get this error:

```
/etc/rc2.d/S99acpi-support: line 7: /usr/share/acpi-support/power-funcs: No such file or directory
```

Any advice?

Besides, what's the consequence of disabling acpi?

---

### Post by MAFoElffen on 2012-02-17
> **Odexios said:**
> Ok, I made some progress.

The system successfully starts if I disable acpi; if I try to start via recovery mode (l)ubuntu without disabling acpi, I get this error:

```
/etc/rc2.d/S99acpi-support: line 7: /usr/share/acpi-support/power-funcs: No such file or directory
```Any advice?

Besides, what's the consequence of disabling acpi?
You went to my sticky and asked for help... that you had started this thread.

In that directory (/usr/share/acpi-support) are 6 scripts for device functions, key constraints, policy functions, power functions, screen blanking, state functions... 

From your error, you are just missing some of those script files.  Go to /usr/share/acpi-support and see if you have 6 files there. Boot on a LiveCD of the same version and compare the sizes. Copy over whatever is different than what is in the LiveCD Live Image.

Advanced Configuration Power Interface interlaces into the kernel,  processor and hardware. Affects Power Management, hardware interrupts,  disks spinning down when not in use, waking from hibernation, recovering from a screen saver, plug-n-play device interrupts, dimming and brightening the  screen, power saving functions... and the list goes on.

So to answer an implied question you had as an aside- 
> 
"What's the consequence of disabling ACPI?"
I think "acpi=off" is a good diagnostic tool until you find what is really wrong. Even if there was some reason that you need to use something (not verified in your case) I have a graphics workaround for one issue and the are 11 other acpi-type boot options that affect "parts" of the acpi system to narrow it down (without shutting the whole system completely off). There are 2 other options for debugging the ACPI...

So I guess what I'm saying is- No, I don't think keeping acpi=off as a long term fix is a good idea.

---

### Post by Odexios on 2012-02-18
Thank you for your reply!

I'm sorry for the crossposting, I noticed the sticky only after I had already started the thread; my fault, I should have looked better.

In /usr/share there was no acpi* folder; apparentely, there was no acpi or acpi-support package installed. I will try to install them next time I get an internet connection for my netbook. I guess this might be the problem.
 
Why would something like this happen? I mean, I'm pretty sure I didn't remove anything, but nothing happens without a cause so... Why did it happen?

---

### Post by MAFoElffen on 2012-02-18
> **Odexios said:**
> Thank you for your reply!

I'm sorry for the crossposting, I noticed the sticky only after I had already started the thread; my fault, I should have looked better.

In /usr/share there was no acpi* folder; apparentely, there was no acpi or acpi-support package installed. I will try to install them next time I get an internet connection for my netbook. I guess this might be the problem.
 
Why would something like this happen? I mean, I'm pretty sure I didn't remove anything, but nothing happens without a cause so... Why did it happen?
No-problem. You actually did it correctly by steering help to the original thread.... and not opening multiple threads.

That's what I thought was going on... And I thought I explained how to do it with a LiveCD (copy from the Live Image to your installed system). Doing it that way does not require any internet connection.  You'd just copy over from the Live Image's filesystem to your installed system's filesystem.

If for some reason, you can't do this... If you told my the version you're running, I could compress the scripts you need into a tar ball (including the directory structure that they should be in) and upload them for you. Personally, I think the way I explained using a LiveCD is easier, but the offer is there as a backup.

You ask how this could happen? Well. I've seen this during a distribution upgrade, but I can envision that it might also happen during a kernel upgrade--> Turn off service > Remove module to be upgraded > install new module > Turn service back on... Usually there is an error generated if something goes wrong or it misses a step.  

Even so, I know that with over a thousand installs on varied hardware, sometimes things get around the safeguards. I try to keep an open mind, a sense of humor and remember a quote- "It's to be expected."

---

### Post by Odexios on 2012-02-19
> **MAFoElffen said:**
> That's what I thought was going on... And I thought I explained how to do it with a LiveCD (copy from the Live Image to your installed system). Doing it that way does not require any internet connection.  You'd just copy over from the Live Image's filesystem to your installed system's filesystem.

If for some reason, you can't do this... If you told my the version you're running, I could compress the scripts you need into a tar ball (including the directory structure that they should be in) and upload them for you. Personally, I think the way I explained using a LiveCD is easier, but the offer is there as a backup.Thanks for the offer, but the issue was that I had no internet connection at the time and was posting through my cellphone.

I apt-got the package and everything worked fine!

> You ask how this could happen? Well. I've seen this during a distribution upgrade, but I can envision that it might also happen during a kernel upgrade--> Turn off service > Remove module to be upgraded > install new module > Turn service back on... Usually there is an error generated if something goes wrong or it misses a step.I'll try and see if I can find any error message somewhere regarding the missing package/files.

> Even so, I know that with over a thousand installs on varied hardware, sometimes things get around the safeguards. I try to keep an open mind, a sense of humor and remember a quote- "It's to be expected."Yeah, I guess sometime things just happen. But I kind of find it annoying when I can't understand why something went wrong XD

Oh, well. Thanks for the support!

---

