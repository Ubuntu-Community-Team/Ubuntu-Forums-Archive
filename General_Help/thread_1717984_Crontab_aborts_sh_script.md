---
title: "Crontab aborts sh script"
date: 2011-03-30
forum: General Help
---

### Post by Don Barnett on 2011-03-30
I am hoping someone can explain.
I have a sh script which when executed from command line works perfectly but when executed via cron it prints out the date and dies.  I attached the script as a txt file

the crontab line is:
15,45 5-23 * * * /var/www/domain/GetOrdersFtp >> /var/www/domain/logs/GetOrders_log.dat

Thanks

---

### Post by blind2314 on 2011-03-30
Cron's PATH isn't the same as yours when you run the script. Therefore, there is most likely a command in that script that Cron doesn't know about, due to its truncated path. To get around that, fully path the commands in the script.

---

### Post by Don Barnett on 2011-03-30
I am not sure I understand.  Other than the normal sh commands all the paths are fully qualified.  I run a number of other scripts through cron and have not had this problem in the past.

---

### Post by blind2314 on 2011-03-30
If all the commands you're using in this script are actually fully pathed, then my idea isn't correct. It's strange that they are, unless you're very deliberate when you write scripts..most people don't bother fully pathing everything.
 
What I meant was that Cron wouldn't know about 3rd party commands or applications you might be using in your script. For example, if you had a command called foomanchu, that you installed as yourself, you could run it with ```
foomanchu -options -whatever filename.txt
```
 
However, Cron would have no idea what foomanchu is, because it doesn't exist in its PATH. So, it would see the command, not know what to do with it, and exit with an error message.
 
You can check /var/log/syslog, and look for any cron related entries to see if its throwing an error.

---

### Post by Don Barnett on 2011-03-30
I just check the syslog and it shows the script has having run successfully but again the only output was the date.  I also rechecked the script and can not find any comands that do not have a fully qualified path.  At a minimum it should place after the date: "No Files to transfer - Finished"

Is this valid in cron?  It seems to be on the command line.

while true; do
...
done

I run this loop until it hits a break.

---

### Post by Krytarik on 2011-03-30
How about that?:
```
    ftp -v < /var/www/domain/ftpScripts/GetOrdersFtpScript

```
```
    **/usr/bin/**ftp -v < /var/www/domain/ftpScripts/GetOrdersFtpScript

```
Although one would expect an error message in the log, right?

Anyway, you may just try it.

Greetings.

---

### Post by Don Barnett on 2011-03-30
I tried the /usr/bin/ftp but no change.  I then put an echo before and after the while loop.  In command mode both echo's respond therefor the while loop executed.  In cron, only the first echo is executed.  Therefore it has to be the while command that is causing the failure but I have no idea how to fix it.

echo "Starting While Loop"
while true; do
	echo "In While Loop"

---

### Post by Krytarik on 2011-03-31
I studied the script a bit, and although I don't know why the execution of the while/do/done-loop doesn't even get started, it seems to me that those loop, even if the included process is successful, runs indefinitely. Is that correct? If so, you should modify the loop to include a conditional. Maybe that also fixes the actual issue.

---

### Post by Don Barnett on 2011-03-31
Actually after the nested while that reads through the file, there is a condition statement that tests the result of the file comparisons.  In each case there is a break statement which kills the while true loop.  The break after the echo "Transfer failed - Starting Over" statement is there temporarily to prevent an endless loop.  I was just being lazy and didn't set a loop counter.

---

### Post by Krytarik on 2011-03-31
> **Don Barnett said:**
> The break after the echo "Transfer failed - Starting Over" statement is there temporarily to prevent an endless loop.  I was just being lazy and didn't set a loop counter.
Ah, that makes sense then. I assumed that the script is set up like it's meant to be, and didn't look up the "break" command for the same reason, laziness. I should have just done so. ;-) Instead I simply concluded that "break" only breaks the current loop round and "starts over" again.

---

### Post by DaithiF on 2011-03-31
capture stdout to your log file too so any error messages get logged:
15,45 5-23 * * * /var/www/domain/GetOrdersFtp >> /var/www/domain/logs/GetOrders_log.dat 2>&1

and add some echo statements at various points so you can see progress and figure out the point of failure.

i notice you're reading in ls -l output -- be aware that ls can change the number of columns it outputs depending on the locale ... the date field can look like **2010-10-29** or **Oct 29**
... crucially that means that if you are filling 8 variables with the output and expecting the 8th to contain filename, in fact it will contain time and filename concatenated together if the 2nd date format is being used.  The locale in cron's environment could differ from your own.  

but these kinds of things will be obvious if you add some debugging echo statements as i mentioned.

---

### Post by Don Barnett on 2011-03-31
Well I tried replacing the while loop with until but the result was the same.  I finally removed the while loop completely and the script runs in cron without any problems. I am trying to come up with an alternative to the while loop.  Probably some kind of a for loop.  I have no idea why the while loop doesn't work but if I ever find out why I'll post the results here for archive.

Thanks for your help.

---

