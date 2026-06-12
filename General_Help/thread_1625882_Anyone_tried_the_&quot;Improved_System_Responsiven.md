---
title: "Anyone tried the &quot;Improved System Responsiveness&quot; modification?"
date: 2010-11-19
forum: General Help
---

### Post by Objekt on 2010-11-19
Recently there have been a few stories about a 200-line patch to the Linux kernel which supposedly increases system responsiveness when it's doing a lot of stuff.

There was also the following article at some guy's website ([http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html]("http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html")), which supposedly shows how to improve system responsiveness without using a revised kernel.  Nutshell: A Red Hat developer, Lennart Poettering, figured out a way to do more or less the same thing with a few console commands & code in your .bashrc (or equivalent) file.

Anyone tried either Poettering's method, or the 200-line patched kernel??  I'm a little afraid to try either, lest I break something in dramatic fashion.  Also, the linked page only offers patched kernels for Ubuntu 10.10 whereas I only recently upgraded to 10.04 (and I'm sticking with it for now).

---

### Post by cstudent on 2010-11-19
Just applied the changes from the WebUpd8 article a few minutes ago. Trying to see now if I notice any improvement. Seems like it does but should know after a few days if it has really made any difference.

---

### Post by dcstar on 2010-11-19
> **cstudent said:**
> Just applied the changes from the WebUpd8 article a few minutes ago. Trying to see now if I notice any improvement. Seems like it does but should know after a few days if it has really made any difference.

I have just installed Ubuntu 10.04 on a PC at work which performed pathetically when under heavy disk I/O (something I have never experienced on my own hardware). I will try these changes on this new system next week and report back if they make any positive improvement.

I have just put them on my own system and will see if things are different (although I don't have any performance issues anyway).

---

### Post by cwwilson721 on 2010-11-19
According to [this link, there is a 233-line patch]("http://www.pcworld.com/businesscenter/article/210966/tiny_linux_kernel_patch_delivers_huge_speed_boost.html") to be applied to the kernel....

Maybe soon in the update stream for Ubuntu....

---

### Post by Objekt on 2010-11-19
I haven't noticed any particular problem with responsiveness during heavy disk writing/reading, but maybe I'm not doing whatever it is that supposedly causes the problem.

---

### Post by mc4man on 2010-11-19
Definitely made a difference, at least during large I/O where lag was most notable. (either copying/moving a small # of large files or a large # of small files, the latter being the worst previous to 'hack'
> Anyone tried either Poettering's method, or the 200-line patched kernel?? I'm a little afraid to try either...

The ubuntu specific method is pretty straightforward, scroll down a bit for instr.'s
(I used a slightly modified cgroup_clean file instead of orig. posted, whole thing needs a bit more testing, ect.

Edit:
While i see an improvement while doing large file operations and add. tasks, as far as general desktop usage, not really. (some comments in article suggested that
Even then the improvement is less on some 'modern' hardware, (core2duo, 4GB ram) vs. for instance, a p4 (3.4, 1 GB ram ), where in some scenarios the diff. is quite dramatic

---

### Post by sdennie on 2010-11-19
The Ubuntu instructions at the bottom of [http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html](http://www.webupd8.org/2010/11/alternative-to-200-lines-kernel-patch.html) work just fine on my 10.04 machine.  My machine is very responsive under usual load so, I can't say for sure if the change will have the desired effect but, it definitely sets up per shell cgroups and gives you all the related cgroup accounting info.  If you follow the instructions as written, it's very, very unlikely to cause you problems and in theory, very likely to improve system responsiveness if that has been an issue for you.

---

### Post by ivarn on 2010-11-20
When will this be available for normal users?
I mean, from the update manager.
Also, I can not find the ubuntu 10.04 method on the site.
EDIT: also, is it still in beta or is it safe to install now?
I really think I need this patch thing.

---

### Post by dcstar on 2010-11-21
Wow, the new 10.04 desktop system that bogged down totally under high disk I/O is now as good as a "normal" system with the non-kernel changes listed on the website.

[SIZE="5"]This really works![/SIZE]

If anyone sees the many threads of people complaining about Ubuntu performance when doing large file copying etc, please refer them to this thread. Thanks to the OP for bring this to our attention.

---

### Post by Objekt on 2010-11-22
> **ivarn said:**
> When will this be available for normal users?
I mean, from the update manager.
Also, I can not find the ubuntu 10.04 method on the site.
EDIT: also, is it still in beta or is it safe to install now?
I really think I need this patch thing.

Err, not sure which "this" you're talking about.  

There are at least 2 different things we're talking about here.  One is

-a series of text file edits that automatically execute some commands with your existing kernel;

the other is

-a different kernel.

Don't hold your breath for the patched kernel to come down in Update Manager.  My Ubuntu 10.04 install still has the 2.6.32 kernel.  Ubuntu kernels always lag a few sub-versions behind the newest Linux kernel (which is 2.6.36.1), or maybe it's just me that's behind.  I used Ubuntu 9.10 until about a month ago.

Because I don't want to wait for Canonical to push a patched kernel, & have no idea how to compile my own, I've tried the method shown at the link I posted.  I can't yet tell whether it does anything good.  My system hasn't come to a crashing halt, which is good news in itself.

---

### Post by igotsanevo4g on 2010-11-22
Well im gonna give it a go, i hope this will cure my youtube problems in this thread [http://ubuntuforums.org/showthread.php?t=1628585&page=2](http://ubuntuforums.org/showthread.php?t=1628585&page=2)

If i can get this patch to work being a complete noob, then all of you experienced guys should do it too haha.

I'll be back with my results...

---

