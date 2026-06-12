---
title: "Three more basic questions."
date: 2011-01-16
forum: General Help
---

### Post by Crux_Dissimilata on 2011-01-16
1. Is it possible to link to a program that runs in the terminal form the menu?

2. Why is it that after I install something and place it in the menu I get a warning that I am not running it as admin and some features might not work, every time I open it and how do I run it as admin?

3. Where can I find more icons online to replace the question mark boxes in the menu?

---

### Post by James78 on 2011-01-16
2. What program are you using? What is the exact (error?) message you're getting?
3. [http://gnome-look.org/](http://gnome-look.org/)

---

### Post by Godspell on 2011-01-16
> **Crux_Dissimilata said:**
> 1. Is it possible to link to a program that runs in the terminal form the menu?

2. Why is it that after I install something and place it in the menu I get a warning that I am not running it as admin and some features might not work, every time I open it and how do I run it as admin?

3. Where can I find more icons online to replace the question mark boxes in the menu?

1. Please try System -> Preferences -> Main Menu OR type "alacarte" in terminal (without the quotes).

That will bring up a window in which you can add/remove programs as well as re-arrange their folders/icons.

If you click on "Properties" of a script or a program, whichever you wish to run on terminal, there's an option called "Type". You can choose "Application in Terminal" there :)
In short, Properties -> Type -> Application in Terminal.

2. Do you not have admin rights for your account? e.g. are you using a shared PC or something.
Usually, whenever in need of admin rights, Ubuntu asks you to enter password.
Can you tell us what version of Ubuntu you're using?
Sorry, I can't be more helpful on this.

3. This probably isn't the right answer but can you not just google it and use whatever you can find? I do the same for my Spotify (since its icon doesn't show by default).
Or are you looking for specific ones?

Thank you.

Regards,
GS

---

### Post by Crux_Dissimilata on 2011-01-16
I am the administrator, I installed Ubuntu yesterday. Downloaded it from the website so it should be the latest version.

The error I get is:
> **Non-root user**
You are trying to run Zenmap with a non-root user!

Some Nmap options need root privileges to work

Next to that. Adding a program that runs in the terminal like how you described results in it opening the terminal and closing it right after.

---

### Post by efflandt on 2011-01-16
If it is an X program that needs to run as root, put **gksu** (and a space) before the command.  Or if it is a terminal program use **sudo**.

But do not do that randomly for all programs, only for ones that need admin or root privileges.

If running some sort of script in a terminal from a launcher or menu and you want to see the output, you could put **sleep 5** (or 10) at the end of the script itself, or however long you want it to pause in seconds.  I have not figured out how to get a script in a Terminal launcher to pause until you press a key (even if that works run from a terminal that is already open).

---

### Post by sanderd17 on 2011-01-16
[I]It's a bit a hacky solution, but if you want to keep the terminal open, you can install xdotool
```

sudo apt-get install xdotool

```

say you want to execute the "top" command, then you should use
```

gnome-terminal && xdotool key t+o+p+Return

```
In fact, that's starting the terminal and manually sending the t,o,p and return keys to it. It's not a beautiful solution, but it works.

If someone has another solution: please use the other one.
[/I]
EDIT: Forget about that: I found a better solution.

Go in the terminal to edit -> profile preferences, go in the tab "title and command" and change the last option "when the command is terminated" to "leave terminal open". I don't use the English version, so some things may be translated wrong.

---

### Post by Godspell on 2011-01-18
> **Crux_Dissimilata said:**
> I am the administrator, I installed Ubuntu yesterday. Downloaded it from the website so it should be the latest version.

Sorry for replying late. I'm afraid I don't have a solution in this case but hopefully, one of the replies here may do the trick.

I found some articles, though.> 
[http://www.tonysnerdblog.com/?cat=21](http://www.tonysnerdblog.com/?cat=21)
[http://ubuntuforums.org/archive/index.php/t-763719.html](http://ubuntuforums.org/archive/index.php/t-763719.html)

Let us know how you get on.

Regards,
GS

---

