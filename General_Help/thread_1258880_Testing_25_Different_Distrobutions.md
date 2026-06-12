---
title: "Testing 25 Different Distrobutions"
date: 2009-09-05
forum: General Help
---

### Post by malura on 2009-09-05
I'm planning on testing around 25 (if not more) linux distros, and the idea of burning twenty five CDs/DVDs doesn't really turn me on. Is there any way to store all of the isos in a single directory, and boot into each of them individually?

---

### Post by NoaHall on 2009-09-05
You could buy a re-writeable dvd. Or if you're just going to use a Virtual Machine, you don't need to burn.

---

### Post by starcraft.man on 2009-09-05
> **malura said:**
> I'm planning on testing around 25 (if not more) linux distros, and the idea of burning twenty five CDs/DVDs doesn't really turn me on. Is there any way to store all of the isos in a single directory, and boot into each of them individually?

Easiest way to try that many distributions is like ya said, download all the ISOs, put em in a directory. Then use a virtual machine of your choice and try em. Installing all of those to drive just to try, that'd be way too much hassle IMO.

VirtualBox is a good solution, in the repos. Install it on Ubuntu, then create a machine with the right specs to run it, then simply tell the settings to mount the ISO and run. Long as your on anything past a P4 level, performance should be acceptable.

If ya need more info on vbox, see the virtual box website. To install, get the virtualbox-ose package from repositories. If ya need help with installing, see my signature.

One or two RW CDs would do if you don't have the power for a VM. Then ya could install them local.

---

### Post by malura on 2009-09-05
I would use virtual machines, but I'm trying to create an accurate performance assessment for each distro. True, I could buy rewritable DVD's and burn each individually, but that would be using time and money I don't have at the moment. Any other ideas?

---

### Post by snowpine on 2009-09-05
Use Unetbootin to create a bootable USB thumb drive?

---

### Post by malura on 2009-09-05
Oooh, that's a start. If only there was a way to use Unetbootin to add more than just one distro, and have something like grub show each of them.

---

### Post by NoaHall on 2009-09-05
Well, you could create a partition, artificially mount the iso, and then install to the other partition from within your OS.

---

### Post by bodhi.zazen on 2009-09-05
> **malura said:**
> Oooh, that's a start. If only there was a way to use Unetbootin to add more than just one distro, and have something like grub show each of them.

no, unetbootin will not do this. In fact you need to completely remove the first distro before you install the second.

---

### Post by starcraft.man on 2009-09-05
> **malura said:**
> I would use virtual machines, but I'm trying to create an accurate performance assessment for each distro. True, I could buy rewritable DVD's and burn each individually, but that would be using time and money I don't have at the moment. Any other ideas?

Do you really need to try 25 distributions? I mean trying 25 of anything will take a lot of time. How much do you plan on devoting to each distro before trying next? Maybe an hour?

As bodhi replied, unetbootin is one at a time. There's no magic solution to trying that many different distros all live on one machine to asses performance.

---

### Post by bodhi.zazen on 2009-09-05
> **starcraft.man said:**
> Do you really need to try 25 distributions? I mean trying 25 of anything will take a lot of time. How much do you plan on devoting to each distro before trying next? Maybe an hour?

+1

The GUI interface is 99.9 % the same, KDE is KDE and gnome is gnome.

Under the hood, 85-90 % of what you know is the same across distros.

Better find one that works well with your hardware and learn what you can.

---

### Post by scion xd on 2009-09-06
Thank you guys, just from reading your posts most of the time I  find the answer. 

like Unibooten, man thats a good program, and i don't have to waste me DVDs to experiment with distros.

Thank you again

---

