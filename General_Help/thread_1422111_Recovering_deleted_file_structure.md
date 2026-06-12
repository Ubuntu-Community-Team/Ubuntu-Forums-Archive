---
title: "Recovering deleted file structure"
date: 2010-03-05
forum: General Help
---

### Post by uShafee on 2010-03-05
Last night i was trying to download an nvidia driver in synaptic. I lost connection during the download and the partially downloaded files got corrupted. After that every time i try, these files get loaded and at the end, when synaptic trys to install it, it gives an error. So i thought I 'd delete them and try again :O

Only i deleted more then i intended to. i deleted all files and folders under /var/cache/apt while trying to delete files under /var/cache/apt/archives/

Now when i try to download any package on synaptic it says the partial directory and lock file doesnt exist. So i manually created them and synaptic works. I am just concerned whether any other application might also misbehave. How do i restore the default directory structure and files in /var/cache/apt/ ?

---

