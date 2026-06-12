---
title: "Firefox doesnt play flash movies any more, but no changes made"
date: 2009-08-16
forum: General Help
---

### Post by moody_mark on 2009-08-16
Hi, Ive been using 8.10 upgraded from 8.04 on my Dell E6400 machine for many months without a problem. Recently I noticed I went onto you tube and I couldnt play the movies any more, I also noticed all flash movies I have to click the big ">" play button, there seems to be a problem with the flash plugin.

Right from the outset I didnt install the flash plugin directly from Adobe as some people do. All I ever done right up until now was install the "ubuntu-restricted-extras" and that always worked ok for me.

Im thinking a recent update has broken it perhaps. Could anyone help me troubleshoot this?

---

### Post by coldReactive on 2009-08-16
Do this in terminal:

```
sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install flashplugin-nonfree
```

Then restart Firefox.

---

### Post by moody_mark on 2009-08-16
Thanks... I seem to be getting further I think, but now on you tube im getting the following message...

Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player.

---

### Post by coldReactive on 2009-08-16
> **moody_mark said:**
> Thanks... I seem to be getting further I think, but now on you tube im getting the following message...

Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player.

Type in **about : plugins** (no spaces) in a blank tab and tell me what it says for Shockwave Flash.

---

### Post by moody_mark on 2009-08-16
Ok, sorted! I noticed there were no shockwave plugins listed in the "about: plugins" previoulsy there was this:

application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

After the command line clean up it had gone. I re-installed the "flashplugin-nonfree" via synaptic and now it works. Thanks for your help. What do you think got screwed up there?

---

### Post by coldReactive on 2009-08-16
> **moody_mark said:**
> Ok, sorted! I noticed there were no shockwave plugins listed in the "about: plugins" previoulsy there was this:

application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

After the command line clean up it had gone. I re-installed the "flashplugin-nonfree" via synaptic and now it works. Thanks for your help. What do you think got screwed up there?

The only reason why you got what you got was probably due to the fact you had more than one flash player installed (IE: Gnash and nonfree clash. Pardon the rhyme.)

---

### Post by Lars Emil Gutt on 2009-08-16
I had the same problem but that command helped :)

---

### Post by moody_mark on 2009-08-17
Well my problem seems to be solved also. Thanks for your help.

---

