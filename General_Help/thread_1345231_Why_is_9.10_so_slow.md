---
title: "Why is 9.10 so slow?"
date: 2009-12-03
forum: General Help
---

### Post by JoeyF on 2009-12-03
I have a Emachines W3650 dual booted with XP and Ubuntu, I know that i didn't give Ubuntu that much space when i first installed it.

Any way, I plan on putting Ubuntu as the only OS on this comp. But it does online video slow sometimes.

Will it be faster when it's the only OS?

I have High Speed DSL BTW.

On a side note, I'm pretty sure it was just a freak thing but when i turned the sound on/higher(I don't remember i heard a pop, What could cause that?)

Any ideas? any way i can speed it up?

I can upgrade the comp (Hardware wise) if i need to.

Thanks,
:p

---

### Post by ed-koala on 2009-12-03
Is it just online video that's slow?

---

### Post by mbrowning2000 on 2009-12-03
Is web surfing slow?

---

### Post by JoeyF on 2009-12-03
Mainly online video, But web surfing is a little slow.

---

### Post by mbrowning2000 on 2009-12-03
I tried 9.10 yesterday and my web surfing was very Slow, not to mention I couldn't even play videos, so I found out that it was a Graphics problem. Then after 10hrs of no progress I reverted back to Jaunty and all is well now.

This may not be the solution you. I'm just telling about a similar problem that I had and what fixed it for me.

-Good Luck
[COLOR="Red"]
Edit: I had many other Problems other than just the web.[/COLOR]

---

### Post by JoeyF on 2009-12-03
> **mbrowning2000 said:**
> I tried 9.10 yesterday and my web surfing was very Slow, not to mention I couldn't even play videos, so I found out that it was a Graphics problem. Then after 10hrs of no progress I reverted back to Jaunty and all is well now.

This may not be the solution you. I'm just telling about a similar problem that I had and what fixed it for me.

-Good Luck
[COLOR="Red"]
Edit: I had many other Problems other than just the web.[/COLOR]

How can i revert?

---

### Post by mbrowning2000 on 2009-12-03
You will have to do a fresh install if Jaunty. 

Here is a link o download it: [Ubuntu 9.04: http://releases.ubuntu.com/9.04/]("http://releases.ubuntu.com/9.04/")

---

### Post by lrcaballero on 2009-12-03
Burn an image of Ubuntu 9.04 into a cd, boot-up with it and play with it!! see how your internet connection is with this version and if you notice a difference, well then maybe 9.04 will work better for you! This is just a possobility! it doesn't hurt to try!!! (you never know)

Luis

---

### Post by newbieinubun on 2009-12-03
> **mbrowning2000 said:**
> You will have to do a fresh install if Jaunty. 

Here is a link o download it: [Ubuntu 9.04: http://releases.ubuntu.com/9.04/]("http://releases.ubuntu.com/9.04/")



reverting back to jaunty will damage all my files, right?

---

### Post by JoeyF on 2009-12-03
> **mbrowning2000 said:**
> You will have to do a fresh install if Jaunty. 

Here is a link o download it: [Ubuntu 9.04: http://releases.ubuntu.com/9.04/]("http://releases.ubuntu.com/9.04/")


Oh. :(

I figured i could revert without having to do a fresh install.
How can i replace 9.10 in my dual boot with 9.04?

I might just wait until 9.10 gets fixed.

Thanks.

I also doubt i could tell a difference with a 9.04 liveCD, Since they are slow also. Guess I'll try Virtual Box.

---

### Post by JoeyF on 2009-12-03
Do you think updating would help?

I have 12 updates.

---

### Post by sideaway on 2009-12-03
Depends what the updates are. If it's cups etc, no :P Also, virtual box will still run slowly if 9.10 is slow, as you're essentially using 9.10 to run 9.04....

---

### Post by sgosnell on 2009-12-03
The problem with slow web browsing is ipv6.  Disable that and it will be normal speed.  There are a few ways to do it, and they have been discussed extensively on the forums here.  A quick search for 'disable ipv6' either here or on Google should give you the information you need.

---

### Post by JoeyF on 2009-12-04
It's going better now.

What does IPV6 do? Is it safe to remove from about:config?

Also, About the audio pop. it did it again when i turned on the computer and when i first played a song. It's just a short pop. Any idea? Drivers?


Thanks,
:D

---

### Post by sgosnell on 2009-12-04
You don't remove it from about:config, you just toggle it off.  It's safe enough, as long as you don't do any more than that.

Dunno about the pop, it could be any number of things.

---

### Post by wojox on 2009-12-04
Audio pop

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

 changing the line

```
options snd-hda-intel power_save=10 power_save_controller=N
```

to read

```
options snd-hda-intel power_save=0 power_save_controller=N
```

Reboot.

---

