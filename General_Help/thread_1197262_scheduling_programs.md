---
title: "scheduling programs"
date: 2009-06-25
forum: General Help
---

### Post by canabal on 2009-06-25
Hey guys,

I also posted this in a crontab tutorial, but I figured I should post it here as well because I may get some non-crontab advice.

> 
Is there a way to schedule a program for a certain amount of time and then shutdown at the end?

Basically, I want to have a slideshow start with feh, so my command inside crontab is "0 0 * * * feh -r -z -D 5 -F -Z --hide-pointer /home/username/Pictures" those -Z etc are just to get the slideshow how I want... i.e. fullscreen.

When I run this command in shell it starts fine, but with cron it does not.

I want it to run for a time because at a certain time (8:00) I want it to shutdown and run firefox for an hour on the weather channel.  Then at 9 to shut firefox and start the slideshow again.

I am making a digital picture frame that shows the weather for an hour before I go to work basically.


So any cron or non-cron ideas to do this?

---

### Post by Villiam on 2009-06-26
From this link: [http://maketecheasier.com/schedule-and-automate-tasks-in-ubuntu/2007/12/11](http://maketecheasier.com/schedule-and-automate-tasks-in-ubuntu/2007/12/11)
"In Ubuntu (or basically Linux), task automation used to involve writing shell scripts and setting cron job, and this is not an easy thing for a new user to do. Luckily, there is the **Gnome-schedule** that come with a simple graphical interface and makes task scheduling a breeze."

check the [link ]("http://maketecheasier.com/schedule-and-automate-tasks-in-ubuntu/2007/12/11")to read more (step by step guide) ...........

[ubuntu]("http://www.linux-archive.org/ubuntu-user/")

---

### Post by canabal on 2009-06-26
Thanks, That is what I have been using to configure cron, so no go there.

---

### Post by canabal on 2009-06-26
I added the line export DISPLAY=:0 to the command and now it works.

Thanks for the help anyway.

I am going to try to make a tutorial and post it up soon.

---

