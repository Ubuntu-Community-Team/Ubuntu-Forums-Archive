---
title: "Can't copy Folders, only files"
date: 2011-09-02
forum: General Help
---

### Post by waylow on 2011-09-02
Hey guys, I'm having problems copying folders.

I'm trying to move files from my older laptop (OSX) and my external drive (apple time capsule) to my second internal HDD in my ubuntu (11.04) box.

If I try to copy any folders - it does not work
I get and error copying the files - No such file or directory.

But I can copy any files in the folders.
so the only way for me to copy all my files is to manually create the folders on my HDD and then drag the files across
(obviously this seems like more work than is necessary)

I don't think it is a permissions problem as it says I am the owner and can read/write all the files and folders.

has anyone come across this issue, or know how I can fix it
the drive is formatted HPFS/NTFS (0x07)
and I'm looking at the disk utility and it says
"The partition is misaligned by 512 bytes. This may result in very poor performance. Repartitioning is suggested"

maybe this is the cause - I'm unsure on how to resolve that too

---

### Post by waylow on 2011-09-03
OK I I have solved the issue

it does seem to be a problem caused by the misalignment

here is how I fixed the drive

I backup it up
reformatted with Gparted
selected primary drive
NTFS
and alignment was set to NONE

now I can drag folders as well as files

---

### Post by waylow on 2011-09-06
It seems I spoke too soon.

it is only partially fixed


-I can drop 'n drag files/folders to any Internal HDD on my ubuntu box
-I can drag 'n drag files/folders from any MacOSX network computer to any HDD in my ubuntu box and vice versa

-I **can not** drag folders from my Apple Time Capsule (1TB 1st generation) to any HDD in ubuntu
(I can only drag files)


I have given up for now as I can work around this for the moment (copy files to a MAC and then drag from there) but I will post a solution if I find one

but hey - at least my HDD is working at full speed now

---

