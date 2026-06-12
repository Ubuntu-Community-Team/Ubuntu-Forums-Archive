---
title: "Geany permissions problem"
date: 2011-01-19
forum: General Help
---

### Post by mollycule on 2011-01-19
I'm trying to run a program in Geany, and when I try hitting F5 for "execute," it just says "permission denied."  What's going on?  Pretty much, I'm trying to do the same thing as hitting Ctrl + F5 in Microsoft Visual Studio does, the "Build without debugging" command.

---

### Post by Vallard on 2011-05-02
> **mollycule said:**
> I'm trying to run a program in Geany, and when I try hitting F5 for "execute," it just says "permission denied."  What's going on?  Pretty much, I'm trying to do the same thing as hitting Ctrl + F5 in Microsoft Visual Studio does, the "Build without debugging" command.

I'm getting the same error here.
I search in the forum and find peoples with the same problem, but I didn't find the solution. x_x'

Anyone can help?

---

### Post by dunnemann on 2011-10-15
I solved this problem (permission denied ... error 126) just saving my file like "****.cpp" or "*****.c"

---

### Post by boeykes on 2013-03-16
Hello

I found the solution to this problem.
Geany doesn't make the script executable and that is why you are getting this error.
If you create your script or just an empty saved file, and than you make it executable (chmod +x filenaam.extension).
Open it again with geany en try to run it.
If everything is correct, you will see that your script is being executed.

I hope this helps.

greetings
Boeykes

---

### Post by overdrank on 2013-03-16
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

