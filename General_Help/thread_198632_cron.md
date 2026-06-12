---
title: "cron"
date: 2006-06-17
forum: General Help
---

### Post by evaristegalois on 2006-06-17
This is puzzling. I have a perl script called sendEmail which will send an email from the command line. I tried sending a timed email with cron. But even though the command 

sendEmail [etc]

yields exactly the desired result if executed directly on the command line, putting the same command into my crontab does nothing, not even log output. cron works fine with other commands, for example 

ls / > test.file

ny suggestions?

--evaristegalois

---

### Post by slothjammin on 2006-06-17
#Create a log file with a redirect for the Standard Error to the Standard Output so you get errors too.
cmd >> logfile 2>&1
#Then mail the log file
mail -s "logfile for cmd" <log.file

---

### Post by evaristegalois on 2006-06-17
no trace, even after following your advice. there is no entry in the logfile, even though if I enter exactly the same command on the shell, it both works and leaves an entry in the logfile. But not so when running cron. Here is my cron entry:

46 13 17 6 * sendEmail -f "Me <myemail@adress>" -t "Me <myemail@address>" -m "this is a test" >> /home/logfile 2>&1

the same command on the command line will work while when cron runs there is nothing in logfile. Other simpler commands on cron work just fine.

--evaristegalois

---

### Post by scxtt on 2006-06-17
what version of cron are you using? anacron? (doesn't look like it) ... what are the permissions on your "sendEmail" scripts?  this seems like a user/permission problem ... are you using /etc/crontab to set it up, or just doing a crontab -e from the command line logged in as a user?  what prog. is "sendEmail" using?

---

### Post by evaristegalois on 2006-06-19
my cron version is Vixie cron

sendEmail is a perl script, the permission of the script is rwxr-xr-x (which should be OK?) 

I write the cron command in a file, type ``crontab filename'' on the shell and then use crontab -l to check if all is well.

---

### Post by scxtt on 2006-06-19
my only suggestion would be to use anacron, only cause it's the only one i ever use and i've never had that problem ... but i generally edit /etc/crontab, and being able to tell it what user to run it as is a nice feature ...

---

### Post by evaristegalois on 2006-06-22
I was able to create a log file by using the option "-l /var/log/sendEmail" to my sendEmail command. The entry reads

Jun 22 10:02:01 stefan sendEmail[15607]: ERROR => You must supply both a username and a password to use SMTP auth.

Now, I did supply a username and password (as I did on the command line where it worked without a hitch), but I'll figure out why cron gives me trouble. More later.

--evaristegalois

---

### Post by evaristegalois on 2006-06-24
One of those things: sendEmail needs my username on the mail server which includes the character "%". That character, however, happens to be a special character in cron. Prefacing it with a backslash solved the problem. From the command line, I now write

sendEmail [etc] -xu thisandthat%hereandthere

whereas in cron I have to write

* * * * 0 sendEmail [etc] -xu thisandthat\%hereandthere

Thanks for everybody's help, especially Brandon who programmed sendEmail. It's a neat little program and very useful for scheduled emails and writing emails with your favourite text editor, such as vi or emacs.

--evaristegalois

---

