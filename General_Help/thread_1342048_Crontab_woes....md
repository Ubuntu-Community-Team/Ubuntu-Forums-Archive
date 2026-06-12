---
title: "Crontab woes..."
date: 2009-11-30
forum: General Help
---

### Post by rp3 on 2009-11-30
Ok,

I have been playing with this, but can't seem to make it work.

Here is what I want to do: Run a program once a night to catalog my mp3 lib and create a web page from it.  I found a neat program that does this for me, called mp3report that does exactly what I need.

So I added this line to the crontab for my user

* 3 * * * cd "/home/rp/scripts"; ./mp3data &

And I get nothing.  I added the & at the end thinking that because this takes about 5 mins to run it was failing due to this, but this didn't help.

When i run ./mp3data it works just fine?  Been fiddling with this for some time, thoughts anyone?

Thanks,

---

### Post by Jive Turkey on 2009-11-30
I'm no crontab expert either but from the look of it you want the command to run every 3 hours?

use "crontab -e"
and edit the line to look like:
```
* */3 * * * ~/scripts/mp3data &
```
and see if that works, in my experience you need the "*/" and you may need the full path to the script.  I've seen some examples where people use "> /dev/null 2> /dev/null" after the command instead of "&" and it works.

---

### Post by rp3 on 2009-11-30
> **Jive Turkey said:**
> I'm no crontab expert either but from the look of it you want the command to run every 3 hours?

use "crontab -e"
and edit the line to look like:
```
* */3 * * * ~/scripts/mp3data &
```
and see if that works, in my experience you need the "*/" and you may need the full path to the script.  I've seen some examples where people use "> /dev/null 2> /dev/null" after the command instead of "&" and it works.

I am pretty sure the way I have it will launch every night at 3am, which is what I want.  I have other scripts that CD to the correct dir then run?  I can't seem to make this work, I have also seen where you can NOHUP it like my example and that seems to work as well.  But just not for me right now?

Bummed...

---

### Post by raktarok on 2009-11-30
I don't know if I am right, but the time entries seem to be wrong for what you want to do For example, if you want it to run at exactly 3 am, and only once every night, try this line:
```
0 3 * * * /home/rp/scripts/mp3data
```
You don't need to do the 'cd' part too, I think. Make sure that the script is executable though, if you do this.

---

### Post by rp3 on 2009-12-04
> **raktarok said:**
> I don't know if I am right, but the time entries seem to be wrong for what you want to do For example, if you want it to run at exactly 3 am, and only once every night, try this line:
```
0 3 * * * /home/rp/scripts/mp3data
```
You don't need to do the 'cd' part too, I think. Make sure that the script is executable though, if you do this.

Doh, I think your on to my mistake, since I was in affect trying to run it every minute of hour 3 it was dying... I will give 
0 3 * * * a try, I bet that fixes my issue, thanks for the info..

I wasn't thinking...

---

### Post by rp3 on 2009-12-05
> **rp3 said:**
> Doh, I think your on to my mistake, since I was in affect trying to run it every minute of hour 3 it was dying... I will give 
0 3 * * * a try, I bet that fixes my issue, thanks for the info..

I wasn't thinking...

Same thing, it didn't work???  Hmmm, the file takes about 3-4 mins to run, but that shouldn't cause any issues?  Any ideas anyone?  I get a blank html file like it mp3report errored out, but when I run it local it works just fine...??

---

