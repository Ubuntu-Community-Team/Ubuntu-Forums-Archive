---
title: "Testing UMASK..."
date: 2011-02-21
forum: General Help
---

### Post by abhiram7 on 2011-02-21
Hi,

I am testing umask functionality on my ubuntu jaunty. Doesn't work!!

Here's what I have done.
1) Uncommented the umask value in ~/.profile file. umask is 022.
2) refreshed the bash with source ~/.bashrc.
3) touch test;
4) ls -l returns
   -rwxrwxrwx permission for test rather that -rwxr--r--.  
what am I missing here? any help please??

---

### Post by cjhabs on 2011-02-21
> **abhiram7 said:**
> Hi,

I am testing umask functionality on my ubuntu jaunty. Doesn't work!!

Here's what I have done.
1) Uncommented the umask value in ~/.profile file. umask is 022.
2) refreshed the bash with source ~/.bashrc.
3) touch test;
4) ls -l returns
   -rwxrwxrwx permission for test rather that -rwxr--r--.  
what am I missing here? any help please??

Run "umask" with no parameters to check what your umask is and compare it to the file permissions when you touch a new file. If you are touching an existing file, it will only update the time stamp, not the permissions.
You can change your umask right in the shell and test with touch. This will narrow down the issue to the umask command or your dot files - I suspect there is an issue with your dot file.

---

### Post by abhiram7 on 2011-02-21
Thanks for the reply..

umask returns 0022
touch command was used to create a new file test.
tried your suggestion. still no luck the ls -l returns the same permission(-rwxrwxrwx) for test file. I removed the test file and touched it again before testing.

assuming it was a problem with dot files, how can I set them right?..

---

### Post by cjhabs on 2011-02-21
> **abhiram7 said:**
> Thanks for the reply..

umask returns 0022
touch command was used to create a new file test.
tried your suggestion. still no luck the ls -l returns the same permission(-rwxrwxrwx) for test file. I removed the test file and touched it again before testing.

assuming it was a problem with dot files, how can I set them right?..

Your dot files are OK. When you create a new file it is by default not executable. Subtract the "x" from your perms and it will match the umask.
Create a folder and you will see that the permissions are as you would expect from the umask.

---

### Post by sisco311 on 2011-02-21
Are you trying to create the file on a FAT or NTFS partition?

FAT & NTFS partitions do not support Unix/Linux file ownership & permissions.

---

