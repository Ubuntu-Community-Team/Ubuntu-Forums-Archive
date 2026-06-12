---
title: "grub2: hide vista recovery"
date: 2009-11-18
forum: General Help
---

### Post by P4man on 2009-11-18
Hi,

Im setting up a machine for a friend, just installed ubuntu, but I would like to **hide the oem's vista recovery partition** in grub to avoid her accidentally booting into that and reformatting the whole drive.

I looked at all grub2 threads and howto's but I cant figure this out. I see how to rename it, I can remove it "temporarily" (until the next update grub is run), but I cant see how to permanently hide /dev/sda1 from grub.

Anyone know?

---

### Post by drs305 on 2009-11-18
To hide the Windows Recovery partition: 

Backup the existing /etc/grub.d/30_os-prober file, remove the executable bit from the backup so it isn't run during updates, and open the original for editing (the section starts around line 83):

```
sudo cp /etc/grub.d/30_os-prober /etc/grub.d/30_os-prober.original  && sudo chmod -x /etc/grub.d/30_os-prober.original
gksu gedit +83 /etc/grub.d/30_os-prober &
```

Add the highlighted entry. It looks for an entry which would be entered as "Windows Vista (loader) (on /dev/sda1)". If the menu entry or partition changes, make the same changes below. The area in [COLOR="Red"]bright red[/COLOR] should be the exact contents between the quotes in the menuentry for the recovery partition:

> for OS in ${OSPROBED} ; do
DEVICE="`echo ${OS} | cut -d ':' -f 1`"
LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
BOOT="`echo ${OS} | cut -d ':' -f 4`"

if [ -z "${LONGNAME}" ] ; then
LONGNAME="${LABEL}"
fi

[B][COLOR="DarkRed"]# Added to remove Windows Recovery
if [ "$LONGNAME" = "[COLOR="Red"]Windows Vista (loader)[/COLOR]" ] && [ "${DEVICE}" = "/dev/[COLOR="Red"]sda1[/COLOR]" ] ; then
continue
fi
# End Added[/COLOR][/B]



Save the file, then run:
```
sudo update-grub
```

I have a Grub 2 Title Tweaks thread. I've worked this problem for another user but I don't think I included it specifically in that thread. Let me know your results, any comments on the instructions, and I'll add it if it works for you. 

Added: Please tell me what how the name for the Recovery partition is listed if it isn't "Windows XXXXX (loader)". That is what it was on the previous user's machine, but on his the recovery and normal partitions were identified with the same designation, which I found odd.

---

### Post by P4man on 2009-11-18
Excellent that seems to do the trick. Cant reboot yet, but update-grub only lists ubuntu and vista on /dev/sda2 so it looks like it did the job :)

Care to explain how this works? I mean I understand the test you're doing what I dont understand is if it matches the recovery entry that "continue" skips it? 

Thank you very much already, also for the excellent grub2 howto's I had already checked, perhaps you can add this to them.

---

### Post by drs305 on 2009-11-18
> **P4man said:**
> Care to explain how this works? I mean I understand the test you're doing what I dont understand is if it matches the recovery entry that "continue" skips it? 

That's right. The 30_os-prober does a search of the partitions and the script is set up as a loop. (for OS in ${OSPROBED} ; do)  
The code you entered told the script to just move on and not create a menuentry if it finds the recovery partition.

Would you please tell me how the recovery partition was listed in your menuentry?

---

### Post by P4man on 2009-11-18
> **drs305 said:**
> That's right. The 30_os-prober does a search of the partitions and the script is set up as a loop. (for OS in ${OSPROBED} ; do)  
The code you entered told the script to just move on and not create a menuentry if it finds the recovery partition.

its the skipping part I dont understand. I suppose "continue" means proceeding to the next "for" loop?

> Would you please tell me how the recovery partition was listed in your menuentry?

Hope this will do:
```

Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2

```

I think this how it appeared in grub as well, no mention of recovery or anything, thats why I wanted to hide it.

---

### Post by drs305 on 2009-11-18
> **P4man said:**
> its the skipping part I dont understand. I suppose "continue" means proceeding to the next "for" loop?


Yes, exactly. Originally, on my first attempt, I used "break" but it broke the link completely and stopped looking for additional kernels/OSs. "continue" tells it to stop the current "for" and continue on to the next one.

> 
Hope this will do:
```

Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2

```

I think this how it appeared in grub as well, no mention of recovery or anything, thats why I wanted to hide it.

Thanks. That confirms that the entry is the same for both the Reovery and normal Vista partitions and that the "/dev/sdXX" must also be included. 

I can see how users would want to hide it. I will add this as an entry to the [Grub 2 Title Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602") post.

---

### Post by mcfunthomas on 2011-02-02
Hello!

On my laptop I've got Vista and Win7 + Ubuntu 10.04 lucid lynx.

To hide my vista recovery partition and change the names of my 2 win systems I commented the default lines, i.e.

[COLOR=Navy]#  if [ -z "${LONGNAME}" ] ; then
#     LONGNAME="${LABEL}"
#  fi[/COLOR]

and added below them the following lines:

[COLOR=Orange][B][COLOR=DarkOliveGreen]if [ "$LONGNAME" = "Windows Vista (loader)" ] && [ "${DEVICE}" = "/dev/sda1" ] ; then
continue
   elif [ "${LONGNAME}" = "Windows Vista (loader)" ] && [ "${DEVICE}" = "/dev/sda2" ] ; then
         LONGNAME="Windows Vista Home Premium"
   elif [ "${LONGNAME}" = "Windows 7 (loader)" ] ; then
         LONGNAME="Windows 7 Ultimate"
   elif [ -z "${LONGNAME}" ] ; then
      LONGNAME="${LABEL}"
fi[/COLOR][/B]

[COLOR=Black]where[/COLOR][/COLOR]**[COLOR=DarkOliveGreen]"Windows Vista (loader)"[/COLOR]** and[COLOR=Orange]**[COLOR=DarkOliveGreen]"Windows 7 (loader)"[/COLOR]** [COLOR=Black]are [/COLOR][/COLOR][COLOR=Black]names given by linux,
[/COLOR][COLOR=Orange][COLOR=Black]and where[/COLOR][/COLOR][COLOR=Orange]**[COLOR=DarkOliveGreen]"Windows Vista Home Premium"[/COLOR]** [COLOR=Black]and [/COLOR][/COLOR]**[COLOR=DarkOliveGreen]"Windows 7 Ultimate"[/COLOR]** are the names of my desire.

[COLOR=Orange][COLOR=Black]I hope somebody might find it helpful.[/COLOR]
[/COLOR]

---

### Post by amont on 2011-04-29
> **drs305 said:**
> To hide the Windows Recovery partition: 

Backup the existing /etc/grub.d/30_os-prober file, remove the executable bit from the backup so it isn't run during updates, and open the original for editing (the section starts around line 83):

(...)

Added: Please tell me what how the name for the Recovery partition is listed if it isn't "Windows XXXXX (loader)". That is what it was on the previous user's machine, but on his the recovery and normal partitions were identified with the same designation, which I found odd.

Thank-you very much, drs305. I had exactly the same problem as P4man, and your suggestion worked perfectly. In my case (netbook Gateway with OS Windows 7) the SO found by grub were:

```
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
```

And, after the change, only the second line remain (despite first line says "Windows Vista (loader)", it recovers the system "Windows 7")

---

### Post by drs305 on 2011-04-29
amont,

Glad it's working.

Since I wrote this guide there is now a GUI app called Grub Customizer which can rename or hide entries in the Grub 2 menu. 

If you are interested in using this app I wrote a little guide. It's linked in my signature line: "Customizer".

---

### Post by oldfred on 2013-02-23
Thread closed.

Scripts have changed a lot since this thread as grub2 has evolved a lot.

Best to start new thread, manually edit grub,  or use grub custromizer.

---

