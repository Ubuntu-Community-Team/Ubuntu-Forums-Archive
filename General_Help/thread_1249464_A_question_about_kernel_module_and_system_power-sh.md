---
title: "A question about kernel module and system power-shutdown"
date: 2009-08-25
forum: General Help
---

### Post by dariyoosh on 2009-08-25
Dear all,


I've just installed a Vanilla kernel (last stable version downloaded from [www.kernel.org](www.kernel.org)) as an exercice in order to better understand how to compile linux kernel. I loaded the .config file of the current kernel in the menuconfig in order to restore all already activated options and I just added the support for NTFS (read and write). I proceeded all instructions as was explained in the HOWTO and apparently it works pretty well. However, there is something a bit strange. Whenever I want to shutdown the system from the command line, I run

```

# shutdown -h now

```

the option -h actually shuts down electrically the computer. Yet, by this new kernel (fortuantely I conserved the old kernel!) I have the following output:

```

# shutdown -h now
.
.  here I see system processes and daemons being shutdown as usual
.
Turning off swap					[ OK ]
Turning off quotas					[ OK ]
Unmounting pipe file systems:				[ OK ]
Halting system...
md: stopping all md devices.
shutdown: hda
System halted.

```

So as you can see at the last line we see "System halted.", but right after that, the computer halts and nothing happens, whereas I excpect it to be shutdown electrically. But this does not happen and I have to push manually the power button.

Is there a particular module that had to be activated in the new kernel that I forgot?


Thanks in advance,

Kind Regards,
Dariyoosh
:)

---

### Post by dariyoosh on 2009-08-25
No idea? :confused:

---

### Post by P4man on 2009-08-25
Dont look at me for me much help (when i started with linux 2 years ago, I set myself as one goal to compile my own kernel, but i have yet to get around even trying :) ).

What I can tell you however, but you you probably already know, is that powering down a machine is an ACPI function. Is ACPI functional in your kernel?

---

### Post by dariyoosh on 2009-08-25
> **P4man said:**
> Dont look at me for me much help (when i started with linux 2 years ago, I set myself as one goal to compile my own kernel, but i have yet to get around even trying :) ).

What I can tell you however, but you you probably already know, is that powering down a machine is an ACPI function. Is ACPI functional in your kernel?


Yessssssssssssssssss !!!!!!! :biggrin: :biggrin: :biggrin:

Man you rock! you solved the problem. I checked the config file and
there were several ACPI options activated (y). Surprisingly I had
ACPI=off in menu.lst, I just changed it to ACPI=on and it worked pretty well.


Thanks a lot for your brilliant solution


Kind Regards,
Dariyoosh

---

### Post by P4man on 2009-08-25
Ha! So now I  know what to look for when my own compiled kernel doesnt turn my machine off. All I need to learn now is the rest of how to compile a kernel LOL.

---

