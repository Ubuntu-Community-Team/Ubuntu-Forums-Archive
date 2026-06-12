---
title: "edit grub of 10.10 from windows partition?"
date: 2011-04-25
forum: General Help
---

### Post by Pen16 on 2011-04-25
I have a dual boot system. a 200gb hd with ubuntu 10.10 and windows pro on 100gb hd. the problem im having is the 'black screen' error.

When i boot ubuntu, it boot fine but it shuts off my screen cause its not supporting my video hardware which is a geforce 6100 or something.

I know the fix is to change the grub to support older video architecture. Something like changing the line 'GRUB_CMDLINE_LINUX_DEFAULT="QUEIT SPLASH NORNODESET"'

But how do i change the grub when the screens off? i can't, right. Is there a way i can change the boot parameters of ubuntu from my windows boot or maybe from the ubuntu virtual desktop?

---

### Post by lithopsian on 2011-04-25
Got a Live CD?

I assume your /boot is on an ext partition of some sort.  Windows can't read or write these on its own.  There is a driver called ext2fsd which is supposed to allow write access to ext partitions, including ext4, but I haven't used it.

---

### Post by wilee-nilee on 2011-04-25
> **Pen16 said:**
> I have a dual boot system. a 200gb hd with ubuntu 10.10 and windows pro on 100gb hd. the problem im having is the 'black screen' error.

When i boot ubuntu, it boot fine but it shuts off my screen cause its not supporting my video hardware which is a geforce 6100 or something.

I know the fix is to change the grub to support older video architecture. Something like changing the line 'GRUB_CMDLINE_LINUX_DEFAULT="QUEIT SPLASH NORNODESET"'

But how do i change the grub when the screens off? i can't, right. Is there a way i can change the boot parameters of ubuntu from my windows boot or maybe from the ubuntu virtual desktop?

So you get a black screen before the grub menu?

If you get the grub menu hit e then put the; I think you want (nomodeset) at the kernel line after the quiet splash. If you remove the quiet splash you will see the text as it boots and any errors if you pay attention.

---

### Post by Pen16 on 2011-04-25
> **wilee-nilee said:**
> So you get a black screen before the grub menu?

If you get the grub menu hit e then put the; I think you want (nomodeset) at the kernel line after the quiet splash. If you remove the quiet splash you will see the text as it boots and any errors if you pay attention.

Nope its completely black, actually once i choose ubuntu it boots the operating system but shuts my monitor off.

but your right if i could get to the grub.

---

### Post by wilee-nilee on 2011-04-25
> **Pen16 said:**
> Nope its completely black, actually once i choose ubuntu it boots the operating system but shuts my monitor off.

but your right if i could get to the grub.

You're just hitting the enter key at the black screen; as Ubuntu was the default boot correct?

If you hit the down key once for the recovery boot then enter does it do the same.

---

### Post by Pen16 on 2011-04-25
> **wilee-nilee said:**
> You're just hitting the enter key at the black screen; as Ubuntu was the default boot correct?

If you hit the down key once for the recovery boot then enter does it do the same.

Yes it does.

---

### Post by Pen16 on 2011-04-26
Ok, well i found a bios driver and thought maybe, maybe, it would fix it. Now when i go to boot ubuntu the cpu goes crazy(boot os) but the monitors turns off and gives me no signal and then three secends later it gets a flicker of a signal and shuts back off.

---

### Post by Pen16 on 2011-04-26
ok, so after like two hours of searching i found the answer and a lot of other peopl with this problem.

[http://ubuntuforums.org/showthread.php?t=1592763](http://ubuntuforums.org/showthread.php?t=1592763)

sorry about that, you can close the thread if you want.

---

