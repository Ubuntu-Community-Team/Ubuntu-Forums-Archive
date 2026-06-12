---
title: "Won't even let me use Sudo in terminal?"
date: 2009-07-13
forum: General Help
---

### Post by Ryan8524 on 2009-07-13
Hi guys,

When I am in my terminal and I try to use Sudo... I get an error message.

The error message is: 



E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/winff.list



Can anyone help me with this error and how to correct it?

Thanks!

---

### Post by snowpine on 2009-07-13
Does this look familiar?

[http://code.google.com/p/winff/wiki/UbuntuInstallation](http://code.google.com/p/winff/wiki/UbuntuInstallation)

Please post the contents of your /etc/apt/sources.list.d/winff.list file. (alt+f2, gedit /etc/apt/sources.list.d/winff.list)

This file is not part of a standard Ubuntu install, so my guess is, it's the likely culprit. :)

---

### Post by Ra-Hoor-Khuit on 2009-07-13
What command are you trying to use?

It appears from the error you posted that you have - potentially - corrupted your sources.list file.

---

### Post by Elfy on 2009-07-13
Your winff sources list has an error in it - if you don;t know how to correct it post it here and we can help you.

Basically the source list should only have line starting with #, deb or deb-src.

Open the file for editing

```
gksudo mousepad /etc/apt/sources.list.d/winff.list
```

and make sure it follows the above.

---

### Post by Ryan8524 on 2009-07-13
> **snowpine said:**
> Does this look familiar?

[http://code.google.com/p/winff/wiki/UbuntuInstallation](http://code.google.com/p/winff/wiki/UbuntuInstallation)

Please post the contents of your /etc/apt/sources.list.d/winff.list file. (alt+f2, gedit /etc/apt/sources.list.d/winff.list)

This file is not part of a standard Ubuntu install, so my guess is, it's the likely culprit. :)


How would i post the contents of  /etc/apt/sources.list.d/winff.list file? Should I run it in my terminal?

Sorry, I am very new to ubuntu.... very very new.....

Thanks!

---

### Post by jocko on 2009-07-13
[This is the first and only google hit]("http://ubuntuforums.org/showthread.php?p=6357128") when searching for "E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/winff.list" (including the quotes). The thread seems to have a fix.

But first check the contents of the file, it may be easy to fix it (I don't have that file, but if you post the contents I'm sure it will be possible to see what's wrong).
To see the file in a terminal:
```
cat /etc/apt/sources.list.d/winff.list
```

---

### Post by snowpine on 2009-07-13
Open it with your text editor.

If you are in Xubuntu, press alt+f2, then type mousepad /etc/apt/sources.list.d/winff.list

Or if you are using "Genome" press alt+f2, then type gedit /etc/apt/sources.list.d/winff.list

---

### Post by snowpine on 2009-07-13
> **jocko said:**
> [This is the first and only google hit]("http://ubuntuforums.org/showthread.php?p=6357128") when searching for "E: Type 'sudo' is not known on line 1 in source list /etc/apt/sources.list.d/winff.list" (including the quotes). The thread seems to have a fix:
```
sudo rm /etc/apt/sources.list.d/winff.list
```

That might make the error go away, but then the OP won't have access to the winff repository any more. Better to edit the file and fix the syntax. :)

---

### Post by Ryan8524 on 2009-07-13
When I do that I get this:

Error stating file '/home/ryan/gedit/etc/apt/sources.list.d/winff.list': No such file or director

---

### Post by jocko on 2009-07-13
> **snowpine said:**
> That might make the error go away, but then the OP won't have access to the winff repository any more. Better to edit the file and fix the syntax. :)
That's right. I edited my post to remove that bit.
Otherwise I'm sure it's quite easy to add the repo back...

---

### Post by jocko on 2009-07-13
> **Ryan8524 said:**
> When I do that I get this:

Error stating file '/home/ryan/gedit/etc/apt/sources.list.d/winff.list': No such file or director
That's because the command should be:
```
gedit /etc/apt/sources.list.d/winff.list
```Not:
```
gedit/etc/apt/sources.list.d/winff.list
```There should be a space between the program (gedit) and the file name (/etc/apt/sources.list.d/winff.list).

But if you're using xubuntu (as the thread title indicates), you probably don't have gedit. So use either "mousepad" or "cat" instead of gedit.

---

### Post by snowpine on 2009-07-13
> **Ryan8524 said:**
> When I do that I get this:

Error stating file '/home/ryan/gedit/etc/apt/sources.list.d/winff.list': No such file or director

Sorry Ryan, I am totally at a loss why you would get that error--it makes no sense to me. :(

The only advice I can give at this point is to switch over to the current version (9.04 Jaunty Jackolope). Winff is in the 9.04 repositories, so you can install it (using add/remove programs, synaptic package manager, or the command line) without the need for an /etc/apt/sources.list.d/winff file. 

Or, fix/delete the offending file and keep your current install (possibly without winff if you can't resolve the issue).

Good luck!

---

### Post by aysiu on 2009-07-13
> **Ryan8524 said:**
> When I do that I get this:

Error stating file '/home/ryan/gedit/etc/apt/sources.list.d/winff.list': No such file or director
Then don't type any commands.

Copy and **paste** this command into the terminal: ```
cat /etc/apt/sources.list.d/winff.list
``` Then copy and paste the output back here.

---

### Post by Ryan8524 on 2009-07-13
> **aysiu said:**
> Then don't type any commands.

Copy and **paste** this command into the terminal: ```
cat /etc/apt/sources.list.d/winff.list
``` Then copy and paste the output back here.


I got:
cat: /etc/apt/sources.list.d/winff.list: No such file or directory

---

### Post by Ryan8524 on 2009-07-13
> **jocko said:**
> That's because the command should be:
```
gedit /etc/apt/sources.list.d/winff.list
```Not:
```
gedit/etc/apt/sources.list.d/winff.list
```There should be a space between the program (gedit) and the file name (/etc/apt/sources.list.d/winff.list).

But if you're using xubuntu (as the thread title indicates), you probably don't have gedit. So use either "mousepad" or "cat" instead of gedit.


I used gedit and it worked... But when i did it it went straight to Text editor.
What do I do from there?

Thanks!

---

### Post by jocko on 2009-07-13
> **Ryan8524 said:**
> I used gedit and it worked... But when i did it it went straight to Text editor.
What do I do from there?

Thanks!
Yes, gedit is a text editor, and it should have opened the file for you. Paste it's contents here so that we can see what's wrong with it.

But your last post seems to indicate that you don't have the file. In that case I don't know what could be wrong (unless you have removed the file with the "rm" command in the thread I linked to earlier, in which case you have already fixed the problem...).

---

### Post by Ryan8524 on 2009-07-13
> **jocko said:**
> Yes, gedit is a text editor, and it should have opened the file for you. Paste it's contents here so that we can see what's wrong with it.


When the text editor popped up, Nothing was written on the page.

The files name was: 

winff.list (/etc/apt/source.list.d)  - gedit

---

