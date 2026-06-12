---
title: "MetaPost - Text Forces Image Not to Render"
date: 2010-02-03
forum: General Help
---

### Post by Dru89 on 2010-02-03
For some reason under Ubuntu 9.10 (x86 and x64), MetaPost refuses to render any images that contain text.  If you open the file for Image.1, it opens evince and it hangs indefinitely.  I can create images perfectly fine and render this as long as there is no text.  Am I missing any specific font packages or something that I should be using?  I know that it works under Windows.  I also know that on a different machine I had a while back (running Ubuntu 8.04, I believe), I had it working then.

Am I missing anything?  Has anyone else had this problem and knows how to fix it?

---

### Post by Dru89 on 2010-02-03
I am currently attempting to install texlive-full on my netbook.  If that works, I'll then do the same on my desktop later on tonight.  The only apps that I installed for LaTeX originally were:

[LIST]
[*]texlive
[*]texlive-latex-extra
[*]texlive-math-extra
[*]texlive-metapost
[/LIST]
I haven't found anything else about this after searching for a while, but I'm guessing I probably just did something stupid.  Is it also possible that this could have something to do with the fact that I am installing things using the user script [apt-fast]("http://www.mattparnell.com/projects/apt-fast-and-axel-roughly-26x-faster-apt-get-installations-and-upgrades.html") and not apt-get?

***Edit:** I've come up with a solution that works for me.  Granted, it doesn't fix my MetaPost problem, but it works.  I took the opportunity to learn Asymptote, and it works more like a "real programming language," so maybe that will be of better service.  Also, text works.  I'm still interested if anyone knows the solution, but I'm going to mark this thread as solved.*

---

