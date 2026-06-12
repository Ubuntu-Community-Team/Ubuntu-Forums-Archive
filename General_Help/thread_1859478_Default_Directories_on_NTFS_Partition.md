---
title: "Default Directories on NTFS Partition?"
date: 2011-10-13
forum: General Help
---

### Post by mvillet on 2011-10-13
Just installed 11.10 on my laptop and everything has been working well by default; however, there's a tweak I'd like to make that I haven't been able to figure out.

I dual-boot with Windows, and I have a large NTFS partition on which I store all my data. I would like to have Ubuntu's default Documents, Music, etc. folders be on this drive (without making the whole drive my home directory - I want to keep all the dotfiles on my Ubuntu partition).

Editing ~/.config/user-dirs.dirs works temporarily, but the file is reset at reboot (despite its claim in the comments that "all local changes will be retained in the next run").

Currently, I have appropriately named symlinks in my home directory that point to corresponding folders on my NTFS partition; the partition is set to automount on boot (via adding a line to fstab). This mostly works, but in Nautilus, the folders appear under "Bookmarks" instead of under "Computer," and don't have the appropriate icons. Additionally, checking my ~/.config/user-dirs.dirs, the default directories that are supposed to be linked have instead been set to my home directory. (Changing /etc/xdg/user-dirs.defaults and setting them to e.g. ../../media/data/Documents has the same effect).

Is there any way to get around this and make folders on an NTFS partition behave identically to native Documents, Music, etc. folders? Is the issue perhaps that the NTFS partition isn't mounted early enough at boot so xdg-user-dirs can't see the drive - and if so, is there a workaround?

Any help would be greatly appreciated!

---

### Post by dcstar on 2011-10-14
> **mvillet said:**
> Just installed 11.10 on my laptop and everything has been working well by default; however, there's a tweak I'd like to make that I haven't been able to figure out.

I dual-boot with Windows, and I have a large NTFS partition on which I store all my data. I would like to have Ubuntu's default Documents, Music, etc. folders be on this drive (without making the whole drive my home directory - I want to keep all the dotfiles on my Ubuntu partition).

Editing ~/.config/user-dirs.dirs works temporarily, but the file is reset at reboot (despite its claim in the comments that "all local changes will be retained in the next run").
.......

NTFS does** not** support Linux filesystem requirements, it is a foreign filesystem that cannot be used for any Linux system folders (like /home).

A filename starting with "." is illegal on NTFS.

---

