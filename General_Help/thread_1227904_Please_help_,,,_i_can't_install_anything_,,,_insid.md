---
title: "Please help ,,, i can't install anything ,,, inside a screenshot of the error"
date: 2009-07-31
forum: General Help
---

### Post by Fayiz on 2009-07-31
[CENTER][SIZE=5]Hello[/SIZE]

[SIZE=5] I can not install any software because there is an error shows after downloading the packages and when attending to install them ...[/SIZE]

[SIZE=5] Here is a screenshot of the error >>>[/SIZE]  
[/CENTER]
 
[IMG]http://www.l44l.com/upfiles9/xt040859.png[/IMG]

[CENTER][SIZE=6][COLOR=Red]

Please anyone can help me here ???...[/COLOR][/SIZE][/CENTER]

---

### Post by bryncoles on 2009-07-31
try the following commands in a terminal (applications -> accessories -> terminal):

```
sudo dpkg-reconfigure -a
sudo apt-get autoremove
sudo apt-get autoclean
```

the first will attempt to fix whatever is wrong. the second two will free up some space. after the first 'sudo' command you'll be prompted for your password, though it wont appear as you type. this is normal, and a security feature. just type your password and press return. 

post back if it works, or any error messages you get

---

### Post by Fayiz on 2009-07-31
[B][COLOR=Red]I have tow options ,,,

witch one should i go with ???[/COLOR][/B]

[IMG]http://www.l44l.com/upfiles9/v4442602.png[/IMG]

---

### Post by t0p on 2009-07-31
Unless you have a particular reason to not trust certificates, I'd suggest you select Yes.  That's what I'd do.

I would also suggest that you start a new thread when you want help with a new problem, and give it a descriptive title so other folk can get an idea of what the issue is.  If you just keep tagging new problems onto the end of this thread, you are going to find you get less helpful replies as people will just assume you're talking about the same problem as before.

Also, when someone gives you advice and it works, it's good to say so.  For instance, bryancoles suggested you try 3 commands: sudo dpkg-reconfigure -a, sudo apt-get autoremove and sudo apt-get autoclean.  Now you're asking about something else, so one of bryancoles' suggestions must have worked.  So can you just tell us which command worked? Then if someone else has the same problem in the future and searches the forums for a fix, that someone will see this thread and will know which command sorted out the problem. 

Oh, and a "thank you" to bryancoles wouldn't go amiss.

---

### Post by Fayiz on 2009-07-31
[CENTER][COLOR=Red][SIZE=5]I run the first command only
then i found two choices
about certification
I choose yes 

and I am progressing now :D
[/SIZE][/COLOR][/CENTER]

---

### Post by bryncoles on 2009-07-31
like t0p says, just accept the defaults it throws at you, unless you know what you're doing / have reason to suspect the defaults. 

and when you're all done and working again, mark the the thread as 'solved' (it used to be in thread tools). or put an edit in your first post saying 'fixed now, cheers everyone', or a last post to the same effect. then other people having the same problem will know there's a solution which works!

between us all, we'll have you up and running in no time! ;)

---

### Post by Fayiz on 2009-07-31
[CENTER][SIZE=4][COLOR=Black]To be honest with you[/COLOR][/SIZE][SIZE=4][COLOR=Black]

[/COLOR][/SIZE][SIZE=4][COLOR=Black]I quit the terminal ,,, because i entered in deep configurations[/COLOR][/SIZE][SIZE=4][COLOR=Black]

[/COLOR][/SIZE][SIZE=4][COLOR=Black]and i didn't know what to do[/COLOR][/SIZE][SIZE=4][COLOR=Black]

[/COLOR][/SIZE][SIZE=4][COLOR=Black]So ,,, i closed the terminal[/COLOR][/SIZE][SIZE=4][COLOR=Black]



[/COLOR][/SIZE][SIZE=4][COLOR=Black]I don't know !!! ,,,  i will stick with this problem rather than facing bigger problem[/COLOR][/SIZE][SIZE=4][COLOR=Black]
[/COLOR][/SIZE][/CENTER]

---

### Post by bryncoles on 2009-07-31
fair enough. can you post the full error code from the original problem then? i suspect theres more to it than is shown in the original screen-grab...

---

