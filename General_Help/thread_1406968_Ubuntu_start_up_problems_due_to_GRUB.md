---
title: "Ubuntu start up problems due to GRUB"
date: 2010-02-14
forum: General Help
---

### Post by theronstar on 2010-02-14
Hello. I just booted into Linux and the Update Manager prompted me to restart. After the restart the GRUB interface I expect to see is no longer there and now it is just a command line that says press tab for more options.
  
I have not got a clue with shell language as I have had no time to learn it as of yet. Do I need to uninstall and reinstall Linux or is there a command that can be typed that boots up the operating system. Even better is there something I can do that can return me to seeing the interface like I was used to. I blame this on the update manager and don't think I will do one again now.

Someone said 'startx?' to me but I could not make head or tail of what they meant.

hi
let us see how your command line looks like. is it
grub resue>
if yes then run following commands step by step.
ls
set prefix=(hdX,Y)/boot/grub   ( where X and Y are your boot partitons )
set root=(hdX,Y)
insmod /boot/grub/linux.mod
linux /vmlinuz root=/dev/sdXY ro
initrd /initrd.img

boot

I followed those instructions but when I typed ls I got a error C/H/S message appear.
The other commands worked up until the insmod. At this point it gave another error message and the commands beyond it would not work for me. Should I just delete Linux? Thanks for reading my question

---

### Post by dinamic1 on 2010-02-14
if you've used wubi to install ubuntu then [https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90)

---

### Post by mechro on 2010-02-14
What dinamic1 said.

But also... if you hold the Shift key when booting, does The Grub menu appear?

---

### Post by lidex on 2010-02-14
OK, download the Boot Info Script [here]("http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.54/boot_info_script054.sh/download")
and follow [these instructions]("http://bootinfoscript.sourceforge.net/"). You'll need to boot from your LiveCD. Post results here.

---

### Post by theronstar on 2010-02-15
Hello everyone. Thanks so much for the help. It turns out following dinamic's instruction to download that patch fixed it, but wow,could pressing the shift key have saved me all that misery.

If you know a way to boost the listing this query gets in the forum for newb's having my problem please do so. I found it impossibly hard to find any info on the Internet to resolve my problem. 

Thanks again.

---

