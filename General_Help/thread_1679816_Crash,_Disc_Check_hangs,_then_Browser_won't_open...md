---
title: "Crash, Disc Check hangs, then Browser won't open..."
date: 2011-02-01
forum: General Help
---

### Post by J Bratton on 2011-02-01
Running Maverick on my desktop. Had a strange happening sometime last night. I generally leave the computer on all the time. When I got up this morning, I saw that my computer had rebooted and it said that it wanted to check for disc errors and that there was a problem with /home

It checked until about 70%, at which point it stopped advancing for a half hour, so I did a hard reboot and choose "I"gnore when I got the message again.

The computer booted fine. The disc manager gui seemed to think my hard drive is fine, but I didn't do the full, slow check. My hard drive is about a month old.

When I opened "open office" there as a document to recover, indicating that the thing did in fact crash sometime last night.

The next odd thing- my "Opera" web browser doesn't open the browser. The command it is calling up is "/usr/bin/opera %U"
Doesn't do anything, nothing shows up as running in the status monitor.

Rebooting doesn't change anything with opera, and I still get the request to do a disc scan and to try to fix errors.

I uninstalled and reinstalled the latest version of opera.
I uninstalled that and installed an earlier version of opera.
Then, I reinstalled the latest version of opera.

In terminal, typing "opera" gives me the message:
Could not initialize Opera.

Typing "sudo opera" opens Opera. Using the icon to open opera still points to the same place, and still doesn't work.

So, here are my questions:
1- How do I get a logfile of the crash that happened last night?
2- How do I figure out if there is a problem with the /home folder or a problem otherwise with my hard disc? How do I fix that?
3- Where would I point the "opera" icon so it opens normally?
4- Is there any way to recover the information that I previously had in Opera, such as passwords? I used "my opera" to recover my latest bookmarks, but that doesn't save passwords. I'm thinking maybe those files are still around, even though I uninstalled and reinstalled opera.

Thanks! My wife is pregnant and the docs are going to induce labor this evening/tomorrow, so if I'm late expressing my appreciation for any help, that's why! Just trying to get the computer at least working OK before the brown stuff hits the fan when the baby comes...

---

### Post by TeoBigusGeekus on 2011-02-01
Opera doesn't open for you as a regular user but it opens when you call it with sudo.
This indicates that there is indeed something wrong with your /home folder where all your settings as a user (including opera settings) are stored.

Boot up with a live cd, open a terminal and fsck your /home partition:
sudo fsck /dev/sda3
Replace of course sda3 with the actual partition.

Leave it working for as long as it takes.

Good luck with your kid... father.

---

### Post by J Bratton on 2011-02-01
> **TeoBigusGeekus said:**
> Opera doesn't open for you as a regular user but it opens when you call it with sudo.
This indicates that there is indeed something wrong with your /home folder where all your settings as a user (including opera settings) are stored.

Boot up with a live cd, open a terminal and fsck your /home partition:
sudo fsck /dev/sda3
Replace of course sda3 with the actual partition.

Leave it working for as long as it takes.

Good luck with your kid... father.

Thanks, I'll give that a shot and see what happens!

---

### Post by J Bratton on 2011-02-01
> **TeoBigusGeekus said:**
> Opera doesn't open for you as a regular user but it opens when you call it with sudo.
This indicates that there is indeed something wrong with your /home folder where all your settings as a user (including opera settings) are stored.

Boot up with a live cd, open a terminal and fsck your /home partition:
sudo fsck /dev/sda3
Replace of course sda3 with the actual partition.

Leave it working for as long as it takes.

Good luck with your kid... father.

That fixed it. Weird. Not sure what happened, but after letting it fix the drive, things work fine, even the passwords and such are grabbed from where they originally were. I wonder if it has something to do with that partition being formatted as ext2 rather than ext4. 

At any rate, thanks very much for the help! Here's how the fix went:
```

ubuntu@ubuntu:~$ sudo fsck /dev/sdb1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/sdb1: clean, 216831/3055616 files, 1396622/12206848 blocks
ubuntu@ubuntu:~$ sudo fsck /dev/sdb2
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/sdb2 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Entry 'bookmarks.adr' in /john/.opera (9011366) has deleted/unused inode 9011693.  Clear<y>? yes

Entry 'link_queue_out_myopera.dat' in /john/.opera (9011366) has deleted/unused inode 9011751.  Clear<y>? yes

Entry 'autosave.win' in /john/.opera/sessions (9011423) has deleted/unused inode 9011628.  Clear<y>? yes

Entry 'opr02T4F.tmp' in /john/.opera/cache/g_007F (40747477) has deleted/unused inode 234438665.  Clear<y>? yes

Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  +18041884 -(18041887--18041888) +(18041904--18041911) -(18041913--18041914) -18041917 -(18041919--18041922) -18041925 +18041940 +(18041942--18041943) +(18041946--18041948) +(18041951--18041952) -(18041953--18041955) -(18041957--18041962) -(18041997--18041998) -(18042012--18042016) -(18042835--18042849) -(18042853--18042864) -(18042866--18042870) -(18042895--18042897) -18042900 -(18042904--18042905) -(18042909--18042910) -18042922 -(18042941--18042943) -(18042951--18042953) -18042958 -(18043027--18043029) -(18043042--18043049) -18043089 -(18043091--18043099) -18043101 -(18043103--18043105) -(18043110--18043112) -18047120 -18413572 -18425866 -(18425876--18425883) -(18425885--18425894) -(18425903--18425904) -(18425906--18425909) -18425924 -(18482110--18482127) -(18482137--18482145) -18482149 -18482151 -(18482508--18482516) -(18482526--18482530) -(18482593--18482599) -(112525941--112525943) -(112538756--112538783) -(358326272--358326279) -(468893726--468893729)
Fix<y>? yes

Free blocks count wrong for group #550 (10596, counted=10682).
Fix<y>? yes

Free blocks count wrong for group #561 (1, counted=2).
Fix<y>? yes

Free blocks count wrong for group #562 (27, counted=53).
Fix<y>? yes

Free blocks count wrong for group #564 (11, counted=61).
Fix<y>? yes

Free blocks count wrong for group #3434 (19296, counted=19327).
Fix<y>? yes

Free blocks count wrong for group #10935 (32165, counted=32173).
Fix<y>? yes

Free blocks count wrong for group #14309 (32214, counted=32218).
Fix<y>? yes

Free blocks count wrong (273455657, counted=273455863).
Fix<y>? yes

Inode bitmap differences:  -9011321 -9011628 -9011693 -9011751 -(9142278--9142323) -9191429 -9207821 -9207826 -9207839 -(56131585--56131603) -(56131619--56131630) -179159043 -234438665
Fix<y>? yes

Free inodes count wrong for group #550 (15166, counted=15170).
Fix<y>? yes

Free inodes count wrong for group #558 (16329, counted=16375).
Fix<y>? yes

Free inodes count wrong for group #561 (16374, counted=16375).
Fix<y>? yes

Free inodes count wrong for group #562 (16343, counted=16346).
Fix<y>? yes

Free inodes count wrong for group #3426 (16337, counted=16368).
Fix<y>? yes

Free inodes count wrong for group #10935 (16365, counted=16366).
Fix<y>? yes

Free inodes count wrong for group #14309 (16374, counted=16375).
Fix<y>? yes

Free inodes count wrong (237631670, counted=237631757).
Fix<y>? yes


/dev/sdb2: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sdb2: 50931/237682688 files (20.2% non-contiguous), 201885961/475341824 blocks
ubuntu@ubuntu:~$

```

---

