---
title: "GRUB entry that runs a BASH script"
date: 2011-11-03
forum: General Help
---

### Post by Binary-Synapse on 2011-11-03
Hello.
 
How can I make a GRUB entry that runs a specific bash script?
 
I know how to create a customized GRUB entry, but I don't know how to run a command/bash script using that same entry.
 
The bash script would be a simple one, that uses basic commands like dd, gzip, etc...
Basically the entry will run a script that decompresses a file and then applies that data to an HDD (just like an HDD restore capability).
 
Can someone show me an example (or more), or provide me some info?
 
Note: I'm using Ubuntu 11.10
 
Thank you.

---

### Post by ajgreeny on 2011-11-03
Does grub use bash as its shell?

I thought it had its own very simple command line shell, in which case you will need to make sure that grub is capable of running the commands in your script.

There is some info here;  [https://help.ubuntu.com/community/Grub2#GRUB_2_Prompt_Usage](https://help.ubuntu.com/community/Grub2#GRUB_2_Prompt_Usage)  but you may find more with a search.

---

### Post by Binary-Synapse on 2011-11-03
> **ajgreeny said:**
> Does grub use bash as its shell?
 
I thought it had its own very simple command line shell, in which case you will need to make sure that grub is capable of running the commands in your script.
 
There is some info here; [https://help.ubuntu.com/community/Grub2#GRUB_2_Prompt_Usage](https://help.ubuntu.com/community/Grub2#GRUB_2_Prompt_Usage) but you may find more with a search.
 
Hello ajgreeny.
 
Yes, the commands are very simple (dd, gzip, rm, cat), but now that you mention it, I'm not sure that the GRUB shell can actually support them. I will have to test that.
 
I think that (while in GRUB) I can press "c" and then "TAB" to see the full list of supported commands, right?
 
Thank you

---

### Post by ajgreeny on 2011-11-03
> **Binary-Synapse said:**
> Hello ajgreeny.
 
Yes, the commands are very simple (dd, gzip, rm, cat), but now that you mention it, I'm not sure that the GRUB shell can actually support them. I will have to test that.
 
I think that (while in GRUB) I can press "c" and then "TAB" to see the full list of supported commands, right?
 
Thank you
Yes, I think so, but I've never tried it, or needed it, so I'm not sure.

---

### Post by WorMzy on 2011-11-03
You could try making a grub entry that boots into a kernel with an init argument.

Not sure how you'd do this on Grub2, but on Grub legacy, you'd just need to add something like

```
title        Runscript
root         (hd2,10)
kernel       /boot/vmlinuz31 root=/dev/sdd11 ro quiet init=/bin/myscript
boot
```

to menu.lst.

Whether or not it'd work, I couldn't say.

---

### Post by Binary-Synapse on 2011-11-03
> **WorMzy said:**
> You could try making a grub entry that boots into a kernel with an init argument.
 
Not sure how you'd do this on Grub2, but on Grub legacy, you'd just need to add something like
 
```
title        Runscript
root         (hd2,10)
kernel       /boot/vmlinuz31 root=/dev/sdd11 ro quiet init=/bin/myscript
boot
```
 
to menu.lst.
 
Whether or not it'd work, I couldn't say.
 
 
Hello WorMzy.
 
Hum....
 
I´m surely going to test your suggestion.
I´ll adapt it to GRUB2 and see how it works.
 
Then I´ll get back to you...
 
Thanks

---

### Post by Binary-Synapse on 2011-11-04
> **WorMzy said:**
> You could try making a grub entry that boots into a kernel with an init argument.
 
Not sure how you'd do this on Grub2, but on Grub legacy, you'd just need to add something like
 
```
title        Runscript
root         (hd2,10)
kernel       /boot/vmlinuz31 root=/dev/sdd11 ro quiet init=/bin/myscript
boot
```
 
to menu.lst.
 
Whether or not it'd work, I couldn't say.
 
 
Hello WorMzy!
 
Some feedback on this matter...
 
I have just adapted your suggestion to GRUB2 and **it worked for me perfectly!**
 
Still have to make some adjustments in the script, but that will be "another battle".
 
Thank you all for your input.

---

### Post by WorMzy on 2011-11-04
Glad to hear it. :)

Good luck with the script.

---

