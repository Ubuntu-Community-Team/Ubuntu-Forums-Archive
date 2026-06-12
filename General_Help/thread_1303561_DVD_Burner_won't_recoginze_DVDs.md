---
title: "DVD Burner won't recoginze DVDs"
date: 2009-10-28
forum: General Help
---

### Post by madprofessor on 2009-10-28
I have a Memorex DVD burner that's SATA and it will recognize CDs blank and written but will not recognize DVDs blank or written. It acts as if nothing is in the drive. Any suggestions?

---

### Post by Giblet5 on 2009-10-28
This can happen when your cat uses the opened DVD tray as a springboard to swan dive into your coffee mug.

Don't ask me how I know this.

I've replaced two DVD burners on my wife's computer because she forgets to close the drawer.

The alignment is critical on those drives.

---

### Post by jward3010 on 2009-10-28
> **Giblet5 said:**
> This can happen when your cat uses the opened DVD tray as a springboard to swan dive into your coffee mug.

Don't ask me how I know this.

I've replaced two DVD burners on my wife's computer because she forgets to close the drawer.

The alignment is critical on those drives.
HA HA HA! Too true!

It's very true, there are two lasers at work in a DVD / CD drive. One laser for DVD's and one for CD's. And typically first to die is DVD due to it's much required accuracy compared to CD. 

It's down to the fact that, as you know DVD capacities are way larger than CD capacities yet on the same size disc. This is possible because the laser light that burns the data pits on is much tinier than the laser light thats used for CD burning - this ends up with creating much denser discs, same goes for BluRay, the light wavelength is tinier once again, down to  the point that it can burn up to 50GB to a disc.

---

### Post by SunnyRabbiera on 2009-10-28
> **madprofessor said:**
> I have a Memorex DVD burner that's SATA and it will recognize CDs blank and written but will not recognize DVDs blank or written. It acts as if nothing is in the drive. Any suggestions?

Did you install all the needed DVD tools, like libdvdcss, libdvdread, etc?
Of course its possible that something went wrong somewhere and your DVD Burner lost its ability to read/write DVD's... I had that happen on me once, not pretty.

---

### Post by madprofessor on 2009-10-28
What all DVD tools would be needed? Would I just check Package Manager?

---

### Post by madprofessor on 2009-10-28
Did a little research and tried

> sudo apt-get install dvd+rw-toolsand got this.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
dvd+rw-tools is already the newest version.
The following packages were automatically installed and are no longer required:
  python-pycurl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by jward3010 on 2009-10-28
Now what would be weird is if Windows was installed too and it worked in Windows. Is this the case?

---

### Post by madprofessor on 2009-10-28
I only have Ubuntu installed.

---

### Post by jward3010 on 2009-10-28
Then more than likely it's the drive. Bear in mind the two laser fiasco again.

---

### Post by P4man on 2009-10-28
A hardware issue sounds most likely. If you want to make sure, perhaps try a bootable DVD, see if you can boot from it. If you can, then we're back to square one, but im pretty sure it wont boot, which would pretty much prove a hardware failure.

---

### Post by madprofessor on 2009-10-28
I'll try that. But if it does work then what?

---

### Post by P4man on 2009-10-28
<insert clever/funny proverb about the pointlessness of speculation>

---

### Post by madprofessor on 2009-10-28
> <insert clever/funny proverb about the pointlessness of speculation>

Lol.

So I just took the burner out and plugged it into an XP machine. And same thing, it doesn't recognize the DVD. So it is a hardware issue. And I need to call Memorex.

---

### Post by jward3010 on 2009-10-29
> **madprofessor said:**
> Lol.

So I just took the burner out and plugged it into an XP machine. And same thing, it doesn't recognize the DVD. So it is a hardware issue. And I need to call Memorex.
Yep, or just buy a new burner, cheap as chips these days.

---

