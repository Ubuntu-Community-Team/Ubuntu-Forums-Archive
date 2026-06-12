---
title: "Cant boot from disc?"
date: 2009-12-05
forum: General Help
---

### Post by mrawlings on 2009-12-05
im currently running 9.10  and i wanted to dual boot fedora 12 on another partition i have free but im having trouble booting the cd.  After configuring bios to boot from cd numerous times and re-burning the iso file im still having the same problem.

Ill go into bios choose device boot options, select the cd-drive and as soon as i select boot from cd-drive grub instantly pops up and my comp just boots ubunut??

why? thanks!

---

### Post by whoop on 2009-12-05
> **mrawlings said:**
> im currently running 9.10  and i wanted to dual boot fedora 12 on another partition i have free but im having trouble booting the cd.  After configuring bios to boot from cd numerous times and re-burning the iso file im still having the same problem.

Ill go into bios choose device boot options, select the cd-drive and as soon as i select boot from cd-drive grub instantly pops up and my comp just boots ubunut??

why? thanks!

Do you have any other bootable cd's? Might be wise to check if it is a hardware/BIOS problem or a cd problem...
Did you perform a checksum on the ISO file?

---

### Post by mrawlings on 2009-12-05
hmm the last time i booted a live cd was about a week ago and it worked fine.

what is a checksum and what does it do

---

### Post by whoop on 2009-12-05
> **mrawlings said:**
> hmm the last time i booted a live cd was about a week ago and it worked fine.

what is a checksum and what does it do

When you download an iso file you can check if you downloaded it correctly by comparing a checksum computation on the iso file compared to a checksum provided by the manufacturer of the iso...

For fedora this page should be usefull:
[https://fedoraproject.org/en/verify](https://fedoraproject.org/en/verify)

---

### Post by mrawlings on 2009-12-05
ah a hash sum. i downloaded it bittorrent so supposedly it should already be fine correct?

---

### Post by mrawlings on 2009-12-05
well either way the checksum says its fine

---

### Post by whoop on 2009-12-05
> **mrawlings said:**
> ah a hash sum. i downloaded it bittorrent so supposedly it should already be fine correct?

Yep... So I would suggest trying another bootable cd, if that works, there is something wrong with the fedora cd...
Could be that something goes wrong when burning it (try slowest possible speed), try booting the cd from a virtual machine. There is the possibility that the version of fedora is not working correctly with you hardware, which would make it a bug...

---

### Post by mrawlings on 2009-12-05
hmmm is there a way i could install it through the virtual boot too?

btw i just ran a windows xp boot cd and it runs fine.  I guess fedora is givin me a hard time ha

so you really think it would be a bug on fedora's part even when i cant get the cd to boot at all?

should i try fedora 11?
my comp is pretty standard i dont see why it wouldnt work

---

### Post by whoop on 2009-12-05
> **mrawlings said:**
> hmmm is there a way i could install it through the virtual boot too?

btw i just ran a windows xp boot cd and it runs fine.  I guess fedora is givin me a hard time ha

so you really think it would be a bug on fedora's part even when i cant get the cd to boot at all?

should i try fedora 11?
my comp is pretty standard i dont see why it wouldnt work

Well, an incorrect burn to cd could still be the case...

---

### Post by lisati on 2009-12-05
The ISO file needs to be burned as a disk image.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by mrawlings on 2009-12-05
i definatly know how to burn an ISO but thanks. ill try and reburn it again

---

### Post by whoop on 2009-12-05
> **lisati said:**
> The ISO file needs to be burned as a disk image.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

That could indeed be the possible cause of the error...

---

### Post by kiwimonster on 2009-12-05
hmm

---

### Post by lisati on 2009-12-05
> **mrawlings said:**
> i definatly know how to burn an ISO but thanks. ill try and reburn it again

Assuming the ISO file's checksum was fine and it was burned as a disk image (not as one big file, there is an important difference) the next most likely cause I can think of is a bad burn.

When you browse the CD after you've burend it, do you see lots of files or just one big one?

---

### Post by mrawlings on 2009-12-05
the disc was burned as an iso it contains many folders

---

### Post by mrawlings on 2009-12-05
im honestly gonna say that something is wrong with fedoras live boot maybe i should take it to their forum ha


ive burned at least 4 seperate cds already all but the first were burned at the slowest speed possible
bios booted windows xp install cd so bios is working fine.
i downloaded the iso through bittorent so checksum shouldnt even be an issue

i dunno what to do ha

its like my computer is completely ignoring this one disc

---

### Post by PRC09 on 2009-12-05
Maybe try it in another computer if possible.....

---

