---
title: "Alt+SysRq+REISUB: Not working, no SysRq key on Dell laptop keyboard"
date: 2012-03-17
forum: General Help
---

### Post by veroslav on 2012-03-17
Hi,

running Ubuntu 11.10 on Dell Inspiron 17r, this morning I've got the first total freeze: I couldn't use mouse, keyboard, Ctrl+Alt+Fx didn't work, neither Ctrl+Alt+Backspace.

So I tried to resort to Alt+SysRq+REISUB, unfortunately, my keyboard seems to lack the SysRq key (see the attached image)!

I know that it is usually found together with Print Scr key, it is on my desktop, but my Dell laptop only has Prt Scr key. Needless to say, trying both Alt+Prt Scr + REISUB and only Prt Scr + REISUB didn't result in anything so I had to do a hard reboot.

Does anybody know what key (if any) is the SysRq key on a Dell laptop? What else can I try to do next time I get a freeze?

Thanks.

Regards,
Veroslav

---

### Post by chipbuster on 2012-03-17
Hurm, a key labeled "Print Screen" works just fine for me.

I notice your alt key isn't actually labeled alt. Is there another key on the left side?

Also, does the combo work when your computer isn't frozen?

---

### Post by veroslav on 2012-03-17
Thank you for your reply, chipbuster.

Yes, that is correct, I have a regular Alt-key on the left side of the keyboard, that was the one I used when issuing Alt+Prnt Scr+REISUB commands.

I also read that each part of REISUB might take few seconds to complete, so I did it fairly slowly, but to no avail. :(

I could try that, what should the outcome be when the computer is not locked? Should I use Alt-key with Prnt Scr or only Prnt Scr?

/Veroslav

---

### Post by chipbuster on 2012-03-17
Definitely use it with ALT, because just a printscreen is usually bound to take screenshots ;)

The point of the REISUB combo is that each section safely shuts down some section of the computer so that you can keep your data. For example, the combo with "E" sends a termination signal to all programs but init. (You can read more about the combo [here]("http://en.wikipedia.org/wiki/Magic_SysRq_key")).

At any rate, the expected behavior of the system would be to shut down. If you'd like, you can try going to the getty terminal (CTRL+ALT+F1) and watching the output from there. Ideally, you should see some messages on the first three keys, which drop to nothing after the I (I forcibly kills all processes), and then a reboot once you get to B.

If nothing happens, then your keyboard probably doesn't support the right key combo. We can always check that with xev if you'd like.

---

### Post by veroslav on 2012-03-17
Hi again!

I just tried the Alt+SysRq+REISUB combo on a normal destop session and it looks as though it works :)

1. Dropped to TTY console (Ctrl+Alt+F1)
2. Alt+SysRq+R:

```
[...] SysRq: Keyboard mode set to system default
```3.  Alt+SysRq+E gives a lot of output like this:

```
init ... main process terminated with status 255
```4. Alt+SysRq+I takes me back to login:

```
user-laptop login:
```5. Alt+SysRq+S:

```
SysRq: Emergency Sync
Emergency Sync complete
```6. Alt+SysRq+U:

```
EXT4-fs (sda7): re-mounted.opts: (null)
Emergency Remount complete
```7. Alt+SysRq+B:
After issuing above, the screen goes black and the disks shuts down (kind of) but the computer is still powered on.

What should I do now? Is it safe to just power it off manually?

Thank for the help so far!

---

### Post by chipbuster on 2012-03-17
Looks beautiful. The I is supposed to kill all processes but init, so that's going to dump you back to a shell. Looks like the sync worked, and U remounts your drives read-only.

> 
7. Alt+SysRq+B:
After issuing above, the screen goes black and the disks shuts down (kind of) but the computer is still powered on.


Huh??:shock:

That's not supposed ter happen! B should immediately reboot your system, same as if you'd hit the reboot button (in a slightly less controlled way, of course).

Did you manage to catch any messages as it shut down? If not, and you want to get to the bottom of this, we could try digging through the syslog. Check syslog in your log viewer and look for where your computer shut down (usually right before a giant bunch of [0.000000000000] that marks the start of the next boot). See what was logged.

I'd say if you can't find the logs, try REISUB  again and extract the logs. For now, it seems that the combo is doing what it's designed to do (namely, protect your data against loss from an uncontrolled shutdown).

I'm wondering if your kernel somehow got screwed up the first time. As long as the kernel is operating, it should be able to respond to the magic combo.

---

### Post by veroslav on 2012-03-17
Thanks for the detailed description, I appreciate it.

Yeah, it just sat there doing nothing, but the laptop was still powered on. I just turned it off by using the power button and it shut down immediately. I managed to boot it the next time without any problems.

Unfortunately, I didnt't see any output after I pressed 'B', if it printed something, it must have been very short message, because as soon as I pressed 'B', the screen went black and I heard disk spinning down.

Even though the REISUB combo didn't work on the lock last time, now I at least know that I did try it at least. I am worried about the possibility of the kernel damage though, as you mention. Do you mean like kernel damage right at that time or do you mean something more permanent? :(

Unfortunately, I wont be at home for a few hours now, but later today when I am at home again, I will have a look at the log you mentioned and come back here if I need more help.

I am very thankful for all the help I was given here, thank you!

Regards,
Veroslav

---

### Post by chipbuster on 2012-03-17
Oh I wouldn't worry about permanent damage. It's just that usually, programs freeze above the kernel. It's pretty strange to have an event that freezes the kernel but doesn't crash it, but it seems like that might be what happened to you, since the kernel *should have* responded to the magic sysrq otherwise.

Anyhoo, as long as it's working now, you'll know that something's really, really sideways if it doesn't :)

---

### Post by dragonfly41 on 2012-03-17
I thought I might try out this process .. since I've had some freezes usually associated with Firefox.

I have a Dell Inspiron 1720 laptop and SysRq (F11 key) requires Fn key to be depressed .. so the key pressing is a bit complicated ..

I found this helpful blog giving a description of the key pressing sequence ... for Dell Inspiron 1720.
5 seconds between each r-e-i-s-u-b

[http://www.bitsbythepound.com/sysrq-and-inspiron-1720-307.html](http://www.bitsbythepound.com/sysrq-and-inspiron-1720-307.html)

and here ..

[http://ubuntuforums.org/showthread.php?t=617349](http://ubuntuforums.org/showthread.php?t=617349)

> 
Left hand: Press and hold &#8220;Fn&#8221; key (between Ctrl and the Windows key)
Right hand: Press and hold &#8220;Alt&#8221; + &#8220;SysRq&#8221; keys (Alt+F11)
Left hand: Release &#8220;Fn&#8221; key
Left hand: Press and release &#8220;r&#8221; key. (Screenshot dialogs may start popping up. Ignore them)
Left hand: Press and release &#8220;e&#8221; key. (Your GUI should collapse to a tty, most processes terminated)
Left hand: Press and release &#8220;i&#8221; key. (Progress of key shown in the tty, most proceses killed)
Left hand: Press and release &#8220;s&#8221; key. (Progress of key shown in the tty, syncs filesystems)
Left hand: Press and release &#8220;u&#8221; key. (Progress of key shown in the tty, unmounts filesystems)
Left hand: Press and release &#8220;b&#8221; key. (Progress of key shown in the tty, starts reboot)
Right hand: Release all keys


---

### Post by veroslav on 2012-03-19
Thank you for your post, dragonfly41.

I find the links you posted very helpful, wasn't sure whether I correctly typed the REISUB sequence, but after reading what has been said there, it appears I have.

Seems that I simply got a kernel freeze, just hope that I didn't get any hardware damage.

After reading what you said about freezing occuring while using Firefox, I remember that I've got the freeze when I hoovered over a link in Firefox, don't really know whether it is just a coincidence.

Regards,
Veroslav

---

### Post by Quackers on 2012-03-19
I don't know if it will make any difference but I always use Alt Gr key in that sequence (rather than the Alt key). Have you tried that?

---

### Post by veroslav on 2012-03-19
Thank you for the reply, Quackers.

I haven't tried it yet, but I will definately give it a go next time the issue occurs.

I was thinking, whether the freeze I experienced has anything to do with adding the kernel parameters (see the thread I posted earlier here: [http://ubuntuforums.org/showthread.php?t=1938356](http://ubuntuforums.org/showthread.php?t=1938356)) in order to combat the power regression bug present on Sandy Bridge machines (mine is such)? I read somewhere that they might (though rarely) cause graphical/freezing glitches on some machines, so perhaps that is the case here as well.

Will keep the current configuration (with the parameters included) for a while and see whether I get the freezes again. If yes, I will revert the changes and check whether that makes any differences.

This is a new computer and I used it for 2-3 weeks without any issues/freezing, and after I added the kernel paramteres I mentioned, 2 days later I've got the first freeze, hmm...

Regards,
Veroslav

---

### Post by veroslav on 2012-03-26
Well,

last night it happened again :( I was running kdenlive and went to click on the "Disable video" button for one of the video tracks there and while I was hoovering over the button, the screen froze. I couldn't use either mouse nor the keyboard.

Nothing helped (Alt+SysRqw+REISUB, Alt+SysRq+K, Ctr+Alt+Del, Ctr+Alt+F1...F6). Again, I forced to hard reboot.

I am starting to really get worried now, because I am worried that I will damage my computer while hard rebooting :(

Could anyone shed some more light on what the root cause could be? Please??

Regards,
Veroslav

---

