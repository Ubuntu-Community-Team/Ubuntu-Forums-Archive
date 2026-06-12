---
title: "Can't burn to a disk?"
date: 2009-10-16
forum: General Help
---

### Post by mikerpiker on 2009-10-16
Hi,

I'm trying to burn a .iso of a Windows installation disk onto a blank CD.  I've tried this using Brasero, and by simply right clicking the .iso file and clicking "write to disc."  

In both cases, it goes through the motions as if it were burning (disk whirrs, computer seems to be working hard, it tells me the writing speed, the progress bar fills up) but when it finishes, the disc that comes out has nothing on it.  When I put it in the CD drive and examine its contents -- there's nothing there.

What's the deal?  Can I install windows from an ISO file without burning it onto a disk?

---

### Post by OpenGuard on 2009-10-16
Install GnomeBaker ( Brasero have never worked right for me ).

---

### Post by mikerpiker on 2009-10-16
> **OpenGuard said:**
> Install GnomeBaker ( Brasero have never worked right for me ).

Thanks, I'll try this.  I'm not sure if it's a problem specifically with Brasero, though, since "CD/DVD creator," which I think is a different program, seemed to have the same problem.

---

### Post by mikerpiker on 2009-10-16
If I simply put the ISO file on a data disk using Gnomebreak, will the CD work properly?

---

### Post by MaindotC on 2009-10-16
> **mikerpiker said:**
> Hi,
Can I install windows from an ISO file without burning it onto a disk?

Absolutely!  Install it in a [Virtual Machine using VirtualBox](http://en.wikipedia.org/wiki/VirtualBox) so you can save an installed image (so you never have to re-install and when the trial period ends you just revert back to the saved image and voila!), plus VBox has support for USB connectivity so you can run all your windows-dependent devices like media players or cell pones on the virtual machine and still keep the safety and stability of a Ubuntu host machine.

If that's not of interest to you, you investigate a [network installation of windoze](http://www.google.com/search?q=windows+network+installation&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a).

---

### Post by mikerpiker on 2009-10-16
Nevermind my last post, I found the "burn cd image" option, and it's now burning.  Hopefully I have more success this time than I did with Brasero and Cd/DVD maker.

---

### Post by wojox on 2009-10-16
You're not making a data disk, you're burning an .iso. 
Did you select that in Brasero?
Hasn't let me down yet.

---

### Post by mikerpiker on 2009-10-16
> **strAlan said:**
> Absolutely!  Install it in a [Virtual Machine using VirtualBox](http://en.wikipedia.org/wiki/VirtualBox) so you can save an installed image (so you never have to re-install and when the trial period ends you just revert back to the saved image and voila!), plus VBox has support for USB connectivity so you can run all your windows-dependent devices like media players or cell pones on the virtual machine and still keep the safety and stability of a Ubuntu host machine.

If that's not of interest to you, you investigate a [network installation of windoze](http://www.google.com/search?q=windows+network+installation&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a).

Hi, thanks for the ideas.  

About using VirtualBox:

The reason I want to install Windows is to be able to play World of Warcraft.  I've tried playing it on Wine, but it ran very slowly. I'm worried that if I use VirtualBox (I haven't tried it on there yet) that I'll have a similar problem.  I can barely run WoW when I'm even when I'm just using Windows, so I think emulating it might be out of the question.

I'll look into your other suggestion.

---

### Post by mikerpiker on 2009-10-16
> **wojox said:**
> You're not making a data disk, you're burning an .iso. 
Did you select that in Brasero?
Hasn't let me down yet.

I didn't select that.  I just right clicked the ISO and clicked "Write with Brasero" or something like that.  

Still, if it wrote it as a data disk, wouldn't I see the ISO file on the disc?  Instead, it stayed blank after it said it was finished burning.

---

### Post by wojox on 2009-10-16
Never done it that way, maybe that's why it didn't work? Open Brasero and click the bottom box "Burn Image"

---

### Post by mikerpiker on 2009-10-16
I had the same problem again with Gnomebaker -- it said it was burning the disk... did that for 20 minutes or so... said it was finished...

but there's nothing on the disk.

---

### Post by mikerpiker on 2009-10-16
bump!:)

---

### Post by mikerpiker on 2009-10-16
It's the most frustrating thing!!  I just tried it again in Brasero.  It spins and whirrs and my computer works and works, and everything seems to be working well and as it should, and it finishes and the disk pops out -- and there's nothing there.

---

