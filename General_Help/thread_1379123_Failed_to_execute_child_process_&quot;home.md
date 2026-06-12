---
title: "Failed to execute child process &quot;/home"
date: 2010-01-12
forum: General Help
---

### Post by villem123 on 2010-01-12
Hi all, 

I can't follow up what I did, but all applications (few ones used with Wine and thunderbird 3.0) refuse to run. Using a custom made application switchers give error message **"Failed to execute child process "/home/..." (Permission denied)"**. I can browse the folders and open files in home folder, but when I try to run i.e. script for launching thunderbird, it open only in text editor (in my case Mousepad). When trying to launch via terminal, bash: ... : Permission denied appears.

Any ideas or hints.

---

### Post by Tourdog on 2010-01-12
almost the same problem............   what is happening?   I can not access "Ubuntu Software Center".   I get that same "Failed to ex .............................. process"/home/  etc.      :(

---

### Post by Flos Headford on 2010-09-16
Identical problem - wrote a shell script, put an icon on the panel and pointed it to the shell script. Ugraded to 10.04, and I now get
Error  Could not launch application
Failed to execute child process "/home/user/directory/script.sh" (Permission denied)
I checked the file is -rwxrwxrwx
NOBODY ought to get that message, surely!
Flos

---

### Post by Flos Headford on 2010-09-17
I think I have nailed this one.
I read a long discussion on using bitorrent under Linux (I have no interest in using torrent to hog bandwidth, but the same error cropped up there, too). By analogy with the solution there, I decided to use the terminal and try, instead of
```
me@mycomputer:~/runabc$ ./runabc.sh
bash: ./runabc.sh: Permission denied
```
this
```
me@mycomputer:~/runabc$ bash runabc.sh
```
It worked!
So, I altered my gnome panel launcher's target from
```
/home/me/runabc/runabc.sh
```
to
```
bash /home/me/runabc/runabc.sh
```
and that, also, works!
(It seems that between U9.04 and U10.04, the default shell {including the one used by the terminal} has been changed, and you haven't been told.
Research elsewhere indicates that it may be dash; I don't know how to confirm that.)
I will leave it to the Original Poster to mark this thread solved, if it works for them.
Phil Headford

---

