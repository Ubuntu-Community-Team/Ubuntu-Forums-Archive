---
title: "Pipe breaks when including grep or sed?"
date: 2011-01-24
forum: General Help
---

### Post by goblinlordx on 2011-01-24
I have been writing some scripts to do a simple recording of incoming data from a serial port.  I set the stty parameters for the serial port.  Then I just cat the serial port.  I am not looking to add any software to do this if at all possible.
  Doing a cat results in a file that has empty lines whenever there is a new line.  Example:

<DATA>

<DATA>

  I am would like to remove these empty lines as the data is streaming in.  To do this I attempted the following

cat /dev/ttyS0|grep -v "^$"  >> <output file>

as well as:

cat /dev/ttyS0|sed '/^$/d'  >> <output file>

  The result is nothing is sent to the output file.  If I do this without the redirection to an output file it displays exactly what I want in the terminal window. 

<DATA>
<DATA>

  For some reason, whenever I add in the sed or grep command it stops working.  Also,  I attempted to do the following:

in Script 1
...
cat /dev/ttyS0  >> <file before formatting>
...

in Script 2
...
tail -f <file before formatting> | grep -v "^$" >> <output file>
(ALSO tried: tail -f <file before formatting> | sed '/^$/d' >> <output file>
...

  All of these show what I need if I do not redirect the output in the terminal window.  None of these actually redirects the desired output to the output file (I get nothing in the output file).  Is there any "proper" way to do this?  Why exactly is the grep and sed commands breaking my pipe only when the output is redirected?

---

### Post by djeikyb on 2011-01-24
Well. I can reproduce this behaviour on Ubuntu 10.04.

1. ping -i 2 10.1.1.1 >> ping.log
2. for((i=1;i>0;i++)) do echo -e "hello world\n\n" >> ping.log; sleep 3; done
3. tail -f ping.log |grep -v "^$"
4. tail -f ping.log |grep -v "^$" >> newping.log
5. tail -f ping.log >> secondping.log

3 outputs as expected. 4 records nothing to newping.log. I thought maybe the problem was with redirecting tail -f output, but 5 works.

---

### Post by djeikyb on 2011-01-24
Aha! I don't really understand what's going on, but it has something to do with bash buffers because of the pipe and the constant data stream. I recommend reading the results of this google search further in depth:
[http://www.google.com/search?q=redirect+output+from+tail+f](http://www.google.com/search?q=redirect+output+from+tail+f)

In the meantime, your workaround is adding "--line-buffered" to your grep command. I have no idea if you need it on all your greps, in case of multiple greps. In my simple reproducing, the working line is:

tail -f ping.log |grep --line-buffered -v "^$" >> newping.log

EDIT:
This link was brief but informative:
[http://mywiki.wooledge.org/BashFAQ#BashFAQ.2BAC8-009.What_is_buffering.3F__Or.2C_why_does_my_command_line_produce_no_output:_tail_-f_logfile_.7C_grep_.27foo_bar.27_.7C_awk_...](http://mywiki.wooledge.org/BashFAQ#BashFAQ.2BAC8-009.What_is_buffering.3F__Or.2C_why_does_my_command_line_produce_no_output:_tail_-f_logfile_.7C_grep_.27foo_bar.27_.7C_awk_...)

---

### Post by goblinlordx on 2011-01-24
Awesome, thanks for the assistance.  This worked perfectly ^ ^.  It was kind of what I thought might be happening but I was confused by the output in the terminal being correct and different from what I got in the file.  The command that is working for me now is

cat $SERIAL_DEV|grep --line-buffered -v "^$" >> $OUTPUT_FILE

This corrects the problem of me having tons of unneeded empty lines spacing out my data file ^^.

---

### Post by sisco311 on 2011-01-24
Also check out the [BashPitfalls]("http://mywiki.wooledge.org/BashPitfalls#cat_file_.7C_sed_s.2BAC8-foo.2BAC8-bar.2BAC8_.3E_file") section at [http://mywiki.wooledge.org/](http://mywiki.wooledge.org/) .

You should use something like:
```
grep --line-buffered -v "^$" $SERIAL_DEV >> $OUTPUT_FILE
```

---

### Post by goblinlordx on 2011-01-24
Ah... good point about being able to grep the block file instead of piping it to a grep.  I didn't even think of that at the time.  Though, the reading and writing to same file is rather irrelevant because I am writing to a different file.  Thanks for the tip ^^.

---

