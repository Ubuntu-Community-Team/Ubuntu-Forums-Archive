---
title: "Xubuntu Scilab problem"
date: 2012-03-09
forum: General Help
---

### Post by bazcor on 2012-03-09
Not sure what causes this but in xubuntu 11.10, when opening scilab gui the window appears in the top left of the screen with no -,+,X in the top bar. 

The window is unmoveable though scilab functions normally in the window.

Any cures or experiences would be much appreciated.

---

### Post by HermanAB on 2012-03-09
Your XFCE window manager crashed.  Restart it with:
$ sudo xfwm4 --daemon 

That will instantly bring the outer frames back.

---

### Post by bazcor on 2012-03-09
No dice with that:-


barry@barry-GA-870A-UD3:~$ sudo xfwm4 --daemon
[sudo] password for barry: 
xfwm4-Message: To replace the current window manager, try "--replace"

(xfwm4:1959): xfwm4-WARNING **: Another Window Manager is already running
barry@barry-GA-870A-UD3:~$ 

Thanks for the idea though .. Barry

---

### Post by Toz on 2012-03-09
> **bazcor said:**
> No dice with that:-


barry@barry-GA-870A-UD3:~$ sudo xfwm4 --daemon
[sudo] password for barry: 
xfwm4-Message: To replace the current window manager, try "--replace"

(xfwm4:1959): xfwm4-WARNING **: Another Window Manager is already running
barry@barry-GA-870A-UD3:~$ 

Thanks for the idea though .. Barry

The command should be:
```
xfwm4 --replace
```

However, it is curious that another window manager is running. Can you tell which one? (ps -ef should help).

Also, is it only this program that is missing its window decorations/controls or is it all windows?

---

### Post by bazcor on 2012-03-10
Would the window manager be xfwm4? That looks the most likely.



Only Scilab is affected, no problems at all with other programs. 

Scilab runs fine in Ubuntu 11.10 it's just Xubuntu which has this problem.

.. Barry

---

### Post by bazcor on 2012-03-10
PS I get this when I type scilab into the terminal:

barry@barry-GA-870A-UD3:~$ scilab

(process:24254): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Error parsing gtk-icon-sizes string: ''
barry@barry-GA-870A-UD3:~$

.. Barry

---

### Post by Toz on 2012-03-10
> **bazcor said:**
> Would the window manager be xfwm4? That looks the most likely.
Yes, it should be.



> Only Scilab is affected, no problems at all with other programs.

Scilab runs fine in Ubuntu 11.10 it's just Xubuntu which has this problem.

.. Barry
Very interesting. I just installed the program from the repos. I noticed that on its first run it was positioned in the top-left corner and the window controls hidden under the top panel. Alt+Left Mouse allowed me to move the window towards the centre of the screen and the controls became visible again.

---

### Post by bazcor on 2012-03-11
Thanks for that, that will definitely do as a work around.

Thanks for the reply and I will mark this thread as solved. .. Barry

---

