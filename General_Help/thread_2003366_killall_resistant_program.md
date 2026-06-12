---
title: "killall resistant program"
date: 2012-06-14
forum: General Help
---

### Post by ki4jgt on 2012-06-14
So I've encountered a You have another process of Firefox running type error. To remedy the situation I usually do "sudo killall firefox" if the process isn't running it's say it's not and then I'll restart firefox. Now I can literally enter it 1,000,000 times and it'll still go back to the $ prompt and Firefox won't start either. I'm shutting down but does firefox have any more programs running in the background that need to be shutdown?

---

### Post by greenpeace on 2012-06-14
You shouldn't need sudo if you started Firefox... but as a last resort you can try: ```
killall -9 firefox
```

Be careful though... it's terminal shorthand for "really, really die, right now." and it cannot be blocked.

Have a look at the **man** pages for **kill** for more exciting examples:

```
man kill
```

(be careful)

---

### Post by Drenriza on 2012-06-14
As stated above.

When you say
```
kill process
```
or 
```
killall process
```

You tell the program "Hey please shut down".

When you do a
```
kill -9 process
```

you just strangle the process until it dies, no questions asked.

So it's a last resort.

---

### Post by greenpeace on 2012-06-14
> **Drenriza said:**
> So it's a last resort.

Well said!

If you need to check for running processes, there is also this command:

```
ps aux | grep firefox
```

This will tell you if you have any firefox processes still running

---

### Post by m_duck on 2012-06-14
> **greenpeace said:**
> ```
ps aux | grep firefox
```

This will tell you if you have any firefox processes still running

Though note that this will *also *return the PID of the above command!

---

### Post by greenpeace on 2012-06-14
> **m_duck said:**
> Though note that this will *also *return the PID of the above command!

Good point, sir... Here's some example outputs from the program to make it nice and clear:

_With_ Firefox running:
```
gp@mariachi:~$ ps aux | grep firefox
gp     21368  9.5  1.1 680924 93364 ?        Sl   11:34   0:02 /usr/lib/firefox/firefox
gp     22016  0.0  0.0   9400   932 pts/2    S+   11:35   0:00 grep --color=auto firefox
```

_Without_ Firefox running (you see the **grep** process that you're using to find Firefox):
```
gp@mariachi:~$ ps aux | grep firefox
gp     23789  0.0  0.0   9400   932 pts/2    S+   11:36   0:00 grep --color=auto firefox

```

Hope that helps!

---

### Post by zeljkojagust on 2012-06-14
One thing worth mention here (it's a big difference actually)... if you use kill you have to know PID of the process and with killall a process name is enough.
(Yeah smartass I know :) )

---

### Post by CharlesA on 2012-06-14
```
sudo kill -9 $(pidof firefox)
```

*hides*

---

### Post by roelforg on 2012-06-14
This little oneliner will kill only the first firefox process:
```

ps ax | grep firefox | sed -n '1p' | grep -v grep | cut -f1 -d" " | xargs kill -9

```

---

### Post by Azdour on 2012-06-14
Hi,

As a side note you can get this message if Firefox is not running but it's lock files have not been deleted:

[http://support.mozilla.org/en-US/kb/firefox-already-running-not-responding](http://support.mozilla.org/en-US/kb/firefox-already-running-not-responding)

This is a common issue that I come across.

---

