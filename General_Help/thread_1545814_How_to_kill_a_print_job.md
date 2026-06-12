---
title: "How to kill a print job"
date: 2010-08-04
forum: General Help
---

### Post by atravnic on 2010-08-04
Hi Folks -- I accidentally submitted a print job twice. So I have this job sitting in the queue and haven't been able to figure out how to clear it. Tried system > administration > printing. Nothing there about how to clear the queue. I'm running 8.04. HELP!!!!       ...Fred

---

### Post by uRock on 2010-08-04
You can either open the printer applet if it is shown, then right click the items and cancel them or enter "lprm" in a terminal. Then to check and makes sure the jobs are cancelled, you can enter "lpstat" in a terminal.

---

### Post by rawlins02 on 2010-08-04
As a last resort, issue the command:

```

> ps -ef |grep username

```

where username is the user that submitted the print job.  The second field of the ps command, with the ef options, is the process ID. Find the print process in the list and then:

```

> kill -9 PID#

```

---

### Post by atravnic on 2010-08-05
> **uRock said:**
> ...enter "lprm" in a terminal. Then to check and make sure the jobs are canceled, you can enter "lpstat" in a terminal.

That's what I used, and it seems to have done the trick. Oddly, there was no feedback of any kind, such as 'print queue empty', or 'print job canceled'. But I'm not complaining. Thanks for your help!!!   ...Fred

---

### Post by uRock on 2010-08-05
> **atravnic said:**
> That's what I used, and it seems to have done the trick. Oddly, there was no feedback of any kind, such as 'print queue empty', or 'print job canceled'. But I'm not complaining. Thanks for your help!!!   ...Fred
If the terminal doesn't give an error, then all went well. I am glad it worked.

Cheers,
uRock

---

