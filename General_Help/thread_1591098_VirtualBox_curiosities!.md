---
title: "VirtualBox curiosities!"
date: 2010-10-08
forum: General Help
---

### Post by Quackers on 2010-10-08
I've just installed VirtualBox 3.2.8 so that I can run Vista without rebooting. VB installed ok and I installed the extras and while they were installing the Software Centre popped up saying I should install an addon (ttf something) so I did. That went ok so I then installed Vista in the VB. While that was installing I got a notice from Sun Microsystems that an update should be installed for VB. I clicked on that and installed it. 
It turns out that the "update" was VB 3.1.2 - so now I have a shortcut on my VB desktop for VB3.1.2 but I have 3.2.8 installed :-k
I've looked in add/remove programs (or whatever it's called in Vista) and there is nothing there about VB 3.1.2 so I can't uninstall it.
Is all this normal for a VB install?
Shall I just throw the shortcut in the trash and forget it? 
Any insight would be appreciated :-) Thanks

---

### Post by lbrty on 2010-10-08
VirtualBox installed 3.1.2 in the actual virtual machine of Vista and placed a shortcut on the desktop of the Vista virtual machine? That is odd. Can you provide a screenshot?

---

### Post by Quackers on 2010-10-08
No. I installed VB 3.2.8 in Ubuntu. I installed Vista in that. The shortcut is on the Ubuntu desktop but that's for VB 3.1.2. I know this because it opens up a second VB window.

---

### Post by lbrty on 2010-10-08
When you open VirtualBox that you installed Vista in (the version you originally downloaded -- 3.2.8, goto Help and click About VirtualBox. What is the version? Mine states Version 3.2.8 r64453.

---

### Post by Quackers on 2010-10-08
I'm sorry lbrty, I'm a numpty. You were right the first time. If I open VB and then Vista, there is a VB shortcut on the Vista desktop which is for VB 3.1.2 and if I open that I get a pop up saying that there is an update to 3.2.8 available. This is what's already running. It appears to have installed VB 3.1.2 in Vista.

---

### Post by lbrty on 2010-10-08
OK =) 

So you installed VirtualBox inside a virtual machine (Vista) which was an older version? Is that correct? Did you want to install VirtualBox inside another virtual machine (Vista) or was that the update that Java requested of you?

If VirtualBox 3.2.8 is installed on Ubuntu Desktop and you have Vista installed inside that virtual machine, then I do not see a reason to have a shortcut inside the virtual machine of Vista (that Java created?) for an older virtual machine that you are not using.

---

### Post by Quackers on 2010-10-08
Yes, you have the correct picture (despite my best efforts!) :-)
It appears that I have VB 3.1.2 installed within Vista which is within VB 3.2.8. This was not my intention and I'm not completely sure how it happened. But it is late here :-) I'll just get rid of the VB inside Vista and all will be well.
It doesn't help that Vista is installing updates (for the last hour) which makes everyhting very laggy.
Thanks for your help sir.

---

