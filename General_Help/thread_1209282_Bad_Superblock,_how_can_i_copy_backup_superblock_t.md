---
title: "Bad Superblock, how can i copy backup superblock to first superblock"
date: 2009-07-10
forum: General Help
---

### Post by shizow on 2009-07-10
Hi

i have a problem with an external USB drive which has ext2 filesystem.
It seems the first 2 superblocks are corrupt.

```

mke2fs 1.41.4 (27-Jan-2009)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
30531584 inodes, 122096582 blocks
6104829 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
3727 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
        102400000

```

When i run e2fsck -y -b 163840, it runs through but at the end it says:
Restarting e2fsck from the beginning
and then it gives out again
e2fsck 1.41.4 (27-Jan-2009)
e2fsck: Bad magic number in super-block while trying to open

i thought normally after finishing going through the whole disk it writes back the superblock from the backups?
How can i copy a backup superblock to the first superblock

---

### Post by Herman on 2009-07-10
I thought the command was 'e2fsck -b 163840', for restoring a superblock from a backup. I'm not sure if it's right to have the '-y' in there.

Try,
```
sudo e2fsck -b 163840
```and see if that will work any better.

---

### Post by shizow on 2009-07-10
> **Herman said:**
> I thought the command was 'e2fsck -b 163840', for restoring a superblock from a backup. I'm not sure if it's right to have the '-y' in there.

Try,
```
sudo e2fsck -b 163840
```and see if that will work any better.

Thanks, but if i do this e2fsck display the usage, so i think i need an extra option
-b only says to read from another superblock, it does not copy a backup superblock back to the first superblock.

---

### Post by Herman on 2009-07-10
> Thanks, but if i do this e2fsck display the usage, so i think i need an extra optionWhat partition contains the file system you are your working on?
```
sudo e2fsck -b 163840 /dev/sda2
```

---

