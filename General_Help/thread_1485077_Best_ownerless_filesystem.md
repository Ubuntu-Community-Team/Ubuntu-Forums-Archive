---
title: "Best ownerless filesystem?"
date: 2010-05-16
forum: General Help
---

### Post by beastrace91 on 2010-05-16
Howdy All,

So I currently have my external hard drive formatted to ext4 - however it is a HUGE pain to have to chown the driver every time I plug it in to a new system so I can delete/edit files on it. What is a good ownerless filesystem I could use for my external hard drive (other than fat32, I have some files on there > 4gigs) 

~Jeff

---

### Post by srs5694 on 2010-05-16
Under Linux, there's no such thing as an "ownerless" filesystem. The concepts of file ownership and permissions are so deeply embedded within Linux that they're forced upon filesystems, such as FAT, that don't support these features, via mount options.

If permissions are giving you problems, I recommend you read up a bit on file ownership and permissions. There *are* ways around the problems you're encountering. Pay particular attention to the umask value, which determines what permissions are given to new files when they're created. By setting lax permissions (0666 on files, 0777 on directories), you won't encounter such problems in the future. Try Googling topics such as "Linux file permissions" or "umask" to learn more about these topics; there are about a bazillion and one Web sites that cover this material.

---

### Post by beastrace91 on 2010-05-17
Meh. I guess I'll just leave it NTFS for now then. Working alright on Nix.

~Jeff

---

