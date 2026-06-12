---
title: "Medion Graphics Tablet"
date: 2010-03-16
forum: General Help
---

### Post by Zayfox on 2010-03-16
So I've got this Medion graphics tablet that I somehow managed to get working with on Karmic, however when I updated to Lucid Lynx, no matter what I do, I can't seem to get the damn thing reconfigured to work. To be honest, I don't even remember how I did it last time, and all of the stuff I've read so far regarding compiling just give me an error:
> ./xf86Wacom.c:545: error: too few arguments to function &#8216;InitValuatorAxisStruct&#8217;
Quick info:
Lucid Lynx Alpha 3(Latest?)
**EDIT** NOW ON KARMIC KOALA.
Medion Graphics Tablet (Waltop, ALDI version)
X.org

I'm not sure where I'm going wrong, or if I'm just not doing it right in the first place. Anyone done this previously?

And please don't just link me to another topic. I've read so many that I've lost count, and none have helped so far.

---

### Post by s.fox on 2010-03-16
Hello,

I recall reading that in lucid lynx alpha 2 some problems with wacom were still present.  I do not know if alpha 3 rectified this.

> The wacom-tools driver cannot be used with Lucid Alpha 2. It is no longer supported for xserver 1.7, and also requires HAL for configuration which is no longer available. A new driver xf86-input-wacom is under development upstream but was not yet available in time for this milestone release. This is expected to be resolved for the final release of Ubuntu 10.04 LTS. 

Information sourced from [here]("http://www.ubuntu.com/testing/lucid/alpha2")

I am sorry I cannot offer more to help than that. :(

-Silver Fox

---

### Post by Zayfox on 2010-03-16
> **Silver_fox_ said:**
> Hello,

I recall reading that in lucid lynx alpha 2 some problems with wacom were still present.  I do not know if alpha 3 rectified this.



Information sourced from [here]("http://www.ubuntu.com/testing/lucid/alpha2")

I am sorry I cannot offer more to help than that. :(

-Silver Fox
Yeah, by the looks of that error in my OP, I think I was using the xf86 version, but that clearly didn't work either. =\

---

### Post by s.fox on 2010-03-16
Hello,

Yes,  sorry this is the part which I think applies to you:

 > A new driver xf86-input-wacom is under development upstream but was not  yet available in time for this milestone release. This is expected to  be resolved for the final release of Ubuntu 10.04 LTS. 			 		

Perhaps xf86 is not finished.

---

### Post by Zayfox on 2010-03-16
> **Silver_fox_ said:**
> Hello,

Yes,  sorry this is the part which I think applies to you:

 

Perhaps xf86 is not finished.
Gah! >_<
I need it for a project that is due soon.
Gotta love work.

Alright, thanks Silver_fox_. :)

---

### Post by Zayfox on 2010-03-17
And I'm back.
After a LONG night, downgraded back to Karmic and I still can't get this ******* thing to work. I'm at the point of almost snapping the tablet in frustration at the complexity of getting a simple drawing device to work with Ubuntu.

Now on Karmic, any help please?

---

### Post by drpjkurian on 2010-03-17
Hi
Please try this thread, It may help you out. I advice you to contact Favux if required in the forum who is a wizard in Wacom tablet drivers

---

### Post by drpjkurian on 2010-03-17
Hi
Please try this [thread]("http://http://ubuntuforums.org/showthread.php?t=1292227"), It may help you out. I advice you to contact Favux if required in the forum who is a wizard in Wacom tablet drivers

---

### Post by Zayfox on 2010-03-17
That's for calibration, but thanks because knowing me I'll need to mess with it even when it's working.

I've gotten as far as being able to move the cursor with the tablet. The standby light (flashes on and off when on, but not being used) turns off when the pen touches the pad, but I still can't 'click'.

---

### Post by Zayfox on 2010-03-18
Bumping for justice.

---

### Post by Zayfox on 2010-03-18
*sigh*
Yet another shameless bump.

---

