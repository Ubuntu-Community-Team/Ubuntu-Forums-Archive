---
title: "&quot;Path&quot; variable in Ubuntu?"
date: 2010-03-29
forum: General Help
---

### Post by mohitd2000 on 2010-03-29
I migrated from a Windows computer onto Ubuntu. I was wondering if there is something like a path variable like in Windows? Where you don't need to be in the exact directory to execute the .exe files. For example, there's an executable called execute.exe in C:\Windows\somedir. If I add C:\Windows\somedir to my PATH variable, then I don't have navigate to C:\Windows\somedir then type execute -somecommand, I can do that from any directory. Same in linux, say I have an executable file called adb in usr/somedir. I don't want to have to navigate to usr/somedir and type adb -somecommand, I could do it from any directory

---

### Post by readycarpenter on 2010-03-29
hmm I'm not quite sure what you mean, but the current user home directory such as /home/me
is
```
~/
```

---

### Post by Ahadiel on 2010-03-29
> **mohitd2000 said:**
> I migrated from a Windows computer onto Ubuntu. I was wondering if there is something like a path variable like in Windows? Where you don't need to be in the exact directory to execute the .exe files. For example, there's an executable called execute.exe in C:\Windows\somedir. If I add C:\Windows\somedir to my PATH variable, then I don't have navigate to C:\Windows\somedir then type execute -somecommand, I can do that from any directory. Same in linux, say I have an executable file called adb in usr/somedir. I don't want to have to navigate to usr/somedir and type adb -somecommand, I could do it from any directory

Check your ~/.bashrc for PATH.

---

### Post by arvevans on 2010-03-29
Pull up a terminal screen and at the prompt "echo $PATH", without the parens
and then hit ENTER.  It should show something like this:

[INDENT]arv@arv-desktop:~$ echo $PATH
/home/arv/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin: /bin:/usr/games
arv@arv-desktop:~$ 
[/INDENT]

Each colon-separated string is a Path Variable, showing where the OS will 
look for commands, and in what order it will look.
[LIST]
[*]In Linux (any UNIX derived OS) your own personally written software is usually in /home/your_ID/bin.  This because it is a multi-user system.  
[*]System software is usually in /bin.
[*]User executable applications are in /usr/bin.  
[*]Software that you have imported and installed from other sources is usually put in /usr/local/bin/.  
[*]Things in the sbin directories are usually for administrators or administration.
[/LIST]

Actually pretty simple once you get the hang of it.
_._

---

### Post by NiGhtMarEs0nWax on 2010-03-29
i too would like to know the answer to this question.

he means add a persistent path environment variable.

much like /usr/bin is, so he can call a script or binary without typing the full path.

---

### Post by NiGhtMarEs0nWax on 2010-03-29
> **arvevans said:**
> Pull up a terminal screen and at the prompt "echo $PATH", without the parens
and then hit ENTER.  It should show something like this:

[INDENT]arv@arv-desktop:~$ echo $PATH
/home/arv/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin: /bin:/usr/games
arv@arv-desktop:~$ 
[/INDENT]

Each colon-separated string is a Path Variable, showing where the OS will 
look for commands, and in what order it will look.
[LIST]
[*]In Linux (any UNIX derived OS) your own personally written software is usually in /home/your_ID/bin.  This because it is a multi-user system.  
[*]System software is usually in /bin.
[*]User executable applications are in /usr/bin.  
[*]Software that you have imported and installed from other sources is usually put in /usr/local/bin/.  
[*]Things in the sbin directories are usually for administrators or administration.
[/LIST]

Actually pretty simple once you get the hang of it.
_._



but how do you create your own? say he wanted to add ~/random  to that list. how would he go about doing that?

---

### Post by Ahadiel on 2010-03-29
> **NiGhtMarEs0nWax said:**
> but how do you create your own? say he wanted to add ~/random  to that list. how would he go about doing that?

You can either edit /etc/profile (IIRC) or use something like the following:
```
export PATH=$PATH:~/random
```

---

### Post by NiGhtMarEs0nWax on 2010-03-29
> **Ahadiel said:**
> You can either edit /etc/profile (IIRC) or use something like the following:
```
export PATH=$PATH:~/random
```


```
export PATH=$PATH:~/random
``` works fine in a shell. echo $PATH shows it's working.

two problems.

1. I put that line in /etc/profile just at the top as it is. restarted the shell but it didn't show up.
2. when I manually added it through the current shell session, i couldn't run a script straight from the shell. usually if the working directory was the same as the script I would ./script_name
how do i run the script assuming the environment variable is working?

---

### Post by Ahadiel on 2010-03-30
1) You probably have to put it after PATH is defined initially in /etc/profile.
2) You should be able to just do script_name if it's in your PATH.

---

### Post by NiGhtMarEs0nWax on 2010-03-30
> **Ahadiel said:**
> 1) You probably have to put it after PATH is defined initially in /etc/profile.
2) You should be able to just do script_name if it's in your PATH.


alright, my second problem was a silly mistake on my behalf,the name of the script was the same as it's root directory. it doesn't like it for some reason.


this is my profile config.

```

# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022

[B]PATH=$PATH:~/test
export PATH[/B]

```

i can't see an initial declaration of PATH, but as you can see it's at the bottom, still no luck. =/

---

### Post by Ahadiel on 2010-03-30
Try adding it to the end of your ~/.bashrc

---

### Post by NiGhtMarEs0nWax on 2010-03-30
> **Ahadiel said:**
> Try adding it to the end of your ~/.bashrc


nice, perfect, works perfectly.   Thank you very much for your time good sir.  i wish there was a rep function. :)

Thanks again mate.

---

### Post by Ahadiel on 2010-03-30
Not a problem.

---

