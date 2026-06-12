---
title: "Any hack/option somewhere to pop up new Empathy messages?"
date: 2010-05-14
forum: General Help
---

### Post by murderslastcrow on 2010-05-14
I don't like having to click twice to do what I had happen automatically in Pidgin- that is, open up my new messages in Empathy. It's just cumbersome- is there any hack or option for this, or should I merely go back to Pidgin for now?

I really like Empathy, but this is just annoying. :|

---

### Post by murderslastcrow on 2010-05-15
Huh, I guess I'll just wishlist it if possible. I'm too lazy to figure out how to code it in myself at the moment. *sigh*

---

### Post by johnnyrevell on 2011-09-15
Try this (needs wmctrl)- I set it to run every minute in cron (note username in cron line):

```

#get dispay of user - 1st check is not xrdp/vnc user
dpl=`ps aux | grep -i Xvn | grep $1 | grep -v grep | cut -c71-73 | sed -e 's/  *$//'`
#if not found default to display 0
if [ -z $dpl ] ; then
dpl=":0"
fi
export DISPLAY=$dpl #set display

for i in {0..11} ; 
do
 for pid in `wmctrl -p -l | grep -i unread | cut -c 15-21` ; #look for pid of processes with unread in title
 do 
 if [ `ps -p $pid -o comm=` == "empathy" ] ; then #if process is empathy
 wmctrl -i -a `wmctrl -lp | grep unread | grep $pid | cut -c1-10` #bring to front
 fi
 done
 sleep 5 #run check for unread messages every 5 seconds
done

```

crontab line:
*/1 *  *   *   *     bash /usr/bin/unread.sh [USERNAME OF ACCOUNT TO CHECK]
e.g.
*/1 *  *   *   *     bash /usr/bin/unread.sh david

---

### Post by brainhammer on 2012-07-19
Edit &#10140; Preferences &#10140; General &#10140; Behavior &#10140; Uncheck Display incoming events in notification area.

Hope this will solve the issue.
found on this page:
[http://askubuntu.com/questions/22292/get-chat-empathy-to-pop-up-when-people-are-talking-to-me](http://askubuntu.com/questions/22292/get-chat-empathy-to-pop-up-when-people-are-talking-to-me)

---

