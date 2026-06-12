---
title: "Launch a program from terminal for only 1 minute"
date: 2012-07-24
forum: General Help
---

### Post by IReadTheManual on 2012-07-24
How can I launch a program from terminal and have it self-issue an x11-xkilsignal after one minute of operation?

---

### Post by cortman on 2012-07-24
> **IReadTheManual said:**
> How can I launch a program from terminal and have it self-issue an x11-xkilsignal after one minute of operation?

Write a script?

```
program_name
sleep 60
kill -9 program_name
```

---

### Post by papibe on 2012-07-24
Hi IReadTheManual.

You cloud write a little script for it using job control.

This is from the top of my mind: run the command in the background, wait a minute, and then kill it:
```
#!/bin/bash
firefox &
sleep 60
kill %1
```
I hope that points you in the right direction. Let's know how it goes.
Regards.

---

### Post by honeybear on 2012-07-25
> **cortman said:**
> Write a script?

```
program_name
sleep 60
kill -9 program_name
```

you meant pkill? -9 can lead to disaster

pkill and hup to target a given process are advised.

---

### Post by honeybear on 2012-07-25
> **papibe said:**
> Hi IReadTheManual.

You cloud write a little script for it using job control.

This is from the top of my mind: run the command in the background, wait a minute, and then kill it:
```
#!/bin/bash
firefox &
sleep 60
kill %1
```
I hope that points you in the right direction. Let's know how it goes.
Regards.
You should really give better quality replies from forum staff.


This code can be improved depending on your needs.

```
#!/bin/sh

firefox "mypage" &

sleep 1000
for s in HUP INT KILL; do
    kill -$s $! &>/dev/null || break
    sleep 5
done
```


I advise: 
man sleep 
man pkill 
man kill

---

### Post by cortman on 2012-07-25
> **honeybear said:**
> you meant pkill? -9 can lead to disaster

pkill and hup to target a given process are advised.

kill -9 can lead to disaster? You do understand that the -9 flag simply means kill the process unconditionally, instead of sending a end process signal?
This would depend on the user's needs- if he absolutely MUST have it stopped after one minute, kill -9 will deliver that every time.

> **honeybear said:**
> You should really give better quality replies from forum staff.


This code can be improved depending on your needs.

```
#!/bin/sh

firefox "mypage" &

sleep 1000
for s in HUP INT KILL; do
    kill -$s $! &>/dev/null || break
    sleep 5
done
```


I advise: 
man sleep 
man pkill 
man kill

First the OP specified sleep ONE MINUTE, not 1000 seconds as you've written. I advise: read the OP. :)
I'm not sure that I understand the point of sending three different kill signals to the running program. Care to elaborate?

---

