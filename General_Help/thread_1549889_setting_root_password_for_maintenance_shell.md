---
title: "setting root password for maintenance shell"
date: 2010-08-10
forum: General Help
---

### Post by tlroche on 2010-08-10
I'd like to keep root pw==sudo pw==user pw on a box with

```
$ lsb_release -ds Ubuntu 9.10
$ uname -rv 2.6.31-22-generic #61-Ubuntu SMP Wed Jul 28 02:02:56 UTC 2010
```

Just now it hung going to sleep, so I shutdown via BRS. On cold boot, HD mount failed and I got the prompt to hit Esc to goto maintenance shell. I did that, got the prompt for the root password, and entered my sudo. That failed! though it has worked before ... but I changed my user password on that box recently, and I'm pretty sure I haven't needed to fsck between then and now. I'm wondering:

[LIST=1]
[*]What do I need to do to set my root pw? I was able to C-d out of the shell, and karmic took care of itself, but I'd prefer not to rely on that.
[*]Is there a way to make my root pw always equal my user pw? If so, is that a Very Bad Idea?
[/LIST]

---

### Post by sisco311 on 2010-08-11
> **tlroche said:**
> 
[LIST=1]
[*]What do I need to do to set my root pw? I was able to C-d out of the shell, and karmic took care of itself, but I'd prefer not to rely on that.
[*]Is there a way to make my root pw always equal my user pw? If so, is that a Very Bad Idea?
[/LIST]

[list=1]
[*]Well, you have to change the root account password.

[*]No, you have to change the root password manually. It's not a bad idea, but it's kinda futile, since sudo, by default, allows you to run any command as root. 
[/list]

The root account password is locked by default, but the sulogin program in Ubuntu is patched to handle the default case of a locked root password, which means that, if the root password is locked, you can boot in single user mode (Recovery Mode and/or BusyBox shell) without a password.

[uhelp]community/RootSudo[/uhelp]

---

### Post by bodhi.zazen on 2010-08-11
> **tlroche said:**
> I'd like to keep root pw==sudo pw==user pw on a box with

```
$ lsb_release -ds Ubuntu 9.10
$ uname -rv 2.6.31-22-generic #61-Ubuntu SMP Wed Jul 28 02:02:56 UTC 2010
```Just now it hung going to sleep, so I shutdown via BRS. On cold boot, HD mount failed and I got the prompt to hit Esc to goto maintenance shell. I did that, got the prompt for the root password, and entered my sudo. That failed! though it has worked before ... but I changed my user password on that box recently, and I'm pretty sure I haven't needed to fsck between then and now. I'm wondering:

[LIST=1]
[*]What do I need to do to set my root pw? I was able to C-d out of the shell, and karmic took care of itself, but I'd prefer not to rely on that.
[*]Is there a way to make my root pw always equal my user pw? If so, is that a Very Bad Idea?
[/LIST]


The only time you are prompted for a password when booting to a recovery shell would be if you are:

1. Using an encrypted system -> Enter encryption password.

2. If you manually set a root password -> use root password, not sudo.

You can use the same password for both your user and root if you like, but IMO it does not add much, if anything to security to do so and only adds hassle.

Keep in mind, if someone has pyysical access they can bypass both your user and root password very easily.

IMO, from what you describe, I would advise you stay with the defaults (use sudo, leave the root account locked) and encrypt your system (using the alternate CD). That would increase security.

---

