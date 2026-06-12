---
title: "Grub and PCBSD"
date: 2010-06-25
forum: General Help
---

### Post by rollaster on 2010-06-25
I'm using grub as my primary boot loader for Ubuntu 9.10 and Windows 7. Works perfectly.

I googled and found this because I wanted to use GRUB as the primary boot loader not PC BSD so I didn't select it on install.

[http://faqs.pcbsd.org/index.php?action=artikel&artlang=en&cat=16&id=10](http://faqs.pcbsd.org/index.php?action=artikel&artlang=en&cat=16&id=10)

I'm lost on what to do

[[IMG]http://img156.imageshack.us/img156/8710/screenshot2df.png[/IMG]]("http://img156.imageshack.us/i/screenshot2df.png/")

---

### Post by Don Barzini on 2010-06-25
Download the bootinfo script to a local directory and follow the instructions and post the output of the Results.txt file.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I also load FreeBSD from Ubuntu's Grub2 and it is fairly easy to setup. You just have to edit one file and then run one command.

Post the output of the above script and I'll help you get PC-BSD loaded.

---

### Post by Don Barzini on 2010-06-26
To give you some preliminary info and idea regarding adding PC-BSD to your Ubuntu GRUB2 menu, you need to edit the **/etc/grub.d/40_custom** file. An entry to that file will survive all ensuing *update-grub* commands.

Edit the **/etc/grub.d/40_custom** and add the following entry...

```

menuentry "PC-BSD" {
	insmod ufs2
       	set root=(hd?,?)
       	chainloader +1
	}

```

The entry you need to make is similar. The opening and closing brackets need to be the same as you see them here. The question marks are to be replaced with the actual drive number and partition number on your machine.

After entering the correct values and saving the file... you would run **sudo update-grub**

```
sudo update-grub
```

With the correct drive and partition values, that should be able to boot PC-BSD without a problem.

---

