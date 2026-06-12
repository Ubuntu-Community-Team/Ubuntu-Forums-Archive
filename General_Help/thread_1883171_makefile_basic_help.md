---
title: "makefile basic help"
date: 2011-11-18
forum: General Help
---

### Post by fouadk on 2011-11-18
hi everyone...

i am trying to build a makefile for a programming course...
i want to create a directive that will run my server and 4 different clients...the trick is to make each instance run inside a new terminal...

here is an example:
```

Tests:
	bash ./server 60
        bash ./client 100 1
        bash ./client 22 2 
        bash ./client 50 3 
        bash ./client 40 4

```

im getting some error messages and it aint working...
please help
thanks in advance

---

