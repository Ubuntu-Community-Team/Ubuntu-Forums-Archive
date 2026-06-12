---
title: "Create LiveCD exactly as system is on HDD"
date: 2011-03-15
forum: General Help
---

### Post by jnelejff on 2011-03-15
For the last several days, I have been trying to create a liveCD exactly like my system is on my HDD.

I have tried doing it with the instructions on this thread:
[http://ubuntuforums.org/showthread.php?t=688872]("http://ubuntuforums.org/showthread.php?t=688872")

as well as using Remastersys.  Both methods certainly gave me a LiveCD with the applications I wanted, but I need the default desktop/files/theme/etc to be exactly as I have it. (am i making sense?)

Is there an easy method to modify the ISO i've already compiled?

---

### Post by jnelejff on 2011-03-16
bump

---

### Post by Rebelli0us on 2011-03-16
I don't think there is an easy way to copy Profile settings in linux. Customisations are all in cryptic files starting with a dot in filename. However you can install to a USB flash drive and then make all the changes you want so that it's exactly like your HDD. Use "startup disk creator".

---

### Post by pqwoerituytrueiwoq on 2011-03-16
do **not** put a swap partition on the flash drive

---

### Post by NumPy on 2011-03-16
I have not actually done this, but looking at the tutorial in section B: if you are following verbatim the command and excluding your /home directory you will not copy over your settings that are currently in your /home directory. (desktop settings, backgrounds, files, etc.) Not excluding this however will likely create a much larger live cd depending on your /home directory size. You can probably instead exclude /home/Documents etc.
Also in the ISO itself you should be able to add default images, and settings to the livecd user, and rebuild the ISO.

---

### Post by jnelejff on 2011-03-16
> **NumPy said:**
> I have not actually done this, but looking at the tutorial in section B: if you are following verbatim the command and excluding your /home directory you will not copy over your settings that are currently in your /home directory. (desktop settings, backgrounds, files, etc.) Not excluding this however will likely create a much larger live cd depending on your /home directory size. You can probably instead exclude /home/Documents etc.
Also in the ISO itself you should be able to add default images, and settings to the livecd user, and rebuild the ISO.

Thanks, now second question involving the first tutorial.  The end result gave the liveCD the default login credential.  Will this give the liveCD my current credentials? if not, how do I define them?

---

### Post by NumPy on 2011-03-18
> **jnelejff said:**
> Thanks, now second question involving the first tutorial.  The end result gave the liveCD the default login credential.  Will this give the liveCD my current credentials? if not, how do I define them?

In section C:8 of that same tutorial you are asked to 'remove' the non-system users. (from the bash script it grabs users from 999 - 65534) This will remove standard user accounts since they start with 1000 typically.
One way I would do it is chroot into the build system again, add the user account via useradd and then rebuild the system and ISO. OR you could follow the steps, but change it to look for users above 1000. (i.e. from the example given:
```

for i in `cat /etc/passwd | awk -F":" '{print $1}'`
do
	uid=`cat /etc/passwd | grep "^${i}:" | awk -F":" '{print $3}'`
	[ "$uid" -gt "1000" -a  "$uid" -ne "65534"  ] && userdel --force ${i} 2>/dev/null
done

```
the modification above says to find user accounts that are greater than (gt) 10000 and not equal to (ne) 65534. )

Since this tutorial is your reference, and it well written is why I keep pointing to it. :-)

---

