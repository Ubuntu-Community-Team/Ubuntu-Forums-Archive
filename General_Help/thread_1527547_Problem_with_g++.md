---
title: "Problem with g++"
date: 2010-07-09
forum: General Help
---

### Post by meadhikari on 2010-07-09
When I try to compile by typing g++ example.cpp i get the message

second.cpp:1:21: error: isostream: No such file or directory
second.cpp: In function ‘int main()’:
second.cpp:8: error: ‘cout’ was not declared in this scope
second.cpp:9: error: ‘cin’ was not declared in this scope
second.cpp:19: error: expected ‘;’ before ‘}’ token

Gcc works fine when compiling .c files

---

### Post by marshmallow1304 on 2010-07-09
First of all, cout, cin, etc. are in iostream, not isostream.

Dunno what's wrong with line 19 without seeing it.

---

### Post by rhd on 2010-07-09
Looks like just a typo and a forgotten semicolon, you're good :D

---

### Post by meadhikari on 2010-07-09
Thanks Problem solved the problem was just with the header file and a ; i am such a idiot to not find this

---

