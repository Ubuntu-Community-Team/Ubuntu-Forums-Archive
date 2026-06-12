---
title: "How to Schedule button to be clicked at a certain time?"
date: 2012-01-19
forum: General Help
---

### Post by johnmollaghan on 2012-01-19
Is there any application that will allow you to specify that a certain area of the screen would be clicked at a certain time.

Example...

The application I have has a button named "Begin" on it. I want to be able to say that at 3am, that button should be clicked.

Thanks

---

### Post by Buntumatic on 2012-01-19
That I do not know, however, a cronjob can execute foo --begin. 
Maybe I should explain. In Linux/UNIX world apps take command line options. Whatever you need to execute there probably is a CLI command to perform it, consequently you can add it to your crontab. Or just use **at** for one time execution.

---

