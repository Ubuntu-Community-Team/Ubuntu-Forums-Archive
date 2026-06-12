---
title: "Every time terminal is launched it shows something"
date: 2010-12-17
forum: General Help
---

### Post by alexandrius on 2010-12-17
Hi, After applying 200 line kernel patch alternative the terminal gives some unknown output:
```
bash: /dev/cgroup/cpu/user/1171/tasks: No such file or directory
bash: /dev/cgroup/cpu/user/1171/notify_on_release: No such file or directory
```
Yeah i know that this issue doesn't really mean anything but it's kinda annoying :)
Please help me if you know how :)

---

### Post by daqron on 2010-12-17
I don't understand what "200 line kernel patch alternative" means, but if this happens every time you launch a terminal or login to a console, perhaps something strange has made its way into your ~/.bashrc file?

---

### Post by alexandrius on 2010-12-17
> **daqron said:**
> I don't understand what "200 line kernel patch alternative" means, but if this happens every time you launch a terminal or login to a console, perhaps something strange has made its way into your ~/.bashrc file?
Happens every time i launch any terminal emulator

200 line kernel patch alternative: [http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html](http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html)

The .bashrc file's content:
[http://pastebin.com/TfPjaMGE](http://pastebin.com/TfPjaMGE)

---

### Post by matt_symes on 2010-12-17
Hi

You problem is 

```
if [ "$PS1" ] ; then
mkdir -p -m 0700 /dev/cgroup/cpu/user/$$ > /dev/null 2>&1
echo $$ > /dev/cgroup/cpu/user/$$/tasks
echo "1" > /dev/cgroup/cpu/user/$$/notify_on_release
fi
```in your ~/.bashrc file (last couple of lines). I assume it was put there by that patch.

Kind regards

---

### Post by alexandrius on 2010-12-17
@matt_symes great thanks! that worked :)

---

### Post by piquat on 2010-12-17
> **alexandrius said:**
> Hi, After applying 200 line kernel patch alternative the terminal gives some unknown output:
```
bash: /dev/cgroup/cpu/user/1171/tasks: No such file or directory
bash: /dev/cgroup/cpu/user/1171/notify_on_release: No such file or directory
```Yeah i know that this issue doesn't really mean anything but it's kinda annoying :)
Please help me if you know how :)

This link lists your problem and basically says you need to undo any changes you made doing it the way you did it and then use the script in this link.

[http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html](http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html)

---

