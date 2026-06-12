---
title: "Problems with mutt"
date: 2012-08-22
forum: General Help
---

### Post by lowell.dennis on 2012-08-22
I have been using mutt successfully for a while now.  However, it recently stopped working.

If I use mutt interactively I am able to send emails, however if I try to use the command line it seems to just hang.

mutt -s "Subject" [EMAIL="name@somewhere.com"]name@somewhere.com[/EMAIL] < /tmp/body

It used to work for me like a champ, but now it just sits there and never completes and I get no error message or any other sort of indication as to what is wrong.

I have not changed my ~/.muttrc file or done anything else that I can think of that would affect mutt.

Anybody have any ideas?

-Lowell

---

### Post by irv on 2012-08-22
I don't use mutt, but maybe you can start with some simple things. To see if something is running that is interfering with the program try restarting the computer clear memory, do not start anything else and try running mutt. If the problem is still there, open another terminal and run
```
top
```
This will show you everything running and might give you a clue at what is going on.
 Now if it does the same thing, then completely remove it and try re-installing it.
This is a good place to start.

---

### Post by lowell.dennis on 2012-08-22
> **irv said:**
> I don't use mutt.
What do you use?
> try restarting the computer clear memory, do not start anything else and try running mutt.I have don this and the problem persists.
> If the problem is still there, open another terminal and run
```
top
```This will show you everything running and might give you a clue at what is going on.Nothing jumps out at me.
> then completely remove it and try re-installing it.I have done this too and it did not change things.

---

### Post by irv on 2012-08-22
You asked what I use, I use GUI mail applications.

Seeing what I recommend didn't work, then I am not sure what to try. I see that mutt has some setup involved and like I said I am not using it so hopefully someone else can jump in here.

---

