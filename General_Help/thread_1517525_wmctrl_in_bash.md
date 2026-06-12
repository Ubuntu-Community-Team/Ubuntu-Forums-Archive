---
title: "wmctrl in bash"
date: 2010-06-25
forum: General Help
---

### Post by Cowboybebop79 on 2010-06-25
Ok so I had a look around for something to clean up my desktop after boot. eg tomboy notes, tasque etc when they are started at boot they are left open even though you may not want to use them right away. I found a command wmctrl which will close, minimize, maximize open windows and I have successfully tested this in the terminal but I haven't been able to repeat this with a script :( the idea being that any programs that don't have the start minimized option can be added to the script and closed to the notification area. Any one have any idea how to do this or an alternate option.

---

### Post by StuartN on 2010-06-25
> **Cowboybebop79 said:**
> I have successfully tested this in the terminal but I haven't been able to repeat this with a script

Perhaps you should use the full path to the command, which you can obtain by **which wmctrl**

---

### Post by DaithiF on 2010-06-25
how are you launching the script, and have you tried logging the output from the script to understand why it isn't working?
ie. something like:

```
yourscript > /path/to/somelogfile 2>&1
```

---

### Post by Cowboybebop79 on 2010-06-25
this is the output of the log file

```

[Debug]: Tasque remote control active.
[Debug]: Found Available Backend: Tasque.Backends.RtmBackend.RtmBackend
[Debug]: Found Available Backend: Tasque.Backends.Sqlite.SqliteBackend
[Debug]: Tasque.exe location:  /usr/lib/tasque/Tasque.exe
[Info]: Searching for Backend DLLs in: /usr/lib/tasque
[Info]: 	Reading /usr/lib/tasque/RtmNet.dll
[Debug]: Storing 'Tasque.Backends.RtmBackend.RtmBackend' = 'Remember the Milk'
[Debug]: Storing 'Tasque.Backends.Sqlite.SqliteBackend' = 'Local File'
[Debug]: CurrentBackend specified in Preferences: Tasque.Backends.RtmBackend.RtmBackend
[Info]: Using backend: Remember the Milk (Tasque.Backends.RtmBackend.RtmBackend)
[Debug]: Found AuthToken, checking credentials...
[Debug]: RTM Auth Token is valid!
[Debug]: Setting configured status to true
[Debug]: ThreadState: Unstarted
[Debug]: Configuration status: True
[Debug]: RtmBackend.UpdateCategories was called
[Debug]: RtmBackend.UpdateCategories is done
[Debug]: RtmBackend.UpdateTasks was called
[Debug]: RtmBackend.UpdateTasks is done
[Debug]: Backend sync finished
[Debug]: Backend sync finished
[Debug]: WindowDeleted was called
[Info]: OnQuit called - terminating application

```

I'm fairly new to bash so I'm learning as I go and I'm not sure if there are any rules about running multiple programs from the same bash script or not.
at the moment the script is just calling tasque then sleeping about 10 seconds and then calling wmctrl -c Tasque to close the window. by the way the last 2 lines are me closing the tasque window and quiting the program manually as apposed to the script doing it.

---

### Post by laceration on 2010-06-25
wmctrl is a great little program.  Try opening the program as a forked process.  Note the ampersand.

```

/usr/bin/tomboy &
sleep 10
wmctrl -c ...

```

---

### Post by Cowboybebop79 on 2010-06-25
> **laceration said:**
> wmctrl is a great little program.  Try opening the program as a forked process.  Note the ampersand.

```

/usr/bin/tomboy &
sleep 10
wmctrl -c ...

```


Ah ha :biggrin: nail on the head laceration thanks for the tip about logging output Daithif in this case it showed what wasn't happening eg. the rest of the script apart from the output of tasque. I stumbled on wmctrl or something similar when looking for a replacement for autoit for automating gui related tasks because not everything can be done from the command line although I am sure I would get burned for saying that by any script fu's :-\"

---

### Post by Cowboybebop79 on 2010-06-27
I spoke to soon the script works fine when run after boot but when it is added to the startup programs it doesn't work it starts the program but by the time the window has appeared the script is sitting by the pool with a cocktail so I will need something to check the output of wmctrl -l for the window so that it hangs around till its actually there before going on to bigger and better things. Any idea's how to grab the output of wmctrl -l to an array and then check that array for the existence of a window? By the way slightly off subject but anybody had any experience with xnee just grabbed the gui which looks like it could do with a bit of work to clean it up a little might do a little testing.

---

