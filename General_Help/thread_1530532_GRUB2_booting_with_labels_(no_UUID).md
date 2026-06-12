---
title: "GRUB2 booting with labels (no UUID)"
date: 2010-07-12
forum: General Help
---

### Post by MountainX on 2010-07-12
> **Leppie said:**
> in the end, you could edit the grub.cfg every time update-grub is run. but why would you do that if it isn't necessary since there's other ways to make it stick? would be kind of masochistic, don't you think?

anyways, if you really do want to edit the grub.cfg, you should delete the piece between the 30_os-prober comments (start and end), but don't remove the comments themselves.

Thanks for your explanations. You are right. I certainly don't want to edit grub.cfg if I can avoid it.

**Speaking of which, do you happen to know how to make update-grub generate a grub.cfg file that uses labels instead of UUID's to identify the root device?**

I have hand-edited grub.cfg now so that my system will boot entirely using filesystem labels. It works. But I need it to stick. I haven't found any help on that yet.

---

### Post by drs305 on 2010-07-12
I'm not sure "labels" has been incorporated yet, although it would certainly be nice.  There are LABEL and LLABEL designations in some of the G2 files but they don't refer to the labels as we commonly think of them.


As far as how 30_op-prober is supposed to work, if you use the "true" statement or make it unexecutable, Grub2 will not search your other partitions for more Linux or other OS's. No 30_os-prober section will appear in /boot/grub/grub.cfg.

I couldn't tell if you had solved the 30_os-prober satisfactorily or not. If not, just elaborate on what you want to do.

Instead of hand-editing grub.cfg, making a custom menu or modifying /etc/grub.d/40_custom is a far better way to do this.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu")

---

### Post by MountainX on 2010-07-12
> **drs305 said:**
> I'm not sure "labels" has been incorporated yet, although it would certainly be nice. 

Yes, it's in there. See here:
[http://www.gnu.org/software/grub/manual/grub.html#search](http://www.gnu.org/software/grub/manual/grub.html#search)

Furthermore, someone at Linux Mint forums figured out how to make it work. He did it by manually editing grub.cfg. I tried it and it works for me too. Now all I need to do it figure out how to make update-grub generate a grub.cfg file that uses labels.

---

### Post by drs305 on 2010-07-12
> **MountainX said:**
> Yes, it's in there. See here:
[http://www.gnu.org/software/grub/manual/grub.html#search](http://www.gnu.org/software/grub/manual/grub.html#search)

:-)

Another reason to review the new GNU Grub (2) Manual !

---

### Post by MountainX on 2010-07-12
> **drs305 said:**
> 
As far as how 30_op-prober is supposed to work, if you use the "true" statement or make it unexecutable, Grub2 will not search your other partitions for more Linux or other OS's. No 30_os-prober section will appear in /boot/grub/grub.cfg.

I couldn't tell if you had solved the 30_os-prober satisfactorily or not. If not, just elaborate on what you want to do.


When I use "true" (with or without quotes) the 30_os-prober section does still appear in grub.cfg. And if I just manually delete that section and do grub-install, the grub menu appears, which I don't want.

However, I decided not to work on the os-prober issue any longer. It isn't essential. 

What is essential is figuring out how to generate a grub.cfg that doesn't include UUID's **anywhere**. I posted that question in a separate thread. I think the moderators may get upset with me for posting that grub2-UUID question more than once. :oops:

---

### Post by drs305 on 2010-07-12
> **MountainX said:**
> What is essential is figuring out how to generate a grub.cfg that doesn't include UUID's **anywhere**. I posted that question in a separate thread. I think the moderators may get upset with me for posting that grub2-UUID question more than once. :oops:

In /etc/default/grub there is a line:
```

[COLOR="Red"]#[/COLOR]GRUB_DISABLE_LINUX_UUID=true

```
If you uncomment that line and update grub UUIDs will not be used in the "linux" line of the menu entries. 

It still appears in the "search" line; if you don't want the "search" line, you can remove it from grub.cfg by following the "Step 4" instructions in this post:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search")

---

### Post by MountainX on 2010-07-12
> **drs305 said:**
> 
It still appears in the "search" line; if you don't want the "search" line, you can remove it from grub.cfg by following the "Step 4" instructions in this post:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search")

Great! That's a helpful link. That's what I needed. Thanks.

---

### Post by MountainX on 2010-07-12
here are the modified sections from my new /usr/lib/grub/grub-mkconfig_lib

This is a bit of a hack because my label is hard-coded. But at least it will make my grub.cfg changes stick.

up top I added this line:
CUSTOM_LABEL=mylabel

  # If there's a valid filesystem label that GRUB is capable of identifying, use it;
  # otherwise set root as per value in device.map.
  echo "set root='`${grub_probe} --device ${device} --target=drive`'"
  #REMOVED if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
  echo "search --no-floppy --label ${CUSTOM_LABEL} --set root"
  #fi

If anyone wants to tell me how to do this without hard-coding my label, that would be great!

---

### Post by MountainX on 2010-07-12
looking a little more closely at this, I don't think my changes are enough.

It isn't clear to me how those edits will generate this line in grub.cfg:

```
linux	/boot/vmlinuz-2.6.32-21-generic root=LABEL=mylabel ro   quiet splash
```

How do I do that automatically (not editing grub.cfg)?

---

### Post by drs305 on 2010-07-13
MountainX,

If you want to get the label into your #10_linux section of grub.cfg, you can modify the /etc/grub.d/10_linux file. Read all the way through before doing this.

Two actions to take before running this:
a. Backup /etc/grub.d/10_linux
b. Test this from the grub menu before commiting to grub.cfg. From the grub menu, highlight your Linux selection, press "e" to get into the edit mode. Go to the "linux" line and type in exactly what you expect the new line to look like. It should be something like:
> linux	/boot/vmlinuz-2.6.32-23-generic root=label=mylabel ro   splash
Press CTRL-x to make sure it boots correctly. If it does, you can make the changes permanent in grub.cfg.

Find this section of /etc/grub.d/10_linux (approx line 95):
> 
  cat << EOF
	linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF


Preceed the line with your label information. These commands extract the label of the linux / partition and replaces the UUID or device name with the label option:
> 
[B][COLOR="DarkRed"]
auto_label="`e2label ${linux_root_device_thisversion}`"
linux_root_device_thisversion="label=${auto_label}"
[/COLOR][/B]
  cat << EOF
	linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF

This will produce a "linux" line of:
> 
linux	/boot/vmlinuz-2.6.32-23-generic root=label=[COLOR="DarkRed"]auto_label[/COLOR] ro   splash


One note: Grub still determines *what* the default partition is. This tweak merely changes the root device designation into a label.

---

### Post by MountainX on 2010-07-13
I cannot fully express my gratitude for your help with this! Thank you!

I will try it and report back. :)

BTW, I have already verified that my hand-edited menu stanza works. I edited grub.cfg and I've been booting up with it for a couple days. But I will proceed carefully, following your advice. (And I am also working on a test machine atm that contains no data.)

---

### Post by MountainX on 2010-07-13
It looks like this approach works :)
I'm still testing, but so far so good. I had to make a few minor changes in the executable portion. I'll post that when I'm done. (It's on another machine, so I can't post it now.)

It looks like we can also edit grub-mkconfig_lib to generate a search line similar to this using your suggestion above

> echo "search --no-floppy --label ${auto_label} --set root"

I think I have it working...

---

### Post by MountainX on 2010-07-13
Thanks drs305. It works!

It would be great if the moderators could split this thread starting at post #8. At that point the conversation turned to using labels with grub2. This is an important question I think. I have seen a lot of people asking about it and I have not found a good solution yet. But the approach drs305 suggested does work. So it would be nice to have it in a new thread with a proper title that reflects grub2 and labels.

Let me summarize what I did. I hope others comment in regard to whether all these steps are necessary and accurate. But this IS WORKING for me.

1. changed /etc/defaults/grub
uncommented this line and used quotes around true:
```
GRUB_DISABLE_LINUX_UUID="true"
```

2. changed /etc/grub.d/10_linux as follows:
```
auto_label="`e2label ${GRUB_DEVICE_BOOT} 2>/dev/null`"
  linux_root_device_thisversion="LABEL=${auto_label}"
  cat << EOF
	linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
EOF
```

3. changed /usr/lib/grub/grub-mkconfig_lib as follows. I know this code could be improved by including it in a proper conditional, but I didn't know how to do that. So it just executes always.
```
  # If there's a filesystem UUID that GRUB is capable of identifying, use it;
  # otherwise set root as per value in device.map.
  echo "set root='`${grub_probe} --device ${device} --target=drive`'"
  #if fs_label="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
    #echo "search --no-floppy --fs-uuid --set ${fs_uuid}"
  #fi
auto_label="`e2label ${device} 2>/dev/null`"
echo "search --no-floppy --label ${auto_label} --set root"
```

Those changes generate perfect (as far as I'm concerned) stanzas in grub.cfg. And my test machine boots as expected.

```
menuentry "Linux Mint 9, 2.6.32-21-generic (/dev/sda1) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --label my_label --set root
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=LABEL=my_label ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
```

my /etc/fstab also uses labels. Here's an example (although this exact example is from another machine)

```
LABEL=home_volume       /home   ext4    noatime,acl,user_xattr 1 2
LABEL=root_volume       /       ext4    noatime,acl,user_xattr 1 1
LABEL=swap_volume       swap    swap    defaults 0 0
LABEL=boot_volume       /boot   ext2    noatime,acl 1 2
```

---

### Post by drs305 on 2010-07-13
> **MountainX said:**
> Thanks drs305. It works!

It would be great if the moderators could split this thread starting at post #8. 

MountainX,

As you can see, I've split the thread and created this new one specifically for your "label" issues.

You may need to resubscribe to your original post:
[http://ubuntuforums.org/showthread.php?t=1529799]("http://ubuntuforums.org/showthread.php?t=1529799")

---

### Post by hotdoog on 2012-10-01
:mad: This is exactly why I hate GRUB2. This is 10x the hack required for GRUB1 to do the same thing. I don't understand why it has to be this complicated. And I fail to see how a bunch of config files spread all over the place and requiring programs to run with them (not just a simple text edit to menu.1st) is an improvement. Also, no longer is all the important config contained within /boot like it SHOULD be.

UUID is a hack in itself and shouldn't be the only easy option.

Thank you MountainX for this excellent summary.

---

