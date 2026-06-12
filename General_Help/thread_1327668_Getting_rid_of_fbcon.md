---
title: "Getting rid of fbcon"
date: 2009-11-15
forum: General Help
---

### Post by shentino on 2009-11-15
I like having a nice snappy 80x25 text console, but every step I try to take to disable the framebuffer console is met with failure.  No matter what I do it gets force loaded immediately on boot.

Is fbcon REQUIRED?

Version: Karmic Koala
Modifications:
   blacklisted fbcon in /etc/modprobe.d/
Up to date as of: Nov 15
KMS: enabled
Graphics card: Intel 845GC

I'd very much like to disable the framebuffer console, preferably without breaking anything.

---

### Post by shentino on 2009-11-15
Confirmed straight from #intel-gfx over at irc.ubuntu.com

text mode implies vga, implies conflict with KMS

If you want to use KMS, you have no choice but to kiss text mode goodbye.

So, not a bug and not a foul up on my end.  But a deliberate policy applied by the developers.

Mind you, I'd like to change this policy.

---

### Post by scorp123 on 2009-11-22
I had the opposite problem ... I like my framebuffers as large as possible. 80x25 is just killing me.

What I did:

1.) Enable the framebuffer as explained in this posting:
[http://ubuntuforums.org/showpost.php?p=3573289&postcount=51](http://ubuntuforums.org/showpost.php?p=3573289&postcount=51)

==> obviously you'd have to do the inverse?

2.) Modify my GRUB config:
My **/etc/default/grub** now has a line that says:
```
GRUB_CMDLINE_LINUX_DEFAULT="verbose splash **vga=0x031a**"
```

==> I'd imagine that **"vga=normal"** would give you a normal 80x25 console?

(BTW ... **GRUB_GFXMODE=1280x1024** does indeed modify the look of the initial GRUB menu but it does _nothing_ for the Linux console later on ... hence why I resorted adding the "vga=" parameter again even though I get an error claiming that this method is deprecated?? ... )

---

### Post by shentino on 2011-02-06
Looks like KMS itself is here to stay.

Intel drivers now require KMS, and KMS now requires fbcon.  The powers that be high on the video driver totem pole have made their decisions and there's not a darn thing I can do about it, so I'm just going to accept it and quit fighting.  Resistance is futile.

Vga, it was nice knowing you and your snappy text cell processing, but I must bid thee farewell forevermore.

):P

This thread can be locked, as it has no further use

---

