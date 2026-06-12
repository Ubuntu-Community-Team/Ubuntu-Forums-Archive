---
title: "call a script from cron"
date: 2011-10-10
forum: General Help
---

### Post by Drenriza on 2011-10-10
Hi all.

I have an entry in my crontab file, where it runs a script on a location stated in the line.
```
0/1 * * * * /Users/crisitanambk/startUpScripts/Level3ShareScript
```
What i'am wondering is, what is the best way to call another script from the first script executed?

My issue is that, crontab executes the script. But inside that script i have a path to a expect script. But this does not get executed.
```
if [ "$test" == "10.1.42" ]
then
        (echo "Connection to the fileserver -> Level3 folder established ${tid} ${tidd}" >> /Users/$hvem/startUpScripts/log)
        /Users/crisitanambk/startUpScripts/Level3ExpectScript #didnt call the script  <--this don't get executed.
        #/Users/$hvem/startUpScripts/Level3ExpectScript #didnt call the script
else
        (echo "Your not on the correct network 10.1.42.* didn't mount ${tid} ${tidd}" >> /Users/$hvem/startUpScripts/log)
fi

```

Hope it makes sense. Or else please don't hesitate to ask.

Thanks on advance.
Kind regards.

---

### Post by papibe on 2011-10-10
Could you post the 'Level3ExpectScript' script?

Regards.

---

### Post by WasMeHere on 2011-10-10
Cron has a very limited environment, so you have to create paths and other environment variables locally (within what is called from cron).

You seem to use full paths, that is good.
What about the '$variables'? Are they recognized?

Who owns the root directory /Users, root or your user account? Are you running cron as root or as user?

Have fun finding out
Olle

---

### Post by Drenriza on 2011-10-10
> **papibe said:**
> Could you post the 'Level3ExpectScript' script?

Regards.

```
#!/usr/bin/expect -f
spawn mount -t smbfs //username@dnsname-or-ip/Level3 /Users/crisitanambk/Level3Share
expect "Password:"
send "MyPassword\r"
wait
```

---

### Post by Drenriza on 2011-10-10
> Who owns the root directory /Users, root or your user account? Are you running cron as root or as user?

root owns the /Users folder.
I am running the script from my crontab file. So i guess i run it as my user.

> What about the '$variables'? Are they recognized?
Yes my ${something} works as intended. And are defined at the start of the script
word=$(command or series of commands)

---

### Post by WasMeHere on 2011-10-10
> **Drenriza said:**
> root owns the /Users folder.
I am running the script from my crontab file. So i guess i run it as my user...
Maybe you run into problems because you are not allowed to write into the subdirectories of /Users. What will happen if you try to write a file into the same directory as cron tries to write into? You might change the permission of that subdirectory using ```
chmod -R
```

---

### Post by Drenriza on 2011-10-10
> **Olle Wiklund said:**
> Maybe you run into problems because you are not allowed to write into the subdirectories of /Users. What will happen if you try to write a file into the same directory as cron tries to write into? You might change the permission of that subdirectory using ```
chmod -R
```

I own a subdirectory in the /Users folder. And its this folder i write to. So i have rights to the destination folder.

---

### Post by WasMeHere on 2011-10-10
Does your script work when called by yourself (directly, not via cron)?

---

### Post by Drenriza on 2011-10-10
> **Olle Wiklund said:**
> Does your script work when called by yourself (directly, not via cron)?

Yes. I only have the issue when calling it from cron

---

### Post by WasMeHere on 2011-10-10
> **Drenriza said:**
> Yes. I only have the issue when calling it from cron
Well, then I think it is because of your limited environment. Look carefully at everything that may be depending on your environment variables, or something else that is initiated or modified in your bash shell, for example aliases.

Good luck
Olle
ps/
 Right now I have confirmed that the current user is recognized by cron: 
```
 *  *  *  *  *  espeak >/dev/null 2>/dev/null "I am $(whoami)"
```
/ds

---

### Post by WasMeHere on 2011-10-10
> /Users/[COLOR="Red"]crisitan[/COLOR]ambk/startUpScripts/Level3ExpectScript

Is it a simple typo: crisitan or cristian?

---

### Post by papibe on 2011-10-10
A few thoughts (despite the fact I don't know 'expect' very much):
[LIST]
[*]Cron runs /bin/sh by default. Since I don't see shebang line of your main script, be careful with the syntax (although it seems that's not the problem here). Note that in Ubuntu sh is really link to dash.
[*]Cron reduce its environment including several important variables, like PATH, SHELL and TERM.
[*]The command mount itself does not ask for a password. I think you are trying to run 'sudo mount...' (just a guess).
[*]While researching about using 'expect' on cron, it seems that a lot of users have little to none success with it. For what I read, it looks like the lack a tty attached. The only success that I found was [this]("http://www.linuxquestions.org/questions/programming-9/expect-script-not-getting-called-in-the-cron-job-682284/") example. The trick seems to be 'spawn' a shell, and then 'send' the commands.
[/LIST]
I hope this points you in the right direction.
Regards.

---

### Post by Drenriza on 2011-10-11
> **Olle Wiklund said:**
> Is it a simple typo: crisitan or cristian?
The name crisitan is "correct" :p When i installed the system i wrote cristian wrong as the user account. Thus i am now crisitan :)

> **papibe said:**
> A few thoughts (despite the fact I don't know 'expect' very much):
[LIST]
[*]Cron runs /bin/sh by default. Since I don't see shebang line of your main script, be careful with the syntax (although it seems that's not the problem here). Note that in Ubuntu sh is really link to dash.
[*]Cron reduce its environment including several important variables, like PATH, SHELL and TERM.
[*]The command mount itself does not ask for a password. I think you are trying to run 'sudo mount...' (just a guess).
[*]While researching about using 'expect' on cron, it seems that a lot of users have little to none success with it. For what I read, it looks like the lack a tty attached. The only success that I found was [this]("http://www.linuxquestions.org/questions/programming-9/expect-script-not-getting-called-in-the-cron-job-682284/") example. The trick seems to be 'spawn' a shell, and then 'send' the commands.
[/LIST]
I hope this points you in the right direction.
Regards.

Isint it possible somehow to check what the environment is for my normal user and "code" that into the bash or expect script to make it work that way? Just curious. 

For god measure i post both scripts. If this gives any good idea to anyone to why i fail as hard as i do :p but please not the scripts are still under work, and their is probably many things that can be made better :D


```
#!/bin/bash

test=$(/sbin/ifconfig en0 |/usr/bin/grep -o 10.1.42)
testThree=$(/bin/df -h |/usr/bin/grep Level3 |/usr/bin/awk '{print $6}')
tid=$(/bin/date +%Y-%m-%d)
tidd=$(/bin/date +%H:%M%:%S)
hvem=$(/usr/bin/whoami)

/bin/rm /Users/$hvem/startUpScripts/log

if [ ! -d /Users/$hvem/Level3Share/ ]
then
        /bin/mkdir /Users/$hvem/Level3Share/
        (echo "The Level3Share folder was created" >> /Users/$hvem/startUpScripts/log)
fi

if [ "$testThree" == "/Users/${hvem}/Level3Share" ]
then
        (echo "The connection to fileserver -> Level3 is already establieshed ${tid} ${tidd}" >> /Users/$hvem/startUpScripts/log)
        exit 0
fi

testOne=$(cat /Users/$hvem/startUpScripts/fileOne)

if [ "$test" == "10.1.42" ]
then
        (echo "Connection to the fileserver -> Level3 folder established ${tid} ${tidd}" >> /Users/$hvem/startUpScripts/log)
        /Users/crisitanambk/startUpScripts/Level3ExpectScript #didnt call the script
        #/Users/$hvem/startUpScripts/Level3ExpectScript #didnt call the script
else
        (echo "Your not on the correct network 10.1.42.* didn't mount ${tid} ${tidd}" >> /Users/$hvem/startUpScripts/log)
fi

exit 0
```

```
#!/usr/bin/expect -f
spawn mount -t smbfs //ch@ip-address/Level3 /Users/crisitanambk/Level3Share
expect "Password:"
send "myPassword\r"
wait
```

---

