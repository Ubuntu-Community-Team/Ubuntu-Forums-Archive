---
title: "restricting child's time on a pc"
date: 2009-11-18
forum: General Help
---

### Post by johnism on 2009-11-18
[COLOR=black][FONT=Verdana][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2]I know there is timekpr that will kill the internet connection. I was wondering if there was an AP that will let me allow certain websites at all times and others for certain times.[/SIZE][/FONT][/SIZE][/FONT][/FONT][/COLOR][FONT=Verdana][FONT=Verdana][SIZE=2]
[SIZE=2][FONT=Verdana][COLOR=black]So lets say my daughter can surf barbie.com from 5-6 only and Ilovemath.com at all times. Does that make more sense? So basically I can block all internet except for the sites I chose and do time blocking. [/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Verdana][COLOR=black]Thanks,[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Verdana][COLOR=black]John[/COLOR][/FONT][/SIZE]
[/SIZE][/FONT][/FONT]

---

### Post by winotree on 2009-11-18
Here is some information that may help [http://www.linux.com/archive/articles/113733](http://www.linux.com/archive/articles/113733)

---

### Post by johnism on 2009-11-18
I have seen where I can set squib and iptables but that does not seem to have the time function I was looking for and easy of use

---

### Post by kyuubi777 on 2009-11-18
this is the problem with raising nerdy kids.. they'll just disable it :D

---

### Post by pootan on 2009-11-18
Perhaps have a look through here:

[http://ubuntuforums.org/showthread.php?t=843510](http://ubuntuforums.org/showthread.php?t=843510)




I know there are add-ons for firefox also but they are easily disabled.

---

### Post by sgosnell on 2009-11-18
Do it in the router.  Most routers have access restriction tables already set up, and all you have to do is set the parameters you want.

---

### Post by lavinog on 2009-11-19
+1 on using the router's builtin filters.

Another way is to use cron to run a script that disables the sites.

---

### Post by dcstar on 2009-11-19
> **lavinog said:**
> +1 on using the router's builtin filters.

Another way is to use cron to run a script that disables the sites.

Easiest way would to write dummy entries to the hosts file so the sites redirect to your own "Your time is up!" website!

---

### Post by lavinog on 2009-11-19
> **dcstar said:**
> Easiest way would to write dummy entries to the hosts file so the sites redirect to your own "Your time is up!" website!

Except the kid could use the ip address the get around the host entry...assuming they are net savy enough...I am sure a kid that frequents barbie.com will not know this.

The goal would need to be to block all sites except for the few she has permission for.

---

### Post by BenAshton24 on 2009-11-19
You could use openDNS... I think that there is a time based filtering option. [http://www.opendns.com](http://www.opendns.com)

---

### Post by dcstar on 2009-11-19
> **lavinog said:**
> Except the kid could use the ip address the get around the host entry...assuming they are net savy enough...I am sure a kid that frequents barbie.com will not know this.

The goal would need to be to block all sites except for the few she has permission for.

A lot of web sites are hosted on shared servers and require the HTTP Header to direct to the correct site, so an IP address does not necessarily get to where you think you are going these days.

---

### Post by nothingspecial on 2009-11-19
For restricting a childs time on a pc rather than just the internet [[COLOR="Magenta"]timekpr[/COLOR]]("https://launchpad.net/timekpr/+download") is what you want.

It`s great, after an hour it just logs my kids out and they can`t log in again untill the next day.

You can set the time limit to whatever you want, different times for different days. Give them a few minutes warning so they can save homework or whatever. You can reward them and give them extra time or take time away if needed.

I just set mine to log them out, no ifs, no buts. That`s it. Coz I`m an evil dad :evil:

Don`t know about what you want though.

---

### Post by Darce on 2009-11-19
+1 for OpenDNS

---

### Post by aaronp on 2009-11-19
> **johnism said:**
> [COLOR=black][FONT=Verdana][FONT=Verdana][SIZE=2][FONT=Verdana][SIZE=2]I know there is timekpr that will kill the internet connection. I was wondering if there was an AP that will let me allow certain websites at all times and others for certain times.[/SIZE][/FONT][/SIZE][/FONT][/FONT][/COLOR][FONT=Verdana][FONT=Verdana][SIZE=2]
[SIZE=2][FONT=Verdana][COLOR=black]So lets say my daughter can surf barbie.com from 5-6 only and Ilovemath.com at all times. Does that make more sense? So basically I can block all internet except for the sites I chose and do time blocking. [/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Verdana][COLOR=black]Thanks,[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Verdana][COLOR=black]John[/COLOR][/FONT][/SIZE]
[/SIZE][/FONT][/FONT]

If you use Firefox there is an extension called KidZui where you can set all kinds of preferences. Not sure about doing it by time but you could take a look.

---

### Post by Onesimus on 2009-11-19
The solution I used for my teenage son was to set up two accounts.  One for his leisure and one for his homework.  

In his homework account, I used the Firefox add-on Procon Latte to restrict all sites that weren't homework related (e.g. Facebook, YouTube, etc.).  In conjunction with timekpr - this effectively restricts his time on websites.

Hope this helps.

---

### Post by johnism on 2009-11-19
> **Onesimus said:**
> The solution I used for my teenage son was to set up two accounts. One for his leisure and one for his homework. 
 
In his homework account, I used the Firefox add-on Procon Latte to restrict all sites that weren't homework related (e.g. Facebook, YouTube, etc.). In conjunction with timekpr - this effectively restricts his time on websites.
 
Hope this helps.
 
 
Nice I like this idea

---

### Post by johnism on 2009-11-19
> **aaronp said:**
> If you use Firefox there is an extension called KidZui where you can set all kinds of preferences. Not sure about doing it by time but you could take a look.
 
this may be an option also

---

