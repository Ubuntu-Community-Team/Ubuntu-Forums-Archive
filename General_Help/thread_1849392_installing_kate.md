---
title: "installing kate"
date: 2011-09-24
forum: General Help
---

### Post by cmcanulty on 2011-09-24
I am trying to install kate with the directions here
[http://kate-editor.org/get-it/]("http://kate-editor.org/get-it/")
I do OK until  I get to the direction. I can't figure out what they mean to do.I made a /doc folder in ~/kde and I used the terminal to get to /kde/kate/doc but I get  
```
cmcanulty@HP:~$ /kde/kate/doc
bash: /kde/kate/doc: No such file or directory
cmcanulty@HP:~$ ^C
cmcanulty@HP:~$ 

```
To create the final html pages, switch to the “doc”-folder and first create a folder called “html”. Here all the html ouput of the *.docbook files will be generated. Then use meinproc4 to generate the html ouput:
```

    mkdir html
    cd html
    meinproc4 --check ../index.docbook
```

---

### Post by sanderd17 on 2011-09-24
you should have created the ~/kde directory before, so ~/kde/run.sh is just a file "run.sh" in that directory.

---

### Post by Lars Noodén on 2011-09-24
Why not use the package manager instead?  Is there a specific reason to try compiling from source?

---

### Post by cmcanulty on 2011-09-24
OK thanks

---

