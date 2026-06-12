---
title: "Can't wake up from suspend"
date: 2011-12-03
forum: General Help
---

### Post by wingman015 on 2011-12-03
My suspend function quit working today.  The screen stays black when I open the lid on my Lenovo S10.  This forces me to hold the power button down until the power switches off and then I can power back up.
My hibernate function appears to still be working correctly.
I have searched thru several threads but nothing I have run across has worked yet.
I have also put the netbook into suspend without lowering the lid and when I press the power button the hard drive light doesn't blink - nothing happens.

If anyone can help me, I would appreciate it.  I'm running Ubuntu 11.10
Thanks,
Brent

---

### Post by pretty_whistle on 2011-12-03
I've had this same problem on 11.10.  I have to hit the power button to shut it off then start it back again.

---

### Post by pretty_whistle on 2011-12-03
In my case, it's random and doesn't do it every time.

---

### Post by pretty_whistle on 2011-12-03
Anyone?

---

### Post by wingman015 on 2011-12-03
Well pretty_whistle, it may be random for me as well.  I have absolutely know idea what I did, but suspend is currently working at the moment.  I've tried it about 4x now and it continues to work.
I couldn't do anything at all with it earlier today.

---

### Post by pretty_whistle on 2011-12-03
> **wingman015 said:**
> Well pretty_whistle, it may be random for me as well.  I have absolutely know idea what I did, but suspend is currently working at the moment.  I've tried it about 4x now and it continues to work.
I couldn't do anything at all with it earlier today.
Sounds like my case.
:(

---

### Post by pretty_whistle on 2011-12-04
I wonder why no ones answering this thread............

---

### Post by pretty_whistle on 2011-12-08
[SIZE=3]Here's a workaround for this problem:

[/SIZE]   	 	 	 	 	 	   [SIZE=3]Here's an askubuntu about it:
[http://askubuntu.com/questions/14289/laptop-does-not-wake-up-after-sleep](http://askubuntu.com/questions/14289/laptop-does-not-wake-up-after-sleep)[/SIZE]
  
  	 	 	 	 	 	   [SIZE=3]Workaround:[/SIZE]
 

 [SIZE=3]> You can resume ok if you enter your password in as though you got the login screen (even if you have automatic login enabled).

Apparently the login in screen is there but is "out of view".  Just treat the screen you're seeing as a click-through by assuming the cursor is in the password field.  Put the password in and it'll resume.[/SIZE][SIZE=3]

Solves the problem of having to do a hard shutdown and startup to reach the desktop.[/SIZE]

---

### Post by flyingfisch on 2011-12-15
I have the same prob, and the workaround works for me. I hope Canonical is working on an update to fix this...

---

### Post by pretty_whistle on 2011-12-15
> **flyingfisch said:**
> I have the same prob, and the workaround works for me. I hope Canonical is working on an update to fix this...
They better be, one would think....

---

### Post by BigRedButton on 2012-02-15
I had the same problem on my Asus Zenbook, I fixed it by disabling the automatic login option.

---

