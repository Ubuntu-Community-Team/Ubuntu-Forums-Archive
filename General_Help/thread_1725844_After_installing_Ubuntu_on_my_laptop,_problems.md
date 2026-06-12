---
title: "After installing Ubuntu on my laptop, problems"
date: 2011-04-10
forum: General Help
---

### Post by fnota on 2011-04-10
Hi, after installing ubuntu inside my windows, they told me to reboot.
But when i reboot, at the page where they ask you to choose which os to boot.
Only window 7 showed up
Is there a fix to this?

---

### Post by RedSingularity on 2011-04-10
Are you sure it installed successfully?  Also, what version of ubuntu did you install?

---

### Post by fnota on 2011-04-10
i installed 10.10 64 bits.

---

### Post by RedSingularity on 2011-04-10
Well that is the most stable release as of now.  Are you sure it installed successfully?  Maybe try the install again?

---

### Post by fnota on 2011-04-10
Problem is i cannot uninstall.
When i try to uninstall an error pop out.
I attached a photo of that error below^^

---

### Post by RedSingularity on 2011-04-10
That looks like an error on the windows side of things.  Unfortunately I wont be of much help there.  Can you attach the error log here for others to see?  Embed the error output in code tags here so it wont take up the whole page.

---

### Post by fnota on 2011-04-10
a clearer image of the error

---

### Post by fnota on 2011-04-10
ok thanks for you help, but what do you mean by embeded the tag? how?
Sorry i am new here :x

---

### Post by SeijiSensei on 2011-04-10
Is this a WUBI installation or a "real" installation where you repartitioned your hard drive and put Ubuntu in a separate partition?

---

### Post by fnota on 2011-04-10
This is a WUBI installation.
However before this installation, i had previously installed an older version of ubuntu which is 10.04.
I accidentally deleted all my bootloader using EasyBCD, but i recovered my window 7 bootloader using a recovery disk.
However for ubuntu i could solve the problem, so i format the whole partition(D drive) that i installed ubuntu 10.04 in.
And i install the lastest version of my ubuntu 10.10 into my c drive. ( Which is my main drive)

---

### Post by RedSingularity on 2011-04-10
> **fnota said:**
> ok thanks for you help, but what do you mean by embedded the tag? how?
Sorry i am new here :x


Sorry.  I am talking about the log file that is quoted at the end of that error window.  Copy all the contents in that file and paste them here.  Before pasting them use the "wrap code".  Thats the button at the top of comment window that looks like #.   (You must hit the "go advanced" button to reply)

Paste the code in between the [CODE]"***"[CODE] like this.

---

### Post by bcbc on 2011-04-10
That failure is Wubi trying to delete the Ubuntu entry from the windows boot manager (bcd). This was obviously missing - the reason you couldn't boot ubuntu in the first place - so trying to remove it is going to fail as well.

I'd try manually uninstalling Wubi using the instructions in the [Wubi Guide]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?")

---

### Post by fnota on 2011-04-10
wow thanks for the link. I downloaded the uninstaller from there, and.... IT WORK!! :popcorn:

---

### Post by RedSingularity on 2011-04-11
> **fnota said:**
> wow thanks for the link. I downloaded the uninstaller from there, and.... IT WORK!! :popcorn:
If you get the chance, mark the thread as "solved" for future viewers.  Thanks :)

---

