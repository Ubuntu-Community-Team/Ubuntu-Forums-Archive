---
title: "Help in Linux C"
date: 2009-10-19
forum: General Help
---

### Post by supravat on 2009-10-19
please help me in the following...

#include<stdio.h>
#include<stdlib.h>

int main()
{
	char d[10];	

	printf("Enter the directory name : ");
	scanf("%s",d);

	system("./s1 d");
	
}

and the content of file s1 is :
mkdir $1;

in this program a directory named "d" is created...but I want to create the directory whose name was taken by the scanf() function...

Please help me....

---

### Post by bnvdarklord on 2009-10-19
Although i haven't really used the system command i suspect sth like this

system("./s1 " + d);

not sure if + can be used in c++ for strings though... try it and tell me...

---

### Post by Giblet5 on 2009-10-19
> **supravat said:**
> please help me in the following...

#include<stdio.h>
#include<stdlib.h>

int main()
{
	char d[10];	

	printf("Enter the directory name : ");
	scanf("%s",d);

	system("./s1 d");
	
}

and the content of file s1 is :
mkdir $1;

in this program a directory named "d" is created...but I want to create the directory whose name was taken by the scanf() function...

Please help me....

```

/* Fixed #1 */
#include<stdio.h>
#include<stdlib.h>

int main()
{
    char d[10];
    char cmd[32];

    printf("Enter the directory name : ");
    scanf("%s",d);

    /* Strip off trailing newline */
    while (d[strlen(d)-1] == '\n') d[strlen(d)-1] = '\0';

    /* Create the bundled command */
    sprintf(cmd, "./sh %s", d);

    system(cmd);
}
```


> **bnvdarklord said:**
> Although i haven't really used the system command i suspect sth like this

system("./s1 " + d);

not sure if + can be used in c++ for strings though... try it and tell me...

That's C++.

OP said C and that won't work under C.

---

