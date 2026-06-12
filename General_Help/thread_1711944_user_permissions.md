---
title: "user permissions"
date: 2011-03-22
forum: General Help
---

### Post by ex_isp on 2011-03-22
How would you run a program with Sam’s privileges if you did not know
his password but had permission to use sudo to run a command with root
privileges? How would you spawn a shell with the same environment that
Sam has when he first logs in?

I assume it would be a pwd program? Maybe with a pipe (|) ?

---

### Post by mcduck on 2011-03-22
Just "sudo" will do it, if you are a member of the admin group (and therefore have the permission to use sudo).

```
sudo -u sam somecommand
```

or to open a shell:
```
sudo -iu sam
```

Unlike people often say, "sudo" isn't a tool for runnign things as root. it's a tool for running things as *any other user* ("**S**ubstitute **U**ser **DO**"), and just defaults to root if you don't specify any user.

---

### Post by ex_isp on 2011-03-22
> **mcduck said:**
> Just "sudo" will do it, if you are a member of the admin group (and therefore have the permission to use sudo).

```
sudo -u sam somecommand
```or to open a shell:
```
sudo -iu sam
```Unlike people often say, "sudo" isn't a tool for runnign things as root. it's a tool for running things as *any other user* ("**S**ubstitute **U**ser **DO**"), and just defaults to root if you don't specify any user.

thanks mcduck...that did the trick :)

---

