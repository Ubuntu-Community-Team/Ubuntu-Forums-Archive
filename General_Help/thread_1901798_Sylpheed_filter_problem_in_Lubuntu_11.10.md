---
title: "Sylpheed filter problem in Lubuntu 11.10"
date: 2011-12-29
forum: General Help
---

### Post by M_Mynaardt on 2011-12-29
Hi there!

I'm having a bit of a strange problem with the filters in the Sylpheed mail client in Lubuntu 11.10.  When I try to run them to filter email, Sylpheed just shuts down.  Which isn't particularly useful.

Does anyone know what would cause Sylpheed to crash when using filters?  And how to fix this little glitch?

Thanks in advance…

---

### Post by amjjawad on 2011-12-29
> **M_Mynaardt said:**
> Hi there!

I'm having a bit of a strange problem with the filters in the Sylpheed mail client in Lubuntu 11.10.  When I try to run them to filter email, Sylpheed just shuts down.  Which isn't particularly useful.

Does anyone know what would cause Sylpheed to crash when using filters?  And how to fix this little glitch?

Thanks in advance…

Hello there,

I have never used it but I hope this will help. Try to run it from LXTerminal and post the output here because if there is a crash or something, it should show up on the terminal.

Please, don't forget to wrap up the output with "CODE" tags.

Thanks :)

---

### Post by M_Mynaardt on 2011-12-30
> **amjjawad said:**
> Hello there,

I have never used it but I hope this will help. Try to run it from LXTerminal and post the output here because if there is a crash or something, it should show up on the terminal.

Please, don't forget to wrap up the output with "CODE" tags.

Thanks :)

Okay, I ran Sylpheed through my LXTerminal, and it crashed trying to use the filters and this was the LXTerminal result:
```
:~$ sylpheed
Segmentation fault
:~$ 
``` 

I don't know if that's much to go on, but that's the result I got...

---

### Post by M_Mynaardt on 2012-01-04
I found a couple of things that seem to be the problem with Sylpheed.  When I turned off the junk filtering, the filters *sort of* worked.

I could tell the computer to filter, but then nothing happened with a filter I told to move files with a from field that "is" address X.  When I changed the criteria to "contained"; it worked.

So, I tried another filter I had, with several "reg expression" statements.  Sylpheed crashed.  I changed those all to "contains" and it worked.  So I'm getting there.  I'm probably missing something else in the settings, but so far it looks like I just have to avoid some kinds of filtering for whatever the reason...

8)

---

