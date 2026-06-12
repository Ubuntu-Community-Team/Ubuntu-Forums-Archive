---
title: "Update Manager won't work right"
date: 2012-08-22
forum: General Help
---

### Post by Feenix217 on 2012-08-22
I'm running 12.94 on an older Compaq laptop.

There's a file in Update Manager listed under "Other updates" and it reads: "Apply a diff file to an original" and the name of the file is "patch."

Because of this "other" update, Update Manager will not allow any of the other files to be updated.

Yes, even when I uncheck this "patch," Update Manager still won't allow the other files to be updated.

I've already tried to install Synaptic and it won't install.

What to do?

---

### Post by matt_symes on 2012-08-23
Hi

Please open a terminal and type

```
sudo apt-get update
```If there are any errors please copy and paste the entire commands text from the terminal into your next post.

If there are no errors then please type (into the terminal)

```
^date^grade
```Post back the text from this last command from the terminal into your next post.

Kind regards

---

### Post by ernestj on 2012-08-23
I am having a similar problem with updates. they seem to keep getting hung up. i have used the update manager and the terminal.

---

### Post by raja.genupula on 2012-08-23
Hi ernestj 

actually if you have issue then you should have to post it on your own thread , so as already you have posted here , edit your post with the output of your ```
sudo apt-get update 
``` from terminal . 

but the primary thing you have to follow is to create your own thread for your issue.

---

### Post by Feenix217 on 2012-08-24
Hey there!

I bypassed Update Manager and updated via the terminal. 

It updated fine. My guess is UM is flaky ATM in 12.04 but the Compaq lappy is my back-up lappy so it's no big deal if UM is flaky. 

Thanks for the help!


> **raja.genupula said:**
> Hi ernestj 

actually if you have issue then you should have to post it on your own thread , so as already you have posted here , edit your post with the output of your ```
sudo apt-get update 
``` from terminal . 

but the primary thing you have to follow is to create your own thread for your issue.

---

### Post by claracc on 2012-08-24
As you got your problem fixed, please mark the thread as solved with "thread tools" in the right upper part of the page.

---

