---
title: "Kernel Boot messages broken"
date: 2011-12-04
forum: General Help
---

### Post by undecidable on 2011-12-04
Have racked my brains about this for months, and spent a couple of days
	messing with every option I can think of,
	and while I now understand better the  problem
	I cannot fix it.
	
	THE PROBLEM - SIMPLIFIED
	I like a noisy boot, with lots of messages
	that tell me what is happening, what is causing delays, 
	what has failed (in case of non-boot) etc,
	not to mention impressing the pants off Windows admins.  
	
	Up to Kubuntu 10.10 I could easily get this just by 
	removing the "splash quiet" options from the grub kernel line.
	
	But with Kubuntu 11.04, even after I remove "splash quiet",
	then during boot, after the grub screen 
        I get a 15" (Fifteen second!!!) black screen,
	then finally a few text lines, then the login prompt.
	
	THE PROBLEM - DETAIL
	Up to 10.10, the boot console would display kernel messages 
		(as shown after boot by dmesg)
	and boot log messages (as in /var/log/boot.log) 
	mixed together.
	
	From 11.04, the boot console only shows boot log messages,
        the kernel messages are missing,
	which leads to a mostly black screen booting process.
	
	In fact I can see that the kernel messages seem to be going to tty1
		(can see them there when I temp switch to tty1 at the gui login prompt).
	So I could probably fix this problem if I could get these kernel 
	messages back to tty7,
		which I think is where boot happens?
		
	But editing /etc/default/grub to:
		GRUB_CMDLINE_LINUX="vga=795 console=tty7 loglevel=7"
	does not return the kernel messages to the boot console where I can see them.
	
	I realize my love of a noisy, turbulent boot process is against the march of progress
	but if anyone knows how to get back my lovely, informative, educational, verbose boot process, I would be grateful

---

### Post by dandnsmith on 2011-12-04
As a desperation measure you could try the effect of noquiet and nosplash options - I seem to remember seeing these in use at some point.

---

### Post by undecidable on 2011-12-04
Remarkably, nosplash brings back the splash screen, interesting but not useful.

noquiet does nothing.

Not surprising really as I think the messages are getting logged, but just not to the boot console.

---

### Post by dandnsmith on 2011-12-05
That's curious - I haven't seen quite that effect with the splash, but have seen noquiet apparently ignored.

I've just recalled that in the last couple of days I've seen difference between what happens when you use grub original as opposed to grub 2 (so called) - I have these on two different PCs - but didn't spend any time to chase it down, after all, life's just too short for some trivia.

---

### Post by drs305 on 2011-12-05
Are you using a theme or grub background image by chance? 

Your frustration has been expressed by others. A few days ago I found that if I turned off a theme I'd employed for testing I was able to get the boot text back. The theme didn't seem to care whether I had 'quiet splash' or not - it wouldn't display the text even after passing control to the kernel.

---

### Post by undecidable on 2011-12-05
Am not using themes or grub background images, so that won't be the problem.

Am using grub 1.99-rc1 in 11.04
whereas 10.10 (which boots correctly) uses 1.98.
However both are grub2, so it is not a grub1 / grub2 difference.

---

### Post by Manu38400 on 2012-02-16
Hi,

I get the same issue, where you finally able tyo find a solution ?

thanks in advance,
Manu

---

### Post by undecidable on 2012-02-17
The problem appears to be with the new boot manager, Plymouth
but those irritated by it are mostly those who run servers
and people like me who find beauty in order 
(rather than a haphazardly flickering screen)
and like to see what is going on.

There is much discussion about how to fix it, eg
[INDENT][http://ubuntuforums.org/archive/index.php/t-1658718.html](http://ubuntuforums.org/archive/index.php/t-1658718.html)
[http://ubuntuforums.org/archive/index.php/t-1457388.html](http://ubuntuforums.org/archive/index.php/t-1457388.html)
[http://ubuntuforums.org/archive/index.php/t-1464639.html](http://ubuntuforums.org/archive/index.php/t-1464639.html)
[http://people.adams.edu/~cdmiller/posts/Ubuntu-Lucid-server-upstart/](http://people.adams.edu/~cdmiller/posts/Ubuntu-Lucid-server-upstart/)
[http://people.adams.edu/~cdmiller/posts/Ubuntu-Lucid-server-text-console/](http://people.adams.edu/~cdmiller/posts/Ubuntu-Lucid-server-text-console/)
[http://people.adams.edu/~cdmiller/posts/Ubuntu-Lucid-server-disable-plymouth/](http://people.adams.edu/~cdmiller/posts/Ubuntu-Lucid-server-disable-plymouth/)[/INDENT]
	
And I tried much of it, in particular:
```
GRUB_CMDLINE_LINUX="vga=795 loglevel=7"
GRUB_CMDLINE_LINUX="vga=795 console=tty7 loglevel=7"
GRUB_CMDLINE_LINUX="vga=795 loglevel=7 noplymouth"	
GRUB_CMDLINE_LINUX="vga=795 loglevel=7 noplymouth INIT_VERBOSE=yes init=/sbin/init -v"
GRUB_CMDLINE_LINUX="vga=795 loglevel=7 nomodeset noplymouth INIT_VERBOSE=yes init=/sbin/init -v"		
GRUB_CMDLINE_LINUX="vga=795 loglevel=7 nomodeset noplymouth init=/sbin/init -v"	
GRUB_CMDLINE_LINUX="vga=795 loglevel=7 nomodeset noplymouth"
```
	

plus I tried
```
sudo mv  /etc/init/plymouth*  /init/temphold/
```
which also did nothing nothing.
	
key points:
[LIST=1]
[*] noplymouth does not work
[*] loglevel=7 makes no difference
[*] there was still a long period of black screen with no messages, nothing.
[*] INIT_VERBOSE=yes init=/sbin/init -v gives lots of useless init messages but not the useful kernel messages.
[/LIST]

Of course you can get the kernel messages after logging in from /var/log/kern.log,
but that is not the point.

I plan to file a launchpad bug against it.

---

### Post by macachuto on 2012-03-11
Have you opened a bug about this problem.
I am testing Xubuntu 12.04 and have completely the same bug - black screen for a 10 sec. and then login prompt. There is no any boot messages.

Thanks

---

### Post by toomas on 2012-03-13
I got kernel messages back by removing the "quiet", "splash", and "vt.handoff" parameters, and editing the `linux_gfx_mode' part of the Grub menu, setting it unconditionally to "text".  You can edit /boot/grub/grub.cfg directly, or make the change permanent by editing the configuration files in /etc/ and running grub-mkconfig:

--- /etc/default/grub.orig	2012-03-13 12:15:36.790657087 +0200
+++ /etc/default/grub	2012-03-13 12:15:48.438656683 +0200
@@ -8,7 +8,7 @@
 GRUB_HIDDEN_TIMEOUT_QUIET=true
 GRUB_TIMEOUT=10
 GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
-GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
+GRUB_CMDLINE_LINUX_DEFAULT=""
 GRUB_CMDLINE_LINUX=""
 
 # Uncomment to enable BadRAM filtering, modify to suit your needs

--- /etc/grub.d/10_linux.orig	2012-03-13 12:03:56.890681321 +0200
+++ /etc/grub.d/10_linux	2012-03-13 12:05:44.858677583 +0200
@@ -153,32 +153,8 @@
 prepare_boot_cache=
 prepare_root_cache=
 
-# Use ELILO's generic "efifb" when it's known to be available.
-# FIXME: We need an interface to select vesafb in case efifb can't be used.
-if [ "x$GRUB_GFXPAYLOAD_LINUX" != x ]; then
-  echo "set linux_gfx_mode=$GRUB_GFXPAYLOAD_LINUX"
-else
-  cat << EOF
-if [ \${recordfail} != 1 ]; then
-  if [ -e \${prefix}/gfxblacklist.txt ]; then
-    if hwmatch \${prefix}/gfxblacklist.txt 3; then
-      if [ \${match} = 0 ]; then
-        set linux_gfx_mode=keep
-      else
-        set linux_gfx_mode=text
-      fi
-    else
-      set linux_gfx_mode=text
-    fi
-  else
-    set linux_gfx_mode=keep
-  fi
-else
-  set linux_gfx_mode=text
-fi
-EOF
-fi
 cat << EOF
+echo set linux_gfx_mode=text
 export linux_gfx_mode
 if [ "\$linux_gfx_mode" != "text" ]; then load_video; fi
 EOF

Cheers,
T.

P.S.  I would have added the above patch as an attachment, but I could not do anything in the window that popped up after I clicked "Manage Attachents".  What could be the matter?  I tried it with Konqueror 4.7.4 (Gnome 2, Ubuntu 11.10 (oneiric)).
T.

---

### Post by toomas on 2012-03-13
Hello again!

Sending the patch again, now from Firefox and as an attachment.

T.

---

### Post by macachuto on 2012-03-13
It didn't help me on Xubuntu 12.04.
I can see only last 30 lines or even less.

---

### Post by undecidable on 2012-04-03
Launchpad bug finally filed:

[https://bugs.launchpad.net/ubuntu/+bug/972375](https://bugs.launchpad.net/ubuntu/+bug/972375)

mc

---

### Post by macachuto on 2012-04-12
Thank you.
Hope that will help to solve this inconvenience.

---

### Post by undecidable on 2012-04-15
Seems unlikely - there has been no activity on the bug, hasn't been confirmed or assigned. 

To file a bug on Launchpad, you have to specify the package against which it is filed.  Not being sure, I filed it against Plymouth.
If anyone has a different view of what it should be filed against, pls let me know.

mc

---

### Post by macachuto on 2012-04-18
Not at all.

Status of your bug is Confirmed.

Developers all are busy.
We have to wait.

I have filled up a lot of bugs for Fedora, and do not have an account in launchpad, but going to create one, as I decided to shift from fedora to xubuntu.

---

### Post by undecidable on 2012-04-19
Thanks, yes, I saw.  
Bugs used to get discussion etc much more quickly,
but 2 weeks is ok as it is not urgent.

Welcome to X/K/L/Ubuntu.
I personally use Kubuntu as it has much more power and control,
even if some bugs.
Xubuntu is nice, and ok for lower power machines:
I use it on an 2001 Dell Dimension that only provides music.

---

### Post by bogan on 2012-04-19
Hi!, **undecidable**,

Have you tried replacing 'quiet splash' with '--verbose text' ??

Or does that only give you the useless boot messages, not the Kernal messages you want?

Chao!, **bogan.**

---

### Post by undecidable on 2012-04-20
I, and many others (do a search), have tried 8,746 different combinations.
The problem is not that I, deliberately or by default, have suppressed the messages.  
As the description makes clear, a few of the kernel messages eventually turn up.

---

### Post by macachuto on 2012-11-10
I know, this is an old thread, but I have something to say here.

I installed Xubuntu 12.10 and faced the same problem - how to see early boot messages.

I have found how - one need to add "vga=..." to the grub.cfg and remove "quiet, splash".
In my case I had to add "vga=795", and now I can see all boot messages - from the first one up to the last.


Thanks.

---

