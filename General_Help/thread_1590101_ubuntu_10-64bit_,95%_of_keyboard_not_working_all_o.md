---
title: "ubuntu 10-64bit ,95% of keyboard not working all of a suden"
date: 2010-10-07
forum: General Help
---

### Post by sbaig on 2010-10-07
Hello, I'm a fairly new migrant from windows to ubuntu. I love it so far. I was using my laptop (HP DV7) fine yesterday and this morning when I turned it on I was unable to log in. I logged in using the universal access feature and the onscreen keyboard.

Basically 95% of my keyboard does not work. Numlock doesn't turn on or off, only 'a', 'z' and 'n' work, when I press 'v' it types random random strings of characters (e.g. Xzzzzcvmm/?.vcx). I've searched everywhere but have only found thread talking about keyboard issues with ubuntu 10 and vmware. But this problem is not limited to my log in screen.. I can't type anywhere properly. The only numbers I see working are the '1' and '3' keys. Pls help very desperate here. Thank you!

---

### Post by P4man on 2010-10-07
I hate to ask the obvious, but are you sure the keyboard is still functional? No key stuck, lose cable or spilt coffee? Can you test in a live session?

---

### Post by sbaig on 2010-10-07
Well I don't know what a live session is. But you can be sure I checked the whole keyboard if something is being pressed, I check the keyboard layout, restored to normal just in case I changed something. It was working perfectly fine last night. Only thing that happened was the laptop shut itself down because the battery went low (less than 20%) but that is all. Ubuntu did update itself yesterday, but I can't even gain root/super user access cause all my keys either don't function or type the worng letters/numbers. Its crazy and I don't know what to do..

---

### Post by P4man on 2010-10-07
I meant if the keyboard is "physically" functioning, that its not a hardware failure. A live session is what you do when you boot ubuntu from a USB stick or CD. This allows you to test the OS, and in this case, the keyboard. If it works fine in a live session, then we need to dig further, but this sounds so odd I think its a hardware problem.

---

### Post by P4man on 2010-10-07
BTW, is there any logic in the keys working and not working? For instance, is it possible the blue Fn key is stuck and keys with an Fn function (usually have a blue icon or text on them) do not work? Or the ones with an Alt+Gr function?

---

### Post by sbaig on 2010-10-07
Well I don't know what could have physically happened to the keyboard in that short period. I'm at work so I can't do a live test :s. But there doesn't seem to be any logic to the madness. If I type 'd' in fire fox repeatedly it opens up my bookmarks without pressing 'ctrl'. My numlock key doesn't work, my Fn (function) is not sticky at all. My number pad doesn't work. My laptop model is HP DV7-1245dx if that helps.

This may sound stupid but.. Do I have a virus :s??

---

### Post by Quackers on 2010-10-07
Have you tried rebooting (I know we're not talking about Windows here, but it has solved the odd little glitch for me on occasion).

---

### Post by P4man on 2010-10-07
No, its not a virus. 
Sounds like your control key is possibly stuck? FWIW Control+numlock doesnt do anything here either. Note Im not saying its the key that is visibly stuck, but it could be generating a constant keypress.

Anyway, Id try with a livecd first, that will make it much clearer if this is a bizarre software issue or a hardware failure.

---

### Post by sbaig on 2010-10-07
Ok well I did reboot many time, no change. I did open up a blank document and start typing and the cursor jumps around as I type the letters 'd' and 'c' and gave me an output of ",Z/,c,mczcxvzc?M2cz/cx/cxm.,"....  But the cursor jumps.. From the beginning to the end, to the middle of the gibberish I'm typing. And then it opened the "file save" dialog box but I didn't press ctrl+s I was still typing random letters like d,x,c,f,g it was just going crazy

---

### Post by simosx on 2010-10-08
See [https://bugs.launchpad.net/gnome-settings-daemon/+bug/625793](https://bugs.launchpad.net/gnome-settings-daemon/+bug/625793)
for description of bug and workaround (package from PPA).
If the PPA package fixes the problem, report it so that it goes to Ubuntu.

---

