---
title: "Icedtea out of date"
date: 2012-08-16
forum: General Help
---

### Post by sir.Evan on 2012-08-16
I am running the latest version of Ubuntu 12.04 on a HP laptop.

I am using Chrome as browser but have got a problem logging into my bank. I am getting this error message: Icetea out of date

AS far as I can see Icedtea is part of the Ubuntu package but it is for some reason not updated by Ubuntu??!!!

I have tried to fix the problem by removing icetea and reinstalling it but without any luck in solving the out of date problem.

Chrome suggest that I update from this website  [http://blog.fuseyism.com/index.php/2012/06/12/security-icedtea6-1-10-8-1-11-3-released/](http://blog.fuseyism.com/index.php/2012/06/12/security-icedtea6-1-10-8-1-11-3-released/)

where a complicated instruction is given.

Is that the way to fix my Icedtea update problem or is there an easier way?

---

### Post by jockyburns on 2012-08-16
Do you get the option to update the plugin and another option to "run this time" ? 
I've been having problems with Java and I now choose the "Run this time " option. Works for me. 
Seems to be a known bug though. ;);)

---

### Post by QIII on 2012-08-16
In the interest of security, your bank has probably decided not to operate when older versions are present.  A recent security exploit in Java exposed the opportunity to "escape" the sandbox and run in the user context.

Oracle Java 7 Update 5 eliminated that.  Oracle Java 7 is now up to Update 6.

OpenJDK and the IcedTea plugin may appear to be old enough to be victims of that exploit.

OpenJDK is the open source reference implementation of Oracle Java, but even though Oracle is heavily involved in its development it may lag behind by an update or two.

Also remember that there is a delay in what appears in the repos while things are tested for inclusion.

---

