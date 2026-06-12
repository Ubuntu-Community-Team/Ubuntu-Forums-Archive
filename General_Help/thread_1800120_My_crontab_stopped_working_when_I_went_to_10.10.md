---
title: "My crontab stopped working when I went to 10.10"
date: 2011-07-08
forum: General Help
---

### Post by Johnnycrulez on 2011-07-08
I had a cronjob that downloaded npr's totn podcast every night for me. It went like this:


/usr/bin/xterm -display :0 -bg black -fg white -e /usr/bin/curl `date +[http://pd.npr.org/anon.npr-mp3/npr/totn/%Y/%m/%Y%m%d_totn_0](http://pd.npr.org/anon.npr-mp3/npr/totn/%Y/%m/%Y%m%d_totn_0)[1-9].mp3` -o /home/tom/Documents/"file_#1.mp3" ;

Now it won't run, though. I tried running the file itself, npr.txt, from the command line and I got this error: "/usr/bin/xterm Xt error: Can't open display: :0" 

Did xterm change in between 10.04 and 10.10, or what?

---

