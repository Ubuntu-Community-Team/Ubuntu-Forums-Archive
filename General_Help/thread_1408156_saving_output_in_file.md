---
title: "saving output in file"
date: 2010-02-16
forum: General Help
---

### Post by shariefbe on 2010-02-16
Hello,
  I am using system() command to save command output in txt file and i am storing in one character variable. for example
```

system("ls>output.txt");

```
but what should i do when i have to save another one command output in the same txt file continuously, for example
```

system("ls>output.txt");
system("lsmod>output.txt");

```
the output of these 2 commands should come in one txt file continously it should get over write.

---

### Post by Satoru-san on 2010-02-16
> **shariefbe said:**
> Hello,
  I am using system() command to save command output in txt file and i am storing in one character variable. for example
```

system("ls,>output.txt");

```but what should i do when i have to save another one command output in the same txt file continuously, for example
```

system("ls,>output.txt");
system("lsmod,>output.txt");

```the output of these 2 commands should come in one txt file continously it should get over write.


Looks like C++ 

for output redirection with no over write is like cout << "bla" you need to use >>

```

system("ls,>>output.txt");
system("lsmod,>>output.txt");

```

---

### Post by pbpersson on 2010-02-16
when  you want to append instead of overwrite you use >>

Therefore:

```
system("w,>a.txt");
system("ps,>>a.txt");
```

---

