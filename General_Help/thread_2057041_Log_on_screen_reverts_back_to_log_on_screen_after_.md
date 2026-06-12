---
title: "Log on screen reverts back to log on screen after entering password"
date: 2012-09-12
forum: General Help
---

### Post by CampLife on 2012-09-12
[FONT=Arial]Ok..I'll explain what I did wrong, and then what I did to fix, which led me to my current dilemma.

I thought I was going to be a smartypants and change my password to something really easy.  Well, I goofed it up.  When I tried to log on, I couldn't.

So I accessed the root shell to change password, but encountered " change password authentication token manipulation error".  I was able to get around that with [SIZE=2]"[/SIZE][/FONT][SIZE=4][FONT=Arial][SIZE=2]mount -o remount,rw /"[/SIZE][/FONT][SIZE=4][SIZE=4][FONT=Arial][SIZE=2], and successfully changed the password.

[SIZE=2]Now, the problem: When I [SIZE=2]enter the password on the log on screen[/SIZE], the screen goes black for a second[SIZE=2], as if it were [SIZE=2]transitioning to an active [SIZE=2]screen, but then it reverts back to the log on screen.

[SIZE=2][SIZE=2]Update: Ran across [SIZE=2]a suggestion to Control+Alt+F1 to get a terminal.  I did that, [SIZE=2]and entered my logon and password.

[SIZE=2]I get this:
[SIZE=2][SIZE=2]keyct1[SIZE=2]_search: Required key not available
[SIZE=2]Perhaps try the interactive 'ecryptfs-mount-private'

[SIZE=2]What does that mean?

[SIZE=2]Thanks[SIZE=2].[/SIZE][/SIZE]
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT][/SIZE][/SIZE][/SIZE]

---

### Post by Ranko Kohime on 2012-09-12
Generally ecryptfs is used for encrypted home folders.  I'm going to assume you have intentionally encrypted yours.

Typically, when it kicks you right back out to the login screen, it means that the home folder did not decrypt upon login, which can sometimes be an issue when changing the user password, as the folder encryption relies on the user password to decrypt.

You might find some potential solutions in this thread: [http://ubuntuforums.org/showthread.php?t=1223354](http://ubuntuforums.org/showthread.php?t=1223354)

---

