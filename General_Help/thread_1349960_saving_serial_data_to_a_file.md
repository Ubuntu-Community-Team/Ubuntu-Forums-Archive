---
title: "saving serial data to a file"
date: 2009-12-08
forum: General Help
---

### Post by radcom on 2009-12-08
I have some code that reads a data stream from a USB to serial converter and stores it in a text file but it stores every thing what I want is for it to delete the contents of the file before adding new data to it i.e. it the file contained "Hello12345" and "goodbye" was added the file would just have the content "goodbye" not "Hello12345goodbye" which is what the code I use at the moment does the code I use at the moment is ```
sudo cat /dev/ttyUSB0 > file.txt
``` so could I make it so it over writes the old data instead of appending to it.
Ideally I would like it to run from a prompt and not be massively complicated

---

### Post by radcom on 2009-12-08
can any one point me in the right direction?

---

### Post by Spiritof76 on 2009-12-08
Im not an expert at this but it seems that  
```
sudo cat /dev/ttyUSB0 >> file.txt
```
Should help.

---

### Post by dcstar on 2009-12-09
> **radcom said:**
> I have some code that reads a data stream from a USB to serial converter and stores it in a text file but it stores every thing what I want is for it to delete the contents of the file before adding new data to it i.e. it the file contained "Hello12345" and "goodbye" was added the file would just have the content "goodbye" not "Hello12345goodbye" which is what the code I use at the moment does the code I use at the moment is ```
sudo cat /dev/ttyUSB0 > file.txt
``` so could I make it so it over writes the old data instead of appending to it.
Ideally I would like it to run from a prompt and not be massively complicated

```
sudo cat /dev/ttyUSB0 >> file.txt | tail -1 >> file2.txt
```

---

### Post by radcom on 2009-12-09
all they do is still append to the file and the second file is empty 
and as I am still very inexperienced could some one please explain what the code dcstar's does

---

### Post by StuartN on 2009-12-09
> **radcom said:**
> all they do is still append to the file and the second file is empty 
and as I am still very inexperienced could some one please explain what the code dcstar's does

Are you sure that the data, for instance "Hello12345goodbye", is not remaining on /dev/ttyUSB0?

The command **cat /dev/ttyUSB0 > file.txt** rewrites a completely new file.txt, whereas **>> file.txt** appends to an existing file.txt. If file.txt contains "Hello12345" after your first run and "Hello12345goodbye" after the second, then it is likely that this string is still in the input buffer. Running **sync** in between calls to cat may flush the buffer.

```
sudo sync && cat /dev/ttyUSB0 >> file.txt && tail -1 file1.txt >> file2.txt
```

Slightly amending this command, synchronises (flushes) buffers, appends the /dev/ttyUSB0 stream to file1.txt and then sends the last line (tail -1) to file2.txt.

---

### Post by radcom on 2009-12-09
I'm getting my data from a current cost energy meter the data it outputs is in an xml format the other thing was for some thing else I was hoping to make work the same way using the same code, but this current cost meter is much more important and I will sort the other thing out when I'm less busy. 
The structure of the data sent can be viewed at [[COLOR="Blue"]http://www.currentcost.com/cc128/xml.htm[/COLOR]]("http://www.currentcost.com/cc128/xml.htm") if that helps, 
ideally each type of history would go to a different file and would be over written with the new replacement data for example all the data arriving every 6 seconds is written to file 1, the data arriving every 10 seconds is written to file 2. and so on, and would it be possible to have some sort of output to terminal to show it is working?

Please ask if I have explained badly or you need clearer explanation

---

### Post by StuartN on 2009-12-10
> **radcom said:**
> ideally each type of history would go to a different file and would be over written with the new replacement data for example all the data arriving every 6 seconds is written to file 1, the data arriving every 10 seconds is written to file 2.

You didn't answer if repeated calls to **cat /dev/USBtty0** duplicate the same messages, and whether **sync** eliminates that problem if you have it.

Here is an answer to the message logging, it is really clunky coding, but it does the job. Some awkist may be along with a neater solution.

```
# Read some input to the buffer from the serial port
cat $input >> $buffer

input="/dev/USBtty0"
buffer="Message_buffer.txt"
next="Message_next.txt"
temp="Message_temp.txt"

# Pop the first message out of the buffer
# This cuts the buffer into head (one message) and tail (everything else)
# and puts the tail back into the buffer
line=`grep -n -m 1 "</msg>" $buffer | cut -d: -f1`
head -$line $buffer > $next
tail --lines=+$(( $line + 1 )) $buffer > $temp
mv $temp $buffer

# If the popped message is a history message, add to hisory
# otherwise add to (replace?) live messages
if grep \<hist\> $next ; then
 cat $next >> history.txt ;
 else cat $next >> live.txt ;
fi
```

---

### Post by radcom on 2009-12-10
repeated calls to cat /dev/USBtty0 do not duplicate the values so data is not getting trapped in the buffer

and how do I use the code in the previous post just copy it into a text file and mark it as executable the run it from terminal or some thing else?

turns out that sudo cat /dev/ttyUSB0 > file.txt was working exactly as it should have been working i.e. when sudo cat /dev/ttyUSB0 > file.txt was entered and ran it then stoped with Ctrl + c and run again it did indeed over write the old data in the file, the reason I thought it wasn't working was because I entered sudo cat /dev/ttyUSB0 > file.txt once and left it running instead of stopping it and starting it every 6 seconds which is  what would have needed to do to get the results I was expecting but that is not what I wanted to have to do as it will be running on a unmanned computer 

What I would like is a script that I can set running and leave running and it does all the splitting and logging as and when the data arrives from the meter (every 6 seconds for the main data and every 10 seconds for the historical)

---

### Post by radcom on 2009-12-11
Any ideas?

---

