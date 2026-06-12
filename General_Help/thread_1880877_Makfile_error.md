---
title: "Makfile error"
date: 2011-11-14
forum: General Help
---

### Post by newport_j on 2011-11-14
What is wrong with this Makefile? I took it word for, symbol for symbol froma makefile tutorial I found on the web.
 
The file is
 
```

[FONT=Times New Roman][SIZE=3]CC=pgcpp[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]CFLAGS=-c -Wall[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]LDFLAGS=[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]SOURCES=main.cpp hello.cpp factorial.cpp[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]OBJECTS=$SOURCES:cpp=.o)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]EXECUTABLE=hello[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]all: $(SOURCES) $(EXECUTABLE)[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]$(EXECUTABLE):    $(OBJECTS)[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]   $(CC) $(LDFLAGS)  $(OBJECTS)  -o $@[/FONT][/SIZE]
 
[FONT=Times New Roman][SIZE=3].cpp.o:[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]   $(CC) $(CFLAGS)   $< -o $@[/FONT][/SIZE]

```
 
[FONT=Times New Roman][SIZE=3]Output[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Makefile:10: *** target pattern contains no `%'. Stop[/SIZE][/FONT]
 
Line 10 starts with $(EXEC...)
 
Any help appreaciated. Thanks in advance.
 
Newport_j

---

### Post by gmargo on 2011-11-14
> **newport_j said:**
> What is wrong with this Makefile? I took it word for, symbol for symbol froma makefile tutorial I found on the web.
 
The file is
 
```

[FONT=Times New Roman][SIZE=3]OBJECTS=$SOURCES:cpp=.o)[/SIZE][/FONT]

```

Your OBJECTS line should be:
```

OBJECTS=$(SOURCES:.cpp=.o)

```

---

### Post by newport_j on 2011-11-14
Thanks, I will try it.
 
Newport_j

---

