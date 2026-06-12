---
title: "how to run ruby on rails file using cronjob"
date: 2012-05-07
forum: General Help
---

### Post by hanishjadala on 2012-05-07
hi all i am trying to run a  ruby file using cronjob but unable to create cronjob properly can any one help me out plz...

i used the following commands
crontab -e to create a conjob and i have entered the following lines

*/10 * * * * ~/Honey/eabyasbio16dec/app/controllers/cronjob.rb(ruby file)
*/10 * * * * echo "hi this is a cronjob"(to check how does it execute and where)


but it is not working properly 
then i used the command crontab -l 
where did i go wrong plz help me out..


Regards
Hanish Jadala

---

### Post by aromo on 2012-05-07
when you enter crontab -e, it opens vi to edit your crontab file.  You type your cron lines, then you have to save it.

In vi, to save and exit you have to press <ESC> and type

```
:wq
```

Once you saved and exited, crontab -l should show the contents of your crontab file.

Your second cron line will send a mail to your user with what you're echoing, that's because cron commands send their outputs (std and err) to the user via a mail message, so make sure to redirect your output to a file if you don't want to get clogged with mail messages.

If this doesn't help, please be more specific as to why it's not working properly.

---

