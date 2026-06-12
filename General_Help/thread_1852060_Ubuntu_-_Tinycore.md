---
title: "Ubuntu - Tinycore"
date: 2011-09-29
forum: General Help
---

### Post by hushkin on 2011-09-29
Hi i'm currently running a triple boot with Ubuntu, Win 7 & Tinycore, at least that's the plan. I installed Tinycore and instead of downloading a GRUB for Tinycore, I wanted to add Tinycore to my existing Ubuntu GRUB.

But for some reason I cannot get it to boot. it says:

"Error file not found."
"Error: you need to load the kernel first."

This is what i added in grub.cfg:

> menuentry "TinyCore" {

set root=(hd0,1)
	
linux /boot/bzImage tce=sda7 
home=sda7 
opt=sda7
initrd /boot/tinycore.gz

}


I read somewhere they you have to change 41_custom too? But i don't know what to change.

I can't really find any info on the web about this.

Any help would be greatly appreciated!

---

### Post by ajgreeny on 2011-09-29
Why did you edit grub.cfg manually; it is a read only file for a good reason and it will revert next time you run "sudo update-grub" or there is a kernel update.

If you had run "sudo update-grub" it should have found tiny-core and added it automatically to the grub menu.  If you have not tried that yet, I recommend that you do so now and see if it all works next time you boot.

---

### Post by hushkin on 2011-09-30
I already tried to let grub update itself but it doesn't add TinyCore to my grub...

Any ideas?

---

