---
title: "My PPA are marked as disabled after ubuntu upgrade ??"
date: 2011-06-27
forum: General Help
---

### Post by q8_legend on 2011-06-27
Hi

when I have updated my ubuntu 10.10 to 11.04, many PPA have been disabled & I can't use them right now. I have checked about them in the repositiries & they are marked as diabled since updated to naty(11.04)...

So my question is, can I enable these repositiries(PPA) ?? Is it safe to re enable them or not ?? if not... what should I do now ?? I have many PPA that have been diabled, such as:
rhythmbox,wine,weupd8 team ... much more...

I hope there is a soulution with that, since each time I upgrade my computer to the new version I'm facing this issue...


Thanks alot

---

### Post by tim3runn3r on 2011-06-27
Those repositories are going to have to be updated to use with 11.04. Make sure you clear the old ones out either through synaptic or terminal. Then add them back like you did in 10.10.

---

### Post by grahammechanical on 2011-06-27
Use the Software Centre. Select Edit>Software Sources. Then Other Software and select each PPA in turn and click Edit and in the little box change the Distribution from Maverick to Natty. It is as simple as that.

Regards.

---

### Post by plucky on 2011-06-27
> **grahammechanical said:**
> Use the Software Centre. Select Edit>Software Sources. Then Other Software and select each PPA in turn and click Edit and in the little box change the Distribution from Maverick to Natty. It is as simple as that.

Regards.

That's assuming there is a  repository for Natty.Otherwise you will get the 404 error.

Good Luck

---

### Post by Frogs Hair on 2011-06-27
PPAs are disabled for upgrade , check if the PPAs compatible with the latest release you have installed . You may find that some are not .

---

