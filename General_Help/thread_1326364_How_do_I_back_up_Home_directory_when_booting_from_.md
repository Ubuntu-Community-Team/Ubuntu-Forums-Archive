---
title: "How do I back up Home directory when booting from CD?"
date: 2009-11-14
forum: General Help
---

### Post by litlfrog on 2009-11-14
As stated in another thread today, my hard drive will not boot up today. I've booted from a live CD and can see all the files in my home directory. When I try to copy them over to an external drive however, I get a "permission denied" error. I tried using sudo to open Nautilus, but I still don't have permissions to copy my Home directory and don't know how to change that. I know there's a way to get permission to copy those files when booting from a CD, but after looking for half an hour I don't understand what commands I'm supposed to use (though I suspect "chmod" will come in there somewhere).

---

### Post by arnab_das on 2009-11-14
> **litlfrog said:**
> As stated in another thread today, my hard drive will not boot up today. I've booted from a live CD and can see all the files in my home directory. When I try to copy them over to an external drive however, I get a "permission denied" error. I tried using sudo to open Nautilus, but I still don't have permissions to copy my Home directory and don't know how to change that. I know there's a way to get permission to copy those files when booting from a CD, but after looking for half an hour I don't understand what commands I'm supposed to use (though I suspect "chmod" will come in there somewhere).

i suggest you use jaunty live cd. log in as root and copy the entire thing. btw, you could burn the files on dvds.
also, instead of trying to copy the entire home directory, try selecting all its contents instead.

---

### Post by litlfrog on 2009-11-14
I got most of the files off that way, but I'd really like to copy the .mozilla and .mozilla-thunderbird directories. Even logging in as root on the Live CD I still don't have permissions to copy those folders from the hard drive.

---

