---
title: "rsync then shutdown, with long task duration - sudo timeout?"
date: 2011-01-16
forum: General Help
---

### Post by candtalan on 2011-01-16
I use a fairly simple manual rsync to copy  a lot of stuff from one drive to another. It is run in a terminal from a script file from a launcher on the desktop. I think that is a correct description, I am  a near novice in this area.

Things work well except I would like to arrange a shutdown at the end of the rsync activity.
Without including frills here like echoes and sleep delays, I am basically doing this
```

sudo rsync --delete -rt --progress --stats -v  /media/data-a/ /media/data-b/

sudo shutdown -h now

```
Sometimes it works ok.  However, because it is likely that the rsync activity duration will exceed the sudoer timeout, then when the shutdown command is arrived at, I am required to again enter password. It is quite ok for me to manually begin running the script, and I can enter my password when initially required. But I am trying to avoid having to be present finally to again enter password before shut down. I want to be in bed.......

The method that first came to mind once I realised (I think) what is going on, was to increase the sudoer timeout. This is a private access machine so there is not much increased risk with that I believe. As long as I can edit the necessary, correctly.

But I wondered if there is another perhaps more elegant method I could use?

Any ideas please? tia

---

### Post by ridetheteapot on 2011-01-16
since your sudoing rsync anyway why not just drop the sudo's from inside the script, and just run it like sudo ./myscript.sh

---

### Post by candtalan on 2011-01-16
Thanks, I will try that approach.

my test script is in /home/user/bin
and echo $PATH shows that    
/home/user/bin  is included.

When in a terminal I use simply  
myscript-1.sh
the test script starts. However when I use
sudo myscript-2.sh

I get the response
sudo: myscript-2.sh: command not found.

My immediate  aim is to run a test script with root privilidges, when the script is located in  /home/user/bin
and I am logged in as user.

tia

---

### Post by tredegar on 2011-01-16
> I get the response
sudo: myscript-2.sh: command not found.

Try **sudo /home/user/bin/myscript.sh**
Ie give the _full path_ to the script

It looks like sudo doesn't use your $PATH
Sometimes ubuntu & sudo are annoying.

I'd have put (as root) the executable script in **/usr/sbin/** and then just **sudo *scriptname*** should work.
Hope this helps.

---

### Post by ridetheteapot on 2011-01-16
you can pass your user $PATH to sudo by
```
sudo env PATH=$PATH script.sh
```
or you could add it too your bash aliases like 
```
alias medo='sudo env PATH=$PATH'
```

---

### Post by ggarron on 2011-01-16
You may want to specify no password for shutdown for your user, in the sudoers file

[http://www.go2linux.org/sudoers-how-to](http://www.go2linux.org/sudoers-how-to)

hope it helps.

---

### Post by ggarron on 2011-01-16
You may want to specify no password for shutdown for your user, in the sudoers file

[http://www.go2linux.org/sudoers-how-to](http://www.go2linux.org/sudoers-how-to)

hope it helps.

---

### Post by candtalan on 2011-01-16
> **tredegar said:**
> Try **sudo /home/user/bin/myscript.sh**
Ie give the _full path_ to the script
 Thanks, but it still did not work.

[/QUOTE] It looks like sudo doesn't use your $PATH
Sometimes ubuntu & sudo are annoying.
I'd have put (as root) the executable script in **/usr/sbin/** and then just **sudo *scriptname*** should work.
Hope this helps.[/QUOTE]

That seems to be a useful solution thanks.
```
 sudo scriptname 
```
then as you say, works from a terminal ok, and I do not have to change too much, except move the script  out of my user area to another directory. 

Am I correct in believing that in this case, the sudo will continue to be active (and not time out) until 'scriptname' completes, however long?

Also, because I want the convenience of launching from a launcher (application in a terminal) on the user desktop, I tried it, but it did not seem to work maybe because I would need to add sudo into the command in the desktop launcher itself rather than with in the subsequent terminal, which itself did not seem to work.

Whatever, I used a desktop launcher to run a starter script file containing ```

sudo myscript-with-shutdown.sh 
``` to call the main script, and this seems to work, I guess because the password is required at launch by the starter script?

Many thanks for all the help and comments.

---

### Post by ridetheteapot on 2011-01-17
you would use gksudo in the launcher's command field, rather then sudo. Also if you want a terminal window to open so you can see progress of the rsync add **Terminal=true** to the launcher file.
(incidentally if you kept the sudo's in your script you would HAVE to use a terminal to get the sudo prompts, this is a nice side-effect of not doing it that way).

as for sudo "not timing out". i think its more like the script will be run as root, and each child process will inherit that uid- so it won't be a problem.

PS - using the full path with sudo should work fine, i would double check that you used the correct path when you tried.

---

