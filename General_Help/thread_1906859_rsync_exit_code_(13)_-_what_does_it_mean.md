---
title: "rsync exit code (13) - what does it mean?"
date: 2012-01-10
forum: General Help
---

### Post by woodyg on 2012-01-10
I get this rsync error code 13 which I can't get my head around. Any website (e.g. [this one]("http://wpkg.org/Rsync_exit_codes")) mentioning these exit codes gives the same "explanation", which is:

> Errors with program diagnosticsWhat does this mean?

---

### Post by dargaud on 2012-01-10
Didn't you get an error message at the same time ? Have you tried with -v, -vv, -vvv ?

---

### Post by woodyg on 2012-01-10
I didn't know about -vvv. I am normally using LuckyBackup in order to escape the command line... Using -vvv It does seem to give me a clue. The output is

```
m-xubuntu@mxubuntu-ThinkPad-Edge:~$ rsync -vvv -h --progress --stats -r -tgo -p -l -D --update --delete-after /home/m-xubuntu/Maj/testfolder/ /media/remote_lubuntu/remote_test_folder/
building file list ... 
[sender] make_file(.,*,0)
[sender] make_file(file3,*,2)
[sender] make_file(file2.XLS,*,2)
[sender] make_file(file1.pdf,*,2)
4 files to consider
send_file_list done
send_files starting
server_recv(2) starting pid=2876
received 4 names
recv_file_list done
get_local_name count=4 /media/remote_lubuntu/remote_test_folder/
generator starting pid=2876
delta-transmission disabled for local transfer or --whole-file
recv_generator(.,0)
send_files(0, /home/m-xubuntu/Maj/testfolder/.)
./
**[COLOR=Red]set gid of . from 1002 to 1000[/COLOR]**
rsync: chgrp "/media/remote_lubuntu/remote_test_folder/." failed: Permission denied (13)
recv_files(4) starting
recv_generator(file1.pdf,1)
**[COLOR=Red]set gid of file1.pdf from 1002 to 1000[/COLOR]**
rsync: chgrp "/media/remote_lubuntu/remote_test_folder/file1.pdf" failed: Permission denied (13)
send_files(1, /home/m-xubuntu/Maj/testfolder/file1.pdf)
recv_generator(file2.XLS,2)
**[COLOR=Red]set gid of file2.XLS from 1002 to 1000[/COLOR]**
recv_files(.)
recv_files(file1.pdf)
rsync: chgrp "/media/remote_lubuntu/remote_test_folder/file2.XLS" failed: Permission denied (13)
send_files(2, /home/m-xubuntu/Maj/testfolder/file2.XLS)
recv_generator(file3,3)
**[COLOR=Red]set gid of file3 from 1002 to 1000[/COLOR]**
recv_files(file2.XLS)
rsync: chgrp "/media/remote_lubuntu/remote_test_folder/file3" failed: Permission denied (13)
send_files(3, /home/m-xubuntu/Maj/testfolder/file3)
send_files phase=1
generate_files phase=1
recv_files(file3)
recv_files phase=1
generate_files phase=2
send_files phase=2
send files finished
total: matches=0  hash_hits=0  false_alarms=0 data=0

rsync[2875] (sender) heap statistics:
  arena:         135168   (bytes from sbrk)
  ordblks:            1   (chunks not in use)
  smblks:             0
  hblks:              2   (chunks from mmap)
  hblkhd:        401408   (bytes from mmap)
  allmem:        536576   (bytes from sbrk + mmap)
  usmblks:            0
  fsmblks:            0
  uordblks:       56192   (bytes used)
  fordblks:       78976   (bytes free)
  keepcost:       78976   (bytes in releasable chunk)
recv_files phase=2
generate_files phase=3
recv_files finished

rsync[2877] (server receiver) heap statistics:
  arena:         135168   (bytes from sbrk)
  ordblks:            1   (chunks not in use)
  smblks:             0
  hblks:              2   (chunks from mmap)
  hblkhd:        401408   (bytes from mmap)
  allmem:        536576   (bytes from sbrk + mmap)
  usmblks:            0
  fsmblks:            0
  uordblks:       23296   (bytes used)
  fordblks:      111872   (bytes free)
  keepcost:      111872   (bytes in releasable chunk)
deleting in .
delete_in_dir(.)
[generator] make_file(file1.pdf,*,2)
[generator] make_file(file3,*,2)
[generator] make_file(file2.XLS,*,2)
generate_files finished

rsync[2876] (server generator) heap statistics:
  arena:         135168   (bytes from sbrk)
  ordblks:            2   (chunks not in use)
  smblks:             3
  hblks:              2   (chunks from mmap)
  hblkhd:        401408   (bytes from mmap)
  allmem:        536576   (bytes from sbrk + mmap)
  usmblks:            0
  fsmblks:          144
  uordblks:       23352   (bytes used)
  fordblks:      111816   (bytes free)
  keepcost:      111648   (bytes in releasable chunk)

Number of files: 4
Number of files transferred: 0
Total file size: 2.02M bytes
Total transferred file size: 0 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 109
File list generation time: 0.001 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 128
Total bytes received: 24

sent 128 bytes  received 24 bytes  304.00 bytes/sec
total size is 2.02M  speedup is 13270.95
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.8]
[sender] _exit_cleanup(code=0, file=main.c, line=1070): about to call exit(23)
m-xubuntu@mxubuntu-ThinkPad-Edge:~$ 
```Why would it try to change gid?

---

### Post by dargaud on 2012-01-10
It's some kind of permission problem.
First check the permissions and username on the destination folder.
Then either do a ```
chown -R $(whoami) /media/remote_lubuntu/remote_test_folder
```
or run rsync as root with the -o option (part of -a):
```
sudo rsync -xavHl --delete
```
And always remember to add -n while testing.

---

### Post by woodyg on 2012-01-10
Using sudo gave similar problem:

```
set uid of file3 from 1002 to 1000 recv_files(file2.XLS) set gid of file3 from 1002 to 1000 rsync: chown "/media/remote_lubuntu/remote_test_folder/file3" failed: Permission denied (13)

```

In the end I simply removed the -g and the -o flags, which removed any error messages.

---

### Post by woodyg on 2012-01-10
> And always remember to add -n while testing.by the way, what does -n do?

---

### Post by CharlesA on 2012-01-10
> **woodyg said:**
> by the way, what does -n do?

Dry-run.

[http://www.manpagez.com/man/1/rsync/](http://www.manpagez.com/man/1/rsync/)

---

