---
title: "Dump serial ports to text files with timestamp"
date: 2010-06-01
forum: General Help
---

### Post by Garyu on 2010-06-01
Hey,

I have a computer with 4 RS232 com-ports (MSI MS-9A19).

To each com-port, I have instruments attached that transmit data like this: 
982000001088420<CR><LF>
982000001088421<CR><LF>
...etc...

The data is not a continuous stream, it transmits on special events. I want to know when these events occur. So I just want a simple way to dump the serial ports transmits with a date/time addition.

I assume I can use something like
```
cat /dev/... > com1.txt &
cat /dev/... > com2.txt &
cat /dev/... > com3.txt &
cat /dev/... > com4.txt &
```
Which would just give me the codes in text files, right? I haven't tried this yet, because I haven't got the equipment set up. I'm asking because I know I won't be able to figure out the time/date thing, and I want to get started as soon as the equipment is ready for use.

I'm guessing I can do something with grep to get <CR><LF> and replace that with <tab>datetime<CR><LF>...? But how?

Also... will the files be locked while cat is running? Or will I be able to read results without interrupting cat?

The final resulting text-files should be com1.txt com2.txt com3.txt and com4.txt with rows like:
982000001088421<tab>date/time<CR><LF>

---

### Post by StuartN on 2010-06-01
> **Garyu said:**
> To each com-port, I have instruments attached that transmit data like this:

Can you use an intermediate variable, so for each port:

```
output=$(cat /dev/...)
if [ "$output" != "" ] ; then
  sleep 1
  output=$output$(cat /dev...)
  echo "$(date): $output" >> com1.txt
fi
```

(The sleep is to catch the remainder if the port is polled in the middle of a report, and hopefully reports complete in less than 1 second and are more than 1 second apart).

---

### Post by dino99 on 2010-06-01
some packages into synaptic: search rs232, setserial, ioctl

googling around:

[http://sjinn.sourceforge.net/](http://sjinn.sourceforge.net/)

---

### Post by Garyu on 2010-06-01
> **StuartN said:**
> Can you use an intermediate variable, so for each port:

```
output=$(cat /dev/...)
if [ "$output" != "" ] ; then
  sleep 1
  output=$output$(cat /dev...)
  echo "$(date): $output" >> com1.txt
fi
```

(The sleep is to catch the remainder if the port is polled in the middle of a report, and hopefully reports complete in less than 1 second and are more than 1 second apart).
I believe the only thing transmitted is the number followed by <CR><LF>. But I will try your way out once I get my equipment connected. I guess your way is Perl, right? Can I just run that on the command line? No shell script or things like that needed on mulitple lines?

I felt sure there was a way to do it just using the basic command line tools, so I wouldn't have to install any other apps. But if push comes to shove, I'll take a look at the S-Jinn app as well.

Thanks.

-------


EDIT: After a bit of googling around, I found "sed" is supposed to be used for replacing things. I found this: 
[http://www.unix.com/shell-programming-scripting/114280-sed-complex-string-replacement.html](http://www.unix.com/shell-programming-scripting/114280-sed-complex-string-replacement.html)
...but it's way over my head and I can't figure out how to write what I want to do with it.

I think it may be something like this:
```
sed 's/\r\n/$(date +"%Y-%m-%d %H:%M:%S")\r\n/g' cat /dev/ttyS0 > com1.txt
```
anyone who knows they can get it right for me? :)
(and yeah, I haven't even got a box with linux installed, that's part of the equipment I'm waiting for. so I'm trying to work this out without being able to get my hands on anything yet)

---

### Post by StuartN on 2010-06-01
> **Garyu said:**
> I guess your way is Perl, right? Can I just run that on the command line?

It is Bash scripting, which runs in the command line, even with multiple lines if you want (using backslash \ to escape the line breaks), although I would store that in a file and make it executable. Googling for "Bash if" and so on gives useful help, or man bash for serious pain (5,000+ lines).

> **Garyu said:**
> I think it may be something like this:
```
sed 's/\r\n/$(date +"%Y-%m-%d %H:%M:%S")\r\n/g' cat /dev/ttyS0 > com1.txt
```

Probably this would work:

```
cat /dev/ttyS0 | sed 's/\r\n/$(date +"%Y-%m-%d %H:%M:%S")\r\n/g' >> com1.txt
```

which pipes the output of cat through sed. The replacement text would be better with \n rather than \r\n for a standard Unix line. And what happens if cat does not return a line? You might find **hd -c** (hexdump, classic mode) useful to check the actual bytes transmitted.

CygWin might also be useful to run a Linux-like command line in Windows, but I have not used it.

---

### Post by Garyu on 2010-06-04
> **StuartN said:**
> Probably this would work:

```
cat /dev/ttyS0 | sed 's/\r\n/$(date +"%Y-%m-%d %H:%M:%S")\r\n/g' >> com1.txt
```

I've tried this, but couldn't get it to work. sed would replace the things but never execute the $(date) so a line would look like so:
$(date)   982000938575

I googled around and found this:
[http://stackoverflow.com/questions/21564/is-there-a-unix-utility-to-prepend-timestamps-to-lines-of-text](http://stackoverflow.com/questions/21564/is-there-a-unix-utility-to-prepend-timestamps-to-lines-of-text)
...where it says to use awk. This actually works:
```
cat /dev/ttyS0 | awk '{print strftime("%Y-%m-%d %H:%M:%S %z"), $0; }'
```
The output looks something like:
2010-06-04 16:31:20 +0200 982000938575
2010-06-04 16:31:21 +0200 982000938575
...etc...

My current problem is that I can't get it to save to a file. I've tried using both **> test.txt** and **>> test.txt**, but all that happens is that an empty file named test.txt is created.

Maybe this has something to do with the fact that I have to end the command with Ctrl-C or Ctrl-Z...?

Is there any way to write unbuffered with > or >> or any other good way of solving this?

---

### Post by Garyu on 2010-06-04
> **Garyu said:**
> Is there any way to write unbuffered with > or >> or any other good way of solving this?

I tried leaving the system on for a longer time, and it does write to the file after a while. But it would be good to know of a way to flush the buffer before hitting Ctrl-Z to quit logging...

---

### Post by StuartN on 2010-06-04
> **Garyu said:**
> I tried leaving the system on for a longer time, and it does write to the file after a while. But it would be good to know of a way to flush the buffer before hitting Ctrl-Z to quit logging...

The little script earlier (if [ "$output" != "" ] ; then ...) is intended to keep reading the port, which mostly returns nothing, and only write output when the input is not blank.

If you put your awk or sed conversion inside the if clause, then it should write your file. The command sync (which is run regularly by Linux) will force a file synchronisation, but should not be necessary.

You would just leave this process running, and monitor it from a separate terminal. The command tail -f will display the end of a file, following and additions or changes to it.

---

### Post by Garyu on 2010-06-04
> **StuartN said:**
> The command sync (which is run regularly by Linux) will force a file synchronisation, but should not be necessary.

OK, will try that, thanks. But right now, I have an even bigger problem.

I added the commands to /etc/rc.local so logging would start automatically when starting the computer.

It turns out that when my loggers start sending data, it seems linux is trying to identify what it is, so it transmits some sort of data to the loggers, which makes them reply with "E01" which I assume is some sort of error. 

My logs (com1.txt etc) grow with about 500 kb per minute because of these errors. Just time - E01, time - E01... Very annoying.

Is there any way of making linux ignore the data that is transmitted on the COM-ports, but still being able to log them this way?
Maybe I can lock the COM-ports so they are only readable, not possible to transmit?

Weirdly enough, I didn't get the E01 errors before, only after I added the log commands to rc.local. But it is an error that the loggers produce when they recieve a command that they don't recognize. (I can send commands like 'P' or 'R' to get more detailed info from the loggers, but now they are obviously getting something else)

---

### Post by StuartN on 2010-06-04
> **Garyu said:**
> I added the commands to /etc/rc.local so logging would start automatically when starting the computer.

That is beyond my competence. My guess is that the port is being queried before it has been initialised, and you would need to delay the polling until after that initialisation has completed. Of course that is possible, but I don't know the details - my interest was with a wireless electricity and gas energy monitor, and very straightforward.

I puzzled over the sed command (out of contrariness - awk is perfect for the job and:

*cat /dev/ttyS0 | sed 's/\r\n/$(date +"%Y-%m-%d %H:%M:%S")\r\n/g' >> com1.txt*

should be:

*cat /dev/ttyS0 | sed **"**s/\r\n/$(date **\**+**\**"%Y-%m-%d**\** %H:%M:%S**\**")\r\n/g**"** >> com1.txt*

The single quotes prevented shell expansion, and the double quotes, plus and space within the date command all needed escaping.

---

### Post by dcstar on 2010-06-05
> **Garyu said:**
> 
.........
Weirdly enough, I didn't get the E01 errors before, **only after I added the log commands to rc.local**. But it is an error that the loggers produce when they recieve a command that they don't recognize. (I can send commands like 'P' or 'R' to get more detailed info from the loggers, but now they are obviously getting something else)

Exactly what commands? there are too many already in this thread to be so ambiguous.

---

### Post by Garyu on 2010-06-05
> **dcstar said:**
> Exactly what commands? there are too many already in this thread to be so ambiguous.

This is what I added to rc.local
```
cat /dev/ttyS0 | awk '{print strftime("%Y-%m-%d %H:%M:%S %z"), $0; }' >> /home/user/com1.txt
cat /dev/ttyS1 | awk '{print strftime("%Y-%m-%d %H:%M:%S %z"), $0; }' >> /home/user/com2.txt
cat /dev/ttyS2 | awk '{print strftime("%Y-%m-%d %H:%M:%S %z"), $0; }' >> /home/user/com3.txt
cat /dev/ttyS3 | awk '{print strftime("%Y-%m-%d %H:%M:%S %z"), $0; }' >> /home/user/com4.txt
```
But surely, that shouldn't cause any outgoing traffic on the com ports? So it has to be something else that has happened.
The actual time-stamping and logging to files works great with this though. It's just that something is writing to the com-ports so that the loggers send error codes back because communication is not understood.

---

### Post by StuartN on 2010-06-05
> **Garyu said:**
> This is what I added to rc.local

Personally, I would put my commands in a script. I would also try to filter out all the blanks, and only write when receiving a non-blank result:

```
output=$(cat /dev/ttyS0)
if [ "$output" != "" ] ; then
  sleep 1
  output=$output$(cat /dev/ttyS0)
  echo "$(date +%y-%m-%d\ %H:%M:%S): $output" >> com1.txt
fi

output=$(cat /dev/ttyS1) ...
```

That should be easy to call from a timed loop, or cron.

---

### Post by Garyu on 2010-06-05
> **StuartN said:**
> Personally, I would put my commands in a script. I would also try to filter out all the blanks, and only write when receiving a non-blank result

How can you be sure that you won't get one line per character? I don't want to timestamp every character that is transmitted, only full lines that are recieved.

Since what I have seems to work well for logging, I see no obvious reason to change it. I just need to figure out why something is sending outgoing data on the COM-ports and how to avoid that.

---

### Post by Garyu on 2010-06-09
Again, after googling around, but not having tried it on my linux system because it is unpractical to gain access right now, I may have found a solution (if anyone is interested in this thread, or if anyone would like to persuade me not to use it):
```
chattr +i /dev/ttyS0
```
This will prevent anyone, including root user, to write to the serial port. So, that should mean that it is impossible to transmit data to my serial devices. Since I am only interested in reading, I am hoping that this will be the fix for my problem. Remains to be tested.

---

### Post by Garyu on 2010-06-14
chattr +i /dev/ttyS0 gives the following error:
Operation not supported while reading flags on /dev/ttyS0

Creating a lock-file with:
echo 1 > /var/lock/ttyS0
makes no difference what-so-ever.

chmod 444 /dev/ttyS0
seems to work in so far that pinging out on the COM-port with "echo 1 > /dev/ttyS0" gives the error "permission denied" or similar, even as root. But as soon as data is being recieved, something is still trying to send out data on the COM-port and ruining everything for me.

cat /dev/ttyS0
is silent at first. Until the first reading comes in. As soon as the first reading comes in, something sends out data on the com-port which confuses my equipment, making the equipment send "*E01" error code over and over and over again in what seems infinity.

Since I've got logging and timestamping working now, it is really frustrating that I haven't found a way to block outgoing traffic. Soon I'll go and cut a hardwire to make sure...

So... Question remains... How on earth do I lock the serial ports for outgoing traffic???

PS. StuartN: I've also tried your scripting, but that didn't produce anything. It just sat there silently without recording anything and without producing any output. I tried changing a few things, but I never got it to work at all, it's not even recording the spew of *E01 coming in.

---

### Post by StuartN on 2010-06-15
> **Garyu said:**
> PS. StuartN: I've also tried your scripting, but that didn't produce anything. It just sat there silently without recording anything and without producing any output. I tried changing a few things, but I never got it to work at all, it's not even recording the spew of *E01 coming in.

Well if you are getting input from cat /dev/ttyS0, then it should be easy to get the script to work. I would start by taking out the if statement, which will create a lot of output, depending on how often you are calling it:

```
output=$(cat /dev/ttyS0)
echo "$(date +%y-%m-%d\ %H:%M:%S): $output" >> com1.txt
```

---

