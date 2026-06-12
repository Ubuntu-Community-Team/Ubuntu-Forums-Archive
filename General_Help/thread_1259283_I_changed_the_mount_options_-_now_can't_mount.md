---
title: "I changed the mount options - now can't mount"
date: 2009-09-06
forum: General Help
---

### Post by NoaHall on 2009-09-06
I changed the mount options on a NTFS disk yesterday, and now I can't mount it. It comes up with the error "Invalid mount options" How can I change the options? When I do mount via the terminal, it comes up with a error saying it's not a vaild NTFS disk.

Haha! The answer was strange, but simple. Mount it with Dolphin , then you can change the mount options with Nautilus. I couldn't do it from the command line though, as it didn't think I was telling the truth about the drive.

---

### Post by uncle-c on 2009-09-06
Any chance of the output of  "sudo fdisk -l" and the actual full command line syntax that you are using to mount the NTFS drive ?

UC

---

