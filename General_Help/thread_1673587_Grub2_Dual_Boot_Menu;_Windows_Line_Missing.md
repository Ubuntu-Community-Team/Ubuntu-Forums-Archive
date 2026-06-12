---
title: "Grub2 Dual Boot Menu; Windows Line Missing"
date: 2011-01-22
forum: General Help
---

### Post by Snappa on 2011-01-22
What can prevent a script file in the directory grub.d running and coming up in my menu ?  My windows file (15_windows7hs) has the same file permissions as all the other files in the directory, ie., -rwxr-xr-x , but does not show up in the boot menu.  Ubuntu 10.10
Thanks

---

### Post by Snappa on 2011-01-23
Anyone, please ?

Here is the offending file:-
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7 Home Starter (on /dev/sda1)"{
insmod ntsf
set root=(hd0,1)
chainloader +1
}
```

---

### Post by decrepit on 2011-01-23
Just a wild guess here, but shouldn't "ntsf" be ntfs?

---

### Post by dandnsmith on 2011-01-23
I agree with the ntfs comment.
My XP entry looks like:
```
menuentry "Microsoft Windows XP Professional (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 0cd8cb21d8cb07c2
	drivemap -s (hd0) ${root}
	chainloader +1
}
```

I'm not sure what the *search* line is there for (but it has the UUID at the end)
The *drivemap* line may be relevant

HTH

---

### Post by Snappa on 2011-01-23
Thanks for your help guys.  I've changed ntsf to ntfs :oops:, but the windows line still doesn't come up in the menu.  What I'd really like to know is what is it which will prevent a line from coming up in the menu, and is there any way to debug the Grub2 script files in /etc/grub.d, line by line.

I'm going to have a look at the Grub2 commands, especially search and drivemap, starting here

[http://grub.enbug.org/CommandList](http://grub.enbug.org/CommandList) 

Maybe I'll also find out how to debug here.

If anyone has further thoughts on this, I'd be most grateful.

Thanks again.

---

### Post by dandnsmith on 2011-01-24
I've found [this site](http://members.iinet.net/~herman546/p20.html) to be helpful in GRUB2 matters.

---

### Post by oldfred on 2011-01-24
I have created 40_customs and not had problems, but some have said extra spaces at the end of lines can cause problems.

---

