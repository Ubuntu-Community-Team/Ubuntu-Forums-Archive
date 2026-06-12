---
title: "How to save cron job in nano text editor?"
date: 2010-01-17
forum: General Help
---

### Post by tripler on 2010-01-17
Sorry for a very basic question. I've looked at tutorials but can't find out how to save a cron job in nano text editor.

I open crontab with 
> crontab -eThe cron job I want to save is
> wget --output-document=dwr_$(date +\%Y\%m\%d\%H\%M).gif [http://imd.gov.in/section/dwr/img/caz_chn.gif](http://imd.gov.in/section/dwr/img/caz_chn.gif)So now I've got this in nano text editor
> # m h  dom mon dow   command
wget --output-document=dwr_$(date +\%Y\%m\%d\%H\%M).gif [http://imd.gov.in/section/dwr/img/caz_chn.gif](http://imd.gov.in/section/dwr/img/caz_chn.gif)
What exactly do I do now to save the cron job? File doesn't have a Save As option,;just Open Terminal, Open Tab and New Profile. 

Thanks

---

### Post by gordintoronto on 2010-01-17
The "File" you're looking at doesn't belong to Nano, since nano is a text mode editor.  Press Ctrl-O to writeOut the file.  Also Ctrl-X to exit from nano.

If you open a terminal and enter the command:
nano trash
you will see the commands at the bottom of the window.  To learn more than you want to know about nano, man nano

---

### Post by sgosnell on 2010-01-17
Ctrl-X to exit, and nano will prompt you to save the changes, and then for a filename.

---

### Post by tripler on 2010-01-17
Thanks guys, that was a great help. I'm getting there...

---

### Post by sgosnell on 2010-01-17
Nano works, but it isn't the most intuitive editor you'll ever open.

---

### Post by mobilediesel on 2010-01-17
> **tripler said:**
> Sorry for a very basic question. I've looked at tutorials but can't find out how to save a cron job in nano text editor.

I open crontab with 
The cron job I want to save is
So now I've got this in nano text editor
What exactly do I do now to save the cron job? File doesn't have a Save As option,;just Open Terminal, Open Tab and New Profile. 

Thanks

Now that someone's said to use CTRL-o to save, how often do you want that command to run?
```
# m h dom mon dow command
0 * * * * wget --output-document=dwr_$(date +\%Y\%m\%d\%H\%M).gif http://imd.gov.in/section/dwr/img/caz_chn.gif
```
Would run it every hour.
> field	 allowed values
-----	 --------------
minute	 0-59
hour		 0-23
day of month	 1-31
month	 1-12 (or names, see below)
day of week	 0-7 (0 or 7 is Sun, or use names)

A field may be an asterisk (*), which always stands for `first-last'.

Ranges of numbers are allowed.  Ranges are two numbers separated with a
hyphen.  The specified range is inclusive.	 For example, 8-11 for an
``hours'' entry specifies execution at hours 8, 9, 10 and 11.

Lists are allowed.	 A list is a set of numbers (or ranges) separated by
commas.  Examples: `1,2,5,9', `0-4,8-12'.

Step values can be used in conjunction with ranges.  Following a range
with `/' specifies skips of the number's value through the
range.  For example, `0-23/2' can be used in the hours field to specify
command execution every other hour (the alternative in the V7 standard is
`0,2,4,6,8,10,12,14,16,18,20,22').  Steps are also permitted after an
asterisk, so if you want to say `every two hours', just use `*/2'.


I can't remember where I found that.

---

### Post by tripler on 2010-01-17
Still not quite there... This is the command I put into crontab -e in nano:
> 0,30 * * * * ~/wget --output-document=hap_$(date +\%Y\%m\%d\%H\%M).jpg [http://www10.plala.or.jp/jin_plala/hkklivec-1.jpg](http://www10.plala.or.jp/jin_plala/hkklivec-1.jpg)Next I do Ctrl x. It says:
> Save modified buffer?I do y for Yes and it says:
> File Name to Write: /tmp/crontab.nXcE94/crontabI hit Enter and it goes to a terminal prompt with the line above the prompt saying:
> crontab: installing new crontabProblem is it doesn't produce any files and var/spool/cron/crontabs is empty. If I run the command from terminal without the time part of it, i.e:
> wget --output-document=hap_$(date +\%Y\%m\%d\%H\%M).jpg [http://www10.plala.or.jp/jin_plala/hkklivec-1.jpg](http://www10.plala.or.jp/jin_plala/hkklivec-1.jpg) it creates the file ok in my home directory.

What am I doing wrong here?

---

### Post by mobilediesel on 2010-01-17
> **tripler said:**
> Still not quite there... This is the command I put into crontab -e in nano:
Next I do Ctrl x. It says:
I do y for Yes and it says:
I hit Enter and it goes to a terminal prompt with the line above the prompt saying:
Problem is it doesn't produce any files and var/spool/cron/crontabs is empty. If I run the command from terminal without the time part of it, i.e:
it creates the file ok in my home directory.

What am I doing wrong here?

Try ```
crontab -l
```
to list the crontab. If your command shows up that way then everything worked.

---

### Post by tripler on 2010-01-17
I did 
```
crontab -l
```and it returns:
```
# m h  dom mon dow   command
0,30 * * * * ~/wget --output-document=hap1_$(date +\%Y\%m\%d\%H\%M).jpg [http://www10.plala.or.jp/jin_plala/hkklivec-1.jpg](http://www10.plala.or.jp/jin_plala/hkklivec-1.jpg)

```Is that ok? Still, the fact is it should be getting a jpg file every 30 mins and it isn't getting any. Is there another way to check the command works?

---

### Post by mobilediesel on 2010-01-17
> **tripler said:**
> I did 
```
crontab -l
```and it returns:
```
# m h  dom mon dow   command
0,30 * * * * ~/wget --output-document=hap1_$(date +\%Y\%m\%d\%H\%M).jpg [http://www10.plala.or.jp/jin_plala/hkklivec-1.jpg](http://www10.plala.or.jp/jin_plala/hkklivec-1.jpg)

```Is that ok? Still, the fact is it should be getting a jpg file every 30 mins and it isn't getting any. Is there another way to check the command works?

Instead of "~/" you have to use the direct path to the script. using "$HOME" wont work from the crontab, either.

Like this:
```
0,30 * * * * /home/[COLOR="Blue"]username[/COLOR]/wget --output-document=hap1_$(date +\%Y\%m\%d\%H\%M).jpg http://www10.plala.or.jp/jin_plala/hkklivec-1.jpg
```
obviously replacing [COLOR="Blue"]username[/COLOR] with your username.

Actually you shouldn't need the /home/username at all.

```
0,30 * * * * wget --output-document=hap1_$(date +\%Y\%m\%d\%H\%M).jpg http://www10.plala.or.jp/jin_plala/hkklivec-1.jpg
```

---

### Post by BUSHYBOB on 2010-01-17
Replace ~/wget with just wget.

~/ is shorthand for your home directory.

---

### Post by iMisspell on 2010-01-17
Dont know if your the same person under a different name, but this thread might be useful to you.

[http://ubuntuforums.org/showthread.php?t=1287788](http://ubuntuforums.org/showthread.php?t=1287788)

_

---

### Post by tripler on 2010-01-17
no, I've only got one username but I have read that post, it's where I got the code from.

---

### Post by tripler on 2010-01-17
looks like it's working. Great! Thanks a lot, guys.

---

### Post by tripler on 2010-01-18
One more question. What's the correct path to make it save in a folder called "jpgs" on my home directory? I've tried:
```
*/2 * * * * /home/username/jpgs/wget --output-document=hap1_$(date +\%Y\%m\%d\%H\%M).jpg http://www10.plala.or.jp/jin_plala/hkklivec-1.jpg
```(replacing "username" with my own) and some other combinations with no luck. It works fine with nothing in front of wget, saving to home. What should the path be?

BTW I'm on ubuntu 9.04.

---

### Post by mobilediesel on 2010-01-18
> **tripler said:**
> One more question. What's the correct path to make it save in a folder called "jpgs" on my home directory? I've tried:
```
*/2 * * * * /home/username/jpgs/wget --output-document=hap1_$(date +\%Y\%m\%d\%H\%M).jpg http://www10.plala.or.jp/jin_plala/hkklivec-1.jpg
```(replacing "username" with my own) and some other combinations with no luck. It works fine with nothing in front of wget, saving to home. What should the path be?

BTW I'm on ubuntu 9.04.

For wget the path should probably be /usr/bin/wget
```
*/2 * * * * /usr/bin/wget --output-document=[COLOR="Blue"]/home/username/[/COLOR]hap1_$(date +\%Y\%m\%d\%H\%M).jpg http://www10.plala.or.jp/jin_plala/hkklivec-1.jpg
```

Use the home directory path for the output.

---

### Post by tripler on 2010-01-18
thanks, mobilediesel. That did it.

---

### Post by mobilediesel on 2010-01-18
> **tripler said:**
> thanks, mobilediesel. That did it.

I knew we'd get it eventually!

---

