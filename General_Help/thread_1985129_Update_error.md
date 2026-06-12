---
title: "Update error"
date: 2012-05-22
forum: General Help
---

### Post by Hungry Man on 2012-05-22
```
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-proposed_main_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-proposed_universe_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-proposed_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-proposed_universe_binary-i386_Packages  Hash Sum mismatch

```

---

### Post by synapsys on 2012-05-22
How many NICs do you have?

When was the last time you ran a file system check?

---

### Post by Hungry Man on 2012-05-22
I have no idea what NIC is. Never I guess.

---

### Post by cortman on 2012-05-22
Hi Hungry Man

Have you tried running

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

??

---

### Post by Hungry Man on 2012-05-23
That seems to have fixed it.

What exactly did that do?

---

### Post by plucky on 2012-05-23
> **Hungry Man said:**
> That seems to have fixed it.

What exactly did that do?

It deleted all the .list files in the /var/lib/apt/lists/ directory and the reloaded them from the repositories again with the "sudo apt-get update" command.

They are just index files from the repositories.

Good Luck

---

