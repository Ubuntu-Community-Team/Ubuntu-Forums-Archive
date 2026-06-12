---
title: "Problems with wine"
date: 2010-07-28
forum: General Help
---

### Post by fred6633 on 2010-07-28
Hello,
I installed wine 1.2 with Synaptic in 10.04.

I installed an application that always have worked with wine.

This program installs dll's in the programs own directory and in C:\Windows\System32.

When I launch the application, it complains about missing files.

The problem is that wine doesn't seem to look for dll's in System32.

If I move the dll's the program copied to System32 to C:\Windows\System, the program launches as it should.

So I need to get wine to look in System32 instead of System.

Thanks

Fred

---

### Post by prodigy_ on 2010-07-28
You can always make symlinks with ```
ln -s
``` command. But if the program worked for you before, you should probably also file a regression bug report to Wine developers:

[http://bugs.winehq.org/enter_bug.cgi](http://bugs.winehq.org/enter_bug.cgi)

---

### Post by Irony on 2010-07-28
This is what I did with Autosketch 7.0.

In terminal type;

```
regedit
```

Navigate to;

```
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Session Manager\Environment
```

and add to the file named PATH which looks like this;

```
C:\windows\system32;C:\windows;C:\windows\system32\wbem
```

So it looks like this;

```
C:\windows\system32;C:\windows;C:\windows\system32\wbem;C:\Program Files\Common Files\Autodesk Shared
```

This tells Wine where to look for the .dll files.

Obviously in your case you will have to type whatever program is that you have.

---

### Post by fred6633 on 2010-07-28
Thanks,

but System32 is in the PATH and and System is not and yet wine looks in System but not in System32.



Fred

---

### Post by ronnielsen1 on 2010-07-28
What are you trying to run?

---

### Post by fred6633 on 2010-07-28
It's an old 16-bit program called Timewiz.

As I said, the program runs fine if I copy the dll's from C:\Windows\System32 to C:\Windows\System.

But that shouldn't be necessary as wine should look in System32.

When I run the same application in Windows Vista, it works fine to have the dll's in C:\Windows\System32.

Fred

---

### Post by fred6633 on 2010-07-28
I read in the program's manual that the files shall be in Windows\System, so I guess everything is okay then.

Strange though that the installation of this program always has been flawless until now.

Fred

---

### Post by Nick_Jinn on 2010-07-28
I have been getting the same message having to due with a dll file when I try to play fallout 3, but it always used to play on my older system which specs that were not as good and the same graphics card.

---

### Post by prodigy_ on 2010-07-28
> **fred6633 said:**
> Strange though that the installation of this program always has been flawless until now.
16-bit programs are handled differently in Wine 1.2. From the release notes:
> - All the 16-bit support code has been moved to a set of independent 16-bit modules. No 16-bit code is loaded or initialized when running a standard Win32 application, unless it starts making 16-bit calls.
And while it's reasonable change, it might have led to some regressions.

---

