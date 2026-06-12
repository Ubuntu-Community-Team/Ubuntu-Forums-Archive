---
title: "cron and crontab"
date: 2011-10-28
forum: General Help
---

### Post by decatur-linux on 2011-10-28
I am running Ubuntu 10.4.  I have been using the **at** command successfully and am wanting to use the **cron** command, but I am having difficulty making it work.

Here is the situation:
(1) the **cron** daemon is running. I checked it using **ps aux | grep cron** and it showed that it was running.

(2) using the command **crontab -e** I have created the following crontab file--

# m h   dom  dow  command
* 9,14 * * * wav.sh
10 9 * * * wav.sh > /home/xxx/cronout.txt

(3) I saved the file; it wrote it to **/tmp/crontab.dZRxsh/crontab**

(4) I did an **ls** command on **/tmp** and could not find the file.

(5) It never ran the crontab file and never wrote to [B]cronout.txt
[/B]

I have the follwing questions:

(1) where should the **my** crontab file exist?

(2) what am I doing wrong?

(3) how should I debug the problem?

Thanks in advance.

decatur-linux

---

### Post by WasMeHere on 2011-10-28
Hi decatur-linux,

> **decatur-linux said:**
> ...

(2) using the command **crontab -e** I have created the following crontab file--
```
[COLOR="Red"]# m  h   dom  month  dow  command
  * 9,14  *     *     *   wav.sh
 10  9    *     *     *   wav.sh > /home/xxx/cronout.txt[/COLOR]
```

(3) I saved the file; it wrote it to **/tmp/crontab.dZRxsh/crontab**

(4) I did an **ls** command on **/tmp** and could not find the file.

(5) It never ran the crontab file and never wrote to [B]cronout.txt
[/B]

I have the follwing questions:

(1) where should the **my** crontab file exist?

Don't worry about that! Just use
**crontab -e** to **e**dit and
**crontab -l** to **l**ist (view)
and have a [COLOR="Red"]clear descriptive header[/COLOR]
> 
(2) what am I doing wrong?

(3) how should I debug the problem?

Thanks in advance.
decatur-linux
The problem might be that your script does not work in the limited environment of ***cron***. I suggest that you debug by running something simple, that should be independent of the environment variables, aliases etc. For example
```

# minute  hour   dom  month  dow  command
    *      *      *     *     *   echo Hello World >> /home/xxx/cronout.txt

```
where xxx is substituted by your user id. This would append to the file every minute. And then ***gradually*** add complexity to your command!

Have fun finding out about Ubuntu :-)
Olle

---

### Post by SeijiSensei on 2011-10-28
> **decatur-linux said:**
> 
# m h   dom  dow  command
* 9,14 * * * wav.sh
10 9 * * * wav.sh > /home/xxx/cronout.txt

Specify the full directory path to wav.sh; see if that helps.

---

### Post by linuxwin2 on 2011-10-28
What you script wav.sh do.
Can you send it here.

---

