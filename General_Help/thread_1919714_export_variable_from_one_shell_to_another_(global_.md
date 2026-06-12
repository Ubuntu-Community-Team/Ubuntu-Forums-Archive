---
title: "export variable from one shell to another (global variable?)"
date: 2012-02-03
forum: General Help
---

### Post by phillips321 on 2012-02-03
Hi guys,

Lets say i have 2 terminals open.
if in terminal 1 i type```
export MYVALUE=1
```

and in terminal 2 i type```
echo ${MYVALUE}
```

I don't get any output, how can i assign a variable in one terminal and ensure it is global so that it can be read in another terminal?

Many thanks

---

### Post by Khayyam on 2012-02-04
philips321 ..

In short, you can't, at least not for variables defined on-the-fly. This is because a shell is a child of a parent process, it takes the characteristics (variables) of the parent but not those of its syblings.

The standard method of defining variables is via the shells profile (/etc/profile ~/.bash_profile, ~/.zprofile, etc) any variable defined in one or other of these files will be set globally for subsqequent child processes. Each variable can be set to a value other than that set by the parent, however, the childs syblings, do not automatically inherit these values. If the variable was written to a file a sybling could source it (see: man source) and so have that same variable, but this, I think, is not what you have in mind

HTH ...

---

