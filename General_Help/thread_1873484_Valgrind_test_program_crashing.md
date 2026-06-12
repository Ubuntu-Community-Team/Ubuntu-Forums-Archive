---
title: "Valgrind test program crashing"
date: 2011-11-01
forum: General Help
---

### Post by newport_j on 2011-11-01
I tried running my program and this is the output that I got:
 
```

[FONT=Times New Roman][SIZE=3]james@james-Precision-WorkStation-T7500:~/Desktop/WEGtestOpt$ valgrind --tool=memcheck  ./grab_gcc_debug[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]valgrind: mmap(0x8062000, 858030080) failed in UME with error 22 (Invalid argument).[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]valgrind: this can be caused by executables with very large text, data or bss segments.[/SIZE][/FONT]
 

```
 
Yes, my program is very big and I know that valgrind (whatever tool is used) has to add a lot of memory and such a load could crash the program. I just would very much like to use valgrind on my program. Is there a workaround? Could this program run if I changed an environmental variable?
 
I would appreciate any help in getting valgrind to run my very memory intensive program.
 
Newport_j

---

