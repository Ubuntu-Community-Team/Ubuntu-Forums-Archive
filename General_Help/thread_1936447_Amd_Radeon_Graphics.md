---
title: "Amd Radeon Graphics"
date: 2012-03-06
forum: General Help
---

### Post by PcMojo on 2012-03-06
I am getting ready to build a new system and wanted to know which would be the most Ubuntu friendly. While I think the Intel i5 2550 would answer all my needs, I really would rather support AMD (if AMD goes under an Intel $250 system will jump to $500+ because there is no competition).  
 

 I was looking at an AMD Fx8120 but now I am considering the AMD A8-3850 with Radeon on board graphics (socket FM1). The way I understand it, if I want to add a separate video card later, and I add a Radeon 6xxx, they will work together with a 35% increase in speed, as opposed to the on board graphics shutting completely off and only the graphics card standing on it's own. I have searched the forums and found many horror stories with Radeon graphics. Many threads have ended with, “wait until 11.04 or 11.10 and there should be more support”. I have also noticed that several senior members have Radeon listed on their CPU specs in their sig lines  ( although I'm not sure if that means that because they are Ubuntu gurus they know that Radeon works well “out of the box” with Ubuntu, or if they are bragging “I'm such a Linux Guru I actually got a Radeon to work with Ubuntu!” :)  ). Anyway, I had a few questions for you all:
 

 
[LIST=1]
[*]Does the Radeon 6xxx on-board 	graphic series and the FM1 chip-set work well with Ubuntu “out of 	the box” or will I have to use some scary terminal commands and 	that evil “sudo command” that keeps trashing my Ubuntu installs, 	to get it to work correctly?
[*]For those of you that were waiting 	for more FM1 and Radeon support in versions 11.04 and 11.10, did you 	get it? Which graphics driver do you use?
[*]Does Ubuntu even support the AMD 	“hybrid” technology that uses the Radeon 6xxx on-board graphics 	in conjunction with a Radeon 6xxx graphics card (as opposed to 	ignoring the on-board graphics totally and solely relying on the 	graphics card, as is normally the case)?
[*]My old dual boot (XP and Ubuntu 	Studio) PC is dead and I am installing this new motherboard; any 	guesses as to what is going to happen when I push the power button 	for the first time? Is there anything I can do to prepare for this 	moment? (download drivers, etc?)
[/LIST]
 

 Thanks in advance for all of your help!  This is the most friendly on-line communities that I have ever been associated with. I am posting this in the General category, if a moderator needs to move it to the “hardware & laptop” category (it's a desktop, wasn't sure) then I apologize.

---

### Post by Mark Phelps on 2012-03-06
The current Ubuntu version does NOT support Hybrid Graphics.  There are kludgy ways to disable one or the other video adapter -- but that's not supporting hybrid graphics, that's disabling it.

I've read that the latest (12.x) AMD restricted drivers will support hybrid graphics -- but I haven't confirmed that because I don't have such a system.

You might want to check in the Video forum to see if that is true.

Also, you could check on the Phoronix forums -- they do a LOT of testing with AMD drivers and may already have a thread about this.

---

### Post by PcMojo on 2012-04-30
Thanks, there was quite a bit of information there.

---

