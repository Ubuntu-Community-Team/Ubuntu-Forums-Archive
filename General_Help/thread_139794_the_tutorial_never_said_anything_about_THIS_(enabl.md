---
title: "the tutorial never said anything about THIS (enabling preemption)"
date: 2006-03-04
forum: General Help
---

### Post by jmxhgyZN8wK7 on 2006-03-04
when i found [ubuntustudio.com]("http://ubuntustudio.com/wiki/index.php/Welcome%2C_Musicians%21"), i thought all of my problems were over.

i started out with the ["enabling preemption"]("http://ubuntustudio.com/wiki/index.php/Breezy:Enabling_Preemption") tutorial... got through the

```
sudo -i
apt-get install linux-source-2.6.12 libncurses-dev kernel-package build-essential gcc-3.4
```

and the

```
cd /usr/src/
tar jxf linux-source-2.6.12.tar.bz2
mv linux linux.old 2> /dev/null
ln -s linux-source-2.6.12 linux
cp /boot/config-2.6.12-10-386 linux/.config
echo CONFIG_PREEMPT=y >> linux/.config
echo CONFIG_PREEMPT_BKL=y >> linux/.config
echo \# CONFIG_DEBUG_PREEMPT is not set >> linux/.config
```

...skipped the stuff about realtime-lsm and nvidia packages (i'm not using a nvidia video card, and the main page has alternatives to realtime-lsm), and went straight to the

```
cd /usr/src/linux/
make-kpkg clean
make-kpkg modules_clean
make-kpkg --append_to_version -50preempt --revision 1 --initrd kernel_image kernel_headers modules_image
```

when i entered the last line, it printed out a whole bunch of scary-looking gibberish, and then gave me

```
#
# using defaults found in .config
#
*
* Linux Kernel Configuration
*
*
* Code maturity level options
*
Prompt for development and/or incomplete code/drivers (EXPERIMENTAL) [N/y/?] (NEW)
```

now i was lost.  regardless, i entered N, and got

```
#
# using defaults found in .config
#
*
* Linux Kernel Configuration
*
*
* Code maturity level options
*
Prompt for development and/or incomplete code/drivers (EXPERIMENTAL) [N/y/?] (NEW) N
*
* General setup
*
Local version - append to kernel release (LOCALVERSION) [] (NEW)
```

not knowing what to do, i pressed enter, and got

```
Support for paging of anonymous memory (swap) (SWAP) [Y/n/?]
```

now i was even more lost.  i pressed ctrl-c and then the "up" arrow to repeat the

```
make-kpkg --append_to_version -50preempt --revision 1 --initrd kernel_image kernel_headers modules_image
```

and entered y.  this time i got

```
#
# using defaults found in .config
#
*
* Linux Kernel Configuration
*
*
* Code maturity level options
*
Prompt for development and/or incomplete code/drivers (EXPERIMENTAL) [N/y/?] (NEW) y
  Select only drivers expected to compile cleanly (CLEAN_COMPILE) [Y/n/?] (NEW)
```

this was a little easier to understand than the thing about "paging of anonymous memory" (after all, "compile cleanly" sounded like a good thing), so i entered Y, and got sent straight back to

```
Local version - append to kernel release (LOCALVERSION) [] (NEW)
```

can anyone help me?

---

### Post by hw-tph on 2006-03-05
You can configure the source by running **make menuconfig** (this requires libncurses5-dev to be installed). This is probably a lot easier than the über old school **make config** (which is what you are up against). Actually, all the settings should be OK so just starting menuconfig and the exiting and saving should do it.


Håkan

---

