---
title: "bash: ./adb: No such file or directory"
date: 2010-06-29
forum: General Help
---

### Post by milasch on 2010-06-29
I installed android SDK, eclipse and all the tools necessary for android development but I'm surprised to see error messages in Eclipse after a boot complaining files do not exist.

Getting to the root of the problem I found that files indeed exist but I can't execute them.

What am I missing here?

```

milasch@milasch-ubuntu:~/android-sdk-linux_86/tools$ ./adb
bash: ./adb: No such file or directory
milasch@milasch-ubuntu:~/android-sdk-linux_86/tools$ ls -l
total 9504
-rwxrwxrwx 1 milasch milasch  341773 2010-05-07 14:47 adb

```

I can't post a screenshot because for some reason when I capture the screen my host OS is actually doing it resulting in a blank image with a cursor in the middle :S.

---

### Post by nmaster on 2010-06-29
have you tried downloading a new tar.gz of the sdk? check the adb there.  it that works then perhaps eclipse caused the problem.

---

### Post by milasch on 2010-06-29
> **neal.m.master said:**
> have you tried downloading a new tar.gz of the sdk? check the adb there.  it that works then perhaps eclipse caused the problem.

Yup, I did. It actually worked once, I was even able to play around but then I had to reboot for some reason and the problem is back. I'm reinstalling ubuntu in my VM.

---

### Post by nmaster on 2010-06-30
is this behavior consistent? does it always not work upon reboot? did you happen to do anything with the eclipse android plugin before that reboot?

---

### Post by webgh0st on 2011-07-29
Sorry for digging up an old post, I just wanted to help any users with this problem cuz this thread is at the top of a google search "ubuntu adb no such file or directory". Installing the package ia32-libs fixes this.

---

### Post by azredwing on 2011-08-11
> **webgh0st said:**
> Sorry for digging up an old post, I just wanted to help any users with this problem cuz this thread is at the top of a google search "ubuntu adb no such file or directory". Installing the package ia32-libs fixes this.

thanks for this, works out perfectly now.

---

### Post by gunnermike53 on 2011-10-10
hey folks. so i am new to ubuntu and linux in general. honestly i have tried working with linux in the past but have given up because it seems that everything is such a fight. but in order to continue learning android i NEED linux. ugh. i know most of you feel differently, and i hope that i will ocme to understand linux aswell. 

so on to my problem

its the same as the op. however i dont have an amd processor, its an i3 intel. for giggles i tried installing the lib file suggested but ubuntu say NO. 

i have deleted and reinstalled adb several times to no avail.

thanks for the help.

---

### Post by nharward on 2011-12-19
I had to also install [FONT=Courier New]ia32-libs-multiarch[/FONT] on 11.10, [FONT=Courier New]ia32-libs[/FONT] alone didn't work.

---

### Post by drkages on 2012-02-04
Thanks this thread was a life saver.

---

### Post by den_ on 2012-03-23
> **webgh0st said:**
> Sorry for digging up an old post, I just wanted to help any users with this problem cuz this thread is at the top of a google search "ubuntu adb no such file or directory". Installing the package ia32-libs fixes this.

Thanks!

---

### Post by crazyJay648 on 2012-05-26
Awesome!!! I had this same problem and installing [FONT=Courier New]ia32-libs fixed it.
[/FONT]

---

### Post by Hyrule on 2012-06-05
I also had to install [FONT="Courier New"]libc6-i386[/FONT] to get this working. 

[FONT="Courier New"]sudo apt-get install --reinstall libc6-i386[/FONT]

---

### Post by oldos2er on 2012-06-05
Old thread closed.

---

