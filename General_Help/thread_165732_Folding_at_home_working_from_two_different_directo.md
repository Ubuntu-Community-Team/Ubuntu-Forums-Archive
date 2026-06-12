---
title: "Folding at home working from two different directories."
date: 2006-04-25
forum: General Help
---

### Post by rippon on 2006-04-25
I run F@H nearly 24/7.

I made a folder in my Home directory so it would be nice and clean. Normally I can cd to the directory and run F@H. It creates its workfiles inside the folder, and we are set to go. The only problem is that I wanted something that would be started automatically, and would run in the background. So I created a start up service, and I selected the .exe in the folder I made inside my home folder. Now, it has decided to create all the files in /home!  Which is really ugly and confusing! Anyone know how I can get it too run in the background and keep its files in the right folder?

Thanks.

---

### Post by rippon on 2006-04-25
Can you see this?

---

### Post by cwmccabe on 2006-04-25
[QUOTE=rippon]Can you see this?[/QUOTE]

Yes.

---

### Post by rippon on 2006-04-26
Does anyone have any idea how to fix this?

---

### Post by professor_chaos on 2006-04-26
I can try, but first whats F@H? and what do you mean by start up service? Do you mean you created a script in /etc/init.d or a cron job?

---

### Post by cwmccabe on 2006-04-26
[QUOTE=professor_chaos]I can try, but first whats F@H? and what do you mean by start up service? Do you mean you created a script in /etc/init.d or a cron job?[/QUOTE]

F@H is "Folding At Home".  See here: [http://folding.stanford.edu/](http://folding.stanford.edu/)
Sorry I'm no more help than that in this thread...

---

### Post by rippon on 2006-04-27
I went to system> preferences > sessions > StartUp Programs

Then I added a new one.

Basically If I go
./FAH-Linux-504

The 'Work' files are placed into the /Folding@Home folder, if I have it as a startup it goes into my home folder.

---

### Post by Bogg3r on 2006-04-27
I've just started using Ubuntu for the first time (linux newbie) and found this to be the best way to set F@H up... Its a script called Finstall. 

[http://fahwiki.net/index.php/A_Complete_Guide_to_Using_FINSTALL_for_NEWbies](http://fahwiki.net/index.php/A_Complete_Guide_to_Using_FINSTALL_for_NEWbies)

See how that goes for you.

---

### Post by jpkotta on 2006-05-07
I have created an installer for Ubuntu.  It can be found in the wiki.  There are a couple of threads in the forums.  You really need to search around, because most of these problems are solved (of course, *I* could have searched a bit harder for finstall, but half of the reason I did it was to learn about making reliable init scripts).

And I can tell you why it creates files all over the place.  It creates files in what ever directory you run it from.  Example:```
cd ~ ; ~/folding/FAH502-Linux.exe
``` will create files in ~, not ~/folding.

[https://wiki.ubuntu.com/FoldingAtHome](https://wiki.ubuntu.com/FoldingAtHome)

I'll also suggest that you join our team.  We just passed in to the top 400 F@H teams, but we can do a lot better.

[https://wiki.ubuntu.com/FoldingAtHomeTeamUbuntu](https://wiki.ubuntu.com/FoldingAtHomeTeamUbuntu)

---

