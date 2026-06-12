---
title: "run process with higher priority"
date: 2009-10-16
forum: General Help
---

### Post by viralmeme on 2009-10-16
I notice that Firefox responds faster if reniced to -15. Only root can reschedule processes. How can I get FF to startup under this priority. Currently I have to type at the bash prompt:

$ ps -e
$ sudo renice -15 ff.process.number

---

### Post by lovinglinux on 2009-10-16
```
nice -n -15 firefox
```

---

### Post by viralmeme on 2009-10-20
> **lovinglinux said:**
> ```
nice -n -15 firefox
```
Except only root can reschedule a process up ..

This works. The problem was that I was typing 'nice -15', instead of 'nice -n -15', as renice only requires a 'renice -15' and I got confused .. always read the FM ..

sudo nice -n -15 firefox

---

### Post by lovinglinux on 2009-10-20
> **ymitchell said:**
> sudo nice -n -15 firefox

I'm not sure, but that wouldn't launch firefox as root too?

Running firefox with sudo can cause lots of profile issues.

---

### Post by P4man on 2009-10-20
> **lovinglinux said:**
> I'm not sure, but that wouldn't launch firefox as root too?

Running firefox with sudo can cause lots of profile issues.

Yes and yes (it will run ff as root, which is not a good idea)

A solution can be based on this I think:
[https://lists.ubuntu.com/archives/kubuntu-users/2007-September/020275.html](https://lists.ubuntu.com/archives/kubuntu-users/2007-September/020275.html)

Replace audicity with firefox and change sudo to gksudo so you get popup asking the pw.

---

### Post by Giblet5 on 2009-10-20
*I* would add an option to /usr/bin/firefox to renice the actual binary after it has been started and detached.

Maybe "--windows3.1mode" would be appropriate.

---

### Post by viralmeme on 2009-10-20
> **lovinglinux said:**
> I'm not sure, but that wouldn't launch firefox as root too? Running firefox with sudo can cause lots of profile issues.

> **Giblet5 said:**
> *I* would add an option to /usr/bin/firefox to renice the actual binary after it has been started and detached.

Maybe "--windows3.1mode" would be appropriate.

Good idea ...

---

### Post by lovinglinux on 2009-10-20
> **ymitchell said:**
> Good idea ...

You probably need to fix Firefox profile permissions by now.

```
sudo chown -R $USER:$USER $HOME/.mozilla
```

---

