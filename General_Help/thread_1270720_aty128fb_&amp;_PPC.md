---
title: "aty128fb &amp; PPC"
date: 2009-09-19
forum: General Help
---

### Post by grundygreen on 2009-09-19
Just reclaimed a loaner g3 which has had Ubuntu on itbefore.
Problem is this time I tried to install 9.04 on it.
When it boots I get some rom error aty128fb.
it then powers down but the power button goes dim but not off.
I've dealt with video issue on G3's before but never have I seen this.
Any ideas?
f Should I just do a CLI install, edit xorg.conf?
 the install desktop. This was fixed a few version ago.
[http://ubuntuforums.org/showthread.php?t=405934](http://ubuntuforums.org/showthread.php?t=405934)
Or is this a new issue?

---

### Post by grundygreen on 2009-09-20
> **grundygreen said:**
> Just reclaimed a loaner g3 which has had Ubuntu on itbefore.
Problem is this time I tried to install 9.04 on it.
When it boots I get some rom error aty128fb.
it then powers down but the power button goes dim but not off.
I've dealt with video issue on G3's before but never have I seen this.
Any ideas?
f Should I just do a CLI install, edit xorg.conf?
 the install desktop. This was fixed a few version ago.
[http://ubuntuforums.org/showthread.php?t=405934](http://ubuntuforums.org/showthread.php?t=405934)
Or is this a new issue?

This does not fix the issue. 
As soon as I reboot I get the Rom error. WTF?
Any ideas?
:confused:

---

### Post by ademonk on 2009-10-20
Hi,

I have/had exactly the same problem: iMac G3, using Ubuntu alternative install all goes very well but booting goes so far then get error:

aty128fb: Invalid ROM contents

and Mac powers down.

To get around this problem press **ctrl-apple-F1** when this error appears on screen. 

Hard disk activity starts, the Mac does not power down and eventually Ubuntu GUI appears.

I am new to linux and macs  but found this key combination somewhere in another thread about blank screens that mentioned about getting a terminal on screen - what it does I have no idea, but thought 'getting a terminal' sounded vaguely useful and so gave it a go.

It was described as ctrl-option-F1 where I assume 'option' is the 'apple' key.

Also, I did not just press ctrl-apple-F1 once but kept ctrl-apple held down and frantically tapped F1 until something happened.

Whilst this is not a fix I hope it should give someone a helping hand to finding a solution.

Hmm, if I try hard enough that someone might be me.

Ade

---

### Post by ademonk on 2009-11-03
I think I have solved 'invalid ROM' problem only for another to appear.
 
To solve the 'invalid ROM' I did 2 things different so can't say for sure which worked:
 
1) made new install CD but burnt at slowest rate possible
 
2) installed with option 'install video=ofonly'
 
Now imac boots perfectly to Ubuntu prompt.
 
Unfortuntely new problem of login not recognizing my username & password :-(
 
Can anyone with the invalid rom problem confirm that 1) & 2) solve the situation?
 
A.

---

