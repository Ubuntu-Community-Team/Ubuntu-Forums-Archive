---
title: "C code to run Hamachi over ssh help"
date: 2011-02-10
forum: General Help
---

### Post by ac90b671 on 2011-02-10
So I'm trying to make a program of sorts, although it's more like a script. 
```
        
        if(argc == 1){
                system("sudo hamachi list");
                char host[30], user[30];
                printf("Target Address: ");
                scanf("%s", &host);
                printf("Target Username: ");
                scanf("%s", &user);
                char combine[80];
                strncat(combine, "ssh ", strlen("ssh "));
                strncat(combine, user, strlen(user));
                strncat(combine, "@", strlen("@"));
                strncat(combine, host, strlen(host));
                system(combine);
        }

```

My problem is when I run it, I get this output.

```

user@computer:~/Source$ ./a.out 
[sudo] password for user: 
 * [050-671-289]  network                      
     * 000-000-000   Computer A                       aaa.aaa.aaa.aaa  direct      UDP  xxx.xxx.xxx.xxx:xxxxx
     * 000-000-001   Computer B                   xxx.xxx.xxx.xxx  direct      UDP  xxx.xxx.xxx.xxx:xxxxx
     * 000-000-002   Computer C                      xxx.xxx.xxx.xxx   direct      UDP  xxx.xxx.xxx.xxx:xxxxx
Target Address: aaa.aaa.aaa.aaa
Target Username: user
**sh: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;ssh: not found**


```

I imagine it's something wrong with my strncat usage, but I can't figure out what. Help would be greatly appreciated, thanks in advance.

---

