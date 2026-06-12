---
title: "Brasero Vs whatever MS Windows based"
date: 2011-03-09
forum: General Help
---

### Post by Ariya243 on 2011-03-09
Lately, I have found that I have to go back to Vista (yes, old Vista no one loves) to burn an iso file on to a CD-RW. 

Brasero simply don't even see the CD-RW to even blank it, let alone burn the new iso file. I am using Ubuntu 10.04. As I have Debian 6 (gnome and KDE) I tried the same CD-RW, but neither Brasero, nor KDE's K3B 'saw' the CD-RW.

But, the in that Vista, the CD/ISO burning software 'saw' the CD-RW without fail. 

Btw, this same problem happens with Unetbootin. Linux Unetbootin works worse than the Vista Unetbootin!

Now, I have to use Vista to burn CD/DVD/Isos.

Is there a some special problem with Linux burning software? I know that some developers are not happy with Brasero, but there must be a way!

---

### Post by kc1di on 2011-03-09
> **Ariya243 said:**
> Lately, I have found that I have to go back to Vista (yes, old Vista no one loves) to burn an iso file on to a CD-RW. 

Brasero simply don't even see the CD-RW to even blank it, let alone burn the new iso file. I am using Ubuntu 10.04. As I have Debian 6 (gnome and KDE) I tried the same CD-RW, but neither Brasero, nor KDE's K3B 'saw' the CD-RW.

But, the in that Vista, the CD/ISO burning software 'saw' the CD-RW without fail. 

Btw, this same problem happens with Unetbootin. Linux Unetbootin works worse than the Vista Unetbootin!

Now, I have to use Vista to burn CD/DVD/Isos.

Is there a some special problem with Linux burning software? I know that some developers are not happy with Brasero, but there must be a way!
I,m not aware of any particular problems with Brasero or k3b used them both here and they burn ISO's just fine. 
Wondering if you say they can't see you cdrw drive if it's installed with all it's drivers.  It might help if you could post the make of the  particular drive in question.  It may need more drivers than are installed.  

I had that problem with an older machine and cd rom drive a few years ago. problem was that there were no drivers available for it.
Hope that's not your case :(
you may want to install fxburn from synaptic it has never failed me either.

you mention that it ISO's that have been giving you problems can you burn other files ok?

just some thoughts that may help.

---

### Post by leviathan8 on 2011-03-09
Have you considered adding the Medibuntu repo? You could download from there codecs for encrypted dvd's and then give it a shot again.

[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

---

### Post by Ariya243 on 2011-03-09
This is a new machine, even though it has old Vista. Its Core2duo machine with a very good CD/DVD writer. I have some CD-RWs and DVD-Rws, which I don't really like to throw away, so I try to use them as much as possible. I found that Vista's CD/DVD Iso burning software would burn the CD-RW (or DVD-RWs) which Brasero cannot 'see' to even blank them. After sometime, instead of throwing these disks without checking them with Vista, I have saved the disks. It doesn't cost much, but I don't really like to spend, if I don't have to. yes, (I have Medibuntu repo too)

Maybe, once we start using Linux, we don't want to use any MS Windows, but for some programs like Google Sketchup, we need MS Windows. Now, to save few CD-RWs this Vista helped. Maybe, I think the Linux developers must think about this and make Brasero very good, I mean in Ubuntu really. I am waiting for the 11.04 in April, and I hope things will be even better!

Thanks guys!

---

### Post by celldweller1591 on 2011-03-09
Try K3B or any one of the listed ones here > [Cd/DVD Burning Tools](www.linoob.com/2010/04/cddvd-burning-tools)

---

### Post by Ariya243 on 2011-03-09
K3b is bit better than Brasero.
Thanks anyway!

---

### Post by Jerry N on 2011-03-09
You could try downloading Nero for Linux and see if it works.  You can try it free for some limited amount of time.  Some people badmouth Nero for Linux, probably because it costs money, but I generally prefer it to the other Linux burning programs.  Nero for Linux is not nearly as bloated as Nero for Windows.

Jerry

---

### Post by cottfcfan on 2011-03-09
+1 for Nero Linux

---

### Post by Roasted on 2011-03-09
That's funny. Yesterday I had two failed ISO burns with ImgBurn in Windows 7 when burned @ 1x speed.

I boot to Ubuntu, fire up Brasero, burn the same ISO and blam - finally on the third try a completed ISO image.

---

### Post by Ariya243 on 2011-03-09
Hey, I didn't want any arguments started. I only wanted to know whether this is normal for most, and if so Ubuntu would make it even better! 

Thank you for help!

---

### Post by TeoBigusGeekus on 2011-03-09
Try from the command line:
```
wodim -v dev=/dev/dvd /path/image.iso
```
Replace dvd with whatever applies to your system (cd, sr0, etc.)

---

### Post by Jerry N on 2011-03-09
> **Ariya243 said:**
> Hey, I didn't want any arguments started. I only wanted to know whether this is normal for most, and if so Ubuntu would make it even better! 

Thank you for help!

No arguments - just comments on what works and doesn't work for different people.  

Jerry

---

