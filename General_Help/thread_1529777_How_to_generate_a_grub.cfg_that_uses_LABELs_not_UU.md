---
title: "How to generate a grub.cfg that uses LABELs not UUID's?"
date: 2010-07-12
forum: General Help
---

### Post by MountainX on 2010-07-12
I want to generate a grub.conf that will search for my /dev/sda1 based on the filesystem label, not the UUID.

I did change /etc/default/grub to so that GRUB_DISABLE_LINUX_UUID="true" and I regenerated grub.cfg.

But I want to go one step further and change the search statements. I notice they still reference the old UUID. I also know grub2 can search by label. Can anyone tell me how to do this? Thanks.

EDIT:

I could use some help understanding this page:
[http://www.gnu.org/software/grub/manual/grub.html#search](http://www.gnu.org/software/grub/manual/grub.html#search)

> 12.3.28 search

&#8212; Command: search [--file|--label|--fs-uuid] [--set var] [--no-floppy] name
Search devices by file (-f, --file), filesystem label (-l, --label), or filesystem UUID (-u, --fs-uuid).

If the --set option is used, the first device found is set as the value of environment variable var. The default variable is &#8216;root&#8217;.

The --no-floppy option prevents searching floppy devices, which can be slow.

The &#8216;search.file&#8217;, &#8216;search.fs_label&#8217;, and &#8216;search.fs_uuid&#8217; commands are aliases for &#8216;search --file&#8217;, &#8216;search --label&#8217;, and &#8216;search --fs-uuid&#8217; respectively.

I'd like my grub.cfg to contain statements similar to this:

```

search --no-floppy --label MyLabel --set
linux /boot/vmlinuz-2.6.3x-xx-generic root=label=MyLabel ro quiet splash
initrd /boot/initrd.img-2.6.3x-xx-generic
```

**Assuming that's the right syntax**, how do I make grub2 generate **label-based** menu entries like that?

---

### Post by MountainX on 2010-07-12
Linux Mint **ROCKS**!!!

See answer here:
[http://forums.linuxmint.com/viewtopic.php?f=46&t=38599](http://forums.linuxmint.com/viewtopic.php?f=46&t=38599)

and support here:
[http://wiki.archlinux.org/index.php/GRUB2](http://wiki.archlinux.org/index.php/GRUB2)

---

