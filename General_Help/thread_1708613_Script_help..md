---
title: "Script help."
date: 2011-03-16
forum: General Help
---

### Post by Coder68 on 2011-03-16
I need a script that will ping a given PC and time stamp each ping so it looks something like this:

64 bytes from 10.0.0.1: icmp_seq=2 ttl=64 time=2.97 ms 2011-03-16 21:55:13 EDT

I need it on the screen and in a file.  

I would use Nmap but work wont allow it, but they want this scan.

I have tried it with sed, but can't seem to get it working right.  I also can't get it to output to the screen and a file at the same time. (File is empty) Tee did not help either. 

Can someone please post a script to do this, and as a beginner, can you explain what each part is doing?

Thanks!

C68

---

### Post by Crusty Old Fart on 2011-03-20
To C68:

Most of the code cats who provide scripting help here recognize homework assignments when we see them. Unfortunately for you, your request smacks of someone trying to have someone else do their homework for them, which is something we generally will not do.

You would probably have much better luck getting some help if you posted your script. It would at least demonstrate that you are trying to learn, rather than hoping that one of us will lay a "get out of homework for free" card on you.

You're welcome,

Crusty

---

### Post by Coder68 on 2011-03-23
This is not homework. But I guess I can see how it could look that way. I was able to do this in Windows a lot easier then in Linux.

:REDO
  
  echo %time% >> C:\Pingbr35.txt
  
  ping 192.x.x.x >> C:\Pingbr35.txt
  
  GOTO REDO

It was not very pretty, but it allowed me to ping the branch with a time stamp so I could correlate downtime to events in other logs. I was also able to graph the all day ping's in Wireshark.

Thanks.
C68

---

### Post by antaios256 on 2011-03-23
my sugestion to you would be if this is work related and you are just trying to correlate downtime via failed pings you dont need to write a script to accomplish this. 

setting up a continuous ping and running the capture in wireshark. Wireshark will actually mark each frame with time arrived (and by checking L2 and L3 headers you would be able to determine exactly where on your network it was going. 
[IMG]http://ubuntuforums.org/picture.php?albumid=2211&pictureid=7487[/IMG]

Hope this helps. as it would be a more beneficial way of monitoring  just filter for the type of packets your looking for (i.e. icmpv4 packets)

---

### Post by Crusty Old Fart on 2011-03-23
> **Coder68 said:**
> This is not homework. But I guess I can see how it could look that way...


Yup...it looked a LOT like homework. But, since it isn't, here you go:
```

#!/bin/bash
set -e

touch pingfile.txt

while [[ true ]]; do
  ping -c 1 192.168.1.2 | \
  awk -v timestamp="$(date +%F" "%T" "%Z)" 'NR==2 {print $0,timestamp}' | \
  tee -a pingfile.txt
done

exit 0

```Happy to answer any questions.

Best of luck,

Crusty

---

### Post by Coder68 on 2011-03-27
antaios256, thanks.  

That is more or less what I did but I wanted the time stamp in the log for better/easier time coloration, hence the Windows script.  I captured the data with Wireshark and then took a look at the timestamp in the log to see what else was going on. From there I graphed it to give a visual of when and how long the branch was down.  That was easier for management.

As it turns out it was not a branch issue, but a company wide issue! The other branches were just not complaining.  They go down for a second or two and then pop right back up.  This is a new behavior. Since they did not call when it started we have no way to be sure, but I believe this is related to an upgrade of some of our equipment.  The timing seems to perfect not to be. It just broke? What did we just change? Always look at what you just changed!

Crusty, 

Thanks!  That is close to what I had for an awk statement, but I suck at programming so I am surprised I got that close. I will give that a try on Monday.

Thanks!

---

### Post by Coder68 on 2011-03-29
Crusty, I had to modify the script just a bit to get it to work.  Here is what worked for me:

```
#!/bin/bash
set -e

touch pingfile.txt

while true; do
  ping -c 1 192.168.1.2 | \
  awk -v timestamp="$(date +%F" "%T" "%Z" "%N )" 'NR==2 {print $0,timestamp}' | \
  tee -a pingfile.txt
done

exit 0
```

I removed the [[]] to get it to work, and I also added %N just for fun. : )

One question though:

Is line 2 just the timestamp part and ping is line 1? Is NR==2 what combines them into one line?  

This will make it much easier to diagnose in the future. 

Thanks again!

C68

---

### Post by Crusty Old Fart on 2011-04-01
> **Coder68 said:**
> Crusty, I had to modify the script just a bit to get it to work...

I removed the [[]] to get it to work, and I also added %N just for fun. : )

Look at the lines in  the following code box:
```

**[COLOR=Green]while [[ true ]]; do #This line works.[/COLOR]**
**[COLOR=Green]while true; do       #This line also works.[/COLOR]**
**[COLOR=Red]while [[true]]; do   #This line will generate a [[true]]: command not found error.[/COLOR]**

```If you didn't separate the **contents** of the double bracket pair, from the **brackets themselves**, by putting a whitespace on each side of the word: true, then you should have gotten an error. Either that, or you are running an old version of bash that doesn't support double bracket conditionals.
> 
One question though:
Okay...I'll answer both of them :cool:
> 
Is line 2 just the timestamp part and ping is line 1?...
Well...sort of, but...not exactly. The ping command is on line 1. However, the entire output of the ping command (all six lines of it) is piped into the awk statement on line 2. The awk statement filters what's coming through the pipe and discards everything but the second line of output from the ping command. Then it appends the timestamp to the end of it, and sends the result through another pipe to the tee command. The tee command takes what is coming to it through the pipe from the awk statement and writes it to the terminal and the file named: pingfile.txt

> 
Is NR==2 what combines them into one line?...  
Nope. NR==2 tells awk to ignore everything in the data stream, coming at it through the pipe from the ping command, EXCEPT input record number 2. In the awk programming language, lines in input files as well as lines in piped data streams, are referred to as "Input Records". NR==2 specifies Input Record Number 2, which is the second line in the data stream. The last part of the awk statement: **{print $0,timestamp}** is what combines the filtered output from the ping command with a trailing timestamp, all on a single line.

Just for the hell of it, let's take a look at what's inside the while loop:
```

[SIZE=+1][B]  ping -c 1 192.168.1.2 [COLOR=Red]|[/COLOR] [COLOR=Green]\[/COLOR]
  awk -v timestamp="$(date +%F" "%T" "%Z" "%N )" 'NR==2 {print $0,timestamp}' [COLOR=Red]|[/COLOR] [COLOR=Green]\[/COLOR]
  tee -a pingfile.txt[/B][/SIZE]

```
This is a ping | awk | tee double pipeline (pipes are shown in red above). It is ***technically*** ONE line. In order for it to be coded to ***visually appear*** as THREE lines, line continuation backslashes (shown in green above) were appended to the end of the ping command and the awk statement. This code could have been written, without the backslashes, on a single line as follows:
```

[SIZE=+1]**  ping -c 1 192.168.1.2 [COLOR=Red]|[/COLOR] awk -v timestamp="$(date +%F" "%T" "%Z" "%N )" 'NR==2 {print $0,timestamp}' [COLOR=Red]|[/COLOR] tee -a pingfile.txt**[/SIZE]

```
And...It would have worked exactly the same. But, it wouldn't have been as easy to read.
> 
This will make it much easier to diagnose in the future. 

Thanks again!

C68
You're mighty welcome. Hopefully I was able to explain what is happening well enough for you to understand it. Awk is a programming language unto itself. It's big, complicated, cryptic and very powerful. It's not easily mastered, though. I explained another awk pipeline in a different thread in more detail. It might help. Here's a link to the post if you'd like to take a peek: [post=10109285]Post ID #10109285[/post]

Sorry for my delay getting back here. Somehow, I must have hosed my subscription to this thread. I'll try to fix that.

Anything else?

Crusty

---

### Post by Coder68 on 2011-04-02
Nope I am good.

I will go over this in more detail a little later but I think I understand it well enough to "see" it, but not yet well enough to write it.  So, I will have to play around later when I have some more time.

Thanks for the great explanation. 

C68

---

