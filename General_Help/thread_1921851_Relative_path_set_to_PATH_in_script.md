---
title: "Relative path set to PATH in script"
date: 2012-02-07
forum: General Help
---

### Post by savagetwinky on 2012-02-07
I'm having a hard time finding a way to do something. This is probably kind of stupid but I want to add a path to the enviroment PATH, the problem is the script isn't going to know where it lives.

There is a tool that comes bundled with a project, project1/tools and that path needs to be set when making project 2. 

so I tried (and failed) to do something like this

> 
#!/bin/bash
PATH=PATH:project1/tools
make project2


---

### Post by Khayyam on 2012-02-07
savagetwinky ..

The reason for it failing is that the word "PATH" isn't a variable .. $PATH is ..

```
PATH=/project1/tools:$PATH
```

HTH ...

---

