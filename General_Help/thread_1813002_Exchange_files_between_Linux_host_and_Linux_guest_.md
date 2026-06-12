---
title: "Exchange files between Linux host and Linux guest - VirtualBox"
date: 2011-07-27
forum: General Help
---

### Post by le1 on 2011-07-27
Hey there,

After installing Linux Additions in guest OS (sudo sh ./VBoxLinuxAdditions.run) in order to exchange files between Linux Host and Linux Guest (Linux that runs inside VirtualBox on Linux host), you need to use this simple command:

sudo mount -t vboxsf <shared_folder_VB> <folder_on_guest_Linux>

--> where <shared_folder_VB> is the name of the folder you added in VirtualBox's 'Shared Folders' settings (host OS) and <folder_on_guest_Linux> is the name of the folder created on guest Linux (where you want to have files from host) e.g. /home/John/name_of_your_folder

That's it.

---

