---
title: "sudo question"
date: 2010-02-19
forum: General Help
---

### Post by hwttdz on 2010-02-19
If I run a command as 

user1 @ hostname > sudo -u user2 "command &"

then I log out of user1 does it kill the process of user2?  Also, on a somewhat unrelated note shouldn't I be able to enter either the admin password or the password of user2 to run this command? (behavior is asking for admin password, though it's a bit confusing because admin username/password is really the same as user1 username/password).

---

### Post by KeyserSoze93 on 2010-02-19
Yes, it does close the process when you close the shell. You may want to look into "nohup", which, when appended to ta command, makes it not "hang up" when you exit. (man nohup should give you some more information.)

If you want fuller control over resuming, you may want to try GNU screen.

```

ssh blah@system
screen
su user2 -c "my_command"

```

Then press CTRL-A and d

Now, you can exit.

When you ssh back in, run:

```

screen -x

```

And you'll resume where you left off.

For (a lot) more info, run "man screen"

---

### Post by hwttdz on 2010-02-19
So I tested it.  Yes it would close the process if the shell did close.  But sudo spawns a new shell for that user.  So when I "top -u user2 -b -n 1" I get 

```
top - 10:23:54 up 49 min,  2 users,  load average: 0.26, 0.27, 0.27
Tasks: 243 total,   2 running, 241 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.3%us,  1.0%sy, 18.6%ni, 78.7%id,  0.2%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   6125112k total,  1202040k used,  4923072k free,    49840k buffers
Swap:  1967952k total,        0k used,  1967952k free,   447088k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND       
 6932 folder    39  19 81712  40m 1880 S   81  0.7  23:09.85 FahCore_a1.exe
 6934 folder    39  19 78008  38m 1668 S   49  0.6  18:35.90 FahCore_a1.exe
 6935 folder    39  19 78276  38m 1680 S   49  0.6  18:31.72 FahCore_a1.exe
 6933 folder    39  19 77680  37m 1668 S   40  0.6  19:00.33 FahCore_a1.exe
 6922 folder    20   0 25936  512  388 S    0  0.0   0:00.09 fah6          
 6930 folder    20   0  4004  556  468 S    0  0.0   0:00.00 sh            
 6931 folder    20   0  8360  676  540 S    0  0.0   0:00.01 mpiexec
```

The significant one being 6930 (second to last, or the users shell).

---

