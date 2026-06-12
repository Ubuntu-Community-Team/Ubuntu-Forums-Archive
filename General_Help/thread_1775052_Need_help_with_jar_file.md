---
title: "Need help with jar file"
date: 2011-06-04
forum: General Help
---

### Post by werner.fletcher on 2011-06-04
Hey all,

I made a Java application that needs to run at logon, so I basically need a script or something to run the .jar file at logon and it also need to run with sudo, otherwise it does not work.  I am currently forced to start the jar from the terminal with sudo, but this is BS.  I'm sure you guys have an easier way of doing it?

Thanks alot!

---

### Post by werner.fletcher on 2011-06-05
So I guess there is no way then?

---

### Post by pqwoerituytrueiwoq on 2011-06-05
is i ok it is runs at the login screen?

---

### Post by werner.fletcher on 2011-06-06
> **pqwoerituytrueiwoq said:**
> is i ok it is runs at the login screen?

That would be fine.  I enabled auto login, i just need it to start up automatically.  Thanks! :)

---

### Post by werner.fletcher on 2011-06-07
bump

---

### Post by jim_deadlock on 2011-06-07
You just need a root cron job.

```
sudo crontab -u root -e
```

... add a line like this

```
@reboot /path/to/jarfile
```

close/save... reboot.

---

### Post by werner.fletcher on 2011-06-07
> **jim_deadlock said:**
> You just need a root cron job.
 
```
sudo crontab -u root -e
```
 
... add a line like this
 
```
@reboot /path/to/jarfile
```
 
close/save... reboot.
 
I did exactly what you said, but nothing starts up when I reboot... :(

---

### Post by hakermania on 2011-06-07
Well, try making this script:
```

#!/bin/bash
echo "your_login_passwd_here" | sudo -S /path/to/the/jar/file

```
Drawback: Be sure that nobody else may access this script because he actually has your password :(
Save it, and at its properties->permissions set the executable bit, or by the command
```
chmod +x script_name
```
Then, open the 'Startup Applications' program and add this script :)

---

### Post by jim_deadlock on 2011-06-07
First of all check your cron job

```
sudo crontab -u root -l
```

... should output your cron job.

The part after @reboot should be the same command you normally use in the terminal.

The only other thing I can think of is that if your jar script uses environment variables that could be the problem, cron jobs sometimes don't import all the environment stuff.

---

### Post by werner.fletcher on 2011-06-08
What I've done is:

I made a startup.sh script with the following line:
```
#!/bin/bash
echo mypswd | sudo java -jar /etc/netchat/myjar.jar
```I put the script in startup applications like this: ```
gksu /etc/init.d/startup.sh
```The app starts when the pc logs on, but it gives me an error, which I only get when the app is not run as "sudo".  I've tried gksu and sudo but none work :(

---

