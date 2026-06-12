---
title: "Conky help cant resize window"
date: 2010-11-29
forum: General Help
---

### Post by Am0s1 on 2010-11-29
Hello all this is my first post, so hi to everyone :)

My friend got me into conky and while I have never played with scripts before well editing them etc, I really liked this one 

[IMG]http://lh3.ggpht.com/_zV1MJRXGQA8/SwQYLk4kbzI/AAAAAAAAAkU/dJJI530pYC8/s800/screen.jpg[/IMG]


so I got all the required scripts etc from the talented guy who made it in his post, however it was all overlappting etc so I manually moved everything until it all fit, this conky setup has 2 configs and 3 scripts conkrc conkyw, calender lua script and weather.

my main problem is for the life of me I cannot get the size of the weather window to be right, its either too big, or the weather info is all over the place.

I wonder if someone can help me or at least point me in the right direction, I have tried to resize the window so you can see it as a seperate window but it doesnt resize at all this is what it looks like atm, its all jumbled up but I can move the items its just the window is not wide enough and too tall.

so here is how it looks atm
[http://img441.imageshack.us/i/weatherd.png/](http://img441.imageshack.us/i/weatherd.png/)

so I took off the window hints and it shows me how big the window is
[http://img413.imageshack.us/i/weatherwindowhint.png/](http://img413.imageshack.us/i/weatherwindowhint.png/)

this is how big I would like the window I did remove the script refer at the bottom of conkyw but I must be doing something wrong as it wont resize at all
[http://img26.imageshack.us/i/windowsresize.png/](http://img26.imageshack.us/i/windowsresize.png/)

excuse the png files as I was in a rush to figure out the issue

if you want me to post the conkyw config I can and thanks to anyone who can help me, am in day 3 of playing with this.

---

### Post by Habitual on 2010-11-29
"day 3 of playing with this".
Welcome to conky!!!

I recognise that layout.

Post the conkyrc files that make up this configuration. (as attachments please).

---

### Post by Am0s1 on 2010-11-29
I had to put it in a tar as the forum didnt like me uploading them, anyway I put in the scripts too tahnks for having a look

---

### Post by Am0s1 on 2010-11-30
I spoke to my friend after some hours and he gave me some help, he said it was the goto's and has limited script expreince so I looked into, anyway I found a bug which was causing my windows not to resize, and that was updating the rc file sometimes would put 2 conky into the processes and screwing everying thing up, but in my case 2 conky process for 1 window actually helped.

anyway here is the 99% finishes article 
[IMG]http://www.purelypcs.co.uk/BAsite/Julia.jpg[/IMG]


only thing I cant get working atm is the calendar

---

### Post by Habitual on 2010-11-30
Am0s1:


So, the weather has been 'fixed'?

The calendar... See my last conky desktop [here...]("http://i771.photobucket.com/albums/xx360/E522260/Desktop-Sep_24_2010.png")

I use a similar (if not the same)

Here's the rc and sh script and lang files, try it and let me know...
(Use it separately from shell conky -c horizontal_calendar)

Modify horizontal_calendar to edit the "/home/jj/Documents/Conky/Calendar/calendar.sh" to suit the path you saved calendar.sh to.

Removing line 40 will remove the Centered Date on top of the calendar bar.
Also, you'll have to adjust the gap_y 60 (line 31 of horizontal_calendar) to suit.
You have screenruler installed?

Lemme know!

Lots of help here... [Super-Thread]("http://ca.ubuntuforums.org/showthread.php?t=281865")
and at cps [(conky pitstop)]("http://conky-pitstop.wikidot.com/")

---

### Post by Am0s1 on 2010-11-30
Thx for that mate,

I did try your calendar and yeh its nice tried to incorporate it into my main .conky and I couldnt work out how to place it right again resizing issue, and then the weirdest thing happend, I was swapping between the first calendar script and yours and now when I try to run it within the main conky script I get unkwon command co and at the end of the calendar I can see {col but I checked the code and narrows it down to the script, I did use your windows rules for conky as it worked better for me.

So I decided to say hell with it and left the date year etc in nice big letters and a greeting underneath it, it looks nice so I am happy.

I must say thanks for the help you have been a diamond, I might try again with the calendar in a couple of days

---

### Post by Habitual on 2010-11-30
Am0s1:

Well, I'm glad something worked out. :)

If ya get stuck, shoot me a PM...

---

### Post by Habitual on 2010-11-30
Am0s1:

I can be of further help but I'd prefer not to do it in a forum.
Skype, or ...?

---

