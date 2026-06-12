---
title: "Kernel Panic on Ubuntu 11.04, XPS 1340"
date: 2011-05-15
forum: General Help
---

### Post by Kareeser on 2011-05-15
Hello all,

I have a Dell XPS 1340, and after resuming from suspend, most days, the laptop will not wake. Some days, Alt-PrScrn-REISUB will reboot the machine, but today, I saw the flashing caps lock, which I believe is indicative of a kernel panic.

In any case, I have no clue what files to dump and submit in a bug report, when this happens again. Can somebody give me a list?

Thanks

---

### Post by michaelzeng7 on 2011-07-03
Yes, I have the same problem, only I'm using a lenovo Thinkpad T61. I don't think it is computer specific, And I also [http://www.ubuntu.com/community/report-problem](http://www.ubuntu.com/community/report-problem) is where you submit a bug to the community I believe.

---

### Post by vitrex on 2011-07-08
Same problem here on a Thinkpad T43p. Is there a launchpad entry so far?

---

### Post by yasith on 2011-08-31
Same happens on a Dell Vostro 3350 running Ubuntu 11.04 64-bit.

---

### Post by thunderbirdje on 2011-09-02
Same problem here on HP Pavilion dv6000 series, no problem when booting into the old kernel 2.6.38-10.

---

### Post by mwolfe on 2011-09-02
I just started having this problem since the update to the 2.6.38-11 kernel.. Also, it only seems to have a problem if I leave my computer suspended for a good deal of time (overnight).. If I suspend it for a short amount of time it resumes just fine.
I'm using a dell studio XPS 435MT

---

### Post by Viman on 2011-09-03
I recently have had more than once experienced something that sounds similar to you guys, like a  kernel panic but as soon as I remove the fully charged battery from my  computer (an old Dell D620)

X is gone and the screen is filled with printed lines presumably  referring to something related to battery state. I cannot input any  commands, cannot shutdown, and hence need to hard reboot.

I don't know how close my problem is related to yours, but I tried searching around for help here before, fruitlessly.

---

### Post by slener1977 on 2011-11-15
> **michaelzeng7 said:**
> Yes, I have the same problem, only I'm using a lenovo Thinkpad T61. I don't think it is computer specific, And I also [http://www.ubuntu.com/community/report-problem](http://www.ubuntu.com/community/report-problem) is where you submit a bug to the community I believe.
I have an IBM T60 with the same issue, but only after I run on battery mode. After much reading I was going to re install with the ACPI option off in the very beginning of the install to see if that helps.

I turned off my power management features in the BIOS, but didn't seem to help either. :-(

---

### Post by slener1977 on 2011-11-17
> **slener1977 said:**
> I have an IBM T60 with the same issue, but only after I run on battery mode. After much reading I was going to re install with the ACPI option off in the very beginning of the install to see if that helps.

I turned off my power management features in the BIOS, but didn't seem to help either. :-(
I actually found this post, and have applied it to my laptop... I will let you know my results...

[http://ubuntuforums.org/showthread.php?t=1839408]("http://ubuntuforums.org/showthread.php?t=1839408")

---

