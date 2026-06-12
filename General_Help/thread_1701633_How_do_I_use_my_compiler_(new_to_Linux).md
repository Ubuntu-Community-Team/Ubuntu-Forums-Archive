---
title: "How do I use my compiler? (new to Linux)"
date: 2011-03-06
forum: General Help
---

### Post by Codeless on 2011-03-06
ok so I've created a flex and bison file and did the following

flex lang.lex
bison -d -o compile.c land.y
cc -o compile compile.c lex.yy.c

"compile" is produced, so I want to compile a text file called "test" using "compile"

I type "compile < test.txt" which is wrong because I get "compile: command not found"

so how do I compile my test file? I only installed linux today so I'm not sure how things work yet

---

