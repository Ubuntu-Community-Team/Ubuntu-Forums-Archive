---
title: "ubuntu boot up problem"
date: 2010-10-26
forum: General Help
---

### Post by rmcellig on 2010-10-26
I am using Ubuntu 10.10. My update manager came up so I installed the updates. When I restarted Ubuntu, it came up with a black window with a login and password prompt. I can't get back to my regular desktop. What do I do?

Is there a command I need to boot back into the regular GUI? I don't want this  happening all the time. I would like Ubuntu to always start up into my Desktop.

---

### Post by TeoBigusGeekus on 2010-10-26
Give your username and password and then type
```
gnome-session
```
Post us any error messages.

---

### Post by rmcellig on 2010-10-26
I get a warning cannot open display after I type in gnome-session

---

### Post by TeoBigusGeekus on 2010-10-26
What about
```
startx
```

---

### Post by rmcellig on 2010-10-26
I see a fatal error no screens found
Failed to load module Nvidia

---

### Post by TeoBigusGeekus on 2010-10-26
Check [this]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10029491") page out.

---

### Post by rmcellig on 2010-10-26
When I click on the link it brings me back to this thread.

---

### Post by TeoBigusGeekus on 2010-10-26
Oops, just testing your reflexes...
[https://answers.launchpad.net/ubuntu/+source/xorg/+question/129821]("https://answers.launchpad.net/ubuntu/+source/xorg/+question/129821")

---

### Post by rmcellig on 2010-10-26
:)

---

### Post by rmcellig on 2010-10-26
I'm OK now. I noticed something in my GRUB listing. It said something like Linux Generic PAE. What is that and can I delete that. When I selected just the Generic kernel, I was able to boot into the GUI no problem.

---

