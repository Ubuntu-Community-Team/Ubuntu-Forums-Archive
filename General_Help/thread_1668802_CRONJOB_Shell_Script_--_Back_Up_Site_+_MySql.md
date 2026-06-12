---
title: "CRONJOB Shell Script -- Back Up Site + MySql"
date: 2011-01-16
forum: General Help
---

### Post by Masked Crusader on 2011-01-16
Hey all.

I am looking for a shell script to backup 2 site folders in my home directory and then 3 databases (all on the same server of course).  

I also want these shell script to run every night at midnight, server time.

Anyone have any good resources to put something like this together?

Thanks!

---

### Post by Crusty Old Fart on 2011-01-16
Yup...I've been doing it for about ten years. At the server, I have a cron job set up to make a bzip2 tarball of everything I want backed up. That happens at 11:00pm server time.

At Midnight, my computer is set up to run a cron job that logs into the server via SSL, downloads the bzip2 tarball to one of my hard drives, and then closes the SSL connection.

In order to make this work, I think you'll need your hosting company to have your site on a Linux/Unix server rather than a Windoze server. You'll also need shell access to the server. Not all hosting companies allow that. Finally, you'll need to be able to schedule cron jobs at the server. Again, not all hosting companies allow you to schedule cron jobs.

Before we begin writing the scripts, one for your hosted server account and one for your home computer, as well as setting up the crontabs, the requirements in the paragraph above should be verified.

If you don't mind saying, the domain name of your site, and the name of your hosting company would help.

---

