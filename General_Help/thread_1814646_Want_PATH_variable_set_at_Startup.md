---
title: "Want PATH variable set at Startup"
date: 2011-07-29
forum: General Help
---

### Post by jplyons on 2011-07-29
Hi,

I need to set PATH environment variables so they will be set every tie I 
startup ubuntu. Is there a startup script that will do this, and where is it located?

Thanks very much
Joe

---

### Post by lmarmisa on 2011-07-29
If you want to add one or more directories to the PATH variable, type this command:

```

export PATH=$PATH:/your/new/directory/here

```

You could insert this command at the end of the file ~/.bashrc if you want to add permanently your directory to the path.

---

### Post by bodhi.zazen on 2011-07-29
Set the path for what ? Your user ? scripts ?

---

