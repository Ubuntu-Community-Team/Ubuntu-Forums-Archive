---
title: "Saving actual day in a terminal variable (via &quot;date&quot;)"
date: 2010-02-22
forum: General Help
---

### Post by dvdsosa on 2010-02-22
Hi all,

I'm just developing some piece of code to download files daily (via cron) from a FTP server, where the name of such files contained the date of the actual day in a format like this:
nameofthefile_0222.nc #for today's file 02->feb and 22 for 22nd

To achieve this automatically I need to get the actual date and to generate the names of that files. I have an idea of how to do this but what I don't know and can't figure out is how to save the actual day on a terminal variable, for example, using the date command in terminal which gives me the full date like next... 
lun feb 22 17:13:28 WET 2010
and then having the day saved in a variable named eg, $theday=22

Does anyone have some clue on this!?

Thank you so much in advance.
David Sosa.

---

### Post by steviefordi on 2010-02-22
```
shellvar=$(date +%d)
```

should give you today's day of the month in the variable shellvar.

```
shellvar=$(date +%m%d)
```

will give you the month and day of todays date in the variable shellvar.

```
shellvar=$(date -d '1 day ago' +%m%d)
```

will give you yesterdays month and day in variable shellvar.

Check out the manpage for the date command, and look at the +Format options which tell date how to format the output.

---

