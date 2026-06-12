---
title: "Problem with export variable"
date: 2011-06-14
forum: General Help
---

### Post by sigma_z_1980 on 2011-06-14
I've installed Aptana Studio 3 and wanted to make the path to the executable file permanent, so I added in .bashrc

PATH=$PATH:/home/MyPath/'Aptana Studio 3'
export PATH

The problem is, it didn't work.

What's interesting, when I do it in terminal, for temporary access, it works just fine. What could be wrong here?

---

### Post by blueridgedog on 2011-06-14
If you open the Run Application dialog and enter 

```
echo $PATH >/tmp/p
``` 

and then 

```
cat /tmp/p
```

You will see that the gnome environment does not source your bash configuration files.  The solution is to place a symlink in the gnome path to your item of interest or create a bash script that sets your path variable, then set that to run when logging in via system preferences and start up applications.

I can help you with the script if you need it, but given your tweaking of the PATH variable, you may have that down pat.

---

### Post by mc4man on 2011-06-14
Just out of curiousity - is it improper in such a case to add a new section to ~/.profile?
Ex.
if [ -d "$HOME/test1" ] ; then
    PATH="$HOME/test1:$PATH"
fi

---

### Post by blueridgedog on 2011-06-14
My quick search indicated that the gnome environment was not getting the path from .profile, but I did not spend a great deal of time looking.  I personally don't mind putting things into .profile (or rc.local for that matter...which would work for the issue at hand).

---

### Post by mc4man on 2011-06-14
> **blueridgedog said:**
> My quick search indicated that the gnome environment was not getting the path from .profile, but I did not spend a great deal of time looking.  I personally don't mind putting things into .profile (or rc.local for that matter...which would work for the issue at hand).
Thanks - it seems to here, (11.04, 11.10 w/dm), was just on my mind because of current [behaviour of lightdm in 11.10]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/794315") which doesn't. (so no ~/bin added automatically if present

---

### Post by AlphaLexman on 2011-06-14
This may seem obvious to some, but did you **source** the ~/.bashrc after you changed it?
```
. ~/.bashrc
```
EDIT: You cannot just change the .bashrc file without re-reading it!

---

### Post by sigma_z_1980 on 2011-06-15
thanks for asking, it's the second time i'm getting this message, which is something like 'syntaxis mistake

`PATH=$PATH:/home/MyPath/Aptana Studio 3'

what have I done wrong? 

> **AlphaLexman said:**
> This may seem obvious to some, but did you **source** the ~/.bashrc after you changed it?
```
. ~/.bashrc
```EDIT: You cannot just change the .bashrc file without re-reading it!

---

### Post by sigma_z_1980 on 2011-06-15
thanks for this, could you pls be more specific about 'tweaking of PATH variable' What have I done wrong? 

> **blueridgedog said:**
> If you open the Run Application dialog and enter 

```
echo $PATH >/tmp/p
```and then 

```
cat /tmp/p
```You will see that the gnome environment does not source your bash configuration files.  The solution is to place a symlink in the gnome path to your item of interest or create a bash script that sets your path variable, then set that to run when logging in via system preferences and start up applications.

I can help you with the script if you need it, but given your tweaking of the PATH variable, you may have that down pat.

---

### Post by sigma_z_1980 on 2011-06-15
OK I think I've sorted out the situation: for some reason .bashrc didn't like Russian characters (I know I never mentioned that, but anyway...). 

I've installed Aptana Studio to a different directory, and it works fine.

---

### Post by AlphaLexman on 2011-06-15
> **sigma_z_1980 said:**
> `PATH=$PATH:/home/MyPath/Aptana Studio 3'
what have I done wrong?
You would need to use double quotes (") with the variable to invoke variable expansion within the variable, and to avoid having to escape the spaces in the pathname.

You may have erroneously copied output from the terminal, which may have added the backtick (`) at the beginning, and the single_quote (') at the end of your variable definition. If you didn't make that error, do NOT add the backtick or single_quote to the variable definition.

Here is an example of properly quoting your variable:
```
PATH="$PATH:/home/MyPath/Aptana Studio 3"
```

Good Luck!

---

