---
title: "Changing command timeout on hard-drives"
date: 2012-01-27
forum: General Help
---

### Post by Venerence on 2012-01-27
The issue I have is that Ubuntu has a 30 second timeout on all hard-drive activity.

Now the issue with that is I do a lot of data recovery from failing hard-drives. The program I use (ddrescue) waits for a timeout before moving onto the next sector if it is bad. What this means is that the program waits for 30 seconds on every bad sector.

If there is only, say, 10 bad sectors that's not a problem. If there are 2000 bad sectors, suddenly the program becomes worthless.

I need a way to change the command timeout on hard-drives for ubuntu to, say, 3 seconds. I have looked at hdparm to do that, but as far as I can tell there is no option within the program to do that. Hours of googling have not turned up any result. Is there a way to do this, or am I stuck with using a 15 year old dos program to do all my data recovery?

---

### Post by wolfen69 on 2012-01-27
```
sudo hdparm -S 0 /dev/sdb
```
should disable timeouts. Of course, adjust /dev/sdb to *your* drives. Setting it to 1 would give a 5 second time out, 2 would be 10 seconds, etc......

---

### Post by Venerence on 2012-01-27
I had a look at that, but I don't think that applies. What I need to change is the amount of time ubuntu waits on a drive before moving on. That command changes the amount of time the drive will idle until it spins itself down.

Just in case though, I went ahead and tested it with a partially failing drive. It still does the 30 second wait, even if the standby is completely disabled.

What it should look like is an I/O timeout parameter for ubuntu.

---

### Post by Venerence on 2012-01-30
After doing some very obscure searches, I have come across the value which I think needs changing.

It is under /sys/block/sdb/device as a text file called "timeout" (the internal value is 30).

However, there is no way to change this value. Even an elevated gedit won't touch it. Also, I don't know if physically changing that text file will actually affect the drive (it may just be a report, not a configuration setting). Is there any command to change this value properly?

---

### Post by dcstar on 2012-02-01
> **Venerence said:**
> The issue I have is that Ubuntu has a 30 second timeout on all hard-drive activity.

Now the issue with that is I do a lot of data recovery from failing hard-drives. **The program I use (ddrescue) waits for a timeout before moving onto the next sector** if it is bad. What this means is that the program waits for 30 seconds on every bad sector.

If there is only, say, 10 bad sectors that's not a problem. If there are 2000 bad sectors, **suddenly the program becomes worthless**.
.........

**Only** if people don't read the MAN page about the various options that **ddrescue** can use.

---

### Post by Venerence on 2012-02-06
> **dcstar said:**
> **Only** if people don't read the MAN page about the various options that **ddrescue** can use.

Are you referring to the command that causes the program to quit if it hits too many timeouts? That will not solve my problem. If you think there's a command that will lower the timeouts associated with a bad sector, by all means let me know what it is.

---

