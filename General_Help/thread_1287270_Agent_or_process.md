---
title: "Agent or process"
date: 2009-10-09
forum: General Help
---

### Post by HAMON on 2009-10-09
Hi!

I was wondering if anyone out there could help a newbie, how does one check if an agent or process has stopped?

I know ps -eof displays them but how can you tell if they have started or stopped?

thanks

---

### Post by Boondoklife on 2009-10-09
Could you give a little more detail? you can use ps -Al to see what processes are running, and obviously if it is not in the list it is not running. if you're just looking to get the status of a specific app then filter the results with grep, if it doesnt return any results again it is not running.

ps -Al | grep appname

---

### Post by HAMON on 2009-10-10
Basically, a agent stops working.. how do i tell? assuming I do not know what to look for is there a specific criteria like "Stopped" or "Running"
 
is there something like "STOPPED" ect..

---

### Post by Boondoklife on 2009-10-10
Could you specify what application you are trying to find out about?

---

### Post by HAMON on 2009-10-12
let's say firefox or thunderbird.

---

### Post by Boondoklife on 2009-10-12
Maybe I am not understanding your question, if you use `ps -Al | grep firefox` you can see if there are any process of firefox running. is this not what you want?

---

### Post by HAMON on 2009-10-27
What do the colums mean?

```

4 S  1000  6560     1  0  80   0 - 13892 skb_re ?        00:00:00 chromium-browse
0 Z  1000  6607  6535  1  80   0 -     0 exit   ?        00:00:02 chromium-browse <defunct>
1 S  1000  6638  6560  7  80   0 - 29714 futex_ ?        00:00:10 chromium-browse

```

---

### Post by HAMON on 2009-10-27
```

4 S  1000  6560     1  0  80   0 - 13892 skb_re ?        00:00:00 chromium-browse
0 Z  1000  6607  6535  1  80   0 -     0 exit   ?        00:00:02 chromium-browse <defunct>
1 S  1000  6638  6560  7  80   0 - 29714 futex_ ?        00:00:10 chromium-browse

```

Now I am guessing

Column 1 Process ID
Column 2 Group Membership
Column 3 - ?
Column 4 - ?
Column 5 - ?
Column 6 - Port
Column 7 - ?
Column 8 - Memory used by app??
Column 9 - Binary file?
Column 10 - File?
Column 11 - Time of last modification
Column 12 - File?

As you can see I am really new and just want to get an understanding of the command in full so I can better use Linux.

Thank You all!

---

### Post by Anonymousable on 2009-10-27
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  19456  1804 ?        Ss   11:37   0:00 /sbin/init

```

That's the columns explained ;)

---

