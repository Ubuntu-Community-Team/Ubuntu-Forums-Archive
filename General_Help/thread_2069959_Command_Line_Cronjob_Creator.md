---
title: "Command Line Cronjob Creator"
date: 2012-10-11
forum: General Help
---

### Post by joecron on 2012-10-11
I can not find a proper spot for this, so it is here. Moderator, please move to the appropriate place if necessary.

Can anybody use this? It is a python script to allow you to create cronjobs from the command line, including cronjobs that pop up reminders as well as send an email to make sure you got the message.

The script is at apasreader.yolasite.com. It is called joecron.

The reason I put it together was that I frequently need to create a reminder, either xx minutes from now or a few days from now.

This is easier for me to use than getting into crontab and typing in the bits that are needed.

It is also easier than using the not-so-good crontab gui programs I have seen.

It is not as useful as kalarm - nothing is; but if you are not running kde, you might prefer not to download the scads of programs you need to install it.

This little utility requires that you have notify-send installed, but I think that comes with ubuntu 12.04. It is part of the lib-notify program.

If you type joecron -h, you get a list of commands.
Here they are:

joecron mm '-reminder message of some kind'
	**** will pop up a reminder in mm minutes ****

joecron mm '+some command'
	**** will run a command in mm minutes ****

joecron
	**** by itself gets a series of prompts to create a cron job ****

joecron m h dom mon dow '+some command'
	**** creates a cron job to run a command ****

joecron m h dom mon dow '-some message'
	**** creates a cron job to create a reminder ****

joecron clear
	**** deletes all cron entries made by joecron. It
	**** targets #joecron, which is added to crontab
	**** entries made by the utility

---

