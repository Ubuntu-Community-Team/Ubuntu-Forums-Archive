---
title: "Bash scrips integers"
date: 2010-08-11
forum: General Help
---

### Post by theevilhamster on 2010-08-11
Hi,

I have an integer in a bash script that I wish to be output as a actual value (see below). This will send control characters over a serial port to some of my devices. (I am familiar with C/C++, but am new to bash.)

For example:
```

i=10
echo $i > /dev/ttyUSB0

```
shows ASCII character "1" and ASCII character "0" (HEX 0x31 and HEX 0x30) as an output, when I want the output to be an actual value (HEX 0x0A).

I hope this is clear enough, I am not too sure how to word this.

Thanks!

---

### Post by AlphaLexman on 2010-08-11
Try putting single quotes around the variable.
```

i=10
echo '$i' > /dev/ttyUSB0

```

---

### Post by nitrogoldfish on 2010-08-11
**@AlphaLexman:** I believe that single quotes are used to tell bash what *not* to interpret, so
```
echo '$i'
```
will actually output a literal "$i"

**@theevilhamster:** to echo out a literal hex 0x0a, use this:
```
echo -e "\x0a"
```
You also may want to use the -n flag to echo to prevent it from adding a newline character to the end of the line.

Your original post also indicates that your variable, i, will be in base 10, and you want to output the hex value, implying that you need to convert dec to hex. The easiest way I've found to do this in bash is with printf, which i'm sure you're already familiar with, having C/C++ background:
```
printf '%x\n' 10
```
will output 'a'.

All together now, to get the literal hex value of a dec variable outputed to your device:
```

i=10
#get the hex
hex_i=`printf '%x' $i`
#send it down the pipe
echo -ne "\x$hex_i" > /dev/ttyUSB0

```

This will do the same thing, but it's only one line and eliminates the need for an extra variable (and is harder to read):
```

echo -ne "\x`printf '%x' $i`" > /dev/ttyUSB0

```

Also, I believe that even if given a single digit hex value, echo will output two-digit hex values. that is, echo -e "\xa" will output "0A".

Hope this helps

---

