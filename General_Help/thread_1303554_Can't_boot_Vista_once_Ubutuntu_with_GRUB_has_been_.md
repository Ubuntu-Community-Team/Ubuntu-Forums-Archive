---
title: "Can't boot Vista once Ubutuntu with GRUB has been uninstalled..."
date: 2009-10-28
forum: General Help
---

### Post by Pott on 2009-10-28
Funny thing happened. I messed around Ubuntu, figured I'd delete it and repart the drive correctly this time. So I booted into Vista, deleted the partition with Ubuntu, booted from the Ubuntu CD and got rid of all my logical partitions under D (Extended) and made them all in one.

Then when I restarted, it said it couldn't find GRUB and didn't even boot Vista.

So I installed Ubuntu gain (installing right now) and will work from there. I'm hoping it works...

But for future reference, what precautionary steps should I take if I want the standard Vista loader to re-become default once GRUB is gone? Even though all my Ubuntu files were deleted, the PC was still looking for GRUB. 

Thanks!

---

### Post by P4man on 2009-10-28
the bootloader sits on the master boot record, not a partition. You cant see it in partition editor. Grub will load initially from the MBR and then load the rest from /boot. That part you deleted, so grub was unable to load completely.

If you want to use windows only, you just reinstall windows bootloader from the windows cd. That will erase grub from the mbr. If you want to keep using grub without ubuntu for some reason, you should make a small /boot partition just for grub.

---

### Post by Giblet5 on 2009-10-28
Previous post is correct.

---

### Post by Pott on 2009-10-28
I don't have an install CD, just a first partition I can boot from (ironically, only using GRUB) to restore the system to factory defaults (though I'd guess I can also use it to reinstall smaller parts of the system)

Anyway... I reinstalled Ubuntu and everything's ok now. But still... good to know... I'll need to find a way around that if I ever need to get rid of Ubuntu again.

Thanks!

---

### Post by Giblet5 on 2009-10-28
If you can boot to windows, you can run "fixmbr" and grub will be toast.

---

### Post by Pott on 2009-10-28
Thanks, good to know. I couldn't run into Windows at all though, nothing.

---

### Post by P4man on 2009-10-28
I think fixmbr and fixboot is only availble on the windows cd, but I could be wrong. (and perhaps you can download it somewhere). Then again if you're not desperate for diskspace you might as well keep ubuntu on there.

---

### Post by Pott on 2009-11-02
Sorry guys, one other question:

if I were to want to get rid of Ubuntu fully, how would I re-set MBR properly so that when I reboot Vista starts as normal..?

---

### Post by P4man on 2009-11-02
See above posts ?

---

### Post by Pott on 2009-11-02
I don't have a Windows boot CD. If I get rid of Ubuntu, I can't boot into Vista anymore. That's how it is so far...

---

### Post by sliketymo on 2009-11-02
> **Pott said:**
> I don't have a Windows boot CD. If I get rid of Ubuntu, I can't boot into Vista anymore. That's how it is so far...

You can try this:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by THE NICKSTER on 2009-11-02
funnily enough this happened to me last week, but i did use vista to delete the partition and expand the vista partition, but i forgot/ didn't know about the mbr. it took me two days to fix as "fixmbr" did not work for me. Eventually i found the answer, not sure if this works differently for vista or not, but i typed in the cmd prompt "**bootrec.exe/fixmbr**"
hope this helps

---

### Post by Pott on 2009-11-03
You can access the command from the boot menu or the bios..?

---

### Post by sliketymo on 2009-11-03
You have to have the CD first for it to work.

---

### Post by Pott on 2009-11-03
Like I said... I have no CD whatsoever. Well I have one for Ubuntu but none for Vista... That's the issue. If I get rid of Ubuntu, I can NOT boot into Vista anymore.

---

### Post by P4man on 2009-11-03
You can say and ask that 100x  but it wont solve your problem.
If you read the posts here you will see you **need** a windows cd, and someone even provided a link for you to download (legally) a win 7 recovery cd. That may or may not work for vista ( I suspect it will) but this really is a windows issue, more precisely one of you not owning a windows cd. What else can we do?

---

### Post by Pott on 2009-11-03
Ooh I missed that sorry! Ok I'll look into this. I still find it a bit awkward that the manufacturers don't give you a recovery CD... I have a recovery partition I can boot from with Grub but not even from Vista.

---

### Post by THE NICKSTER on 2009-11-03
there is an option in vista, if you still have access to it, to make your own recovery cd! if you can't do this then you can download the hirens boot cd which will give you access to a command prompt and you should be able to fix the mbr from there. i was about to do that but then i found the recovery cd that I made and it gave me access to a command prompt when i put that disk in.

---

