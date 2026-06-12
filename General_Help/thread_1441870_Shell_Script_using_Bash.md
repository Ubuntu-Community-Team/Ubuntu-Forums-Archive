---
title: "Shell Script using Bash"
date: 2010-03-29
forum: General Help
---

### Post by ayozito on 2010-03-29
Hi!!! I am looking for a little help with a script i need to make for university.

I need show the number of process per user, and after the date of the oldest process per user also.

With "ps -eo user | sort -u" i get all users that are running any process. And with "ps U username | wc -l" i get the number of process that the user "username" is running.

But how can i merge both commands for do what i need? Like a FOR or something like that. There is any method of make a FOR using the list that i get with the first command?

And then for show the date of the oldest process.. with "ps U username | sort -k 4" (4 is TIME field) i can show the process of the user "username" sorting they by time. But how can i get the date of the process takes longer running?? I can get only the time, but no the date.



I know that this isn't a question of Ubuntu, but it's related with Linux commands.

---

### Post by ayozito on 2010-03-29
Mmm ok i just got made the first part. Now only need show the DATE instead the TIME of the oldest process running

---

### Post by xifer on 2010-03-29
> **ayozito said:**
> Hi!!! I am looking for a little help with a script i need to make for university.

I need show the number of process per user, and after the date of the oldest process per user also.

With "ps -eo user | sort -u" i get all users that are running any process. And with "ps U username | wc -l" i get the number of process that the user "username" is running.

But how can i merge both commands for do what i need? Like a FOR or something like that. There is any method of make a FOR using the list that i get with the first command?

And then for show the date of the oldest process.. with "ps U username | sort -k 4" (4 is TIME field) i can show the process of the user "username" sorting they by time. But how can i get the date of the process takes longer running?? I can get only the time, but no the date.



I know that this isn't a question of Ubuntu, but it's related with Linux commands.

Define a function in the script to get the number of processed for a user.
Another to get the process date (I( think if it's today it will show time, if older then date and time)

Then pipe your userlist to a while loop that calls the functions

something like this but I won't write the functions for you ;-)


```

ps -eo user|sort -u|while read -d ":" userlist;do
       echo $userlist functiontogetpscount($userlist)  functiontogetoldestdate($userlist) 
done

#define functions
functiontogetpscount
functiontogetoldestdate

```

---

### Post by ayozito on 2010-03-29
Ok what you say is for show the number of process of every user. I already did it with a FOR.

Now need the date, but according to you, maybe TIME field show only time and no DATE because it is a process started today?

With which command can i select just the last line of PS command?

---

### Post by xifer on 2010-03-29
> **ayozito said:**
> 
And then for show the date of the oldest process.. with "ps U username | sort -k 4" (4 is TIME field) i can show the process of the user "username" sorting they by time. But how can i get the date of the process takes longer running?? I can get only the time, but no the date.



oh - you do realise that TIME is the elapsed CPU time - you probably want STIME.

---

### Post by xifer on 2010-03-29
> **ayozito said:**
> Ok what you say is for show the number of process of every user. I already did it with a FOR.

With which command can i select just the last line of PS command?

```

ps|tail -1

```

but why do you want to do that?

---

### Post by ayozito on 2010-03-29
i though make a ps U user | sort -k 4, and after select the last line. On this way i would have the PID of the process and the TIME no? I mean the line with this info. Then i will CUT the 2 fields i need


mmm and how can i select the line before the last?? My output of the ps with the sort is:

....
...
 1766 ?        Ssl    0:53 /usr/bin/pulseaudio --start
 3218 ?        Sl     1:02 audacious2
 3017 ?        Sl     1:21 wish8.5 /usr/bin/amsn
 3367 ?        Sl     3:29 /usr/lib/firefox-3.5.8/firefox
  PID TTY      STAT   TIME COMMAND

I need select  **3367 ?        Sl     3:29 /usr/lib/firefox-3.5.8/firefox**

I tried with tail -2, but with this i get this line and the last. I need only this line.

Or the other way is how can i hide headers when i use sort?

---

### Post by xifer on 2010-03-29
> **ayozito said:**
> i though make a ps U user | sort -k 4, and after select the last line. On this way i would have the PID of the process and the TIME no? I mean the line with this info. Then i will CUT the 2 fields i need


mmm and how can i select the line before the last?? My output of the ps with the sort is:

....
...
 1766 ?        Ssl    0:53 /usr/bin/pulseaudio --start
 3218 ?        Sl     1:02 audacious2
 3017 ?        Sl     1:21 wish8.5 /usr/bin/amsn
 3367 ?        Sl     3:29 /usr/lib/firefox-3.5.8/firefox
  PID TTY      STAT   TIME COMMAND

I need select  **3367 ?        Sl     3:29 /usr/lib/firefox-3.5.8/firefox**

I tried with tail -2, but with this i get this line and the last. I need only this line.

Or the other way is how can i hide headers when i use sort?
```

ps eh U $userlist -o stime|head -1


```

---

### Post by ayozito on 2010-03-31
mmm question, STIME is Start time.  ETIME is Elapsed Time. And TIME is???

---

### Post by xifer on 2010-03-31
TIME is accumulated CPU 
STIME is process start time
ETIME is  elapsed time since the process was started

and - with tongue in cheek - RTFM means read the fscking manual!

seriously - good luck with your studies.

---

