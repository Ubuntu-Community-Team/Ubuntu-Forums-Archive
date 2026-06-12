---
title: "No memtest in Grub (and system crashes)"
date: 2011-10-10
forum: General Help
---

### Post by circuit_bent on 2011-10-10
Hello!

So I am currently trying to debug an issue with my ubuntu set-up. My machine hangs randomly, and I am unsure why. I suspect its an X issue...

To start debugging that, I wanted to perform a memtest, but for some reason memtest does not show up in my grub boot options. 20_memtest86+ is in /etc/grub.d , has the correct permissions (755) and /boot/memtest86+.bin exists. I have done update-grub and that did not fix the problem (it doesn't pull the memtest entry).

Not really sure what to do next to get memtest to show up. Any advice?

Here is my 20_memtest86+ file, just in case:

```
#!/bin/sh
set -e

if [ -f /usr/lib/grub/grub-mkconfig_lib ]; then
  . /usr/lib/grub/grub-mkconfig_lib
  LX=linux16
elif [ -f /usr/lib/grub/update-grub_lib ]; then
  . /usr/lib/grub/update-grub_lib
  LX=linux
else
  # no grub file, so we notify and exit gracefully
  echo "Cannot find grub config file, exiting." >&2
  exit 0
fi

# We can't cope with loop-mounted devices here.
case ${GRUB_DEVICE_BOOT} in
  /dev/loop/*|/dev/loop[0-9]) exit 0 ;;
esac

prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"

if test -e /boot/memtest86+.bin ; then
  MEMTESTPATH=$( make_system_path_relative_to_its_root "/boot/memtest86+.bin" )
  echo "Found memtest86+ image: $MEMTESTPATH" >&2
  cat << EOF
menuentry "Memory test (memtest86+)" {
EOF
  printf '%s\n' "${prepare_boot_cache}"
  cat << EOF
	$LX	$MEMTESTPATH
}
menuentry "Memory test (memtest86+, serial console 115200)" {
EOF
  printf '%s\n' "${prepare_boot_cache}"
  cat << EOF
	$LX	$MEMTESTPATH console=ttyS0,115200n8
}
EOF
fi

#if test -e /boot/memtest86+_multiboot.bin ; then
#  MEMTESTPATH=$( make_system_path_relative_to_its_root "/boot/memtest86+_multiboot.bin" )
#  echo "Found memtest86+ multiboot image: $MEMTESTPATH" >&2
#  cat << EOF
#menuentry "Memory test (memtest86+, experimental multiboot)" {
#EOF
#  printf '%s\n' "${prepare_boot_cache}"
#  cat << EOF
#	multiboot	$MEMTESTPATH
#}
#menuentry "Memory test (memtest86+, serial console 115200, experimental multiboot)" {
#EOF
#  printf '%s\n' "${prepare_boot_cache}"
#  cat << EOF
#	multiboot	$MEMTESTPATH console=ttyS0,115200n8
#}
#EOF
#fi
```

---

