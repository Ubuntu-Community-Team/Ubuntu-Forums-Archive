---
title: "Precompilation/Compilation/Linking with gcc [Embedded SQL]"
date: 2010-05-05
forum: General Help
---

### Post by TheSkid on 2010-05-05
Hello,

in my study we have the assignment to build a sql-application based on c.
i've created a file with some commands like that:
```

//  Begin DECLARE SECTION
EXEC SQL BEGIN DECLARE SECTION;

VARCHAR gUsername[NAME_LEN];        //  Required for Connection to MySQL-Database
VARCHAR gPassword[PSW_LEN];

//...

    printf("\nConnect to database ... please wait");
    EXEC SQL CONNECT :gUsername IDENTIFIED BY :gPassword;
    printf("\nSuccessfully connected to database ...");
    printf("\nLogged in with alias: %s\n", gUsername.arr);

```If i want to precompile/compile this file i got the following errors:
```

GebaeudeCleaner.c:33: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘SQL’
GebaeudeCleaner.c:38: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gUsername’
GebaeudeCleaner.c:39: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gPassword’
GebaeudeCleaner.c:59: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘SQL’
GebaeudeCleaner.c:62: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘SQL’
GebaeudeCleaner.c: In function ‘sqlError’:
GebaeudeCleaner.c:100: error: ‘EXEC’ undeclared (first use in this function)
GebaeudeCleaner.c:100: error: (Each undeclared identifier is reported only once
GebaeudeCleaner.c:100: error: for each function it appears in.)
GebaeudeCleaner.c:100: error: expected ‘;’ before ‘SQL’
GebaeudeCleaner.c:108: warning: unknown conversion type character ‘,’ in format
GebaeudeCleaner.c:111: error: expected ‘;’ before ‘SQL’
GebaeudeCleaner.c:112: warning: incompatible implicit declaration of built-in function ‘exit’
GebaeudeCleaner.c: In function ‘login’:
GebaeudeCleaner.c:122: error: ‘gUsername’ undeclared (first use in this function)
GebaeudeCleaner.c:124: error: ‘gUserame’ undeclared (first use in this function)
GebaeudeCleaner.c:125: warning: incompatible implicit declaration of built-in function ‘exit’
GebaeudeCleaner.c:130: error: ‘gPassword’ undeclared (first use in this function)
GebaeudeCleaner.c:130: error: ‘PWD_LEN’ undeclared (first use in this function)
GebaeudeCleaner.c:136: error: ‘EXEC’ undeclared (first use in this function)
GebaeudeCleaner.c:136: error: expected ‘;’ before ‘SL’
GebaeudeCleaner.c: In function ‘logout’:
GebaeudeCleaner.c:145: error: ‘EXEC’ undeclared (first use in this function)
GebaeudeCleaner.c:145: error: expected ‘;’ before ‘SQL’
GebaeudeCleaner.c: In function ‘connect’:
GebaeudeCleaner.c:152: error: ‘EXEC’ undeclared (first use in this function)
GebaeudeCleaner.c:152: error: expected ‘;’ before ‘SQL’
GebaeudeCleaner.c:154: error: ‘gUsername’ undeclared (first use in this function)

```But i dont know in this errors.
I installed mysql-server and set up a database (it works).
After that i installed the gcc compiler without any problems, but if i tried to precompile this file, i got these errors.

In my study we used the following commands:
```

Precompile: proc <file>
Compile: cc –c –o<file>.o <file>.c
Make: make <file>

```But we used ORACLE and not MYSQL.

Can someone tell me whats wrong with my program ?

Thank you for your help,
SkiD.

// EDIT: If i habe a simple program like that:
```

#include <iostream>

int main()
{
    std::cout << "Goodbye, badly World!\n";
    return 0;
}

```All works fine ...

---

