---
title: "large hidden directory?"
date: 2011-07-08
forum: General Help
---

### Post by daveli on 2011-07-08
Hi, can anyone explain what kind of directory is the one from the list below that uses up about 3Gb and is called ./ and if it is possible to see its content?
It was created automatically by a program that seemed to produce an error.


$ ls -la
total 3172933
drwxrwx--- 1 root plugdev 3248984064 2011-07-08 08:38 .
drwxrwx--- 1 root plugdev        168 2011-07-08 08:34 ..
drwxrwx--- 1 root plugdev      36864 2011-07-06 15:43 correct_pi_arg
-rwxrwx--- 1 root plugdev         95 2011-07-08 08:38 .directory
drwxrwx--- 1 root plugdev      12288 2011-06-06 13:14 s3
drwxrwx--- 1 root plugdev      12288 2011-06-03 08:03 s4
drwxrwx--- 1 root plugdev      12288 2011-06-01 13:39 s5
drwxrwx--- 1 root plugdev      12288 2011-06-01 16:15 s6
drwxrwx--- 1 root plugdev      12288 2011-06-02 16:11 s7


Thanks

Dave

---

### Post by Habitual on 2011-07-08
The names of these two directories are the single dot "." and the double dot ".." and they represent the current and the parent directories, respectively. 

Can you elaborate on "It was created automatically by a program that seemed to produce an error." please?

Please clarify.

[http://140.120.7.20/LinuxKernel/LinuxKernel/node20.html](http://140.120.7.20/LinuxKernel/LinuxKernel/node20.html)

---

### Post by daveli on 2011-07-11
Dear Habitual,

sorry about being too short on explanations. Seeing your answer I am thinking I got the wrong impression about these two directories. I run a script (bedtools) on a large dataset and as I usually just print 'ls' most of the time I had forgotten about these two directories. When checking on the dir using 'ls -la' I suddenly saw them occupying large amounts of memory and thought they had been created by this program. It is just that the output of the program is also large and thus the size of the current directory. What I don't understand then is why the parent directory '..' is not at least as large as the current '.' dir.

Thanks,

Dave

---

### Post by grahammechanical on 2011-07-11
Hi,

> What I don't understand then is why the parent directory '..' is not at least as large as the current '.' dir.I guess it is because the command is only showing the size of each directory on its own and not the accumulated size of all the directories under a directory.

Regards.

---

### Post by psusi on 2011-07-11
The size field of a directory is meaningless.  To find out how much space all of the files in a directory ( and sub directories ) are using, use the du command.

---

