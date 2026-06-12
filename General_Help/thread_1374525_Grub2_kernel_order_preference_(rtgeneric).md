---
title: "Grub2 kernel order preference (rt/generic)"
date: 2010-01-06
forum: General Help
---

### Post by daltore on 2010-01-06
I got a new laptop a couple of days ago, and although I've been running Karmic for a while on my old laptop, this is the first fresh install I've used.  Tonight, I found out that Grub2 has completely replace the old version, and does not work the same way.

Since I've installed the UbuntuStudio updates and the realtime kernel, I wanted to go through and set the kernels flagged with "-rt" to be higher in preference to those flagged with "-generic" when it decides a default.  I've also go Windows 7 on a different partition, but I want to boot Linux most of the time.

Right now, the kernels labelled "-generic" are taking preference.  How do I tell Grub2 that "-rt" is more important without rewriting /etc/default/grub every time I install a new kernel?

---

### Post by falconindy on 2010-01-06
Grub is a dumb animal and will only do what it's told. There's no way to "weight" entries. A little manual maintenance every few weeks isn't so bad, eh?

---

### Post by daltore on 2010-01-07
Interesting.  Alright, thanks for the help.

---

### Post by funkyhat on 2010-01-18
I've worked out a solution to this problem - see my blog post:

[http://funkyhat.org/2010/01/19/putting-rt-kernels-first-in-grub2/](http://funkyhat.org/2010/01/19/putting-rt-kernels-first-in-grub2/)

The gist of it is this:

```

cd /etc/grub.d
sudo cp 10_linux 09_linux-rt
sudo sed -i 's:\(vmlinu[^ ]*\)-\*:\1-*rt:g' 09_linux-rt #<-edits 09_linux-rt and makes
sudo update-grub                                          #  it only find -rt kernels

```

Hope this helps!

---

### Post by canakas on 2010-08-31
Nice work. Thank you!

Your sed command is not working, but manual editing of 09_linux-rt did the same job. 
update-grub now finds the rt kernels first.

lets hope the reboot goes smoothly =)

EDIT: Looks good =)

---

### Post by Peter7K on 2010-09-23
Just found this, very useful, thanks guys!

Edit: Had a few questions but sorted them out.

---

