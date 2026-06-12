---
title: "Log files for suspend/hibernate"
date: 2011-01-12
forum: General Help
---

### Post by hamartia on 2011-01-12
Please can anybody tell me which ubuntu log file records when a suspend happened?

I was ssh'ing into my ubuntu box periodically yesterday, when I discovered that it was no longer reachable. On getting home last night I discovered that it was still switched on, but I think in suspend mode as moving the mouse brought it back to life. The clock however, still showed 12:15pm, which is roughly when I stopped being able to ssh to it. I'd like to see the logs to confirm this.

Thanks.

---

### Post by matt_symes on 2011-01-12
Hi

```
cat /var/log/pm-suspend.log
```

Kind regards

---

### Post by hamartia on 2011-01-12
hmm, I don't have one of those. I do have a /var/log/pm-powersave.log, but this does not give event times.

Do you think my deductions are correct, or could there be another reason why I was no longer able to remotely ssh into my machine?

Thank you.

---

### Post by hamartia on 2011-01-12
hmm, I don't have one of those. I do have a /var/log/pm-powersave.log, but this does not give event times.

Do you think my deductions are correct, or could there be another reason why I was no longer able to remotely ssh into my machine?

Thank you.

---

### Post by hamartia on 2011-01-12
hmm, I don't have one of those. I do have a /var/log/pm-powersave.log, but this does not give event times.

Do you think my deductions are correct, or could there be another reason why I was no longer able to remotely ssh into my machine?

Thank you.

---

### Post by hamartia on 2011-01-12
hmm, I don't have one of those. I do have a /var/log/pm-powersave.log, but this does not give event times.

Do you think my deductions are correct, or could there be another reason why I was no longer able to remotely ssh into my machine?

Thank you.

---

### Post by hamartia on 2011-01-12
hmm, I don't have one of those. I do have a /var/log/pm-powersave.log, but this does not give event times.

Do you think my deductions are correct, or could there be another reason why I was no longer able to remotely ssh into my machine?

Thank you.

---

### Post by matt_symes on 2011-01-12
Hi

No pm-suspend.log ? You could have a look in messages, syslog, kern.log

```
sudo cat /var/log/messages | grep suspend

sudo cat /var/log/syslog | grep suspend

sudo cat /var/log/kern.log | grep suspend
```

> /var/log/pm-powersave.log

That is a different log

[https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)

Kind regards

---

### Post by matt_symes on 2011-01-12
Hi

Maybe this will help

[http://askubuntu.com/questions/2246/wake-from-hibernate-on-ssh-request](http://askubuntu.com/questions/2246/wake-from-hibernate-on-ssh-request)

Kind regards

---

### Post by hamartia on 2011-01-13
I discovered last night that my server is set to never suspend, so why my computer was unreachable, and why the clock resumed from midday when I unlocked the desktop that night are still mysteries to me.

Thanks for your help.

---

