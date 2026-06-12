---
title: "Grub: edited grub.cfg, broke it, and can't recover"
date: 2010-01-21
forum: General Help
---

### Post by SiliconS on 2010-01-21
Karmic / 9.10 (Grub2)
 Dual boot on HP/Compaq laptop with WinXP
 Installed in November (?) using LiveCD
 I'm a noob
 
Every kernel update since November has updated my grub.cfg file which leads me to get a --no-floppy error with every boot up. This gets boring really quickly so I su nano /boot/grub/grub.cfg to remove this line from the grub menu entries each time. Successfully done this about five times so far.
 
 This time I was too confident and like a fool I messed up grub.cfg.
 
Now when I boot I see no grub menu but instead just a grub console. I don't know what my grub.cfg file contains so I've read lots of pages and I think I should be typing the following into the grub console:
 
 ```

 sh:grub> linux /boot/vmlinuz-2.6.31-17-generic
     [Linux-bzImage, setup=0x3400, size=0x3b2780]
 sh:grub> initrd /boot/initrd.img-2.6.31-17-generic
     [Initrd, addr=0x2f8d4000, size=0x7476dd]
 sh:grub> boot
```Boot seems to kick-start the machine and I get lots of the white status feedback lines whizzing past, before the last one:
 ```
Begin: Waiting for root file system... ...
 Done.
 Gave up waiting for root device. Common problems:
  - Boot args (cat /proc/cmdline)
    - Check rootdelay= (did the system wait long enough?)
    - Check root- (did the system wait for the right device?)
  - Missing modules (cat /proc/modules; ls /dev)
 ALERT! does not exist. Dropping to a shell!
 
 BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
 Enter 'help' for a list of built-in commands.
 
 (initramfs)
```My reading tells me I probably need to set a root= parameter before the linux line in grub but how do I find out what to set? It's either /dev/hda# or root=UUID=xxxxxxxxxxx but I don't know. I'm sure my grub.cfg file uses root=UUID=xxxxxxxxxxx but I don't know how to get to a shell where I can read the laptop's filesystem to find out what the UUID should be.
 
 I've tried inserting my LiveCD again to boot from that so I can fix grub (using [this guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")) but the LiveCD hangs after the 'What do you want to do' menu. Is this a coincidence or is the broken grub causing this too?
 
I'm sure this is an easy one for someone but I haven't found anybody else posting in this situation so I'm not sure what to do. :( Would appreciate any advice.

---

### Post by sisco311 on 2010-01-21
[uhelp]community/Grub2#Command%20Line%20&%20Rescue%20Mode[/uhelp]

You can use ls to find the root partition:
```
ls	
Display the drives/partitions known to GRUB 2.

ls (hdX,Y)/	
Display the contents of the / folder of the designated drive/partition.

ls (hdX,Y)/boot	
Display the contents of the /boot folder. Example: ls (hd0,5)/boot

ls (hdX,Y)/boot/grub	
Display the contents of the /boot/grub folder. Example: ls (hd0,5)/boot/grub
```


Assuming that /dev/sda2 is your root (/) partition:
```
insmod ext2
set root=(hd0,2)
linux	/boot/vmlinuz-**<hit tab to auto-complete>**  root=/dev/sda2  ro quiet splash
initrd	/boot/initrd.img**<hit tab to auto-complete>**
boot
```

---

### Post by SiliconS on 2010-01-21
Thank you for the quick reply.
```
insmod ext2
set root=(hd0,2)
```No errors or acknowledgements after these two lines.
I begin typing
```
linux /boot/vmlinuz-
```but the autocomplete no longer works. Never mind - I type out what I quoted above. When I hit <enter> I get 
```
error: no such partition
```Do you know: is it (hd0,2) that's wrong or root=/dev/sda2 that would cause this error?

Edit: Sorry - I'm just reading the page to which you linked.

Typing ls into the grub prompt gives me:
```
sh:grub> ls
(hd0) (hd0,5) (hd0,1)
error: out of disk
```
Does that help?

---

### Post by SiliconS on 2010-01-21
Hehe our edits are crossing each other. I'll try your extra suggestions and report back. Thank you again for your quick response. My children will be able to watch DVDs again soon, which will make everybody happy. :D

---

### Post by SiliconS on 2010-01-21
OK. Things are getting better. I think.
```
sh:grub> ls (hd0)
Device hd0: Partition table
sh:grub> ls (hd0,5)
       Partition hd0,5: Filesystem type ext2, Last modification time 2009-12-26, UUID 90af46f4-xxxxxxxxxxxxxxxxxxxx
sh:grub> ls (hd0,1)
       Partition hd0,1: Filesystem type ntfs, UUID 72f44xxxxxxxxxxx

```So, looks like hd0,5 is the one. :D
I try
```
sh:grub>set root=(hd0,5)
```No problems. But now, what do I put at the end of the
```
linux /boot/vmlinux-2.6.31-17-generic
```command? How do I know the correct sda#? Or should I use the UUID for hd0,5?

I think I'm so close I can almost taste the prize. Thank you.

---

### Post by sisco311 on 2010-01-21
> **SiliconS said:**
> 
(hd0) (hd0,5) (hd0,1)
error: out of disk[/code]
Does that help?

Yes, the (hd0,1) is probably the Windows partition and (hd0,5) is the Ubuntu partition.
Try:
```

...
set **root=(hd0,5)**
linux ... **root=/dev/sda5** ro quiet splash
initrd ...

```

EDIT: You don't have to use the UUID, you can use the /dev/sda5 device name.

---

### Post by SiliconS on 2010-01-21
> **sisco311 said:**
> Try:
```

...
set **root=(hd0,5)**
linux ... **root=/dev/sda5** ro quiet splash
initrd ...

```EDIT: You don't have to use the UUID, you can use the /dev/sda5 device name.
[SIZE=4]YES![/SIZE]
Thank you very much for your quick help. I'm back at Gnome again. I've run update-grub and I'll remove the search --no-floppy lines a bit more carefully this time. #-o

I really appreciate your helpful responses. May the rest of your day be happy and easy.

---

### Post by sisco311 on 2010-01-21
You are welcome!

The main menu file, /boot/grub/grub.cfg, is not meant to be edited, even by 'root'.

This guides will help you to customize your Grub2 menu:
[uhelp]community/Grub2[/uhelp]
[thread=1195275]The Grub 2 Guide[/thread]
[thread=1302743]Grub 2 - 5 Common Tasks[/thread]
[thread=1287602]Grub 2 Title Tweaks[/thread]

---

### Post by SiliconS on 2010-01-21
> **sisco311 said:**
> The main menu file, /boot/grub/grub.cfg, is not meant to be edited, even by 'root'.
Yes, sorry - I've seen the warnings. :oops:

But I don't know how to stop the *search --no-floppy* lines being included in the menu entries every time grub.cfg is rebuilt by the system. Removing those lines manually is a hack I've read about when trying to find a solution to this common grub2 problem and it has worked for me in the past.

(Do you know of any way to stop update-grub adding the *search --no-floppy* lines into grub.cfg again?)

---

### Post by Leppie on 2010-01-21
just a FYI, you didn't actually need to specify the kernel versions.
images (vmlinuz.img and initrd.img) for the latest kernel are created in the root of your filesystem.
the linux line can be shortened to this:
```
linux /vmlinuz root=/dev/sda5 ro
```and the initrd line to this:
```
initrd /initrd.img
```

the kernel versions are only required when using a separate boot partition ;)

why do you want to remove the search command from grub.cfg?

---

### Post by SiliconS on 2010-01-21
Thanks Leppie.

The search command stops grub booting smoothly. At every boot I have to manually edit the menu item script to remove that line and then Ctrl-X to run the amended list of commands. Removing the search lines from grub.cfg stops this inconvenience. (And since my laptop doesn't seem to be 100% compatible with a vanilla Karmic install, I can't put it to sleep or into hibernation. Every time I've finished with it, I have to shut down completely.)

---

### Post by sisco311 on 2010-01-21
> **SiliconS said:**
> Thanks Leppie.

The search command stops grub booting smoothly. At every boot I have to manually edit the menu item script to remove that line and then Ctrl-X to run the amended list of commands. Removing the search lines from grub.cfg stops this inconvenience. (And since my laptop doesn't seem to be 100% compatible with a vanilla Karmic install, I can't put it to sleep or into hibernation. Every time I've finished with it, I have to shut down completely.)

What's the output of:
```
cat /usr/lib/grub/update-grub_lib

```
and
```
cat /usr/lib/grub/grub-mkconfig_lib

```?

---

### Post by SiliconS on 2010-01-22
```
me@Laptop:~$ cat /usr/lib/grub/update-grub_lib 
prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib

. ${libdir}/grub/grub-mkconfig_lib

grub_warn "update-grub_lib is deprecated, use grub-mkconfig_lib instead"
``````

me@Laptop:~$ cat /usr/lib/grub/grub-mkconfig_lib 
# Helper library for grub-mkconfig

transform="s,x,x,"

prefix=/usr
exec_prefix=${prefix}
datarootdir=${prefix}/share
datadir=${datarootdir}
sbindir=${exec_prefix}/sbin
pkgdatadir=${datadir}/`echo grub | sed "${transform}"`

grub_probe=${sbindir}/`echo grub-probe | sed ${transform}`

grub_warn ()
{
  echo "Warning: $@" >&2
}

make_system_path_relative_to_its_root ()
{
  path=$1
  # abort if file doesn't exist
  if test -e $path ; then : ;else
    return 1
  fi

  # canonicalize
  if path=`readlink -f $path` ; then : ; else
    return 1
  fi

  # if not a directory, climb up to the directory containing it
  if test -d $path ; then
    dir=$path
  else
    dir=`echo $path | sed -e "s,/[^/]*$,,g"`
  fi

  num=`stat -c %d $dir`

  # this loop sets $dir to the root directory of the filesystem we're inspecting
  while : ; do
    parent=`readlink -f $dir/..`
    if [ "x`stat -c %d $parent`" = "x$num" ] ; then : ; else
      # $parent is another filesystem; we found it.
      break
    fi
    if [ "x$dir" = "x/" ] ; then
      # / is our root.
      break
    fi
    dir=$parent
  done

  # This function never prints trailing slashes (so that its output can be
  # appended a slash unconditionally).  Each slash in $dir is considered a
  # preceding slash, and therefore the root directory is an empty string.
  if [ "$dir" = "/" ] ; then
    dir=""
  fi

  # XXX: This fails if $dir contains ','.
  path=`echo "$path" | sed -e "s,^$dir,,g"` || return 1

  case "`uname 2>/dev/null`" in
    CYGWIN*)
      # Cygwin: Check if regular or emulated mount.
      if [ -z "$dir" ] || [ "`stat -c %D "$dir/.."`" != 620000 ] ; then
        # Reached some mount point not below /cygdrive.
        # GRUB does not know Cygwin's emulated mounts,
        # convert to Win32 path and remove drive letter.
        path=`cygpath -m "$path" | sed -n 's,^[A-Za-z]:,,p'`
        test ! -z "$path" || return 1
      fi ;;
  esac

  echo "$path"
}

is_path_readable_by_grub ()
{
  path=$1

  # abort if path doesn't exist
  if test -e $path ; then : ;else
    return 1
  fi

  # abort if file is in a filesystem we can't read
  if ${grub_probe} -t fs $path > /dev/null 2>&1 ; then : ; else
    return 1
  fi

  return 0
}

convert_system_path_to_grub_path ()
{
  path=$1

  grub_warn "convert_system_path_to_grub_path() is deprecated.  Use prepare_grub_to_access_device() instead."

  # abort if GRUB can't access the path
  if is_path_readable_by_grub ${path} ; then : ; else
    return 1
  fi

  if drive=`${grub_probe} -t drive $path` ; then : ; else
    return 1
  fi

  if relative_path=`make_system_path_relative_to_its_root $path` ; then : ; else
    return 1
  fi

  echo ${drive}${relative_path}
}

save_default_entry ()
{
  if [ "x${GRUB_DEFAULT}" = "xsaved" ] ; then
    echo 'saved_entry=${chosen}'
    echo 'save_env saved_entry'
  fi
}

prepare_grub_to_access_device ()
{
  device=$1

  loop_file=
  case ${device} in
    /dev/loop/*|/dev/loop[0-9])
      loop_file=`losetup ${device} | sed -e "s/^[^(]*(\([^)]\+\)).*/\1/"`
      case $loop_file in
        /dev/*) ;;
        *)
          loop_device=${device}
          device=`${grub_probe} --target=device "${loop_file}"`
        ;;
      esac
    ;;
  esac

  # Abstraction modules aren't auto-loaded.
  abstraction="`${grub_probe} --device ${device} --target=abstraction`"
  for module in ${abstraction} ; do 
    echo "insmod ${module}"
  done

  fs="`${grub_probe} --device ${device} --target=fs`"
  for module in ${fs} ; do
    echo "insmod ${module}"
  done

  # If there's a filesystem UUID that GRUB is capable of identifying, use it;
  # otherwise set root as per value in device.map.
  echo "set root=`${grub_probe} --device ${device} --target=drive`"
  if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
    echo "search --no-floppy --fs-uuid --set ${fs_uuid}"
  fi

  if [ "x${loop_file}" != x ]; then
    loop_mountpoint="$(awk '"'${loop_file}'" ~ "^"$2 && $2 != "/" { print $2 }' /proc/mounts | tail -n1)"
    if [ "x${loop_mountpoint}" != x ]; then
      echo "loopback loop0 ${loop_file#$loop_mountpoint}"
      echo "set root=(loop0)"
    fi
  fi
}

grub_file_is_not_garbage ()
{
  if test -f "$1" ; then
    case "$1" in
      *.dpkg-*) return 1 ;; # debian dpkg
    esac
  else
    return 1
  fi
  return 0
}

version_test_numeric ()
{
  local a=$1
  local cmp=$2
  local b=$3
  if [ "$a" = "$b" ] ; then
    case $cmp in
      ge|eq|le) return 0 ;;
      gt|lt) return 1 ;;
    esac
  fi
  if [ "$cmp" = "lt" ] ; then
    c=$a
    a=$b
    b=$c
  fi
  if (echo $a ; echo $b) | sort -n | head -n 1 | grep -qx $b ; then
    return 0
  else
    return 1
  fi
}

version_test_gt ()
{
  local a=`echo $1 | sed -e "s/[^-]*-//;s/[._-]\(pre\|rc\|test\|git\|old\)/~\1/g"`
  local b=`echo $2 | sed -e "s/[^-]*-//;s/[._-]\(pre\|rc\|test\|git\|old\)/~\1/g"`
  local cmp=gt
  if [ "x$b" = "x" ] ; then
    return 0
  fi
  case $a:$b in
    *.old:*.old) ;;
    *.old:*) a=`echo -n $a | sed -e s/\.old$//` ; cmp=gt ;;
    *:*.old) b=`echo -n $b | sed -e s/\.old$//` ; cmp=ge ;;
  esac
  dpkg --compare-versions "$a" $cmp "$b"
  return $?
}

version_find_latest ()
{
  local a=""
  for i in $@ ; do
    if version_test_gt "$i" "$a" ; then
      a="$i"
    fi
  done
  echo "$a"
}
me@Laptop:~$ 

```
[-o<

---

### Post by lordskid on 2010-01-22
> **SiliconS said:**
> Yes, sorry - I've seen the warnings. :oops:

But I don't know how to stop the *search --no-floppy* lines being included in the menu entries every time grub.cfg is rebuilt by the system. Removing those lines manually is a hack I've read about when trying to find a solution to this common grub2 problem and it has worked for me in the past.

(Do you know of any way to stop update-grub adding the *search --no-floppy* lines into grub.cfg again?)

well you can try to edit /etc/default/grub then on line 9 or so

or search for

GRUB_CMDLINE_LINUX_DEFAULT="ro quiet splash search --no-floppy"

then remove the search --no-floppy from here and do a sudo update-grub or 
sudo grub-mkconfig -o /boot/grub/grub.cfg

---

### Post by sisco311 on 2010-01-22
Backup then edit the /usr/lib/grub/grub-mkconfig_lib file & comment out the lines which add the search --no-floppy line to grub.cfg:
```
...
  # If there's a filesystem UUID that GRUB is capable of identifying, use it;
  # otherwise set root as per value in device.map.
  echo "set root=`${grub_probe} --device ${device} --target=drive`"
  **#**if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
  **#**  echo "search --no-floppy --fs-uuid --set ${fs_uuid}"
  **#**fi
...

```

then run:
```
sudo update-grub
```

---

### Post by Leppie on 2010-01-22
> **lordskid said:**
> well you can try to edit /etc/default/grub then on line 9 or so

or search for

GRUB_CMDLINE_LINUX_DEFAULT="ro quiet splash search --no-floppy"

then remove the search --no-floppy from here and do a sudo update-grub or 
sudo grub-mkconfig -o /boot/grub/grub.cfg
AFAIK "search --no-floppy" isn't a kernel option and doesn't seem to do anything (i've tried it with the standard grub-mkconfig_lib and the modified one). anyway, the default kernel options are "ro quiet splash"

---

### Post by SiliconS on 2010-01-22
> **sisco311 said:**
> Backup then edit the /usr/lib/grub/grub-mkconfig_lib file & comment out the lines which add the search --no-floppy line to grub.cfg:
```
...
  # If there's a filesystem UUID that GRUB is capable of identifying, use it;
  # otherwise set root as per value in device.map.
  echo "set root=`${grub_probe} --device ${device} --target=drive`"
  **#**if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
  **#**  echo "search --no-floppy --fs-uuid --set ${fs_uuid}"
  **#**fi
...

```then run:
```
sudo update-grub
```
OK, so I've done this (commented out the three if...fi lines) and the update-grub command went fine, but now when I choose any item to boot in the grub menu I get
```
error: out of disk

Press any key to continue...
```
Typing out the same commands as before into the grub console boots the machine just fine:
```
insmod ext2
set root=(hd0,5)
linux	/boot/vmlinuz-**2.6.31-17-generic**  root=/dev/sda5  ro quiet splash
initrd	/boot/initrd.img-2.6.31-17-generic
boot
```
Any idea what's gone wrong?

---

### Post by sisco311 on 2010-01-22
> **SiliconS said:**
> OK, so I've done this (commented out the three if...fi lines) and the update-grub command went fine, but now when I choose any item to boot in the grub menu I get
```
error: out of disk

Press any key to continue...
```
Typing out the same commands as before into the grub console boots the machine just fine:
```
insmod ext2
set root=(hd0,5)
linux	/boot/vmlinuz-**2.6.31-17-generic**  root=/dev/sda5  ro quiet splash
initrd	/boot/initrd.img-2.6.31-17-generic
boot
```
Any idea what's gone wrong?

restore the /usr/lib/grub/grub-mkconfig_lib file, run update-grub and post the grub.cfg menu entry and mark the line you want to remove from it.

---

### Post by SiliconS on 2010-01-22
OK. This is weird now. Thank you for your continued patient help, sisco311.

After commenting out the lines in grub-mkconfig_lib and running update-grub:
```
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        saved_entry=${chosen}
        save_env saved_entry
        insmod ext2
        set root=(hd0,5)
        linux   /boot/vmlinuz-2.6.31-17-generic root=UUID=90af46f4-b286-4625-a984-0deaa8262516 ro  vga=773  quiet splash
        initrd  /boot/initrd.img-2.6.31-17-generic
}
```Restoring grub-mkconfig_lib and running update-grub again:
```
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        saved_entry=${chosen}
        save_env saved_entry
        insmod ext2
        set root=(hd0,5)
        search --no-floppy --fs-uuid --set 90af46f4-b286-4625-a984-0deaa8262516
        linux   /boot/vmlinuz-2.6.31-17-generic root=UUID=90af46f4-b286-4625-a984-0deaa8262516 ro  vga=773  quiet splash
        initrd  /boot/initrd.img-2.6.31-17-generic
}
```The only difference I can see is the search --no-floppy line. And yet if I remove that line from the start-up script manually, the machine boots perfectly.

Am I missing something obvious? :confused:

---

### Post by Leppie on 2010-01-22
if you're system doesn't get the correct uuid of your ubuntu partition at boot, tell grub to not use uuid's together with the modified version of grub-mkconfig_lib. open your grub defaults file with an editor:
```
gksudo gedit /etc/default/grub
```uncomment the following line like this:
```
GRUB_DISABLE_LINUX_UUID=true
```save and exit and run update-grub:
```
sudo update-grub
```if you modify your grub-mkconfig_lib like this, it will check if the GRUB_DISABLE_LINUX_UUID option is set and leave search out accordingly:
  ```
if [ ! "x${GRUB_DISABLE_LINUX_UUID}" = "xtrue" ] ;then
      if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
      echo "search --no-floppy --fs-uuid --set ${fs_uuid}"
      fi
  fi

```since you don't have a seperate /boot partition,  a quicker way to boot from the grub prompt would be:
```
insmod ext2
set root=(hd0,5)
linux    /vmlinuz  root=/dev/sda5  ro quiet splash
initrd    /initrd.img
boot
```

---

### Post by SiliconS on 2010-01-22
> **Leppie said:**
> if you're system doesn't get the correct uuid of your ubuntu partition at boot, tell grub to not use uuid's together with the modified version of grub-mkconfig_lib.
Sorry Leppie - I don't think I understand why the UUID string could be causing a problem.

When I prevented grub-update_lib from including the *search --no-floppy* line in the grub commands, I couldn't boot. When that line is there but I remove it manually at boot, the machine boots with no problem. When I edit grub.cfg to remove the line, the machine boots OK. The UUID string is the same in all cases.

---

### Post by Leppie on 2010-01-22
> **SiliconS said:**
> Sorry Leppie - I don't think I understand why the UUID string could be causing a problem.

When I prevented grub-update_lib from including the *search --no-floppy* line in the grub commands, I couldn't boot. When that line is there but I remove it manually at boot, the machine boots with no problem. When I edit grub.cfg to remove the line, the machine boots OK. The UUID string is the same in all cases.
when you delete the "search --no-floppy" line at boot, are you still using the "root=UUID=..."?

---

### Post by SiliconS on 2010-01-22
> **Leppie said:**
> when you delete the "search --no-floppy" line at boot, are you still using the "root=UUID=..."?
Yes - literally the only thing that changes is that I delete the whole line that begins *search --no-floppy*. :confused:

---

### Post by Leppie on 2010-01-22
> **SiliconS said:**
> Yes - literally the only thing that changes is that I delete the whole line that begins *search --no-floppy*. :confused:
that makes no sense...
have you tried reinstalling grub2? maybe during some update something went wrong...
usually the "search --no-floppy" creates issues when UUID's are messed up, but if you're system boots normally using the "root=UUID=..." part it can't be that.
to reinstall grub2:
```
sudo apt-get purge grub grub-pc grub-common
sudo apt-get install grub-pc grub-common
```

make backups of grub files you customized first.

---

### Post by meierfra. on 2010-01-22
> usually the "search --no-floppy" creates issues when UUID's are messed up 

The "search" command itself is a little buggy and can cause problems, even when the UUID is correct. 

For more details and  how to remove the search line permanently check out this link:

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

Edit:  Opps. I only had glanced over the thread and hadn't realized you already tried this.

---

### Post by Leppie on 2010-01-22
> **meierfra. said:**
> The "search" command itself is a little buggy and can cause problems, even when the UUID is correct. 

For more details and  how to remove the search line permanently check out this link:

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)
thanks for the heads up :)

the OP edited the grub-mkconfig_lib like suggested on that page (ot, but is that yours as well?). says that the system only boots if he manually removes the search line, any ideas? or has the OP just found a new bug?

---

### Post by meierfra. on 2010-01-22
> but is that yours as well?)
yes.

> edited the grub-mkconfig_lib like suggested on that page
Opps, one should never post without reading the whole thread.:redface: 


SiliconS: The "out of disk" error might be some strange coincident. Could you try again:

Edit "grub-mkconfig_lib" as before. But don't run "update-grub" immediately.  I would like to compare the grub.cfg's:


```
cd /boot/grub
sudo cp grub.cfg grub.cfg.saved
sudo update-grub
diff grub.cfg  grub.cfg.saved

```
Did the "diff" command find  any differences?

Then reboot and see whether you still get the out of disk error.

---

### Post by SiliconS on 2010-01-23
Wow - thank you all for responding with help.

It's getting stranger and I think my problem is more complex.

I just booted this machine and got *error: out of disk* even with the vanilla grub.cfg exactly as update-grub made it. So something is more wrong than just the *search --no-floppy* line.

Here's the menu entry that I'm trying to boot:
```
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        saved_entry=${chosen}
        save_env saved_entry
        insmod ext2
        set root=(hd0,5)
        search --no-floppy --fs-uuid --set 90af46f4-b286-4625-a984-0deaa8262516
        linux   /boot/vmlinuz-2.6.31-17-generic root=UUID=90af46f4-b286-4625-a984-0deaa8262516 ro  vga=773  quiet $
        initrd  /boot/initrd.img-2.6.31-17-generic
}
```At boot just now I had to remove everything before *insmod ext2* plus the *search --no-floppy* line before the machine would boot.

Does that tell you anything?

I thought I'd try and re-install grub as Leppie suggested, but when I ran the first of Leppie's commands:
```
sudo apt-get purge grub grub-pc grub-common
```I got
```
user@Laptop:~$ sudo apt-get purge grub grub-pc grub-common
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
The following packages were automatically installed and are no longer required:
  menu kdelibs4c2a linux-headers-2.6.31-14 fakeroot kdelibs-data libshp1
  liblualib50 libavahi-qt3-1 dkms libqt3-mt-sqlite fglrx-kernel-source patch
  liblua50 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  grub-common* grub-pc* startupmanager*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 5,267kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
```The line saying *Package grub is not installed* worried me so I aborted. Should I be removing grub*2* instead or something?

I'll re-install grub and then try again with editing grub-mkconfig_lib once everything is working perfectly again.

---

### Post by Leppie on 2010-01-23
> **SiliconS said:**
> 
I thought I'd try and re-install grub as Leppie suggested, but when I ran the first of Leppie's commands:
```
sudo apt-get purge grub grub-pc grub-common
```I got
```
user@Laptop:~$ sudo apt-get purge grub grub-pc grub-common
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
The following packages were automatically installed and are no longer required:
  menu kdelibs4c2a linux-headers-2.6.31-14 fakeroot kdelibs-data libshp1
  liblualib50 libavahi-qt3-1 dkms libqt3-mt-sqlite fglrx-kernel-source patch
  liblua50 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  grub-common* grub-pc* startupmanager*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 5,267kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
```The line saying *Package grub is not installed* worried me so I aborted. Should I be removing grub*2* instead or something?

I'll re-install grub and then try again with editing grub-mkconfig_lib once everything is working perfectly again.
don't worry about grub not being installed. i just put that package in to make sure you're not using some mixed version (grub2 and grub legacy). the grub package is grub legacy, so you can either leave it out now or just go ahead with the command as is. it cannot remove something you don't have installed on your system ;)

---

### Post by drs305 on 2010-01-23
> **SiliconS said:**
> ... worried me so I aborted. Should I be removing grub*2* instead or something?

I'll re-install grub and then try again with editing grub-mkconfig_lib once everything is working perfectly again.

You are also going to be greeted by a warning saying that your system will be unbootable if you continue without installing a bootloader. This is also normal - continue and just be sure to install grub-pc and set it up before you reboot.

---

### Post by SiliconS on 2010-01-24
I need my laptop for a meeting in the morning so I can't risk breaking it tonight with my clumsy fingers. :)
I'll try uninstalling/installing grub tomorrow and post my results.

---

### Post by Leppie on 2010-01-24
> **SiliconS said:**
> I need my laptop for a meeting in the morning so I can't risk breaking it tonight with my clumsy fingers. :)
I'll try uninstalling/installing grub tomorrow and post my results.
re-installing grub shouldn't really break your system...

let us know tomorrow :)

---

### Post by SiliconS on 2010-01-27
> **Leppie said:**
> to reinstall grub2:
```
sudo apt-get purge grub grub-pc grub-common
sudo apt-get install grub-pc grub-common
```
OK, I've done it:
```
user@Laptop:~$ sudo apt-get purge grub grub-pc grub-common
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
The following packages were automatically installed and are no longer required:
  menu kdelibs4c2a linux-headers-2.6.31-14 fakeroot kdelibs-data libshp1
  liblualib50 libavahi-qt3-1 dkms libqt3-mt-sqlite fglrx-kernel-source patch
  liblua50 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  grub-common* grub-pc* startupmanager*
0 upgraded, 0 newly installed, 3 to remove and 13 not upgraded.
After this operation, 5,267kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 204625 files and directories currently installed.)
Removing startupmanager ...
Purging configuration files for startupmanager ...
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/menu.info.gz'
user@Laptop:~$ sudo apt-get install grub-pc grub-common
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages were automatically installed and are no longer required:
  menu kdelibs4c2a linux-headers-2.6.31-14 fakeroot kdelibs-data libshp1
  liblualib50 libavahi-qt3-1 dkms libqt3-mt-sqlite fglrx-kernel-source patch
  liblua50 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  multiboot-doc grub-emu desktop-base
The following NEW packages will be installed
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 13 not upgraded.
Need to get 1,428kB of archives.
After this operation, 4,170kB of additional disk space will be used.
Get: 1 http://gb.archive.ubuntu.com karmic-updates/main grub-common 1.97~beta4-1ubuntu4.1 [994kB]
Get: 2 http://gb.archive.ubuntu.com karmic-updates/main grub-pc 1.97~beta4-1ubuntu4.1 [434kB]
Fetched 1,428kB in 5s (256kB/s)                           
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 204297 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.97~beta4-1ubuntu4.1_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.97~beta4-1ubuntu4.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/menu.info.gz'
Processing triggers for ureadahead ...
Setting up grub-common (1.97~beta4-1ubuntu4.1) ...

Setting up grub-pc (1.97~beta4-1ubuntu4.1) ...

Creating config file /etc/default/grub with new version
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found Microsoft Windows XP Professional on /dev/sda1
done

user@Laptop:~$ 
```
The terminal window prompted me for a couple of options during the install process and I just accepted the default values. If anybody spots anything wrong in the output above I'd be grateful for a warning before I reboot this machine for the first time. :)

---

### Post by Leppie on 2010-01-27
> **SiliconS said:**
> The terminal window prompted me for a couple of options during the install process and I just accepted the default values. If anybody spots anything wrong in the output above I'd be grateful for a warning before I reboot this machine for the first time. :)
it's looking good ;)

---

### Post by SiliconS on 2010-01-27
OK - first reboot coming up. Wish me luck. I may be gone some time. ;)

---

### Post by SiliconS on 2010-01-27
Great. Now at boot-up I don't get a grub menu. I get:```
GRUB loading.
error: out of disk
grub rescue>
```

Oh joy.

*goes off to Google yet again. :(

---

### Post by Leppie on 2010-01-27
> **SiliconS said:**
> Great. Now at boot-up I don't get a grub menu. I get:```
GRUB loading.
error: out of disk
grub rescue>
```Oh joy.

*goes off to Google yet again. :(
boot off the livecd (again), mount your ubuntu partition and then open the 10_linux file in a text editor:
```
sudo -i
mkdir /mnt/temp
mount /dev/sda5 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
gedit /mnt/temp/etc/grub.d/10_linux
```find the followin lines:
```
menuentry "$1" {
recordfail=1
if [ -n \${have_grubenv} ]; then save_env recordfail; fi
```and comment out the second of these, like this:
```
menuentry "$1" {
recordfail=1
[COLOR=Red]**#**[/COLOR] if [ -n \${have_grubenv} ]; then save_env recordfail; fi
```save and exit, then run update-grub and reboot:
```
update-grub
shutdown -r now
```more info about this issue on this page: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)

---

### Post by SiliconS on 2010-01-27
Leppie - thank you once again for your help. I'd be stuck without your clear instructions.

Unfortunately, no luck with what you suggested. I still can't boot from my LiveCD. After the menu screen it seems to work for about 5 minutes (with the pulsing Ubuntu logo) and then the CapsLock light comes on and everything stalls. FML.

A few days ago I downloaded something called grub-rescue-cdrom.iso that was supposed to help when grub had a major benny, so I burnt the iso and used that at bootup to run my standard
```
insmod ext2
set root=(hd0,5)
linux    /boot/vmlinuz-**2.6.31-17-generic**  root=/dev/sda5  ro quiet splash
initrd    /boot/initrd.img-2.6.31-17-generic
boot
```start-up commands. It worked, and I got back to the Gnome desktop. Happy days.

BUT, while everything was booting, I saw a load of worrying status outputs scroll past, saying stuff like:
```
Buffer I/O error on device sr0, logical block 632
end_request: I/O error, dev sr0, sector 2528
```I don't know much about computer hardware, but the word 'sector' made me wonder whether I have a disk hardware problem. Perhaps that's causing a problem that re-installing grub is never going to solve. FML.

Do you have any ideas or suggestions please? Without my grub rescue bootable CD I'm still at the```
GRUB loading.
error: out of disk
grub rescue>
```prompt. At that prompt I can't even type 'help' or 'cat'. They're both unknown commands, which seems strange.

Edit: I've rebooted and I'm running a self-test on the HDD in the BIOS. 85 minutes remaining...

---

### Post by Leppie on 2010-01-27
do you ever do a md5sum check after downloading and burning cd images? this usually helps preventing (and analyzing) cdrom issues.

---

### Post by SiliconS on 2010-01-28
> **Leppie said:**
> do you ever do a md5sum check after downloading and burning cd images? this usually helps preventing (and analyzing) cdrom issues.
I haven't yet. :oops: I'll re-burn my LiveCD and check it.

Anyway, using my grub-rescue-cdrom I'm back into Gnome. grub.cfg looks like it always did.
Using Synaptic (sorry - I'm still a GUI guy) I've 'completely' uninstalled grub-pc and grub-common but the /boot/grub folder still exists including grub.cfg. Can I / should I delete that folder to absolutely guarantee that no trace of the original config remains? Are there any other files I should manually remove? Or should I just re-install those two packages and hope for the best?

Or is there something else I should try? Is there a way of doing a hardware check on the MBR using Linux? (It passed the BIOS check.)

---

### Post by Leppie on 2010-01-28
> **SiliconS said:**
> I haven't yet. :oops: I'll re-burn my LiveCD and check it.
it would be good habit to do the checks ;)

> **SiliconS said:**
> Using Synaptic (sorry - I'm still a GUI guy) I've 'completely' uninstalled grub-pc and grub-common but the /boot/grub folder still exists including grub.cfg. Can I / should I delete that folder to absolutely guarantee that no trace of the original config remains? Are there any other files I should manually remove? Or should I just re-install those two packages and hope for the best?
that's why i advise to use the "apt-get purge" option. delete (or rename if you want to keep a backup) the folder /boot/grub, then reinstall

> **SiliconS said:**
> Or is there something else I should try? Is there a way of doing a hardware check on the MBR using Linux? (It passed the BIOS check.)
it's probably a bug in grub2, reinstall grub2 and let us know if it's working or if you're getting the out of disk error again.

---

### Post by SiliconS on 2010-01-28
I've reinstalled grub-pc and grub-common using Synaptic, but the only thing in the new /boot/grub folder is a file called grubenv.

Should I be installing grub as root? Or is sudo enough?

---

### Post by Leppie on 2010-01-28
> **SiliconS said:**
> I've reinstalled grub-pc and grub-common using Synaptic, but the only thing in the new /boot/grub folder is a file called grubenv.

Should I be installing grub as root? Or is sudo enough?
sudo should be enough.
strange that you only have grubenv in the grub folder. did dpkg not fire up the configurtion scripts for the 2 packages you installed?

---

### Post by SiliconS on 2010-01-30
I'm back, but no further forward than I was. :(

Leppie, I used your shell commands to apt-get the grub packages and they have recreated the contents of the /boot/grub folder, but the machine still crashes out at boot with the *error: out of disk* problem. I can boot if I use my grub-rescue-cdrom and type the commands manually. The grub.cfg file looks the same as it always did.

Maybe there's some way of formatting the MBR so I can try and rebuild it from scratch? Is that an option? I can't help feeling that there's something fundamentally wrong with the MBR.

I really appreciate your continued help, Leppie, but I might try and find my local LUG so someone can see it for themselves. It's embarassing to waste your time by asking questions without knowing what information to provide to help you answer them.

*Edit:* On the upside, I burnt the Karmic LiveCD .iso to a new disk and it now boots perfectly. Does that give me any extra tools or options for getting grub working again?

---

### Post by Leppie on 2010-01-30
> **SiliconS said:**
> I'm back, but no further forward than I was. :(

Leppie, I used your shell commands to apt-get the grub packages and they have recreated the contents of the /boot/grub folder, but the machine still crashes out at boot with the *error: out of disk* problem. I can boot if I use my grub-rescue-cdrom and type the commands manually. The grub.cfg file looks the same as it always did.
there are still several issues with grub2 and especially the search command it uses. it may well be that it just will not operate with your system.

> **SiliconS said:**
> Maybe there's some way of formatting the MBR so I can try and rebuild it from scratch? Is that an option? I can't help feeling that there's something fundamentally wrong with the MBR.
you can clear the mbr like this:
```
sudo apt-get install lilo
sudo lilo -M /dev/sdX mbr  ##sdX being the mbr of the destination drive. e.g. sda for the first drive, sdb for the second, etc.
```> **SiliconS said:**
> I really appreciate your continued help, Leppie, but I might try and find my local LUG so someone can see it for themselves. It's embarassing to waste your time by asking questions without knowing what information to provide to help you answer them.
don't worry, we're here to help each other out. maybe i'll come up with an issue you are able to solve ;)

> **SiliconS said:**
> *Edit:* On the upside, I burnt the Karmic LiveCD .iso to a new disk and it now boots perfectly. Does that give me any extra tools or options for getting grub working again?
try the instructions in post #20 again: [http://ubuntuforums.org/showpost.php?p=8706524&postcount=20](http://ubuntuforums.org/showpost.php?p=8706524&postcount=20)


another way to clear the mbr is with the dd command, but this can be very destructive:
```
sudo dd if=/dev/zero of=/dev/sdX bs=446 count=1
```

---

### Post by SiliconS on 2010-02-04
Leppie: It's been a few days. I wasn't ignoring you - I just wanted to get away from this problem for a while and try coming back to it fresh again. I'm still using my grub-rescue-cdrom to boot, and typing out the commands manually every time. Yeah, it's tedious. For the last four days I've used Windows, which I can suspend/resume successfully without needing to touch grub. :-/
  
  So, I thought I'd try your latest advice. It seems very reasonable, and thank you again.
  
  I shut down XP and loaded the grub CD. I typed out the commands that I've been using for the last couple of weeks:
  ```
insmod ext2
set root=(hd0,5)
linux /boot/vmlinuz-**2.6.31-17-generic**  root=/dev/sda5  ro quiet splash
initrd /boot/initrd.img-2.6.31-17-generic
boot
``` Now even this doesn't work. I get various errors, such as 'file not found', 'error reading file' etc. (I'm paraphrasing - I can't remember *exactly *what they say. Tell me if it's important to know.)
  
  So, logically perhaps the kernel image is corrupt or something. I try 2.6.31-**16** instead and boot successfully. Good. (I can still get into Windows using the menu commands from grub.cfg too.)
  
  Right then, I'm back into Gnome. I try your suggestion of installing lilo instead.
  ```
user@Laptop:~$ sudo apt-get install lilo
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  The following packages were automatically installed and are no longer required:
    kdelibs4c2a linux-headers-2.6.31-14 fakeroot kdelibs-data libshp1 liblualib50 libavahi-qt3-1
    dkms libqt3-mt-sqlite fglrx-kernel-source patch liblua50 linux-headers-2.6.31-14-generic
  Use 'apt-get autoremove' to remove them.
  Suggested packages:
    lilo-doc
  The following NEW packages will be installed
    lilo
  0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
  Need to get 0B/390kB of archives.
  After this operation, 1,221kB of additional disk space will be used.
  Preconfiguring packages ...
  Selecting previously deselected package lilo.
  (Reading database ... 204636 files and directories currently installed.)
  Unpacking lilo (from .../lilo_1%3a22.8-8ubuntu1_i386.deb) ...
  Processing triggers for man-db ...
  Processing triggers for menu ...
  Setting up lilo (1:22.8-8ubuntu1) ...
  
  WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
  WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
  WARNING: Please read /usr/share/doc/lilo/README.Debian
  
  
  Processing triggers for menu ...
  user@Laptop:~$ 
``` That's not looking good. More support to the idea that the 2.6.31-17 stuff (kernel + boot image + whatever = "2.6.31-17 stuff") has become somehow unusable or corrupt. Maybe?
  
  After some Gooooogling (and reading of [your other posts]("http://ubuntuforums.org/showthread.php?t=1392894")) it seems the boot info script is a valuable tool, so to pre-empt your request, I ran it for you. ;)
  ```
============================= Boot Info Summary: ==============================
  
   => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
      partition #5 for /boot/grub.
  sda1: _________________________________________________________________________
  
      File system:       ntfs
      Boot sector type:  Windows XP
      Boot sector info:  No errors found in the Boot Parameter Block.
      Operating System:  Windows XP
      Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS
  
  sda2: _________________________________________________________________________
  
      File system:       Extended Partition
      Boot sector type:  -
      Boot sector info:  
  
  sda5: _________________________________________________________________________
  
      File system:       ext4
      Boot sector type:  -
      Boot sector info:  
      Operating System:  Ubuntu 9.10
      Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
  
  sda6: _________________________________________________________________________
  
      File system:       swap
      Boot sector type:  -
      Boot sector info:  
  
  =========================== Drive/Partition Info: =============================
  
  Drive: sda ___________________ _____________________________________________________
  
  Disk /dev/sda: 160.0 GB, 160041885696 bytes
  255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
  Units = sectors of 1 * 512 = 512 bytes
  Disk identifier: 0xaa14aa14
  
  Partition  Boot         Start           End          Size  Id System
  
  /dev/sda1    *             63   248,959,304   248,959,242   7 HPFS/NTFS
  /dev/sda2         248,959,305   312,576,704    63,617,400   5 Extended
  /dev/sda5         248,959,368   309,861,719    60,902,352  83 Linux
  /dev/sda6         309,861,783   312,576,704     2,714,922  82 Linux swap / Solaris
  
  
  blkid -c /dev/null: ____________________________________________________________
  
  Device           UUID                                   TYPE       LABEL                         
  
  /dev/sda1        72F44334F442FA3D                       ntfs                                     
  /dev/sda5        90af46f4-b286-4625-a984-0deaa8262516   ext4                                     
  /dev/sda6        d918ac89-0719-45fa-bed7-3eaf5bf560d6   swap                                     
  
  ============================ "mount | grep ^/dev  output: ===========================
  
  Device           Mount_Point              Type       Options
  
  /dev/sda5        /                        ext4       (rw,errors=remount-ro)
  /dev/sda1        /media/sda1              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
  /dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=ben)
  
  
  ================================ sda1/boot.ini: ================================
  
  [boot loader]
  timeout=30
  default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
  [operating systems]
  multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
  
  =========================== sda5/boot/grub/grub.cfg: ===========================
  
  #
  # DO NOT EDIT THIS FILE
  #
  # It is automatically generated by /usr/sbin/grub-mkconfig using templates
  # from /etc/grub.d and settings from /etc/default/grub
  #
  
  ### BEGIN /etc/grub.d/00_header ###
  if [ -s /boot/grub/grubenv ]; then
    have_grubenv=true
    load_env
  fi
  set default="0"
  if [ ${prev_saved_entry} ]; then
    saved_entry=${prev_saved_entry}
    save_env saved_entry
    prev_saved_entry=
    save_env prev_saved_entry
  fi
  insmod ext2
  set root=(hd0,5)
  search --no-floppy --fs-uuid --set 90af46f4-b286-4625-a984-0deaa8262516
  if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
    insmod gfxterm
    insmod vbe
    if terminal_output gfxterm ; then true ; else
      # For backward compatibility with versions of terminal.mod that don't
      # understand terminal_output
      terminal gfxterm
    fi
  fi
  if [ ${recordfail} = 1 ]; then
    set timeout=-1
  else
    set timeout=10
  fi
  ### END /etc/grub.d/00_header ###
  
  ### BEGIN /etc/grub.d/05_debian_theme ###
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
  ### END /etc/grub.d/05_debian_theme ###
  
  ### BEGIN /etc/grub.d/10_linux ###
  menuentry "Ubuntu, Linux 2.6.31-17-generic" {
          recordfail=1
          if [ -n ${have_grubenv} ]; then save_env recordfail; fi
      set quiet=1
      insmod ext2
      set root=(hd0,5)
      search --no-floppy --fs-uuid --set 90af46f4-b286-4625-a984-0deaa8262516
      linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=90af46f4-b286-4625-a984-0deaa8262516 ro  splash  quiet splash
      initrd    /boot/initrd.img-2.6.31-17-generic
  }
  menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
          recordfail=1
          if [ -n ${have_grubenv} ]; then save_env recordfail; fi
      insmod ext2
      set root=(hd0,5)
      search --no-floppy --fs-uuid --set 90af46f4-b286-4625-a984-0deaa8262516
      linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=90af46f4-b286-4625-a984-0deaa8262516 ro single  splash
      initrd    /boot/initrd.img-2.6.31-17-generic
  }
  menuentry "Ubuntu, Linux 2.6.31-16-generic" {
          recordfail=1
          if [ -n ${have_grubenv} ]; then save_env recordfail; fi
      set quiet=1
      insmod ext2
      set root=(hd0,5)
      search --no-floppy --fs-uuid --set 90af46f4-b286-4625-a984-0deaa8262516
      linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=90af46f4-b286-4625-a984-0deaa8262516 ro  splash  quiet splash
      initrd    /boot/initrd.img-2.6.31-16-generic
  }
  menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
          recordfail=1
          if [ -n ${have_grubenv} ]; then save_env recordfail; fi
      insmod ext2
      set root=(hd0,5)
      search --no-floppy --fs-uuid --set 90af46f4-b286-4625-a984-0deaa8262516
      linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=90af46f4-b286-4625-a984-0deaa8262516 ro single  splash
      initrd    /boot/initrd.img-2.6.31-16-generic
  }
  menuentry "Ubuntu, Linux 2.6.31-15-generic" {
          recordfail=1
          if [ -n ${have_grubenv} ]; then save_env recordfail; fi
      set quiet=1
      insmod ext2
      set root=(hd0,5)
      search --no-floppy --fs-uuid --set 90af46f4-b286-4625-a984-0deaa8262516
      linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=90af46f4-b286-4625-a984-0deaa8262516 ro  splash  quiet splash
      initrd    /boot/initrd.img-2.6.31-15-generic
  }
  menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
          recordfail=1
          if [ -n ${have_grubenv} ]; then save_env recordfail; fi
      insmod ext2
      set root=(hd0,5)
      search --no-floppy --fs-uuid --set 90af46f4-b286-4625-a984-0deaa8262516
      linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=90af46f4-b286-4625-a984-0deaa8262516 ro single  splash
      initrd    /boot/initrd.img-2.6.31-15-generic
  }
  menuentry "Ubuntu, Linux 2.6.31-14-generic" {
          recordfail=1
          if [ -n ${have_grubenv} ]; then save_env recordfail; fi
      set quiet=1
      insmod ext2
      set root=(hd0,5)
      search --no-floppy --fs-uuid --set 90af46f4-b286-4625-a984-0deaa8262516
      linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=90af46f4-b286-4625-a984-0deaa8262516 ro  splash  quiet splash
      initrd    /boot/initrd.img-2.6.31-14-generic
  }
  menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
          recordfail=1
          if [ -n ${have_grubenv} ]; then save_env recordfail; fi
      insmod ext2
      set root=(hd0,5)
      search --no-floppy --fs-uuid --set 90af46f4-b286-4625-a984-0deaa8262516
      linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=90af46f4-b286-4625-a984-0deaa8262516 ro single  splash
      initrd    /boot/initrd.img-2.6.31-14-generic
  }
  ### END /etc/grub.d/10_linux ###
  
  ### BEGIN /etc/grub.d/30_os-prober ###
  menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
      insmod ntfs
      set root=(hd0,1)
      search --no-floppy --fs-uuid --set 72f44334f442fa3d
      drivemap -s (hd0) ${root}
      chainloader +1
  }
  ### END /etc/grub.d/30_os-prober ###
  
  ### BEGIN /etc/grub.d/40_custom ###
  # This file provides an easy way to add custom menu entries.  Simply type the
  # menu entries you want to add after this comment.  Be careful not to change
  # the 'exec tail' line above.
  ### END /etc/grub.d/40_custom ###
  
  =============================== sda5/etc/fstab: ===============================
  
  # /etc/fstab: static file system information.
  #
  # Use 'blkid -o value -s UUID' to print the universally unique identifier
  # for a device; this may be used with UUID= as a more robust way to name
  # devices that works even if disks are added and removed. See fstab(5).
  #
  # <file system> <mount point>   <type>  <options>       <dump>  <pass>
  proc                                       /proc          proc         defaults                 0  0  
  # / was on /dev/sda5 during installation
  UUID=90af46f4-b286-4625-a984-0deaa8262516  /              ext4         errors=remount-ro        0  1  
  # swap was on /dev/sda6 during installation
  UUID=d918ac89-0719-45fa-bed7-3eaf5bf560d6  none           swap         sw                       0  0  
  /dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8    0  0  
  /dev/sda1                                  /media/sda1    ntfs         nls=iso8859-1,umask=000  0  0  
```Can/should I remove the 2.6.31-17 stuff completely and let the update-manager reinstall it all? If so, how?

Do you have any other ideas please? I *hate *feeling this helplessly stupid. :(

Edit: BTW...
> don't worry, we're here to help each other out. maybe i'll come up with an issue you are able to solve ;)
LOL. Unless you want to know something about mid-'70s Stingrays I doubt there's much I can help you with. :)

---

### Post by SiliconS on 2010-02-05
An update:
Update Manager told me about a new kernel today, so I let it do its thing. I thought maybe that would solve the 'broken' 2.6.31-17 stuff.

But grub still won't start - it still gives me an out of disk error - so I try my commands with the rescue CD again. If I type out the commands to choose the new 2.6.31-19 kernel I get an error: '*cannot read the linux header*'

2.6.31-16 still works though.

Forgot to mention yesterday that I looked at the S.M.A.R.T. diagnosis report for the HDD in this laptop - it came up fine. If there are any bad sectors it hasn't realised yet.

---

### Post by SiliconS on 2010-02-05
Whoah! Triple post madness.
I crashed onwards and ran the second of your lilo installation commands to see what happened.
Now at least the machine will boot without the rescue CD... but straight into Windows with no options. That feels like progress although the Linux purists might disagree. ;)

(The rescue CD still allows me to type the grub commands and boot into 2.6.31-16.)

*a few minutes later...*

I did an apt-get purge lilo after getting back into Gnome, then an apt-get autoremove (as recommended by aptitude when installing/removing lilo). I then did a purge and install of grub...

...WITH SUCCESS! (Sort of.)

The grub menu now appears correctly when I boot the machine, but one problem remains. If I choose the 2.6.31-19 option, I get the *Cannot read the linux header *error. If I choose the 2.6.31-17 option I get a *Couldn't read file* error.
That's gotta be a simple problem to solve, right? ;)

---

### Post by drs305 on 2010-02-05
> **SiliconS said:**
> 
The grub menu now appears correctly when I boot the machine, but one problem remains. If I choose the 2.6.31-19 option, I get the *Cannot read the linux header *error. If I choose the 2.6.31-17 option I get a *Couldn't read file* error.
That's gotta be a simple problem to solve, right? ;)

One thing you could do for troubleshooting:

At the Grub menu, press "e" after highlighting the working kernel menu item. Change the *version number (-16, etc)* in the linux and initrd lines to one of the versions that isn't working and see if it boots.

Have you checked Synaptic to see if the -19 headers are installed?

Random thought: If this is an older machine and you put in a larger hard drive, have you ever updated the BIOS?

---

### Post by SiliconS on 2010-02-05
Hi drs305. Thanks for responding.
 
 > **drs305 said:**
> One thing you could do for troubleshooting:

At the Grub menu, press "e" after highlighting the working kernel menu item. Change the *version number (-16, etc)* in the linux and initrd lines to one of the versions that isn't working and see if it boots.
I like this idea of changing 2.6.31-16 (a working menu entry) to 2.6.31-**19** but I still get *error: cannot read the linux header* when I Ctrl-X to boot the commands.
 
> **drs305 said:**
>  Have you checked Synaptic to see if the -19 headers are installed?
In Synaptic, if I quick search for 2.6.31-19 I see the following three packages are marked as installed:

linux-headers-2.6.31-19
linux-headers-2.6.31-19-generic
linux-image-2.6.31-19-generic

None of the 2.6.31-19 backports packages is installed.

> **drs305 said:**
> Random thought: If this is an older machine and you put in a larger hard drive, have you ever updated the BIOS?
I didn't update the BIOS when I put this 160GB HDD in, but everything worked for two months without a problem so I hope that wouldn't have caused this.

---

### Post by Leppie on 2010-02-05
booting into the 16 kernel version, try to completely remove the 17 and 19 kernel packages:
```
sudo apt-get purge linux-headers-2.6.31-19 linux-headers-2.6.31-19-generic linux-image-2.6.31-19-generic linux-headers-2.6.31-17 linux-headers-2.6.31-17-generic linux-image-2.6.31-17-generic
```
then re-install the 19 kernel packages:
```
sudo apt-get install linux-headers-2.6.31-19 linux-headers-2.6.31-19-generic linux-image-2.6.31-19-generic
```
then try rebooting

---

### Post by SiliconS on 2010-02-08
Sorry Leppie - I didn't realise you'd replied. Thanks for the commands.

```
user@Laptop:~$ sudo apt-get purge linux-headers-2.6.31-19 linux-headers-2.6.31-19-generic linux-image-2.6.31-19-generic linux-headers-2.6.31-17 linux-headers-2.6.31-17-generic linux-image-2.6.31-17-generic
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  menu fakeroot dkms fglrx-kernel-source patch
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  linux-generic* linux-headers-2.6.31-17* linux-headers-2.6.31-17-generic*
  linux-headers-2.6.31-19* linux-headers-2.6.31-19-generic*
  linux-headers-generic* linux-image-2.6.31-17-generic*
  linux-image-2.6.31-19-generic* linux-image-generic*
0 upgraded, 0 newly installed, 9 to remove and 0 not upgraded.
After this operation, 345MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 204015 files and directories currently installed.)
Removing linux-generic ...
Removing linux-headers-2.6.31-17-generic ...
Removing linux-headers-2.6.31-17 ...
Removing linux-headers-generic ...
Removing linux-headers-2.6.31-19-generic ...
Removing linux-headers-2.6.31-19 ...
Removing linux-image-2.6.31-17-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found Microsoft Windows XP Professional on /dev/sda1
done
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-2.6.31-17-generic ...
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found Microsoft Windows XP Professional on /dev/sda1
done
Removing linux-image-generic ...
Removing linux-image-2.6.31-19-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found Microsoft Windows XP Professional on /dev/sda1
done
**The link /vmlinuz is a damaged link**
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
**The link /initrd.img is a damaged link**
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-2.6.31-19-generic ...
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found Microsoft Windows XP Professional on /dev/sda1
done
user@Laptop:~$ sudo apt-get install linux-headers-2.6.31-19 linux-headers-2.6.31-19-generic linux-image-2.6.31-19-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  menu fakeroot dkms fglrx-kernel-source patch
Use 'apt-get autoremove' to remove them.
Suggested packages:
  fdutils linux-doc-2.6.31 linux-source-2.6.31
The following NEW packages will be installed
  linux-headers-2.6.31-19 linux-headers-2.6.31-19-generic
  linux-image-2.6.31-19-generic
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/39.0MB of archives.
After this operation, 172MB of additional disk space will be used.
Selecting previously deselected package linux-image-2.6.31-19-generic.
(Reading database ... 161847 files and directories currently installed.)
Unpacking linux-image-2.6.31-19-generic (from .../linux-image-2.6.31-19-generic_2.6.31-19.56_i386.deb) ...
Done.
Selecting previously deselected package linux-headers-2.6.31-19.
Unpacking linux-headers-2.6.31-19 (from .../linux-headers-2.6.31-19_2.6.31-19.56_all.deb) ...
Selecting previously deselected package linux-headers-2.6.31-19-generic.
Unpacking linux-headers-2.6.31-19-generic (from .../linux-headers-2.6.31-19-generic_2.6.31-19.56_i386.deb) ...
Setting up linux-image-2.6.31-19-generic (2.6.31-19.56) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-19-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found Microsoft Windows XP Professional on /dev/sda1
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-19-generic          
 *  fglrx (8.660)...                                                            fglrx (8.660): Installing module.
.........
......
                                                                         [ OK ]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

Setting up linux-headers-2.6.31-19 (2.6.31-19.56) ...
Setting up linux-headers-2.6.31-19-generic (2.6.31-19.56) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-19-generic          
 *  fglrx (8.660)...                                                            fglrx (8.660): Already installed on this kernel.
                                                                         [ OK ]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

user@Laptop:~$ 
```I haven't tried rebooting yet - I'm in the middle of doing a first sync with Unison of my music folders - but I'll try in a while. I'll post the results.

---

### Post by SiliconS on 2010-02-08
Nope. That broke grub again. :(
At boot I just get the grub shell - there's no menu.
I'll try the various fixes again using the rescue CD. Not now though - I'm too tired.

---

### Post by Leppie on 2010-02-08
it looks like your system is a bit messed up:
```
**The link /vmlinuz is a damaged link**
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
**The link /initrd.img is a damaged link**

```and this:
```

Examining /etc/kernel/postinst.d.
[COLOR=Blue]run-parts: executing /etc/kernel/postinst.d/dkms[/COLOR]
 * Running DKMS auto installation service for kernel 2.6.31-19-generic          
 *  fglrx (8.660)...                                                            fglrx (8.660): Installing module.
.........
......
                                                                         [ OK ]
[COLOR=Red] run-parts: executing /etc/kernel/postinst.d/nvidia-common[/COLOR]

Setting up linux-headers-2.6.31-19 (2.6.31-19.56) ...
Setting up linux-headers-2.6.31-19-generic (2.6.31-19.56) ...
Examining /etc/kernel/header_postinst.d.
[COLOR=Blue]run-parts: executing /etc/kernel/header_postinst.d/dkms[/COLOR]
 * Running DKMS auto installation service for kernel 2.6.31-19-generic          
 *  fglrx (8.660)...                                                            fglrx (8.660): Already installed on this kernel.
                                                                         [ OK ]
[COLOR=Red]run-parts: executing /etc/kernel/header_postinst.d/nvidia-common[/COLOR]


```
why are these scripts run twice?

---

### Post by SiliconS on 2010-02-08
> **Leppie said:**
> why are these scripts run twice?
I don't know. :redface: This laptop doesn't even have NVidia graphics. I guess that NVidia thing is the default package installed in Karmic, but I don't know. I don't want to remove any of the NVidia packages in case I mess something else up.

---

### Post by Leppie on 2010-02-08
> **SiliconS said:**
> I don't know. :redface: This laptop doesn't even have NVidia graphics. I guess that NVidia thing is the default package installed in Karmic, but I don't know. I don't want to remove any of the NVidia packages in case I mess something else up.
i have those scripts as well on my system, but they don't run after a kernel upgrade (at least, they don't show any output).

---

### Post by SiliconS on 2010-02-08
Can you think of anything I should try next to get these kernel packages working? I'm hoping I can fix grub using earlier instructions but rather than hack about with the kernels perhaps I should just wait until the 2.6.31-20 upgrades are released - perhaps they'll work instead. 2.6.31-16 is working nicely for me, and even suspend/resume has started working.

I'm going to try for some sleep again. 4am here in the UK.

---

### Post by Leppie on 2010-02-09
i really don't understand why the nvidia script jumps in... i've never seen that before (at least not on a machine with no nvidia card).

---

### Post by SiliconS on 2010-02-15
I need to close this off somehow, I guess.

I gave up with trying to get 2.6.31-17 or -19 to work with grub, so I *apt-get remove*d them in the way you suggested above, Leppie. Having edited grub-mkconfig_lib to comment out the search --no-floppy lines and re-run update-grub, my system now boots smoothly into either Windows or 2.6.31-16. For the moment it's all going OK again, but who knows what'll happen when kernel 2.6.31-20 appears. At least I've become familiar enough with grub to have a go at rebuilding it if it breaks again, with the help of my trusty grub rescue disk.

Leppie and others, thanks again for all your help. I really appreciate it.

---

