---
title: "Mouse cursor"
date: 2006-05-24
forum: General Help
---

### Post by Ramses de Norre on 2006-05-24
I just dist-upgraded to dapper but I have a little problem: when I get to gdm I get a little black mouse cursor, which remains when I log into fluxbox.
I used to have the human cursor which I liked a lot, but I can't figure out how to change the cursor for gdm and fluxbox.

Anybody who knows?

---

### Post by Stinger on 2006-05-24
What does your /etc/alternatives/x-cursor-theme file say ? 
Mine says:
```
[Icon Theme]
Inherits=Human

```
:-k
Oh ! it's a symlink to /usr/share/themes/Human/cursor.theme
Mabe you are missing this symlink , or your symlink is is pointing somwhere else ?

---

### Post by Ramses de Norre on 2006-05-24
That didn't do.. the file is exactely the same..

---

### Post by Stinger on 2006-05-25
Just for the fun of it I tried renaming my /etc/alternatives/x-cursor-theme file to cursor-theme instead , this would prevent it from loading correctly when restarting the Xserver , and default to the black default mouse cursors.:rolleyes: 

That was exactly what happend when I restarted the Xserver (ctrl-alt-backspace).
Now if I select the human-cursors in my Gnome-session I have the human-cursors back but only in my Gnome-session , not in my Xfce-session and gdm , here I still have the default black mouse cursors.
So I seem to be able to duplicate your problem !8) 

My best guesses would be:
1. Something is preventing the /etc/alternatives/x-cursor-theme file from loading correctly.

2. There could be a spelling or syntax error in the /etc/alternatives/x-cursor-theme file.

3. It could be a file permission problem.

hope it helps troubleshooting;)

---

### Post by Ramses de Norre on 2006-05-25
```
ramses@icarus:~$ ls -lA /etc/alternatives/|grep x-cursor
lrwxrwxrwx 1 root root  36 May 25 15:55 x-cursor-theme -> /usr/share/themes/Human/cursor.theme
ramses@icarus:~$ ls -lA /usr/share/themes/Human|grep cursor
-rwxr-xr-x 1 root root   28 May 25 16:43 cursor.theme

```
The contents of that file:```
[Icon Theme]
Inherits=Human

```
And I couldn't find no mentions in the X log nor in .xsession-errors of an error while loading the cuirsor..

Any idea why it isn't working? All seems fine to me..

---

### Post by Stinger on 2006-05-25
Here you can see the permissions on my files:
```
ls -lA /etc/alternatives/|grep x-cursor
lrwxrwxrwx  1 root root  36 2006-02-20 22:54 x-cursor-theme -> /usr/share/themes/Human/cursor.theme

```
and
```
ls -lA /usr/share/themes/Human|grep cursor
-rw-r--r--  1 root root  28 2005-10-05 01:13 cursor.theme

```

As you can see the  /usr/share/themes/Human/cursor.theme file differs a bit.:-k 

The contents of /usr/share/themes/Human/cursor.theme is exactly the same as yours.

I'll try my xubuntu dapper machine too and see what it gives me.

---

### Post by Stinger on 2006-05-25
[QUOTE=Stinger]
I'll try my xubuntu dapper machine too and see what it gives me.[/QUOTE]
Well Xubuntu only comes with the default black mouse cursors , so I decided to copy the Human cursor theme from Breezy.
I copyed /usr/share/themes/Human and /usr/share/icons/Human
Made a symlink from usr/share/themes/Human/cursor.theme to /etc/alternatives/x-cursor-theme , made sure the permissions where like Breezy , hit ctrl-alt-backspace and held my breath:mrgreen: 

It worked !8) 
Now I have the Human cursor theme in gdm and my Xfce-session on my Xubuntu dapper too.

---

### Post by Ramses de Norre on 2006-05-25
I came up with a fairly simple solution: ```
sudo aptitude reinstall ubuntu-artwork
``` all seems fine now.. 
One issue less to solve after dist-upgrading..

---

### Post by Sye d'Burns on 2006-06-18
Strangely enough, xfce stopped using the human mouse theme after the latest (huge) batch of downloads in Dapper and instead defaulted to the black mouse cursor. 

Sudo aptitude reinstall ubuntu-artwork fixed it. good idea Ramses!

---

