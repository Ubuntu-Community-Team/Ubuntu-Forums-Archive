---
title: "Variable media size and &quot;missing&quot; folders"
date: 2011-04-17
forum: General Help
---

### Post by flight243 on 2011-04-17
Hi forum!

Recently I installed Ubuntu Lucid on my sister's laptop and apparently everything was working fine but she was complaining of some subfolders and files not showing in the file manager and we've noticed a strange behaviour when mounting removable media. So, here is the thing. 

1.- When inserting a cd or removable media, Ubuntu automatically mounts it and the file manager -Nautilus in my case- pops out showing the cd or partition contents, but it doesn't display all the visible files and folders. At first I thought it was a problem with Nautilus but then I switched to the terminal and it doesn't show the files either. In this case (a cd), the media size listed under Nautilus or via the *mount* command is around 475 MB of the real 686 MB burned in the cd.

2.- We extract the cd and insert it again. Ubuntu mounts the device as usual and this time some of the folders and files which were missing the first time appear, but the rest are still "gone". The volume size is 616 MB out of 686 MB which is the real size.

3.- We're back to step 2, with a different media size and so on... So far, we have not managed to display all the files and folders of the cd. However, using the same laptop running a Windows OS, everything is fine and all the contents are displayed.

This issue with not showing all files and folders occurs for all removable media, including NTFS and FAT partitions but here the volume size remain the same every time they are mounted. Just to clarify, this happens to VISIBLE files and folders, it's not a matter of hidden files and pressing Ctrl+H in Nautilus or something, which is by far the only related issue I found in this forum.

To make sure it's not a bug I've tried a bunch of cd's on my desktop which is also running 10.04 LTS but here everything went fine and all the contents were displayed.

Have you experienced this strange behaviour? Is there a solution? Any help is appreciated.

Thanks in advance!

---

