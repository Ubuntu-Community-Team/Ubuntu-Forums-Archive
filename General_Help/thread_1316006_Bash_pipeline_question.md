---
title: "Bash pipeline question"
date: 2009-11-05
forum: General Help
---

### Post by jtauke on 2009-11-05
Hi, I'm currently taking a class on linux operating systems and I've come across this question on one of our homework assignments


Write a command (pipeline) to display files 15 through 20 in subdirectory /bin, with numbers by the
file names. (You may assume there are more than 20 files.) Sample output:
     neo$ #  Magic command here
        15   chown
        16   cp
        17   cpio
        18   csh
        19   cut
        20   date
     neo$

I've gotten as far as the command "ls /bin | cat -n"  this gives me a list of all files in /bin on seperate lines with numbers denoting the line of output.

My question is how would I filter out the first 14 lines and the last 21-(end of output) lines?

Thanks for any help guys

---

### Post by sisco311 on 2009-11-05
```
man tail
man head
```

---

### Post by Giblet5 on 2009-11-05
> **sisco311 said:**
> ```
man tail
man head
```

+1

---

### Post by diesch on 2009-11-05
I'd use awk '/.../,/.../' instead.

---

### Post by jtauke on 2009-11-05
> **sisco311 said:**
> ```
man tail
man head
```

](*,)...wow I feel dumb now, I completely forgot about head and tail.

@diesch we won't go over awk, sed, and grep until next week so I think their looking for us to use head and tail

Completed command is : ls /bin | cat -n | head -n 20 | tail -n 6

Thanks for jogging my memory guys

---

### Post by Giblet5 on 2009-11-05
> **diesch said:**
> I'd use awk '/.../,/.../' instead.

You owe me a keyboard. Mine is covered with coffee.

---

