---
title: "Doom3: arrow keys not working"
date: 2009-07-07
forum: General Help
---

### Post by tszanon on 2009-07-07
Since Ubuntu 8.10, the arrow keys have not behaved as expected in Doom3.
The default keys for moving forward are both W and the up arrow. But the up arrow does not work.
If I try to rebind the up arrow to that action, in its place is shown "0x00" instead of "UP ARROW".
The same happens to the right arrow and down arrow. The Left arrow behaves like it was the ALT key.

I'm using the default keyboard driver "kbd", and xev reports the keys as expected:
left arrow = 0xff51
up arrow = 0xff52
right arrow = 0xff53
down arrow = 0xff54
(not sure about these numbers, but, anyway, it's something like that :smile:)

Since it worked fine before, and the only thing that changed was the ubuntu version, I believe it's something that changed from 8.04 to 8.10 related to the keyboard.

I'm using 9.04 and the problem still persists.

Any ideas?

---

### Post by oberonking on 2009-07-29
> **tszanon said:**
> Since Ubuntu 8.10, the arrow keys have not behaved as expected in Doom3.
The default keys for moving forward are both W and the up arrow. But the up arrow does not work.
If I try to rebind the up arrow to that action, in its place is shown "0x00" instead of "UP ARROW".
The same happens to the right arrow and down arrow. The Left arrow behaves like it was the ALT key.

I'm using the default keyboard driver "kbd", and xev reports the keys as expected:
left arrow = 0xff51
up arrow = 0xff52
right arrow = 0xff53
down arrow = 0xff54
(not sure about these numbers, but, anyway, it's something like that :smile:)

Since it worked fine before, and the only thing that changed was the ubuntu version, I believe it's something that changed from 8.04 to 8.10 related to the keyboard.

I'm using 9.04 and the problem still persists.

Any ideas?

Same here..... I'm going crazy :(

---

### Post by bvanaerde on 2009-10-24
This still exists in Ubuntu 9.04 (64bit), sadly :(
I've posted a question to the Activision support... hoping to get a quick reply.

---

### Post by bvanaerde on 2009-11-17
Activision *(the id Software website referred me to them)* didn't want to give any support at all:

[quote="bvanaerde"]I'm using Ubuntu 9.04, and installed Doom3 using the linux binary (+ copying the pak files from the CDs).
Everything seems to work, except for specific key bindings:
* the arrow keys
* the right ctrl key
* the keys above the arrow keys (ins, del, home, ...)
I'm not the only one with this problem (with different keyboards), but I haven't found a solution so far. Turning off numlock does not help.
Is there a solution for this?[/quote]
[quote="Activision"]Please note that we are only able to provide support for the game when playing on the Windows Operating system. The Ubuntu/Linux systems are not guaranteed to work with the game properly as the game was not specifically designed for the Linux operating systems.[/quote]
[quote="bvanaerde"]But I downloaded an official linux installer from the id software website?
Does this mean you're not giving any support at all? I am sure that there are a lot of other people with the same problem.[/quote]
[quote="Activision"]We are not able to provide support for the use of the Linux operating system with the Doom 3 game. We have not seen Linux users contact us regarding this game as the vast majority of users use the Windows Operating system to play their game. If you would like to seek support for using the Linux version of the game, then we suggest that you refer to online Doom 3 forums for assistance with running your game on the Linux/Ubuntu OS.[/quote]

LeatherMan from the "The Dark Mod" forums wrote down [a solution]("http://modetwo.net/darkmod/index.php?/topic/9982-the-dark-mod-doom3-in-linux/page__view__findpost__p__198356") for this (involves installing Doom with wine).

---

### Post by The Cog on 2009-11-17
I gave up trying to use the arrow keys, but I found that I could reconfigure to use the number-pad arrow keys. OK if you've got a number-pad.

---

### Post by bvanaerde on 2009-11-17
I installed Doom3 with Wine myself, and everything is working well.
The only problem is when you need to keep a button pressed down. But a solution for this is also posted in the link above.

---

### Post by tszanon on 2009-11-17
Thanks for the support!

---

### Post by Cordess on 2009-12-27
Installing the Windows version of Doom 3 and using Wine ist not a solution,
when there is a native Linux version of Doom 3 available.


So this bug is still open and i have the same problem here.

The cursor keys do not work and i can't use the numblock for selecting the weapons in Doom3.

Does anyone has a real solution for this problem?


My distribution ist Ubuntu 9.10.

---

### Post by tszanon on 2009-12-27
In 9.10, turning numlock off "solved" the problem: now I can use the numeric pad to move around, and 0 (Ins) to run, instead of Shift.

No, I don't like it, but it's the closest to a solution I've got. :(

And my very first question is still unanswered:
> 
Since it worked fine before, and the only thing that changed was the ubuntu version, I believe it's something that changed from 8.04 to 8.10 related to the keyboard.

I'm using 9.04 and the problem still persists.
And still in 9.10. Does anyone know what may have changed in Ubuntu, causing this? Maybe the way Doom3 interprets the keys has become obsolete in the system, and therefore not working anymore? I don't know, just brainstorming...

---

### Post by bvanaerde on 2009-12-28
> **Cordess said:**
> Installing the Windows version of Doom 3 and using Wine ist not a solution, when there is a native Linux version of Doom 3 available.

When Activision says that *the game was not specifically designed for the Linux operating systems*, it isn't a native Linux game in my point of view. So I try to make it run as good as possible, and for me that is by using Wine. I'd love to do it otherwise, but right now it isn't possible.

And yes, tszanon, it seems to be Ubuntu related, but that doesn't necessarily mean it's Ubuntu's fault.
Feel free to file a bug report at launchpad though.

---

### Post by tszanon on 2009-12-28
> **bvanaerde said:**
> When Activision says that *the game was not specifically designed for the Linux operating systems*, it isn't a native Linux game in my point of view. So I try to make it run as good as possible, and for me that is by using Wine. I'd love to do it otherwise, but right now it isn't possible.

And yes, tszanon, it seems to be Ubuntu related, but that doesn't necessarily mean it's Ubuntu's fault.
Feel free to file a bug report at launchpad though.
Hey man, calm down. Sorry if I offended you or anyone else, I didn't mean it.

I have to agree with Cordess. In my opinion, it doesn't matter what Activision said, they just don't seem to have qualified people to deal with problems in Linux versions of whatever they distribute. id software made available an official Linux installer, so, yes, it's a native Linux game.

But this kind of discussion takes us nowhere. Thanks again for you proposed solution (using wine). I would have already filed a bug report, but I won't do it until I have the time to help the developers find out what's up. Filing a bug report and abandoning it won't help and will be a waste of developers' time, and that's something I'll try not to do. :)

---

### Post by bvanaerde on 2009-12-29
> **tszanon said:**
> Hey man, calm down. Sorry if I offended you or anyone else, I didn't mean it.
No need to say sorry... I wasn't offended at all. I can understand why it would look that way after re-reading my post though. I'll add more smileys to my posts from now on ;)

We're actually talking about the same thing: I'd love to see this fixed, as I want to be able to run programs *natively* (is this even a word?) as much as possible.
It's really sad that there's no support coming from Activision, even though they released a Linux client.

I have yet to find out where the problem lies (ubuntu, kernel, gnome, ...), so I'm not sure what to do with it myself.

---

### Post by Cordess on 2010-01-10
> **bvanaerde said:**
> When Activision says that *the game was not specifically designed for the Linux operating systems*, it isn't a native Linux game in my point of view. So I try to make it run as good as possible, and for me that is by using Wine. I'd love to do it otherwise, but right now it isn't possible.


If i used wine, i would rather use a real Windows XP.
I own a license of WinXP, so this is not a problem for me.

---

### Post by bvanaerde on 2010-01-10
> **Cordess said:**
> If i used wine, i would rather use a real Windows XP.
I own a license of WinXP, so this is not a problem for me.
I don't think that's part of this discussion though. I'm sure that there are a lot of people here that have a Windows license (including myself). I don't want to have to reboot every time I want to play a game.

---

### Post by mikeossur on 2010-08-07
I don't know why no one has a clue to why Doom3 arrow keys stopped working.  Before I upgraded a year ago, Ubuntu 8 or 9 it was working fine.  Suddenly the last two upgrades, it has became a problem.  I am sure it has something to do with a distro upgrade.

---

### Post by bvanaerde on 2010-08-10
> **mikeossur said:**
> I don't know why no one has a clue to why Doom3 arrow keys stopped working.  Before I upgraded a year ago, Ubuntu 8 or 9 it was working fine.  Suddenly the last two upgrades, it has became a problem.  I am sure it has something to do with a distro upgrade.

Which Ubuntu are you using right now? I haven't tried it with 10.04 yet...

---

### Post by mikeossur on 2010-09-07
I am using the latest Ubuntu64 10.04.  Same issue as before.  What is odd is the Quake 4 does not have this issue.  I would love to find a hack around this problem.  Just not sure where to start.

---

### Post by oldos2er on 2010-09-07
FWIW, Doom3 works fine here (arrow keys and all) on 10.04 64-bit.

---

### Post by mikeossur on 2010-09-10
Wow...there must be something different about your install.  I am using a standard 101 key board and I am using the center arrow keys with out success. Not the key pad. The key pad works fine. I just cannot get use to it.

---

### Post by necrosymbiont on 2011-01-17
Hey all,

I also get this bug. Once upon a time, I tried reporting it, and also got brushed off. Today, I found this how-to, and it contains the seeds for a workaround:

[https://wiki.archlinux.org/index.php/Map_scancodes_to_keycodes](https://wiki.archlinux.org/index.php/Map_scancodes_to_keycodes)


Step 1:
Execute
```
sudo /lib/udev/findkeyboards
```
This will yield something like "input/eventX" which you can subsitute into...


Step 2:
```
sudo /lib/udev/keymap -i input/eventX
```
CAUTION: this can produce weird behaviour! It worked fine for me the first time, but on other times I tried it, it started doing all sorts of weird things to my computer which required a reboot. YMMV.

Anyway, the goal in this step is to get scancode mappings. These are close to the kernel, so will work even when programs like XModMap don't give any love. Get the scancodes of all the keys that don't work in Doom 3, and also the scancodes of some keys which do work (but which you don't want to use).


Step 3:
Find the keyboard most like yours in /lib/udev/keymaps/. Copy this keymap file to a file that you will use just for Doom 3, eg put a "_doom3" suffix on it.

Using your editor of choice, open your new Doom 3 keymap file, paste in all the scan codes you found in step 2, and delete anything that doesn't looks like it belongs (look at the mappings already in the file to get an idea of what your new mappings should look like).

Now switch all the scancodes for the keys you don't want with the scancodes for the keys that you do want.


Step 4:
Run
```
sudo /lib/udev/keymap input/eventX /path/to/keymap && doom3
```
where /path/to/keymap is the path to the doom3 keymap you made in Step 3.


If all goes well, you should now be in Doom 3, with the ability to use arrow keys and any other keys that weren't working.


Caveat:
When I finished playing Doom 3 and tried restoring my original keymap, I got a "EVIOCGKEYCODE: Invalid Argument". I don't know what that means, but it had the effect that a reboot was required before my original keymap would re-establish itself.

(Maybe there is something in /etc/init.d/ that could be restarted instead of going all out with a reboot? You'd think it would be /etc/init.d/udev, but that didn't work...)


I hope this helps!

---

### Post by necrosymbiont on 2011-01-17
Hey all,

I also get this bug. Once upon a time, I tried reporting it, and also got brushed off. Today, I found this how-to, and it contains the seeds for a workaround:

[https://wiki.archlinux.org/index.php/Map_scancodes_to_keycodes](https://wiki.archlinux.org/index.php/Map_scancodes_to_keycodes)


Step 1:
Execute
```
sudo /lib/udev/findkeyboards
```
This will yield something like "input/eventX" which you can subsitute into...


Step 2:
```
sudo /lib/udev/keymap -i input/eventX
```
CAUTION: this can produce weird behaviour! It worked fine for me the first time, but on other times I tried it, it started doing all sorts of weird things to my computer which required a reboot. YMMV.

Anyway, the goal in this step is to get scancode mappings. These are close to the kernel, so will work even when programs like XModMap don't give any love. Get the scancodes of all the keys that don't work in Doom 3, and also the scancodes of some keys which do work (but which you don't want to use).


Step 3:
Find the keyboard most like yours in /lib/udev/keymaps/. Copy this keymap file to a file that you will use just for Doom 3, eg put a "_doom3" suffix on it.

Using your editor of choice, open your new Doom 3 keymap file, paste in all the scan codes you found in step 2, and delete anything that doesn't looks like it belongs (look at the mappings already in the file to get an idea of what your new mappings should look like).

Now switch all the scancodes for the keys you don't want with the scancodes for the keys that you do want.


Step 4:
Run
```
sudo /lib/udev/keymap input/eventX /path/to/keymap && doom3
```
where /path/to/keymap is the path to the doom3 keymap you made in Step 3.


If all goes well, you should now be in Doom 3, with the ability to use arrow keys and any other keys that weren't working.


Caveat:
When I finished playing Doom 3 and tried restoring my original keymap, I got a "EVIOCGKEYCODE: Invalid Argument". I don't know what that means, but it had the effect that a reboot was required before my original keymap would re-establish itself.

(Maybe there is something in /etc/init.d/ that could be restarted instead of going all out with a reboot? You'd think it would be /etc/init.d/udev, but that didn't work...)


I hope this helps!

---

### Post by necrosymbiont on 2011-01-17
Hey all,

I also get this bug. Once upon a time, I tried reporting it, and also got brushed off. Today, I found this how-to, and it contains the seeds for a workaround:

[https://wiki.archlinux.org/index.php/Map_scancodes_to_keycodes](https://wiki.archlinux.org/index.php/Map_scancodes_to_keycodes)


Step 1:
Execute
```
sudo /lib/udev/findkeyboards
```
This will yield something like "input/eventX" which you can subsitute into...


Step 2:
```
sudo /lib/udev/keymap -i input/eventX
```
CAUTION: this can produce weird behaviour! It worked fine for me the first time, but on other times I tried it, it started doing all sorts of weird things to my computer which required a reboot. YMMV.

Anyway, the goal in this step is to get scancode mappings. These are close to the kernel, so will work even when programs like XModMap don't give any love. Get the scancodes of all the keys that don't work in Doom 3, and also the scancodes of some keys which do work (but which you don't want to use).


Step 3:
Find the keyboard most like yours in /lib/udev/keymaps/. Copy this keymap file to a file that you will use just for Doom 3, eg put a "_doom3" suffix on it.

Using your editor of choice, open your new Doom 3 keymap file, paste in all the scan codes you found in step 2, and delete anything that doesn't looks like it belongs (look at the mappings already in the file to get an idea of what your new mappings should look like).

Now switch all the scancodes for the keys you don't want with the scancodes for the keys that you do want.


Step 4:
Run
```
sudo /lib/udev/keymap input/eventX /path/to/keymap && doom3
```
where /path/to/keymap is the path to the doom3 keymap you made in Step 3.


If all goes well, you should now be in Doom 3, with the ability to use arrow keys and any other keys that weren't working.


Caveat:
When I finished playing Doom 3 and tried restoring my original keymap, I got a "EVIOCGKEYCODE: Invalid Argument". I don't know what that means, but it had the effect that a reboot was required before my original keymap would re-establish itself.

(Maybe there is something in /etc/init.d/ that could be restarted instead of going all out with a reboot? You'd think it would be /etc/init.d/udev, but that didn't work...)


I hope this helps!

---

### Post by necrosymbiont on 2011-01-17
Hey all,

I also get this bug. Once upon a time, I tried reporting it, and also got brushed off. Today, I found this how-to, and it contains the seeds for a workaround:

[https://wiki.archlinux.org/index.php/Map_scancodes_to_keycodes](https://wiki.archlinux.org/index.php/Map_scancodes_to_keycodes)


Step 1:
Execute
```
sudo /lib/udev/findkeyboards
```
This will yield something like "input/eventX" which you can subsitute into...


Step 2:
```
sudo /lib/udev/keymap -i input/eventX
```
CAUTION: this can produce weird behaviour! It worked fine for me the first time, but on other times I tried it, it started doing all sorts of weird things to my computer which required a reboot. YMMV.

Anyway, the goal in this step is to get scancode mappings. These are close to the kernel, so will work even when programs like XModMap don't give any love. Get the scancodes of all the keys that don't work in Doom 3, and also the scancodes of some keys which do work (but which you don't want to use).


Step 3:
Find the keyboard most like yours in /lib/udev/keymaps/. Copy this keymap file to a file that you will use just for Doom 3, eg put a "_doom3" suffix on it.

Using your editor of choice, open your new Doom 3 keymap file, paste in all the scan codes you found in step 2, and delete anything that doesn't looks like it belongs (look at the mappings already in the file to get an idea of what your new mappings should look like).

Now switch all the scancodes for the keys you don't want with the scancodes for the keys that you do want.


Step 4:
Run
```
sudo /lib/udev/keymap input/eventX /path/to/keymap && doom3
```
where /path/to/keymap is the path to the doom3 keymap you made in Step 3.


If all goes well, you should now be in Doom 3, with the ability to use arrow keys and any other keys that weren't working.


Caveat:
When I finished playing Doom 3 and tried restoring my original keymap, I got a "EVIOCGKEYCODE: Invalid Argument". I don't know what that means, but it had the effect that a reboot was required before my original keymap would re-establish itself.

(Maybe there is something in /etc/init.d/ that could be restarted instead of going all out with a reboot? You'd think it would be /etc/init.d/udev, but that didn't work...)


I hope this helps!

---

### Post by necrosymbiont on 2011-01-17
Sorry for the multiple posts, is there a button I'm missing that would let me delete the extra ones?

---

### Post by Elfy on 2011-01-17
> **necrosymbiont said:**
> Sorry for the multiple posts, is there a button I'm missing that would let me delete the extra ones?

No - reporting them and asking us to do so is the right thing to do.

Thanks

---

