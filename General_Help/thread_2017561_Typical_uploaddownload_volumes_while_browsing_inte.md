---
title: "Typical upload/download volumes while browsing internet."
date: 2012-07-05
forum: General Help
---

### Post by arroy_0209 on 2012-07-05
I am usning broaband service for connecting to internet. I am a bit suspicious looking at the amount of upload and download volumes of data provided by my ISP. Since there is an upper limit on total volume I can exchange per month, I need to know whether the values they are showing can be correct or not. If I just connect to the internet through adsl modem, open firefox, log in and promptly log out of ubuntu forum (without visiting any page/question), and disconnect the net, I am told by ubuntu log that I sent 42KB byte of data and received 300KB byte (approximately) in 0.7 minutes. Similarly if I connect to the net, open firefox, log in my gmail account and log out of it promptly, and disconnect the net, I am told that within 1.9 mimutes, I had sent 84KB data and received 1.5MB of data. (I had not opened any email in the inbox). I am suspicious since last month I was notified that my quota for the month has exhausted few days prior to the last day of the month. This happened for the first time. Do you think that the values quoted above are typical or do these show that somehow excess data are being exchanged without my notice? (e.g., I noted some add-ons were updating regularly without my notice and this must had contributed to my early problem last month. This I had corrected.) Thanks.

---

### Post by lukeiamyourfather on 2012-07-05
That sounds a little high but to be honest I've never checked what something like Gmail uses. Things like auto updates could be running in the background. Even just grabbing the lists of packages and not actually installing anything will grab a few megabytes worth of data. Where are you getting those numbers from? Are they from the ISP directly or are they from a tool running on your machine?

---

### Post by arroy_0209 on 2012-07-05
The data I have quoted are from ISP itself. I do not have any software to get these numbers from. It is difficult to prove to the ISP that something may be wrong with my connection. What should I do?

---

### Post by Cheesemill on 2012-07-06
I use vnstat to monitor my network usage:
```
sudo apt-get install vnstat
```

It's a command line program, just run 'vnstat' to see your usage. You can also use to to display how much you've used in the last 24 hour, the last month etc.
```
man vnstat
```

---

### Post by lukeiamyourfather on 2012-07-06
> **arroy_0209 said:**
> The data I have quoted are from ISP itself. I do not have any software to get these numbers from. It is difficult to prove to the ISP that something may be wrong with my connection. What should I do?

Compare their numbers with your own numbers. Install a networking monitor if your machine is the only one on the connection and keep an eye on it as you use the connection. Or some routers if you're using one keep track of cumulative bandwidth usage. vnStat a nice network traffic monitor for Linux that provides a lot of information including a history of the last hour, day, week, month, for individual network interfaces (like wired and wireless).

Note that their cycle might not coincide with your cycle of a month (or whatever the billing period is). Another network monitor that provides realtime information like if you just want to see how much bandwidth checking your Gmail uses try iptraf. It has detailed information about the current session but doesn't log history of previous sessions like vnStat.

A non-technical solution would be to find another ISP, maybe one that doesn't have such restrictive limits. I don't know the specifics of your plan or region but if you're worried about 1.5 MB of data from Gmail maybe they're not a good fit for you.

---

### Post by lukeiamyourfather on 2012-07-06
> **Cheesemill said:**
> I use vnstat to monitor my network usage:
```
sudo apt-get install vnstat
```

It's a command line program, just run 'vnstat' to see your usage. You can also use to to display how much you've used in the last 24 hour, the last month etc.
```
man vnstat
```

You beat me to it!

---

### Post by stinkeye on 2012-07-06
...also check with your ISP to see if they have any unmetered websites.
Many, like my ISP, have an Ubuntu mirror which doesn't count towards my downloads.
Then you can choose the mirror in software sources.
[ATTACH]220769[/ATTACH]


P.S. If you use vnstat you will need to start a database using
```
sudo vnstat -u -i [COLOR="Magenta"]eth0[/COLOR]
```
Using your [COLOR="magenta"]network interface[/COLOR] which can be found in
the connection manager in the panel.
[ATTACH]220770[/ATTACH]
Then to view just enter in terminal
```
vnstat
```

You may also have a look at this new app
[**_[COLOR="DarkRed"]Monitor Network Usage With Download Monitor[/COLOR]_**]("http://www.webupd8.org/2012/07/monitor-network-usage-with-download.html")

---

