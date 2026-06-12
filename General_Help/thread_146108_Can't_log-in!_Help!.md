---
title: "Can't log-in! Help!"
date: 2006-03-17
forum: General Help
---

### Post by Tosa on 2006-03-17
Hi everybody,

I've been a happy (k)ubuntu user for two months. An hour ago I loged-out and restarted my computer, but I can't log-in any more. I type my password and then I'm prompted to type it again, and again, and again...
I've tried console log-in and it works! The problem is I don't know what to do next. I typed kdm to try starting graphics, but all I got was *only root wants to run kdm*...

What should I do to have kubuntu working again?
(I'm in Win now, the first time after a month and a half...)

---

### Post by gborzi on 2006-03-17
This has happened to me some times (with other distributions too). In my cases it was:
a) the partition containing /home was full: log in a console, check with df if the partition is full and delete some file (you don't need to delete much, only to create some small free space);
b) due to some user (me)/system mistake, the ownership of some file was changed from the normal user to some other user or the superuser: log in the console and type chown -R <your username> .
Every time kdm (or any other login manager) starts the window manager, there is the need to write some file in your home directory, so if this is no longer possible you can't login graphically.

---

### Post by Tosa on 2006-03-17
Thanks for the reply.

a) I've checked and there is planty of space.

b) I've tried chown -R <username> but got *too few arguments* as a reply. Well, I did it literaly as you wrote it; have no idea about commands and syntax in linux. Am I missing something?

---

### Post by Rouge8 on 2006-03-17
```
sudo chown -R username /home/username
```

---

### Post by Tosa on 2006-03-18
Thanks.

I did it and this time no error messages.

Unfortunately, no luck either. Still the same, login is going round, round...
When I typed kdm, there was again *only root wants to run kdm*. Then I tried *su kdm*, but nothing happend.

I'm getting a bit desperate...

---

### Post by gborzi on 2006-03-18
[QUOTE=Tosa]Thanks for the reply.

a) I've checked and there is planty of space.

b) I've tried chown -R <username> but got *too few arguments* as a reply. Well, I did it literaly as you wrote it; have no idea about commands and syntax in linux. Am I missing something?[/QUOTE]
The command was "chown -R <username> ." the final dot meaning the current (i.e. home) directory.
Look for errors in your ~/.xsession-errors file, and eventually post it here.

---

### Post by Tosa on 2006-03-18
Thank you guys for your help. I'm in Linux again. :D 

Neither *sudo chown -R username /home/username* nor *chown -R <username> .* did the trick. It couldn't have, I suppose, 'couse I've made a mess.
I was looking at a wiki to enable 5 buttons on my mouse and I put this
	[I]Option		"Emulate3Buttons"	"true"
	Option		"Buttons"	       	"9"
	Option		"ZAxisMapping"		"6 7"[/I]
in my xorg.conf, per wiki. Before, it was
	*Option		"Buttons"	       	"7"*
Then there were some other things to do and finally a note that it would enable 5 buttons mice in firefox only. Mine allready worked in FF so I quit it without doing those other things... In the end Buttons 9 instead of 7 messed up login...:oops:

---

