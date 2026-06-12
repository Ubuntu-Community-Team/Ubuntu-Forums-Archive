---
title: "Need Help With Crontab"
date: 2011-05-07
forum: General Help
---

### Post by TheAlexCole on 2011-05-07
Okay, so I want to play different chimes from 7AM to 7PM. I've read tutorials on what to do in crontab, but it still isn't working. I think I've messed up on the path; but I'm not sure. The files I'm trying to play are in my downloads folder. Heres my crontab:

crontab -l
* 07 * * * root play alex/downloads/chimes/seven o'clock.mp3
* 08 * * * root play alex/downloads/chimes/eight o'clock.mp3
* 09 * * * root play alex/downloads/chimes/nine o'clock.mp3
* 10 * * * root play alex/downloads/chimes/ten o'clock.mp3
* 11 * * * root play alex/downloads/chimes/eleven o'clock.mp3
* 12 * * * root play alex/downloads/chimes/twelve o'clock.mp3
* 13 * * * root play alex/downloads/chimes/one o'clock.mp3
* 14 * * * root play alex/downloads/chimes/two o'clock.mp3
* 15 * * * root play alex/downloads/chimes/three o'clock.mp3
* 16 * * * root play alex/downloads/chimes/four o'clock.mp3
* 17 * * * root play alex/downloads/chimes/five o'clock.mp3
* 18 * * * root play alex/downloads/chimes/six o'clock.mp3
* 19 * * * root play alex/downloads/chimes/seven o'clock.mp3

Thanks in Advance,
-Cole

---

### Post by yetiman64 on 2011-05-07
I'll give you an example of my users crontab to compare with. 

```
# m h  dom mon dow   command
00 06 * * *   play "/home/<u-name>/Sounds/Time/01-6_am.wav"  
30 06 * * *   play "/home/<u-name>/Sounds/Time/02-6_30_am.wav"
00 07 * * *   play "/home/<u-name>/Sounds/Time/03-7_am.wav"
30 07 * * *   play "/home/<u-name>/Sounds/Time/04-7_30_am.wav"
00 08 * * *   play "/home/<u-name>/Sounds/Time/05-8_am.wav"
30 08 * * *   play "/home/<u-name>/Sounds/Time/06-8_30_am.wav"
00 09 * * *   play "/home/<u-name>/Sounds/Time/07-9_am.wav"
30 09 * * *   play "/home/<u-name>/Sounds/Time/08-9_30_am.wav"
00 10 * * *   play "/home/<u-name>/Sounds/Time/09-10_am.wav"
30 10 * * *   play "/home/<u-name>/Sounds/Time/10-10_30_am.wav"
00 11 * * *   play "/home/<u-name>/Sounds/Time/11-11_am.wav"
30 11 * * *   play "/home/<u-name>/Sounds/Time/12-11_30_am.wav"
00 12 * * *   play "/home/<u-name>/Sounds/Time/13-12_pm.wav"
30 12 * * *   play "/home/<u-name>/Sounds/Time/14-12_30_pm.wav"
00 13 * * *   play "/home/<u-name>/Sounds/Time/15-1_pm.wav"
30 13 * * *   play "/home/<u-name>/Sounds/Time/16-1_30_pm.wav"
00 14 * * *   play "/home/<u-name>/Sounds/Time/17-2_pm.wav"
30 14 * * *   play "/home/<u-name>/Sounds/Time/18-2_30_pm.wav"
00 15 * * *   play "/home/<u-name>/Sounds/Time/19-3_pm.wav"
30 15 * * *   play "/home/<u-name>/Sounds/Time/20-3_30_pm.wav"
00 16 * * *   play "/home/<u-name>/Sounds/Time/21-4_pm.wav"
30 16 * * *   play "/home/<u-name>/Sounds/Time/22-4_30_pm.wav"
00 17 * * *   play "/home/<u-name>/Sounds/Time/23-5_pm.wav"
30 17 * * *   play "/home/<u-name>/Sounds/Time/24-5_30_pm.wav"
00 18 * * *   play "/home/<u-name>/Sounds/Time/25-6_pm.wav"
30 18 * * *   play "/home/<u-name>/Sounds/Time/26-6_30_pm.wav"
00 19 * * *   play "/home/<u-name>/Sounds/Time/27-7_pm.wav"
30 19 * * *   play "/home/<u-name>/Sounds/Time/28-7_30_pm.wav"
00 20 * * *   play "/home/<u-name>/Sounds/Time/29-8_pm.wav"
30 20 * * *   play "/home/<u-name>/Sounds/Time/30-8_30_pm.wav"
00 21 * * *   play "/home/<u-name>/Sounds/Time/31-9_pm.wav"
30 21 * * *   play "/home/<u-name>/Sounds/Time/32-9_30_pm.wav"
00 22 * * *   play "/home/<u-name>/Sounds/Time/33-10_pm.wav"
```When in use it announces the time every half hour between 6 am and 10 pm. The wave files are stored in a folder in my home directory (I have replaced my real user name with <u-name> for posting this here).

I note the first field for minutes has been left as a * in your crontab (Is that your crontab or roots btw? Every user on the system will have their own crontab) in my example note the 00 for on each hour and 30 for on each half hour.

Just for extra info, to edit your crontab use,

```
crontab -e
```And to edit roots crontab use,

```
sudo crontab -e
```It works so well here it actually gets annoying and I end up commenting out (#) each of the lines to keep it quiet, when I need reminding of the time its very easy to go back and uncomment the lines. 

Hope you can find some useful info in this to get it working. :smile:

yetiman64

P.S. I am assuming you have the "**sox**" package installed to use the "**play**" command, otherwise that could also stop it.

**Edit: **I would also suggest you don't leave spaces in the filenames (or enclose the path in quotes like in my example), and consider replacing the apostrophes, it may help. eg.

You currently have:
```
* 19 * * * root play alex/downloads/chimes/seven o'clock.mp3
```Try something like,
```
00 19 * * * play "/home/alex/Downloads/chimes/seven-o_clock.mp3"
```You will need to rename all your files and change the crontab to suit. 

Make sure you do this in your user crontab not root's.

**Edit 2**: The Downloads folder uses a capital "D" in Downloads, paths are case sensitive. eg **/home**/alex/**D**ownloads.

---

### Post by TheAlexCole on 2011-05-07
It is my crontab, so since it is I imagine I don't have to put root as the user controlling it? I renamed/updated it; and even installed the sox package (in synaptic package manager). Here's what I got so far:

> 00 07 * * * play /home/alex/downloads/Chimes/seven-chime.mp3
00 08 * * * play /home/alex/downloads/Chimes/eight-chime.mp3
00 09 * * * play /home/alex/downloads/Chimes/nine-chime.mp3
00 10 * * * play /home/alex/downloads/Chimes/ten-chime.mp3
00 11 * * * play /home/alex/downloads/Chimes/eleven-chime.mp3
00 12 * * * play /home/alex/downloads/Chimes/twelve-chime.mp3
00 13 * * * play /home/alex/downloads/Chimes/one-chime.mp3
00 14 * * * play /home/alex/downloads/Chimes/two-chime.mp3
00 15 * * * play /home/alex/downloads/Chimes/three-chime.mp3
00 16 * * * play /home/alex/downloads/Chimes/four-chime.mp3
00 17 * * * play /home/alex/downloads/Chimes/five-chime.mp3
00 18 * * * play /home/alex/downloads/Chimes/six-chime.mp3
00 19 * * * play /home/alex/Downloads/Chimes/seven-chime.mp3

Thanks,
-Cole

---

### Post by dino99 on 2011-05-07
take note that everything is case sensitive: so "Downloads" is not "downloads"

---

### Post by TheAlexCole on 2011-05-07
Ahh, thanks for reminding me. I did the bottom one, but forgot to change the other ones to a capital D. Still doesn't work though.. :(

-Cole

**Edit:**
This is my crontab file.. located in the filesystem(?)/etc folder.
> # /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
00 07	* * * 	root	/usr/bin/mpg321 /home/alex/Downloads/Chimes/seven-chime.mp3
00 08	* * * 	root	/usr/bin/mpg321 /home/alex/Downloads/Chimes/eight-chime.mp3
00 09	* * * 	root	/usr/bin/mpg321 /home/alex/Downloads/Chimes/nine-chime.mp3
00 10	* * * 	root	/usr/bin/mpg321 /home/alex/Downloads/Chimes/ten-chime.mp3
00 11	* * * 	root	/usr/bin/mpg321 /home/alex/Downloads/Chimes/eleven-chime.mp3
00 12	* * * 	root	/usr/bin/mpg321 /home/alex/Downloads/Chimes/twelve-chime.mp3
00 13	* * * 	root	/usr/bin/mpg321 /home/alex/Downloads/Chimes/one-chime.mp3
00 14	* * * 	root	/usr/bin/mpg321 /home/alex/Downloads/Chimes/two-chime.mp3
00 15	* * * 	root	/usr/bin/mpg321 /home/alex/Downloads/Chimes/three-chime.mp3
00 16	* * * 	root	/usr/bin/mpg321 /home/alex/Downloads/Chimes/four-chime.mp3
00 17	* * * 	root	/usr/bin/mpg321 /home/alex/Downloads/Chimes/five-chime.mp3
00 18	* * * 	root	/usr/bin/mpg321 /home/alex/Downloads/Chimes/six-chime.mp3
00 19	* * * 	root	/usr/bin/mpg321 /home/alex/Downloads/Chimes/seven-chime.mp3

#

I have edited this file via the terminal (gksudo nautilus) and have inputed those lines myself. It however, still does not work. I'm almost positive my paths are correct (considering I went into the terminal and typed 'mpg321 /home/alex/Downloads/Chimes/<whatever-chime>.mp3' and it played. Also, the path for the program '/usr/bin/mpg321' is correct because it opens in the terminal whenever it's typed.

I'm clueless and lost and need ALOT of help on what to do. The terminal did not help for me, so opening the file and editing it with the editor seems better to me. But still, any help is appreciated and I would appreciate it very much.

Thanks,
-Cole

---

### Post by yetiman64 on 2011-05-07
> **TheAlexCole said:**
> ...
**Edit:**
This is my crontab file.. located in the filesystem(?)**/etc folder.**


I have edited this file via the terminal (gksudo nautilus) and have inputed those lines myself.....

**This is why**, the wrong crontab fiie, I recommend you clean out the entries you have put in there, it is for system use being in /etc.

You don't actually edit a file directly as such, just use the next command 
```

crontab -e
```and input (note I have corrected the case of "D"), with sox installed this should work,
 
```
00 07 * * * play /home/alex/Downloads/Chimes/seven-chime.mp3
00 08 * * * play /home/alex/Downloads/Chimes/eight-chime.mp3
00 09 * * * play /home/alex/Downloads/Chimes/nine-chime.mp3
00 10 * * * play /home/alex/Downloads/Chimes/ten-chime.mp3
00 11 * * * play /home/alex/Downloads/Chimes/eleven-chime.mp3
00 12 * * * play /home/alex/Downloads/Chimes/twelve-chime.mp3
00 13 * * * play /home/alex/Downloads/Chimes/one-chime.mp3
00 14 * * * play /home/alex/Downloads/Chimes/two-chime.mp3
00 15 * * * play /home/alex/Downloads/Chimes/three-chime.mp3
00 16 * * * play /home/alex/Downloads/Chimes/four-chime.mp3
00 17 * * * play /home/alex/Downloads/Chimes/five-chime.mp3
00 18 * * * play /home/alex/Downloads/Chimes/six-chime.mp3
00 19 * * * play /home/alex/Downloads/Chimes/seven-chime.mp3
```
The file this command changes it stored in /var/spool/cron/crontabs and is inserted there by the above command. 

This folder /var/spool/cron/crontabs is not accessible as user, be very careful if you open it as root (nautilus-gksu package will allow you to do so though - use it with care).

Do not directly open and edit the crontabs, use the 2 (user and root) commands I pointed out in post 2. The command changes all files necessary for crontab to work.

Good luck.

---

### Post by TheAlexCole on 2011-05-07
> The file this command changes it stored in /var/spool/cron/crontabs and is inserted there by the above command. 

Whenever I save, it says- **File Name to Write: /tmp/crontab.ZUpuLO/crontab **
Is this correct or do I need to move it and if so how? 

-Cole

---

### Post by yetiman64 on 2011-05-07
> **TheAlexCole said:**
> Whenever I save, it says- **File Name to Write: /tmp/crontab.ZUpuLO/crontab **
Is this correct or do I need to move it and if so how? 

-Cole

Yes it uses the /tmp location before transferring to the crontab itself, what you are seeing is normal, also the /tmp/crontab.* name will change each time you edit (temporary literally :-))

No need to do anything but save the file, the terminal will return with a notice if the crontab is altered or not.

Edit: after you save it, try the "crontab -l" command, your changes will now be obvious. :-)

---

### Post by TheAlexCole on 2011-05-07
I see it but it still does not work. I copied exactly what you had.. and it still doesn't work. I am soo CLUELESS on what to do. :(

But Thanks So Far,
-Cole

---

### Post by yetiman64 on 2011-05-07
> **TheAlexCole said:**
> I see it but it still does not work. I copied exactly what you had.. and it still doesn't work. I am soo CLUELESS on what to do. :(

But Thanks So Far,
-Cole

My last ideas are, **double check all paths and filenames, in relation to as they actually exist in your system, are correct, including with regard to case** (one mistake anywhere and the commands are useless to crontab - this is critical) and contain no spaces (unless you enclose the whole path in quotation marks) or special characters.

> I copied exactly what you had if you copied and pasted from the browser window to the crontab editor you may have a problem. I would suggest you start afresh and follow the formatting crontab requires from its headers (# m h dom mon dow user    command) etc. Note the # in the header line is only a comment to block the line, do not copy that.

crontab is extremely finicky with regard to the command layout, but once working will stay so. Main thing is you use the crontab editor only and not directly edit files.

I am just wondering if you have returned the original file you tried editting in /etc to its original state as well. Hope this now isn't blocking you.

Edit: I just checked /etc/crontab, that shouldn't be too much of a worry if you only cleared out your changes. I just noted you are trying to run mp3s, I have been working with  .wav files. You may need to install the libsox-fmt-all or libsox-fmt-mp3 packages for mp3 support with the play command. Use Synaptic and its search box to see and read details about them.

---

### Post by TheAlexCole on 2011-05-07
I returned the original file to normal. Still not working though, I think it's permission/user issues or something?

-Cole

---

### Post by yetiman64 on 2011-05-07
> **TheAlexCole said:**
> I returned the original file to normal. Still not working though, I think it's permission/user issues or something?

-Cole
Read my edits in my last post, we posted them pretty close together, if your files and paths are correct and you own them, you are editing you crontab with this so permissions shouldn't be a worry.

---

### Post by TheAlexCole on 2011-05-07
> Edit: I just checked /etc/crontab, that shouldn't be too much of a worry if you only cleared out your changes. I justed noted you are trying to run mp3s, I have been working with .wav files. You may need to install the libsox-fmt-all or libsox-fmt-mp3 packages for mp3 support with the play command. Use Synaptic and its search box to see and read details about them.

Just got it man! Thanks for walking me through this bud, really does mean alot. I thank you so very much for helping me.. BIG kudos to you!

Cheers,
-Cole

---

### Post by yetiman64 on 2011-05-08
> **TheAlexCole said:**
> Just got it man! Thanks for walking me through this bud, really does mean alot. I thank you so very much for helping me.. BIG kudos to you!

Cheers,
-Cole

You're most welcome,
Good on you for persevering and getting it working, took me nearly three days of fighting it and researching UF for info at the time, and now I have to turn it off with commenting the lines out or it annoys me too much :lol:.

---

### Post by TheAlexCole on 2011-05-08
Haha, well I really didn't do much; I thank you for the help. I had an old clock that made a chime every hour and it broke, I miss it plus I think it helped me sleep.. haha. So hopefully I won't get tired of it.. :P

Thanks Again!
-Cole

---

