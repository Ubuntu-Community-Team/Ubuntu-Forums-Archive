---
title: "Used a command in terminal..how to know it if is working?"
date: 2011-10-02
forum: General Help
---

### Post by sammya on 2011-10-02
So I used the following command to wipe my HDD completely while running UBUNTU LIVE USB.

Command:

```
sudo dd if=/dev/zero of=/dev/sda

```Nothing has seemed to happened but when I went to close the terminal it said something on the lines of "closing my terminate operation" giving the indication something was happening...?

Here is a screen shot of it in action:

[IMG]http://i55.tinypic.com/27ytj7d.png[/IMG]

---

### Post by matt_symes on 2011-10-02
Hi

dd does not give any user feedback while working unless it fails (IIRC). 

When you get the command prompt again then dd has finished.

If i am wrong about this then someone will correct me as its been ages since i used dd.

Kind regards

---

### Post by 2F4U on 2011-10-02
If you close the terminal while dd is running, you terminate dd, since it is a child process of the terminal.

---

### Post by sammya on 2011-10-02
thanks guys. any idea how long dd will take on a 250gb HDD?

cheers

---

### Post by matt_symes on 2011-10-02
Hi

It will take a while (not sure exactly how long). It's a good excuse to put the kettle on :)

Kind regards

---

### Post by JKyleOKC on 2011-10-02
> **sammya said:**
> thanks guys. any idea how long dd will take on a 250gb HDD?

cheersI use dd to create iso-format copies of setup CDs, and for an average half-gigabyte CD it usually takes 30 minutes to an hour. For a 250-GB drive I would expect it to take about 500 times that long -- and a whole week has only 168 hours in it, so a rough estimate would be about a month...

EDIT -- My son has used DBAN to wipe a much smaller drive, as I recall it was about 30 GB, and it ran for most of a day. That would probably be much faster than using dd. DBAN is a self-booting package and I think it's built on a Linux base. A Google search will turn up many sources for downloading it.

---

### Post by sammya on 2011-10-02
lol jesus christ...
tbh all i am really after is a clean hdd that is properly formatted but more thorough then what ubuntu's disk manager provides..

any tips?

---

### Post by foureyesboy on 2011-10-02
> **matt_symes said:**
> Hi

dd does not give any user feedback while working unless it fails (IIRC). 

When you get the command prompt again then dd has finished.

If i am wrong about this then someone will correct me as its been ages since i used dd.

Kind regards

There is a way to ask dd to print current I/O stats to stderr by sending a USR1 signal to it.
```
kill -USR1 pid-of-dd
```

---

### Post by sammya on 2011-10-02
> **foureyesboy said:**
> There is a way to ask dd to print current I/O stats to stderr by sending a USR1 signal to it.
```
kill -USR1 pid-of-dd
```
just put the command in. where do i go to see the results?

---

### Post by matt_symes on 2011-10-02
Hi

> **foureyesboy said:**
> There is a way to ask dd to print current I/O stats to stderr by sending a USR1 signal to it.
```
kill -USR1 pid-of-dd
```

Nice!!! Thanks for this tip.
[FONT=monospace]
```
[/FONT]kill -USR1 $(pgrep -x dd)[FONT=monospace]
```[/FONT]

I will try it out next time i use dd.

Kind regards

---

### Post by foureyesboy on 2011-10-02
> **sammya said:**
> won't that just kill the command?

Not unless you omit the -USR1 option. ;) You can do a man on dd.

---

### Post by foureyesboy on 2011-10-02
> **sammya said:**
> just put the command in. where do i go to see the results?

The stats will be printed on the terminal window that you executed the dd command.

---

