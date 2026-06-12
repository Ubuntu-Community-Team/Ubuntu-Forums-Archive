---
title: "shell script using file name"
date: 2011-01-06
forum: General Help
---

### Post by afrazin on 2011-01-06
I'm trying to create a script that will back up my databases daily, then keep a weekly version, then keep a monthly version.  I know there's a script out there that will make a mysqldump on the first of the month and call that the monthly version, but that doesn't seem right to me.  So I was thinking maybe I could put the date +%s in the file name (along with other things like the name of the db, etc) and then do some kind of if statement based off of that date in the file name in order to take the monthly (and weekly) versions.  does that make sense?  how would one do that?

thanks!

---

### Post by TeoBigusGeekus on 2011-01-06
Install Mysql Administrator (it's in the software center), run it and go to the backup option. You can arrange scheduled backups from there.

---

### Post by DaithiF on 2011-01-06
if you want to script your own you could use something like:
```
today=$(date +%Y%m%d)
day=$(date +%a)
day_of_month=$(date +%d)

if [[ $day_of_month == "01" ]]; then
        prefix="monthly"
elif [[ $day == "Mon" ]]; then
        prefix="weekly"
else
        prefix="daily"
fi

filename="database-$prefix-$today.dump"
echo "Filename is $filename"

```

---

### Post by afrazin on 2011-01-06
Teo: thank you, i'll look into that.

Daithif: that's exactly what I DON'T want.  That will create a "monthly" backup on the first of the month.  What happens if, on the 2nd of the month you realize you need to go back to your previous month's version?  you don't have it anymore because all you have in your "monthly" backup is yesterday's!

---

### Post by DaithiF on 2011-01-06
> **afrazin said:**
> Daithif: that's exactly what I DON'T want.  That will create a "monthly" backup on the first of the month.  What happens if, on the 2nd of the month you realize you need to go back to your previous month's version?  you don't have it anymore
Yes you do, its database-monthly-20101201.dump, or whatever the previous months date was.

perhaps you could explain exactly what you DO want.

---

### Post by afrazin on 2011-01-06
I'm sorry, I guess I didn't do a good job of explaining what I want.  In the end, I want a dump of the db from 30 days ago, not from the first of the month.  I could easily do that if i saved 30 days' worth of db backups, but there's got to be a better way to do it.  I was thinking that if it's possible to use the file name and say something like (in a twisted sql):
WHERE {today's date minus 30 days} >= '{first part of filename}%'

Does that make sense?  I want to compare today's date (maybe in %s) to some part of the file name to see if it's a week/month previously, and then save it.

---

### Post by drpunkerz on 2011-01-06
er, nevermind. I didn't read the entire post.

---

### Post by DaithiF on 2011-01-06
how can you do this **without** keeping 30 days worth of backup?

today is 6th Jan.  30 days ago is 7th Dec.  So you need a daily backup to exist for 7th Dec so that you can rename it to monthly.dump.  But when we get to tomorrow, 7th Jan, 30 days ago will then be 8th Dec.  So you also need a daily backup for 8th Dec...

So you need daily backups for each of the last 30 days.

Or maybe you want to rotate dumps from daily to weekly files, and then from weekly to monthly.  In that case you would have 12 dumps (7 daily, 4 weekly, 1 monthly) rather than 30, but the age of your monthly dump would vary from 28 -> 34 days.  And it would be more complicated.

---

### Post by afrazin on 2011-01-06
> **DaithiF said:**
> 
Or maybe you want to rotate dumps from daily to weekly files, and then from weekly to monthly.  In that case you would have 12 dumps (7 daily, 4 weekly, 1 monthly) rather than 30, but the age of your monthly dump would vary from 28 -> 34 days.  And it would be more complicated.

In fact, this is exactly what we were planning.  But instead of 7 daily and then 4 weekly and one monthly it turns out to be 12 days in a row, just named monthly (which is only actually 12 days old).  That's why i was thinking to use the file name to test to see if it's a month old (or two weeks).  But in either case, I think you're right.  Simple rule of thumb, huh - you need to have the thing around in order to save it!  If I don't have the backup from Dec 8 around, then tomorrow's 30-day backup simply doesn't exist.  arrrgh.  it's the simple logic that confounds me (that's not to mention the more complicated stuff like 1+1).

thanks all for letting me waste your time.  :confused:

---

