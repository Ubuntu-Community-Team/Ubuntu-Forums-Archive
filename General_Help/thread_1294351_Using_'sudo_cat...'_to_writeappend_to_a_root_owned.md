---
title: "Using 'sudo cat...' to write/append to a root owned file/folder not working?"
date: 2009-10-18
forum: General Help
---

### Post by stylishgnome on 2009-10-18
Over the last few releases of Ubuntu (8.04 and higher I believe) I've noticed that its not possible to write to a root owned file or folder
using 'sudo cat...', e.g:

```
stylishgnome@localhost:/var$ sudo cat >> test.txt << EOF
bash: test.txt: Permission denied
stylishgnome@localhost:/var$ su 
root@localhost:/var$ cat >> test.txt <<EOF
>test
>EOF
root@localhost:/var$ cat test.txt
test
root@localhost:/var$
```


Anybody have any idea why this is so? Thanks.

---

### Post by sisco311 on 2009-10-18
[uhelp]community/RootSudo[/uhelp]

> Redirecting the output of commands run with sudo requires a different approach. For instance consider sudo ls > /root/somefile will not work since it is the shell that tries to write to that file. You can use ls | sudo tee -a /root/somefile to append, or ls | sudo tee /root/somefile to overwrite contents. You could also pass the whole command to a shell process run under sudo to have the file written to with root permissions, such as sudo sh -c "ls > /root/somefile".

---

### Post by Sam on 2009-10-18
You must use tee for this.
```
cat << EOF | sudo tee test.txt
```

---

### Post by stylishgnome on 2009-10-20
Thanks for the help guys. Strange, I seem to remember being able to do this with older versions of Ubuntu (and other versions of Linux).

For the benefit of anyone who may come upon this later on, use the -a tag to append to the file:
```

cat << EOF | sudo tee -a test.txt

```

---

