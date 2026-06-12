---
title: "Cron and Bash script"
date: 2011-10-20
forum: General Help
---

### Post by histamineblkr on 2011-10-20
Here's what I got:

I have a cron job setup to run every Friday (I couldn't figure out how to run a cron job every other Friday, but if you know how then that solves my problem immediately) and then calls a bash script that runs which calls a zenity dialog box that tells me it's pay day. A very simple bash script that's really not that interesting but the problem I have is getting it to run every other Friday since I am paid every 2 weeks.

The work around half assed kind of solution I came up with in my script is this:

```

#! /bin/bash
export DISPLAY=:0

count="0"
whichFriday=$(date | awk '{ print $1$2$3 }')
fridayList="FriOct28 FriNov11 FriNov25 FriDec9 FriDec23"

for i in $fridayList
do
        if [ "$i" = "$whichFriday" ]
        then    
                zenity --info --title="Pay Day" --text="It's Payday\!"
                (( count++ ))
        fi
done

if [ $count = 0 ]
then
        zenity --info --title="Pay Day" --text="Payday next week\!"
fi


```What I have done is manually insert dates of days I am paid. This is of course terrible since I will need to always update the list manually. For correct programming I want it to run on it's own an never need input or updating from me. 

I have tried to think of ideas like does "date" have a way to view the entire year as 365/366 days a year so I can find my first Friday pay day and then add 14 days to test if it's the next pay day? Or if anyone has a better idea of how to tackle my every other Friday problem?

I must just be losing it because I don't feel this should be that hard of a problem to solve but I have been thinking of solutions for over a week and haven't come up with anything but this list idea....

Thank you for any help.

---

### Post by aeiah on 2011-10-20
does 5/2 do every other friday? (5 being friday). for other fields, /2 does every other. from the man page:

> Step values can be used in conjunction with ranges.  Following a	 range
       with  "<number>"	 specifies  skips  of  the  number's value through the
       range.  For example, "0-23/2" can be used in the hours field to specify
       command	execution every other hour

so

0 17 * * 5/2 <command>


it might not work in the day of week field though

another solution is to tell your script to make a lock file if a lock file doesn't exist. in pseudocode just:
```

if ~/.paydaylock exists:
    rm ~/.paydaylock
    run the main bit of the script
else:
    touch ~/.paydaylock


```

and run it once a week. easy to test, too. it should alternate between running the commands and creating the lock

---

### Post by histamineblkr on 2011-10-20
> 
does 5/2 do every other friday? (5 being friday). for other fields, /2 does every other. from the man page:

so

0 17 * * 5/2 <command>
From what I researched and read this does not work on the day field. I did not try it but I'm pretty sure it will not work. If anyone has done it this way and I am wrong please correct me.

> 
another solution is to tell your script to make a lock file if a lock file doesn't exist. in pseudocode just:
     Code:
     if ~/.paydaylock exists:     rm ~/.paydaylock     run the main bit of the script else:     touch ~/.paydaylock 
and run it once a week. easy to test, too. it should alternate between running the commands and creating the lock 
I'm not sure I understand the lock file concept. Is it a way to alternate between Fridays by making a file and then testing if it's there? Then if it is there; remove it then do something And if it's not there; do something else?

---

### Post by aeiah on 2011-10-20
> **histamineblkr said:**
> 
I'm not sure I understand the lock file concept. Is it a way to alternate between Fridays by making a file and then testing if it's there? Then if it is there; remove it then do something And if it's not there; do something else?


yea. if the file is there, remove it and run your commands. the next time the script checks, the file won't be there (you removed it last time) so create it and exit.


first time the script is run:
- is the file there? (no, so we create it and exit)

second time the script is run:
- is the file there? (yes, so remove it for next time and run some commands)

third time the script is run:
- is the file there? (no, so we create it and exit)

etc etc.

---

### Post by histamineblkr on 2011-10-20
Ah, I was trying to use a counter and just modulus it by two and when it evaluated to 0 I could run and if and else but I need a counter outside the scope of my script so the counter wasn't always redefined to an initial value every time. This is basically my counter outside my bash script. I was thinking of just creating an environmental variable counter and importing it into my script but this is probable a better practice no?

---

### Post by Lars Noodén on 2011-10-20
You might consider moving this to perl to take advantage of the [Date::Calc](http://search.cpan.org/~stbey/Date-Calc-6.3/lib/Date/Calc.pod) module from CPAN.

---

### Post by histamineblkr on 2011-10-20
> **Lars Noodén said:**
> You might consider moving this to perl to take advantage of the [Date::Calc]("http://search.cpan.org/%7Estbey/Date-Calc-6.3/lib/Date/Calc.pod") module from CPAN.

Oh I know I could do it with Perl, Python, Ruby, or another scripting language but I wanted to keep it simple and in cron and bash. Although I appreciate the suggestion and thank you for it.

---

### Post by Lars Noodén on 2011-10-20
You could check if the week number is odd or even:

```

[expr](http://manpages.ubuntu.com/manpages/oneiric/en/man1/expr.1.html) $([date](http://manpages.ubuntu.com/manpages/oneiric/en/man1/date.1.html) +"%U") % 2

```

That will work for a year at a time.

---

### Post by Lars Noodén on 2011-10-20
> **aeiah said:**
> 
another solution is to tell your script to make a lock file if a lock file doesn't exist. 

There's a lot of ways that could go wrong, but just for the record, there is already a tool to handle file locks: [flock](http://manpages.ubuntu.com/manpages/oneiric/en/man1/flock.1.html)

---

### Post by histamineblkr on 2011-10-20
> **Lars Noodén said:**
> You could check if the week number is odd or even:

```

[expr]("http://manpages.ubuntu.com/manpages/oneiric/en/man1/expr.1.html") $([date]("http://manpages.ubuntu.com/manpages/oneiric/en/man1/date.1.html") +"%U") % 2

```That will work for a year at a time.

Hmmm, I will have to play around with this. I went through the date man page and didn't see much about  the "+ '%U'". I saw someone else do something similar with "+ '%d'" but I couldn't figure out exactly what you are telling date with those C like specifiers.

> 
There's a lot of ways that could go wrong, but just for the record, there is already a tool to handle file locks: [flock]("http://manpages.ubuntu.com/manpages/oneiric/en/man1/flock.1.html")           7 Hours Ago 12:41 PM
What could go wrong with the lock file beside it getting accidentally deleted?

---

### Post by Lars Noodén on 2011-10-21
> **histamineblkr said:**
> What could go wrong with the lock file beside it getting accidentally deleted?

That's the main thing.  I just wouldn't count on them being long term persistent.

---

### Post by Lars Noodén on 2011-10-22
Or use **let**, which is faster

```

[let](http://manpages.ubuntu.com/manpages/oneiric/en/man1/bash.1.html) a=$([date](http://manpages.ubuntu.com/manpages/oneiric/en/man1/date.1.html) +"%U")%2


```

---

### Post by histamineblkr on 2011-10-23
> **Lars Noodén said:**
> Or use **let**, which is faster

```

[let]("http://manpages.ubuntu.com/manpages/oneiric/en/man1/bash.1.html") a=$([date]("http://manpages.ubuntu.com/manpages/oneiric/en/man1/date.1.html") +"%U")%2


```

Thank you.

---

### Post by hwttdz on 2011-10-23
Do you get paid every two weeks or twice a month on friday?

Assuming it's the second (because that's how I get paid)
In a given month, 
Friday #1 occurs between day #1 and #7,
Friday #2 occurs between day #8 and #14,
Friday #3 occurs between day #15 and #21,
Friday #4 occurs between day #22 and #28,
Friday #5 occurs between day #29 and #31 (true because no days have more than 31 days).

Now we want to know if it's friday, which is easy enough, using someone else's run at 17:00 hours
#m h  dom mon dow   command
0 17 * * 5 command # tells us if it's friday

so:
0 17 1-7 * 5 command # tells us if it's friday during the first week
0 17 15-21 * 5 command # tells us if it's friday during the third week
0 17 1-7,15-21 * 5 command # tells us if it's friday during the first or third week

I don't know exactly how you get paid, but hopefully that gets you close.

Every two weeks is actually both easier and harder.  I'd ask date if the week of the year is even or odd (%U), and if it's the wrong one do nothing, if it's the right one then do whatever.  Then I'd put that in a crontab that runs every friday.

---

### Post by histamineblkr on 2011-11-17
> **hwttdz said:**
> Do you get paid every two weeks or twice a month on friday?

..........

Every two weeks is actually both easier and harder.  I'd ask date if the week of the year is even or odd (%U), and if it's the wrong one do nothing, if it's the right one then do whatever.  Then I'd put that in a crontab that runs every friday.

I get paid every 2 weeks. I actually did what you suggest at the end and ran a cron job every friday and then evaluated if the week was odd or even. Thank you for your help though.

---

### Post by mwright84 on 2011-11-17
confused with the codes but I keep on following this thread so yeah..thanks!

[Los Angeles Magento Programmers]("http://claremontdesign.com/")

---

