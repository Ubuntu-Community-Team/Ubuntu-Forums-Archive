---
title: "Trouble Navigating directories in terminal"
date: 2010-09-22
forum: General Help
---

### Post by reese8220 on 2010-09-22
I am new to using ubuntu, and I am trying to get the basics of the terminal down. I understand the concept of the cd command to change directories, but apparently I am not using it right. I downloaded some programs that i need to install using the terminal, but everytime i try to navigate to the downloads directory, it tells me no such file or directory. To give you an idea of what im trying to do, here is an example (most likely wrong)

alex@alex-desktop:~$ ls
Desktop    Downloads         GoogleEarthLinux.bin  Music     Public     Videos
Documents  examples.desktop  libflashplayer.so     Pictures  Templates

alex@alex-desktop:~$ cd /Downloads
bash: cd: /Downloads: No such file or directory


can anyone give me some tips on how to navigate correctly if I am doing this wrong?

---

### Post by azertyh on 2010-09-22
hi,
it's ```
cd Downloads
```.

---

### Post by oldos2er on 2010-09-22
What azertyh said. When you add "/" in front of Downloads, you're telling bash to start looking from root (root = /). More info here: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by madmax75 on 2010-09-22
> **oldos2er said:**
> What azertyh said. When you add "/" in front of Downloads, you're telling bash to start looking from root (root = /)[l]("https://help.ubuntu.com/community/UsingTheTerminal")

By default, you start in your home directory (/home/your-username).

You can use > pwd to check your current working directory (= it tells you where you are right now).

If you write "pwd" as soon as you fire up your Terminal, it will give you this:

> user@machine:~$ pwd
/home/user

So it tells you that you are actually in your home directory and not under root directory.

Change directory:

> user@machine:~$ cd sub-directory

Now give "pwd" again:

> user@machine:~/sub-directory$ pwd
/home/user/sub-directory

Now you find yourself in the sub-directory where you changed into. You can also see that your prompt already tells you where you are at present (so this second "pwd" is actually unnecessary... :)).

---

