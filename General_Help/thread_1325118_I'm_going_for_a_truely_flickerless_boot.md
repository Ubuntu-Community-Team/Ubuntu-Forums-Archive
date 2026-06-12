---
title: "I'm going for a truely flickerless boot"
date: 2009-11-13
forum: General Help
---

### Post by AwesomeTux on 2009-11-13
So I've set grub to my resolution...
[I]
/boot/grub/grub.cfg[/I]
```
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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 1fb6502f-4aff-4ff4-a46f-2ab6ebac8a84
if loadfont /usr/share/grub/unicode.pf2 ; then
**set gfxmode=1280x1024**
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
```

And my usplash...

/etc/usplash.conf
```
# Usplash configuration file
[B]xres=1280
yres=1024[/B]

```

And of course my X.Org resolution, (we all know how to do that one) but I'm having trouble getting rid on the last flicker.

When my computer first boots, it shows my memory count, and which drives it's using, like normal. My problem is at this point the resolution is 640x480.

Is there any way to change is? BIOS? Jumpers?

Thanks

---

