---
title: "tar gz install into a specific folder"
date: 2010-03-21
forum: General Help
---

### Post by Daverobb on 2010-03-21
a real noob question

i need to install this downloaded tar gz file into the /proc/driver directory and i dont know how to 

can anyone lead me through?

---

### Post by asmoore82 on 2010-03-21
Something is very wrong there, the files in "/proc" don't exist on the physical disk.
It's like a window into the running kernel.

Perhaps you should post more info with the big picture of what you are trying to accomplish.

---

### Post by Daverobb on 2010-03-22
I'm running 9.10 on an older acer laptop.  TO use wireless I need to activate the acer hotkeys which control the wireless led switch/light. WIthout it active there is no wireless, which makes a big problem for me.

So a workaround is offered through acergui which works with the the acerhk files to activate the functions.  i've downloaded and have installed the files but in the acergui program i get this error message.  so i'm trying to figure out how to make it work.

---

### Post by gordintoronto on 2010-03-23
What error message?

In your initial message, you said:
"i need to install this downloaded tar gz file into the /proc/driver directory"

A tar.gz file can go anywhere.  (I have a folder in Documents called download that I put downloads into.)  It's what is *in* the tar that counts.  So what file is it, and where did you get it?  If you just double-click on the file, you should see what is in it.  If it contains a folder, double-click on that, and you should see the files.  With any luck, one of them is called README, and you should read it.

---

### Post by Megafag on 2010-03-23
> **Daverobb said:**
> tar gz install into a specific folder

does anyone else read this as "install from source code into a specific folder" ?

---

### Post by Daverobb on 2010-03-23
thanks -- i actually figured it out - installed through wget and dpkg and it set it up as it should -- currently now just trying to actually solve the original problem which was getting my older acer laptop wireless card to turn on and work....

if anyone has had any experience/success  feel free

---

### Post by bodhi.zazen on 2010-03-23
To address the original question ...

.tar are archives, like zip files.

To extract the contents use the tar command , the exact options depend on the archive ...

.tar.gz = ```
tar xzf file.tar.gz
```That command will extract the contents to the current directory. To specify a target directory, use the -C option

```
tar xzf file.tar.gz -C /target
```

If the directory is owned by root, you will need to use sudo.

Otherwise, glad you got it sorted, in the future it would help if you are able to provide additional information.

---

