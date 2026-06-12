---
title: "How Do I Tell Which User Currently Has The Console?"
date: 2011-08-26
forum: General Help
---

### Post by msp3k on 2011-08-26
Say user1 sits down and logs in (tty8, :0).  Later, user1 locks the screen and leaves.  While user1 is gone, user2 sits down, clicks "Switch User", and logs in on the console (tty9, :1).  Users 1 and 2 come and go, each one switching to resume their desktop, and then locking when they leave.

At any given time, /usr/bin/who looks something like this:
```

    user1    tty8        2011-08-26 16:50 (:0)
    user2    tty9        2011-08-26 17:25 (:1)

```

And the output of last looks something like this:
```

    user2    tty9        :1              Fri Aug 26 17:25   still logged in
    user1    tty8        :0              Fri Aug 26 16:50   still logged in

```
Is there any way for me to tell which one *currently* has the active console?  Difficulty: command line only.

---

### Post by hasardeur on 2011-08-26
Type:

```
whoami
```

---

### Post by apollothethird on 2011-08-26
> **msp3k said:**
> Say user1 sits down and logs in (tty8, :0).  Later, user1 locks the screen and leaves.  While user1 is gone, user2 sits down, clicks "Switch User", and logs in on the console (tty9, :1).  Users 1 and 2 come and go, each one switching to resume their desktop, and then locking when they leave.

At any given time, /usr/bin/who looks something like this:
```

    user1    tty8        2011-08-26 16:50 (:0)
    user2    tty9        2011-08-26 17:25 (:1)

```And the output of last looks something like this:
```

    user2    tty9        :1              Fri Aug 26 17:25   still logged in
    user1    tty8        :0              Fri Aug 26 16:50   still logged in

```Is there any way for me to tell which one *currently* has the active console?  Difficulty: command line only.

You're have two consoles in use.  You have tty8 in use by user1.  You have tty9 in use by user2.  There are two consoles running at the same time.  They are both active.  They are both running.  I don't think there is a way to tell which user is setting at the console.  Both have active consoles.

You can notice they are both active by hitting alt-cntrl-F8 and you'll see that user1's screen.  You can hit alt-cntrl-F9 and see user2's screen.  You can hit alt-cntrl-F1 and you won't see either person's screen.  Their programs will still be running, much like they are in a screen saver.  But you can't tell which one is active and which one is in the background.  The same way you can't tell if someone is looking at the alt-cntrl-F1 or alt-cntrl-F2 or the alt-cntrl-F3 (etc) screen.  The screens are not suspended. They are all running simultaneously.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by msp3k on 2011-08-29
> **apollothethird said:**
> But you can't tell which one is active and which one is in the background.  The same way you can't tell if someone is looking at the alt-cntrl-F1 or alt-cntrl-F2 or the alt-cntrl-F3 (etc) screen.  The screens are not suspended. They are all running simultaneously.


So I guess what I really need is a way to tell which tty is currently in the foreground, or has the focus of the physical screen/keyboard/mouse.  And I don't know of a  way to do that.

---

### Post by apollothethird on 2011-08-29
> **msp3k said:**
> So I guess what I really need is a way to tell which tty is currently in the foreground, or has the focus of the physical screen/keyboard/mouse.  And I don't know of a  way to do that.

I don't think there is away except possibly some very low level screen and mouse polling.

If someone knew the objective they might have suggestions.  There are ways to send messages to the various sessions.  If the user replies to your message quickly you'll know they are physically there at that exact moment.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

