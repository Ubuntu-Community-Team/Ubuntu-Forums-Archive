---
title: "History File Limit"
date: 2010-09-07
forum: General Help
---

### Post by bashologist on 2010-09-07
Edit: Problem Solved.

Problem:
A new version of bash added these lines to the top of ~/.bashrc:
```
HISTSIZE=1000
HISTFILESIZE=2000
```

Making these lines which I appended to the bottom of the file useless:
```
export HISTSIZE=999999
export HISTFILESIZE=999999
```

Maybe I shouldn't have been using export. In any case it's frecking annoying that they added these lines.

Solution is to not use export.

---

