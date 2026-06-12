---
title: "Disk operations freeze system"
date: 2010-06-19
forum: General Help
---

### Post by Barafu Albino Cheetah on 2010-06-19
When I do some copying of files, or any background disk activity with file reading (transcoding a movie, uploading a big file to FTP, virus scanning) all computer becomes so slow, that I hardly can move my mouse, not to mention any productive use. 
I have SATA HDD, and Intel Quad CPU. I took measures to be sure it is not CPU or memory resource problem. Gentoo, Fedora, Windows don't freese that much on file reading. It is not a filesystem problem, or HDD, cuse I tried exactly this partition with other OSes. 
Nice has a minor effect, but is is not enough, and I can't always start Nautilus with another nice level when I want to copy a file. 
What can I do to lower the priority of disk operations globally, and make apps to share disk thoughtput equally, not the one to occupie the disk until it finishes?
My fstab
```
/dev/sda6 /               ext4    errors=remount-ro 0       1
```

---

### Post by dino99 on 2010-06-19
make some checking and cleaning:

are you using some "exotic" packages or some manual install ? be sure to use genuine ubuntu repo and trusted ppa if any

check that driver(s) is/are activated (system admin hardware driver)

clean the system with gconf-cleaner (yes to all) and bleachbit (as admin, but set prefs carefully)

any usefull errors into .xsession-errors and/or /var/log/ ?

sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by dcstar on 2010-06-19
> **Barafu Albino Cheetah said:**
> When I do some copying of files, or any background disk activity with file reading (transcoding a movie, uploading a big file to FTP, virus scanning) all computer becomes so slow, that I hardly can move my mouse, not to mention any productive use. 
I have SATA HDD, and Intel Quad CPU.
.........

Check the BIOS SATA settings, see if you can turn on AHCI.

---

### Post by Barafu Albino Cheetah on 2010-06-19
1,3 ) The mess is right from the installation. 
2) What do you mean? Jockey offers me only my Nvidia driver which is on, of cause. 
4) No, nothing catchy, except for lots of networking errors. (Local network designed upsidde down by some human and computer haters. )

---

### Post by Barafu Albino Cheetah on 2010-06-19
AHCI on. Turning off doesn't help. SATA Native Mode on. Turning off.. you know. 
No more HDD related setting.

---

### Post by Natanael on 2012-01-30
The same problem here (Kubuntu 11.10) on notebook. If I run any disk operation (operations on big file) I can't do anything till it ends, because computer slows dramatically. But it depends on program you use. I see system copy of file doesn't make problems. If i use program like DeVeDe - it freezes system, but not when converting file, only when it copies it.

In my BIOS there's no option AHCI, other suggestions from this thread doesn't work. Any ideas?

---

