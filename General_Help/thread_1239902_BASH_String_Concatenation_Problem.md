---
title: "BASH String Concatenation Problem"
date: 2009-08-14
forum: General Help
---

### Post by discodan on 2009-08-14
Hi,

I have been struggling for hours with what should be a simple bash scripting issue.  I would really appreciate any and all help and suggestions.

The problem I'm having relates to bash string concatenation.

The goal of the script is as follows:

1)  Windows PCs and Servers on the lan do an ntpdate -q (from the login script) to determine the the time sync deviation from the ntp server.  The results are written to a txt file and ftp'd to the fileserver (ubuntu 9.04 server).

2)  Periodically the fileserver will run the script below to parse each of the time sync txt files and write the results to a single txt file, then email it to me.

Here's a sample of the time sync txt file coming from the PCs:

Hostname:OM3
Date:08/13/2009 21:19
server 192.43.244.18, stratum 1, offset 30.923419, delay 0.04561

Here's the code:

```
#!/bin/bash

echo "Windows Time Sync Report - "$(date) > /var/log/win_timesync.log
echo "" >> /var/log/win_timesync.log

for file in /data/ntplogs/*; do

        dt1=`cat $file | grep "Date:" | awk '{print f $1}' | tr -d "Date:"`
        echo $dt1
        dt2=`cat $file | grep "Date:" | awk '{print f $2}'`
        echo $dt2
        dt=$dt1" "$dt2
        echo $dt
        cname="`cat $file | grep "Hostname:" | tr -d "Hostname:"`"
        echo $cname
        ofst=`cat $file | grep "offset" | awk '{print f $6}' | tr -d ","`
        echo $ofst
        echo $dt" "$cname" "$ofst
        echo $dt" "$cname" "$ofst >> /var/log/win_timesync.log

        echo ""

done

```

Here's the output using the example I provided:

```


08/13/2009
21:19
08/13/2009 21:19
OM3
30.923419
 30.923419 21:19


```

What it seems like is happening, is that echo $dt" "$cname" "$ofst is somehow layering $cname **on top of** $dt then layering $ofst **on top of** the other two.

replacing the line:

```


echo $dt" "$cname" "$ofst


```

with...

```


echo $dt" "$cname


```

confirms it.  See output below:

```


08/13/2009
21:19
08/13/2009 21:19
OM3
30.923419
 OM33/2009 21:19


```

So obviously I am doing something wrong with the way i am joining these strings together, or maybe how I am defining the variables. I don't know.  I've tried various combinations of single quotes vs. double quotes.  I read the relevant sections of the "Advanced Bash Scripting Guide", as well as anything I found on google.  No luck.

Thanks to anyone who can help with this.     :confused:

-disc-

---

### Post by DaithiF on 2009-08-14
Hi,
interesting one ... i tried out your example and it worked fine for me.  I was stumped for a bit then I realised that for you the files are coming from windows, and so you have extra carriage return characters on each line.  These make their ways into your variables, and so when echo'ing a variable the 'cursor' gets reset back to the start of the line each time.

so the fix could be done several ways ... you could add another tr to each line where you extract a variable to delete the \r characters...
```
| tr -d '\r'
```
or to make the fix in just one place you can convert the file to unix line endings at the beginning of your loop:
```
sed -i 's/\r//' $file
```

cheers
d

---

### Post by discodan on 2009-08-14
Whew, Thank you, d.  My brain was really starting to hurt last night.  I knew it had to be something simple.

You are a super-star! :guitar:

Marking this one as solved.

---

