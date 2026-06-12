---
title: "Ubuntu 9.10 System Recovery Help Needed"
date: 2010-02-25
forum: General Help
---

### Post by cwfrad on 2010-02-25
Having trouble booting Ubuntu 9.10, it gets hung at the first screen where the Ubuntu logo apears. Right now I'm running my Ubuntu 8.10 Live CD. Can anyone please help?

---

### Post by mikewhatever on 2010-02-25
Post you computer specs. Is 9.10 installed or are you booting from CD?

---

### Post by cwfrad on 2010-02-25
I have 9.10 installed but right now I'm running 8.10 on a Live CD so I can at least get online

---

### Post by Johnny B on 2010-02-25
so, what changed since your last good configuration?

---

### Post by cwfrad on 2010-02-25
When I tried to log on earlier it went to a command prompt and said the 'file system check failed' and to run fsck manually. I ran 'sudo fsck' and I selected "y" to fix all the bad inodes, when it was complete it told me to restart, I then typed 'sudo restart' at the prompt and it said 'sudo uuid unknown'

---

### Post by Johnny B on 2010-02-25
if you can get to the grub screen you can disable the usplash image to see what errors there may be:

Press 'e' to start editing.
select your usual kernel
Press 'e' again to edit this line.
remove "quiet splash"
press Enter to accept the editing.
Then press 'b' to boot using that kernel and those parameters.



*edit: i think you can get back to the command prompt by adding "root" to the end of the line

---

### Post by cwfrad on 2010-02-25
Ok I removed the "quiet splash" from the end of the kernel and tried booting it with just that removed(no root). It scrolled through a list of stuff and ended with the line " failure: AppArmor profiles failed to load"...same outcome when I went back and put "root" at the end of the kernel.

---

### Post by Timothy Taylor on 2010-02-26
Having been impressed with 9.10 UNR working perfectly on my new netbook, I decided to upgrade from 9.04 to 9.10 on my PC.

BIG mistake :(

I've got the same problem now.  After starting the PC, I just see a white Ubunto logo and a message saying my disk is being checked.  This gets to about 31% before throwing the fsck / ctrl-D message and then just sitting there.  

Rebooting produced the same result, so I tried "running fsck manually" as it suggested.  That seemed to do the trick, but Ubuntu promptly fell over and died shortly after re-booting.  

I'm now having to type this from Windows as my Ubuntu seems to be completely bolloxed now.

Anybody have any idea how I can recover my Ubuntu installation or have I lost everything?

As you might guess, I'm NOT very happy about this...

:(

ETA:
I originally posted on [this]("http://ubuntuforums.org/showthread.php?t=1409754") thread, which describes a similar problem.  One poster suggested that using fsck can trash your disk:  I'm really hoping this hasn't happened to mine...

---

