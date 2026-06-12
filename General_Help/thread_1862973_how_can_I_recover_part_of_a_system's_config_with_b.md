---
title: "how can I recover part of a system's config with bash tools"
date: 2011-10-17
forum: General Help
---

### Post by HotForLinux on 2011-10-17
I want to use the bash in my Ubuntu and an ssh connection to recover part of the previous configuration of another Linux system. I have two versions of the same small Linux system for the same PC. One is Linux-A, which is the default configuration with a correct sound configuration, and the other is Linux-B, which has many further and desired configurations but the sound is misconfigured. So I want to copy as much as I can from A's sound configuration to B. I tried and copied several files from A to B and also deleted files in B whcih were not in A, hidden and not hidden, but still B's sound system is misconfigured and there's no sound.
Since there are many more sound files I want to run a more complex command or series of commands to do this task.

The basic idea would be to delete all the files with names "*sound*" or "*alsa*" in B and copy all the files with those names from A to B. There are normal files and hidden files in many different directories and maybe internal links. I would like to save all those files from A in a tar ball, zip file or similar, and then extract them in B. I know rsync, find and cp are good tools for that But I don't know how to use them so that there are no broken links and to make the needed directories when copying the files.

Is there anyone willing to help me?

---

### Post by papibe on 2011-10-18
Unless the computer are identical (hardware and software), I would recommend creating a thread specifically to solve Linux-B's audio problems.

Just a thought,
Regards.

---

### Post by HotForLinux on 2011-11-06
> **papibe said:**
> Unless the computer are identical (hardware and software), I would recommend creating a thread specifically to solve Linux-B's audio problems.

Just a thought,
Regards.

It is for the same machine. That's why I wrote: "I have two versions of the same small Linux system for the same PC"

Actually Linux-A and Linux B are the same version but two different installations. I want only the sound config of one system and the rest of the configs of the other one.

I tried finding all files with  "alsa", "sound" in their paths and copying them to the other install but it didn't work. Maybe I didn't do it ok

---

