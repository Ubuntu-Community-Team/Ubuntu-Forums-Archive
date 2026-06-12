---
title: "Gimp command 'Save As' saves but closes Gimp"
date: 2012-09-27
forum: General Help
---

### Post by ffrr on 2012-09-27
Hi all,

Since I upgraded to 12.04 the Gimp command "Save As" saves all right but then closes the editor every time with all recent edits unsaved. What may  be the problem?

Dell Latitude E6500
Ubuntu 12.04
Gimp 2.6.12

Frederic

---

### Post by LinuxUser50 on 2012-12-29
> **ffrr said:**
> Hi all,

Since I upgraded to 12.04 the Gimp command "Save As" saves all right but then closes the editor every time with all recent edits unsaved. What may  be the problem?

Dell Latitude E6500
Ubuntu 12.04
Gimp 2.6.12

Frederic

I am also running 12.04/Gimp 2.6 on Toshiba Satellite and have same problem. Can't help you with technical why's and wherefore's as all I know about computers is they are square-ish and plug into a socket. However I do use a simple but slightly more time-consuming tactic to get around this problem. Figuring how many different versions of the original image I wish to produce, I right click and copy the image that many times back into the folder it's residing in, so you end up with (example) image1, image1(copy), image1(another copy), image1(a 3rd copy) and so on.
Then open Gimp, and crop/modify each copy to what you want from it, and just SAVE, not SAVE AS. For your next version of the original image, just pull up another copy and repeat the process. Leave your original untouched. I do it this way to split up group photos into individual shots, or crop different scenes out of larger images, apply artistic effects to some versions etc.
It's a setback to getting on with the job quickly, but at least Gimp stays open and keeps flowing pretty normally, and it's a lot quicker and less frustrating than restarting Gimp over and again.

Cheers.

---

### Post by ibjsb4 on 2012-12-29
Maybe a bug

[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1067514](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1067514)

---

