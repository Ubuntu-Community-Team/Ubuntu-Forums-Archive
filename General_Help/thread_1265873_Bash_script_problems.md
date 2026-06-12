---
title: "Bash script problems"
date: 2009-09-14
forum: General Help
---

### Post by storskogen on 2009-09-14
I want to use a little script to show my serverstatus on a webpage.

Here is the script:
```

#!/bin/bash
date > test.html
/usr/sbin/hddtemp /dev/sda1 |grep sda1 >> test.html
free -m  | grep Mem: > free
awk '{print $1 $2 $3 $4 $5}' free >> test.html
df -H | grep sda1 > df
awk '{print $1 $2 $3 $4 $5 $6}' df >> test.html
[/code

]And the output:
[code]
Sun Sep 13 21:59:41 CEST 2009 /dev/sda1: ST3400620A: 41°C Mem:970889800 /dev/sda1362G309G35G91%/media/sda1 /dev/loop03.9G3.9G0100%/media/sda1/public/iso

```NOT very nice :(

How can i preserve the normal terminal output of these commands or at least add some line-feeds
I tried using awk but can't get it right. It removes all spaces between characters.

I want it like:

```

Sun Sep 13 21:59:41 CEST 2009
/dev/sda1: ST3400620A: 41°C
Mem: 970 889 800
/dev/sda1 362G 309G 35G 91%/media/sda1

```

---

### Post by kaibob on 2009-09-14
> **storskogen said:**
> I tried using awk but can't get it right. It removes all spaces between characters.
I'm not familiar with HTML and can't help you there. Some comma's will fix the awk issue. For example, try the following in a terminal window:

> $ free -m | grep Mem: | awk '{print $1,$2,$3,$4,$5}'
Mem: 1001 533 468 0

$ df -H | grep sda1 | awk '{print $1,$2,$3,$4,$5,$6}'
/dev/sda1 27G 3.2G 24G 12% /media/windows

---

### Post by KiLaHuRtZ on 2009-09-14
Try this,...it will give you a W3C compliant web page.  Just make sure to change the variables under the comment "Set Local Variables" to your needs.  Also, you can modify line 27 to add headings / format the display of the output.  Enjoy!

```
#!/bin/bash

# Set Environment Variables
SHELL=/bin/bash
PATH=/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin

# Set Local Variables
myFilePath="/path/to/my/web/file.html"
myPageTitle="My Server Stats"
bgColor="black"
fgColor="white"

# Gather System Info
dateTime=`date`
hddTemp=`hddtemp /dev/sda1 | grep "sda1"`
memUsage=`free -mo | grep "Mem" | awk -F " " '{print $1" "$2" "$3" "$4}'`
hddUsage=`df -H /dev/sda1 | grep "sda1" | awk -F " " '{print $1" "$2" "$3" "$4" "$5" "$6}'`

# Print HTML File
echo '<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">' > "$myFilePath"
echo '<html xmlns="http://www.w3.org/1999/xhtml">' >> "$myFilePath"
echo '  <head>' >> "$myFilePath"
echo '    <meta http-equiv="content-type" content="text/html; charset=utf-8" />' >> "$myFilePath"
echo "    <title>$myPageTitle</title>" >> "$myFilePath"
echo '  </head>' >> "$myFilePath"
echo "  <body bgcolor=\"$bgColor\" text=\"$fgColor\">" >> "$myFilePath"
echo "    <font>$dateTime<br />$hddTemp<br />$memUsage<br />$hddUsage</font>" >> "$myFilePath"
echo '  </body>' >> "$myFilePath"
echo '</html>' >> "$myFilePath"

# End Of File
#eof
```

---

### Post by storskogen on 2009-09-14
Thanks for your answers, I went with the "W3C-version".

Now i want to add more to my script, (eh well, it's not mine anymore, but you understand)

I want to show the output of ps aux |grep something, after i chosen what to print with awk I want to drop the rest of the output from ps, but i can't remeber how to do that.
EDIT: I don't want the last line that always comes with ps, the actual ps i just run

---

### Post by KiLaHuRtZ on 2009-09-14
Give me an example of what you want from 'ps' and I'll give you code that will get you there. :)

---

### Post by storskogen on 2009-09-15
Question 1:
I want to use the first line in this example, and drop the last one.

```

#ps aux |grep bash

mathias  11344  0.3  0.0  20812  3624 pts/0    Ss   06:27   0:00 bash
mathias  11398  0.0  0.0   7524   904 pts/0    S+   06:28   0:00 grep bash

```

Question 2:
I think there also is a command to read the first line from "bas" and drop the "h" in the end. I think the command is looking for a "b" and then goes on until it finds a "h" (I don't know if you understand what i want :$)

---

### Post by KiLaHuRtZ on 2009-09-15
Prune it like this.

```
ps aux | grep "bash" | grep -v "grep"
```

Is that what you are looking for?

---

