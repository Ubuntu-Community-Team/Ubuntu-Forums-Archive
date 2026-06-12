---
title: "PC Won't Power Off at Shutdown v2"
date: 2011-04-03
forum: General Help
---

### Post by Kross on 2011-04-03
Hello,.
A few years back I had a PC with (Asus) MotherBoard. 
And everything work wonderfully, subtract that it would not finish the power off or shutdown, HD would spin down,,Screen off,,but PC still lite and fans still running..

seemed to be something to do with ACPI or something about power managment.

Back Then I found a workaround.
Link here - [http://ubuntuforums.org/showthread.php?t=307643]("http://ubuntuforums.org/showthread.php?t=307643")

which was in short 

[COLOR="Red"]append="acpi=off apm=power_off"

to /etc/lilo.conf and 

apm power_off=1

in /etc/modules

and add to grub so acpi=off apm=power_off in my /boot/menu.lst
file.[/COLOR]

And that Force a complete PowerOff. 
I have since given this PC to my bother.
He Put Ubuntu 10.04 on it,, Which I think has Grub2.
So when he asked me to help with his little shutdown problem,,
I found my old post & applied it to the system best we could..

But Still No PowerOff.

So I opened a Post, Anyone know why or what step can be taken...
If you do please list all steps..So if need be I can use the post, As i was so happy to find my old post when needed.

Thank You,
Kross

---

### Post by Kross on 2011-04-07
ANyONe?

---

