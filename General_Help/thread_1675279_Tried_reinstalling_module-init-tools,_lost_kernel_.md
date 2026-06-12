---
title: "Tried reinstalling module-init-tools, lost kernel :-/"
date: 2011-01-25
forum: General Help
---

### Post by NeverSage on 2011-01-25
Well, that might have been stupid.  I was having an issue which I narrowed down to module-init-tools by following threads of similar problems.  I attempted to reinstall through synaptic but apparently I'm not supposed to do that.  My computer crashed and now I only get memtest86 in grub on boot.  I'm still fairly new to Linux but my novice opinion is that my kernel seems to be missing.  I tried fixing this through chroot by following this thread: [http://ubuntuforums.org/showthread.php?t=1632856](http://ubuntuforums.org/showthread.php?t=1632856) but couldn't actually get chroot to work, with the error:

```
mount: mount point /mnt/temp/dev does not exist
mount: mount point /mnt/temp/dev/pts does not exist
mount: mount point /mnt/temp/proc does not exist
mount: mount point /mnt/temp/sys does not exist
```Anyway, I decided that I think that other thread doesn't apply to my issue and thought I should start a new one specifically mentioning module-init-tools.  Does this need to be reinstalled?  How should I go about doing this?

I should mention I am (was? hopefully soon again) running lucid.

Thanks for any advice you can give me.

---

### Post by NeverSage on 2011-01-27
I just reinstalled Lucid.  Keeping  /home on a separate partition is good when you mess things up as often as I do :)

---

### Post by cgroza on 2011-01-27
I really hate when this happens to me. My HDD is kind of OLD and sometimes I get errors like that due to corruption.

---

