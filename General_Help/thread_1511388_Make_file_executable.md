---
title: "Make file executable?"
date: 2010-06-16
forum: General Help
---

### Post by 8jwong14 on 2010-06-16
I have  the file for Conky Wizard ver.1 but in order to run it, i need to make it executable.  From what I know, I'm supposed to right click the file and press properties then go to permissions and check "allow executing as program"  However, this option is missing.  [Here]("http://www.omgubuntu.co.uk/2010/06/easy-to-use-lucid-themed-conky-bar-now.html") is the link to the ConkyWizard Ver1 Beta 1 file.

---

### Post by wojox on 2010-06-16
It is executable.

---

### Post by 8jwong14 on 2010-06-17
> **wojox said:**
> It is executable.
I know that it appears that way but it won't run for me.

---

### Post by bodhi.zazen on 2010-06-17
Post the error message you are getting when you try to run the file.

Is the file stored in a (home) partition mounted noexec ?

output of ```
mount
```

---

### Post by Vaphell on 2010-06-17
because it is borked, from terminal:

```
$ ./ConkyWizard_64bits_V1.0_Beta1
QMetaObject::connectSlotsByName: No matching signal for on_Wizard_finished(int)
./ConkyWizard_64bits_V1.0_Beta1: symbol lookup error: ./ConkyWizard_64bits_V1.0_Beta1: undefined symbol: _ZN9QListData11detach_growEPii

```

---

### Post by bodhi.zazen on 2010-06-17
> **Vaphell said:**
> because it is borked, from terminal:

```
$ ./ConkyWizard_64bits_V1.0_Beta1
QMetaObject::connectSlotsByName: No matching signal for on_Wizard_finished(int)
./ConkyWizard_64bits_V1.0_Beta1: symbol lookup error: ./ConkyWizard_64bits_V1.0_Beta1: undefined symbol: _ZN9QListData11detach_growEPii

```

Well , that problem is not because the file is not executable.

You will need to file a bug report =)

---

### Post by 8jwong14 on 2010-06-18
So the problem isn't that the file is not executable and that it just can't run?  How do I run it from terminal to get the output?  Thanks for helping.

@[[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054")
Running it will not pop up any errors.  Errors may show in terminal but they don't pop up.  It doesn't seem to do anything at all.

---

### Post by bodhi.zazen on 2010-06-18
> **8jwong14 said:**
> So the problem isn't that the file is not executable and that it just can't run?  How do I run it from terminal to get the output?  Thanks for helping.

@[[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054")
Running it will not pop up any errors.  Errors may show in terminal but they don't pop up.  It doesn't seem to do anything at all.

That is correct. The program has a bug. Some bugs will show graphical error messages, many will not.

You should post the output you are getting in the terminal on the mailing list or home page for the application.

---

### Post by 8jwong14 on 2010-06-24
> **bodhi.zazen said:**
> That is correct. The program has a bug. Some bugs will show graphical error messages, many will not.

You should post the output you are getting in the terminal on the mailing list or home page for the application.
How do I run if from terminal?

---

### Post by bodhi.zazen on 2010-06-24
Open a terminal

Enter the command or the full path to the command.

[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

---

### Post by boron on 2010-07-21
> **8jwong14 said:**
> I have  the file for Conky Wizard ver.1 but in order to run it, i need to make it executable.  From what I know, I'm supposed to right click the file and press properties then go to permissions and check "allow executing as program"  However, this option is missing.  [Here]("http://www.omgubuntu.co.uk/2010/06/easy-to-use-lucid-themed-conky-bar-now.html") is the link to the ConkyWizard Ver1 Beta 1 file.

Thanks for the tip on making a file executable. It's easywhen you know how, isn't it?;)

---

### Post by 8jwong14 on 2010-07-31
> **bodhi.zazen said:**
> Open a terminal

Enter the command or the full path to the command.

[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)
Sorry for taking so long to reply.  I read a lot of that but I still don't know how to run the file in terminal.

---

### Post by bodhi.zazen on 2010-07-31
> **8jwong14 said:**
> Sorry for taking so long to reply.  I read a lot of that but I still don't know how to run the file in terminal.

Imagine you have a file "foo" in your home directory ...

```
chmod a+x ~/foo

~/foo
```If it is a windows program, you would need to use wine.

---

