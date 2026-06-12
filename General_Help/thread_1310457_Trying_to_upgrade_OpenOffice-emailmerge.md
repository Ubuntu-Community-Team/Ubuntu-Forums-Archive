---
title: "Trying to upgrade OpenOffice-emailmerge"
date: 2009-11-01
forum: General Help
---

### Post by JackRock on 2009-11-01
I keep getting the following message, despite that Openoffice is not open.  Keep in mind that I just switched to Linux a few days ago, so I have been looking for something like Windows' Task Manager, but no luck.  I don't have any OO icons open.


"OpenOffice.org is running right now. A running OpenOffice.org makes extension (de-)registration not possible and it causes problems with (de-)registering components.

Please close OpenOffice.org (including an eventually running Quickstarter)."


Any help would be appreciated.  There is another error message later on, similar, but for another part an OO.org upgrade.

---

### Post by JackRock on 2009-11-03
Nobody?  Bump for an answer.  I stll haven't been able to work this out.

---

### Post by Mike Beggs on 2009-11-11
I'm having this problem as well, in the upgrade to 9.10.

Jack, you can find the Task Manager equivalent under System>Administration>System Monitor.

But in my case, I don't find any processes that are obviously related to OpenOffice.

Cheers,
Mike

---

### Post by JackRock on 2009-11-12
I thought I had the problem taken care of, but not so much.  Now, these items no longer show up in the upgrade list, but I still keep getting the errors when upgrading something - be it through Terminal or the Upgrade Manager.

I was suggested to use "sudo skill" on the pid, but that only seemed to make the problem go away.  I still get the errors.  I have a question logged at [https://answers.launchpad.net/ubuntu/+question/88376](https://answers.launchpad.net/ubuntu/+question/88376) as well.

---

### Post by chazhall on 2009-11-13
I'm having almost the identical problems, so it's not just one instance of the "problem".

---

### Post by axelsvag on 2009-11-17
Seems to be alot of people having this problem including me. Hope a cure will come soon.

---

### Post by JackRock on 2009-12-20
I resolved the issue by downloading the ISO for the current ubuntu version, and installing it.  It kept all my files, programs and settings, but did the last few updates that were unable to do so until now.

This kept the programs from starting their services prior to the upgrading.

---

### Post by powerfade1 on 2010-02-05
This happened to me, too.

Does anyone know if this is the only solution?  Is there another way?

---

### Post by iris_v on 2010-03-10
> **powerfade1 said:**
> This happened to me, too.

Does anyone know if this is the only solution?  Is there another way?

I managed to solve the issue by booting in Recovery Mode and selecting the option to repair broken packages.

---

