---
title: "Where is  O_SHLOCK and O_EXLOCK defined?"
date: 2010-11-17
forum: General Help
---

### Post by alexchen on 2010-11-17
I am trying to use 'open()' with some file control flags. According to Ubuntu's manual of 'open()': 
 
_int_
**open**(_const_ _char_ _*path_, _int_ _flags_, _..._);
 
......
The flags specified are formed by _or_’ing the following values
 
O_RDONLY open for reading only
O_WRONLY open for writing only
O_RDWR open for reading and writing
O_NONBLOCK do not block on open
O_APPEND append on each write
O_CREAT create file if it does not exist
O_TRUNC truncate size to 0
O_EXCL error if create and file exists
O_SHLOCK atomically obtain a shared lock
O_EXLOCK atomically obtain an exclusive lock
O_DIRECT eliminate or reduce cache effects
O_FSYNC synchronous writes
O_SYNC synchronous writes
O_NOFOLLOW do not follow symlinks
O_NOCTTY don’t assign controlling terminal
 
But when I tried to use O_SHLOCK or O_EXLOCK bits, I got compilation errors:
[SIZE=2][COLOR=#ff0000][SIZE=2][COLOR=#ff0000]error: ‘O_SHLOCK’ was not declared in this scope[/COLOR][/SIZE]
[/COLOR][/SIZE]I check 'fcntl.h' and there is no such bit definition.
 
Anyone knows where these bits are defined.

---

