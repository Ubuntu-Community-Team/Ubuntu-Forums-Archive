---
title: "Help with wget and a changing URL"
date: 2010-07-10
forum: General Help
---

### Post by redfox1160 on 2010-07-10
Hello!

I want to download videos from a website in this format:

[COLOR="Black"]http://videos.revision3.com/revision3/web/tekzilla/0148/tekzilla--0148--5th_anniversary--large.wmv9.wmv[/COLOR]

The parts in red change each week when a new episode comes out. Here are two weeks links:

[COLOR="Black"]http://videos.revision3.com/revision3/web/tekzilla/[/COLOR][COLOR="Red"]0148[/COLOR]/tekzilla--[COLOR="Red"]0148[/COLOR]--[COLOR="Red"]5th_anniversary[/COLOR]--large.wmv9.wmv
[COLOR="Black"]http://videos.revision3.com/revision3/web/tekzilla/[/COLOR][COLOR="Red"]0147[/COLOR]/tekzilla--[COLOR="Red"]0147[/COLOR]--[COLOR="Red"]quietpc[/COLOR]--large.wmv9.wmv

Does anyone know how I can use wget to download from each weeks link automatically? I know i can make a crontab and schedule it, but I don't know how to do it when the URL changes each week. Also, this is the link where I can get the download links from: [http://revision3.com/tekzilla/feed/WMV-Large?subshow=false]("http://revision3.com/tekzilla/feed/WMV-Large?subshow=false").
Thanks!

---

### Post by redfox1160 on 2010-07-10
Currently when my cron job is set up like this:
```
0 0 * * 5 wget -A.mp4 -O /home/eric/media/videos/tekzilla.wmv http://videos.revision3.com/revision3/web/tekzilla/0148/tekzilla--0148--5th_anniversary--large.wmv9.wmv && chmod 777 /home/eric/media/videos/tekzilla.wmv
```
This should download the video every friday at midnight every week, then chage the permissions of the file to allow read, write, and execute for all users. The only problem is that I have to change the link each week, and I don't want to have to do this. Thanks again for any help.

---

### Post by DaithiF on 2010-07-10
Hi, 
this will get the grab the most recent url and store it in a file:
```
wget -q http://revision3.com/tekzilla/feed/WMV-Large?subshow=false -O - | grep "http" | grep "\.wmv" | grep "enclosure" | sed 's/^.*"http/http/;s/\.wmv".*$/.wmv/' | head -1 > lasttekzilla.url

```

then you could retrieve it like:
```
wget -O tekzilla.wmv $(cat lasttekzilla.url)

```

so you would need a couple of cron jobs, one to grab the url, and a second to download it.  You'll want to specify full paths to the tekzilla url file for the cron entries.

---

### Post by redfox1160 on 2010-07-10
> **DaithiF said:**
> Hi, 
this will get the grab the most recent url and store it in a file:
```
wget -q http://revision3.com/tekzilla/feed/WMV-Large?subshow=false -O - | grep "http" | grep "\.wmv" | grep "enclosure" | sed 's/^.*"http/http/;s/\.wmv".*$/.wmv/' | head -1 > lasttekzilla.url

```

then you could retrieve it like:
```
wget -O tekzilla.wmv $(cat lasttekzilla.url)

```

so you would need a couple of cron jobs, one to grab the url, and a second to download it.  You'll want to specify full paths to the tekzilla url file for the cron entries.

So the following cron job should work then?
```
0 0 * * 5 wget -q http://revision3.com/tekzilla/feed/WMV-Large?subshow=false -O - | grep "http" | grep "\.wmv" | grep "enclosure" | sed 's/^.*"http/http/;s/\.wmv".*$/.wmv/' | head -1 > lasttekzilla.url
1 0 * * 5 wget -O tekzilla.wmv $(cat lasttekzilla.url)
```
I think it will get the URL at 12:00, and download the file at 12:01. Thanks for the help.

---

### Post by DaithiF on 2010-07-10
Hi,
personally for anything other than a trivially simple command I would put the command into a script and call the script from cron (rather than including a complicated command in a cron entry.  It makes it easier to test outside of cron, ie. you can run the script to verify it does what it is supposed to.

I would suggest using full paths to the tekszilla url file and the output file, so something like /home/you/videos/lasttekzilla.url, etc

good luck

---

### Post by redfox1160 on 2010-07-10
> **DaithiF said:**
> Hi,
personally for anything other than a trivially simple command I would put the command into a script and call the script from cron (rather than including a complicated command in a cron entry.  It makes it easier to test outside of cron, ie. you can run the script to verify it does what it is supposed to.

I would suggest using full paths to the tekszilla url file and the output file, so something like /home/you/videos/lasttekzilla.url, etc

good luck

Could I put both commands into the same script (/usr/local/bin/tekzilla.sh):
```
#!/bin/bash
wget -q http://revision3.com/tekzilla/feed/WMV-Large?subshow=false -O - | grep "http" | grep "\.wmv" | grep "enclosure" | sed 's/^.*"http/http/;s/\.wmv".*$/.wmv/' | head -1 > /home/eric/media/videos/lasttekzilla.url
wget -O tekzilla.wmv $(cat /home/eric/media/videos/lasttekzilla.url)

```
and then make the cron job like so:
```
0 0 * * 5 tekzilla.sh
```

Again, Thanks SO much for all the help!

---

### Post by redfox1160 on 2010-07-10
Also, if I made a the following script, would it work?
```
#!/bin/bash
chmod 777 /home/eric/media/videos/tekzilla.wmv
```
Thanks!

---

### Post by redfox1160 on 2010-07-10
I tested your code, and it did not work. Here is your code with my edits (highlighted in red):
```
wget -q http://revision3.com/tekzilla/feed/WMV-Large?subshow=false -O - | grep "http" | grep "\.wmv" | grep "enclosure" | sed 's/^.*"http/http/;s/\.wmv".*$/.wmv/' | head -1 > /home/eric/media/videos/lasttekzilla.[COLOR="Red"]txt[/COLOR]
wget -O tekzilla.wmv $(cat /home/eric/media/videos/lasttekzilla.[COLOR="Red"]txt[/COLOR])
```
When the file was saved as a '.url' it did not have any value. If it is saved in a '.txt' file, it can be read with cat.

---

### Post by DaithiF on 2010-07-11
Hi,
you can put all the commands into a single script, ie. the url-grabbing command, the wget download command, and the chmod command.

the .txt vs. .url extension doesn't make any difference, file extensions have no intrinsic meaning in unix/linux, unlike windows.  The file name could by lasttekzilla.anything or indeed not have an extension at all and it will work just the same.  The only difference you may see is if using a GUI to view the files, the OS will know to open a .txt file in Gedit or similar, whereas you might need to do an 'open with...' to tell it what to use to open a differently-named file.  I don't often use a gui for file stuff so it wouldn't occur to me to name files as .txt for that reason

---

### Post by redfox1160 on 2010-07-11
> **DaithiF said:**
> Hi,
you can put all the commands into a single script, ie. the url-grabbing command, the wget download command, and the chmod command.

the .txt vs. .url extension doesn't make any difference, file extensions have no intrinsic meaning in unix/linux, unlike windows.  The file name could by lasttekzilla.anything or indeed not have an extension at all and it will work just the same.  The only difference you may see is if using a GUI to view the files, the OS will know to open a .txt file in Gedit or similar, whereas you might need to do an 'open with...' to tell it what to use to open a differently-named file.  I don't often use a gui for file stuff so it wouldn't occur to me to name files as .txt for that reason

I thought that you could do that, but when I tried running the commands individually, the .url files didn't have any content. When I ran ```
cat lasttekzilla.url
```nothing showed up. Also, when I ran the second script, an error popped up saying wget was missing a url. I may have mistyped something else, I'll have to check. Thanks again.

---

