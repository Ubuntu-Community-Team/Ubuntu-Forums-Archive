---
title: "Edit fstab from recovery shell?"
date: 2009-12-03
forum: General Help
---

### Post by HinKraka on 2009-12-03
**[COLOR="DarkRed"]PROBLEM SOLVED![/COLOR]**

After running Windows XP for a while I recently went back to Ubuntu (haven't used it for about a year). My disc has 3 partitions (one is a swap) and I hadn't fixed so my larger (for storage) disc was automatically mounted on startup. I followed an online "how to" and apparently I missed something. I guess I have written the filesystem wrong, since I haven't wiped and changed filesystem on that partition since Windows.

Well, I can't know for sure since when I restart my laptop I just don't get my GUI to start. I get this message when Ubuntu is loading:
One of more of the mounts listed in /etc/fstab cannot yet be mounted:
/:waiting for /dev/disk/by-uuid/c590c05f-8fdd-4fa9-8348b3419a36/tmp:waiting for (null)
#: waiting for du
/media/Mediadisk: waiting for /dev/sda5
press ESC to enter recovery shell.

Here I get most of my suspicions confirmed. So I press esc and want to enter fstab to correct my error.

when I write sudo gedit /etc/fstab I get this message:
Gtk-WARNING **: cannot open display:

It is here I am stuck. I have googled my *** of and cannot find a way to edit fstab without a GUI. Please help me here.

I have the most recent version of Ubuntu.

---

### Post by RiceMonster on 2009-12-03
```
sudo nano /etc/fstab
```

---

### Post by HinKraka on 2009-12-03
Thanks alot!

and not surprisingly this ntfs-partition was defined as ext3 because I didn't change that from my copy+paste changes.

The problem I have now is that when I try to save the changed file it says "error writing /etc/fstab:Read Only Filesystem"

Even though I entered with sudo. It did not ask me for password though. Any way I can bypass this? I mean if I can comment it out I can get in and edit everything through the GUI.

Thanks in advance.

---

### Post by Some Penguin on 2009-12-03
It's telling you that you can't write, because the filesystem was mounted read-only.  Logically, you want to remount it with writes enabled, if you want to write.

mount -o remount,rw  <your_root_partition such as /dev/sda#> /

---

### Post by HinKraka on 2009-12-03
When I do, it says [mntent]: line 1 in /etc/fstab is bad

I haven't edited that part of fstab at all, so I am all confused now. Do I have to edit fstab to be able to remount my root so I can edit fstab? edit: apparently I have misplaced a couple of letters in there... damn me and my clumsy fingers.

This is my fstab now:
du # /etc/fstab: static file system information
#
# <file system> <mount point> <type> <options> <dump> <pass>
     proc          /proc       proc   defaults    0     0
# /dev/sda7
UUID=c590c05f-8fdd-4fa9-b4f4-8348b3419a36 / ext3 relatime,erro$ 
# /dev/sda6
UUID=31463f5a-889b-4d20-a7bb-01076dfd0238 none swap sw $
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda5 /meda/Mediadisk ext3 [COLOR="Red"](here is where I went wrong)[/COLOR] defaults 0 2

the red is my own pointed out now... and the "du" in the start is apparently the bad in line 1

How on earth do I edit this if I can't reboot it in writable mode?

---

### Post by HinKraka on 2009-12-03
I got help from a friend (it is his "fault" I use anything even similar to a unix system).

Well I managed to do the remount, as long as I remounted /dev/sda7 into /. Then I could edit the fstab file and then I was home free!

Thanks all of you for your help in this =) :popcorn::KS

---

### Post by user024 on 2010-02-06
To just give my feedback,  I wanted to use the vi editor to change the fstab file but I couldn't, because of the read only problem.
I tried to remount the volume, but there was something wrong about what I did.
No luck either to copy my fstab.bak file back to fstab. The read only curse.

So, I tried the following and it actualy worked much better than I hoped:
During the GRUB listing I pressed "e" for editing the commands before booting and I changed the "ro" argument for the drive to rw.
Then, I pressed ctrl-x to boot.

I expected to confront the same "waiting to mount" error, but I didn't.
The system started as normally did.
I sudo gedit-ed the fstab file back to the original with a smile from one ear to another and rebooted.
The GRUB file was back to the original "ro" (read only) argument and I just came to register to the forum to write about it, since I 've read about your solution by my phone.

I should say I am using karmic koala with GRUB 1.97

---

